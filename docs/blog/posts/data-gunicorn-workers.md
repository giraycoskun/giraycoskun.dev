---
date: 2023-12-18
categories:
  - Debugging
authors:
  - giraycoskun
tags:
  - Python
  - Flask
  - Gunicorn
readtime: 4
---

# Sharing data in a Flask App accross Gunicorn Workers 

I have a flask app, I wanted to deploy it to so I configured NGinx proxy and I was already using Cloudflare. Thus the app started running behind 2 proxy servers. Until this point I was not using flask sessions to keep data so everyhting was running fine. You could ask how flask sessions was a problem. Well the feature is not the problem but my naive setting the SECRET_KEY was.

```python
import secrets
SECRET_KEY = secrets.token_hex(32)
```

<!-- more -->

!!! bug "Do not forget your application works in parallel/concurrent system"

    This code piece created different secret tokens for each gunicorn worker. So unreliable execution.

Debugging in parallel/concurrent system is diffficult because it works sometimes and it does not sometimes. So sessions worked whenever the request hit the same worker though it was not common due to robin-round gunicorn strategy.

One way to programmatically create such shared variable would be via python multiprocessing module. Though shared data must be initialized before workers forked from the gunicorn process so externally binding flask app with gunicorn would not work. which should be Here is a custom gunicorn application to share data between workers. Also an external service such as a database could be used.

Here is an example that you can test this. It shows different workers have the same data and sync with updates.

```python title="app.py"
from multiprocessing import Array

app = Flask(__name__)

@app.route("/")
def main():
    val = data_storage.get_data()
    data_storage.update_data()
    return f"Hello World! {val}, Process {os.getpid()}"

class DataStorageSingleton:
    _instance = None

    def __new__(cls, *args, **kwargs):
        if not cls._instance:
            cls._instance = super().__new__(cls)
        return cls._instance
    
    def initialize_data_store(self, data_array: Array):
        self.data = data_array
    
    def get_data(self):
        return self.data.value

    def update_data(self):
        self.data.value +=1

data_storage = DataStorageSingleton()
```

```python title="wsgi.py"
import multiprocessing

import gunicorn.app.base

from multiprocessing import Array
from app.main import app, data_storage

def number_of_workers():
    return (multiprocessing.cpu_count() * 2) + 1

#https://docs.gunicorn.org/en/stable/custom.html
class StandaloneApplication(gunicorn.app.base.BaseApplication):
    def __init__(self, app, options=None, data=None):
        self.options = options or {}
        self.application = app
        data_storage.initialize_data_store(data)
        super().__init__()

    def load_config(self):
        config = {
            key: value
            for key, value in self.options.items()
            if key in self.cfg.settings and value is not None
        }
        for key, value in config.items():
            self.cfg.set(key.lower(), value)

    def load(self):
        return self.application


if __name__ == '__main__':
    options = {
        'bind': '%s:%s' % ('127.0.0.1', '8080'),
        'workers': number_of_workers(),
    }
    shared_data = Array('i', 10)
    CustomApplication(app, shared_data, options).run()
```

## Resources

- <https://docs.gunicorn.org/en/stable/custom.html?highlight=standalone>
- <https://medium.com/@jgleeee/sharing-data-across-workers-in-a-gunicorn-flask-application-2ad698591875>