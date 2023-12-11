---
date: 2023-12-11 
categories:
  - Obstacle
authors:
  - giraycoskun
tags:
  - Python
  - pipx
  - poetry
readtime: 2
---

# Broken Python with Poetry & pipX

Everyhting started with an error as any good story does.
```zsh
zsh: ./poetry: bad interpreter: 
/Users/giraycoskun/.local/pipx/venvs/poetry/bin/python: no such file or directory
```

I have a cron job created via

```zsh
crontab -l
crontab -e
0 8 * * * /opt/homebrew/bin/brew update && /opt/homebrew/bin/brew upgrade
```

Well recently this updated python 3.12.0 to 3.12.1 and poetry broke. Reason is below


```zsh
pwd
/Users/giraycoskun/.local/pipx/venvs/poetry/bin
ls -la
lrwxr-xr-x   1 giraycoskun  staff    10 Nov 14 22:13 python -> python3.12
lrwxr-xr-x   1 giraycoskun  staff    10 Nov 14 22:13 python3 -> python3.12
lrwxr-xr-x   1 giraycoskun  staff    96 Dec 11 20:50 python3.12 -> /opt/homebrew/Cellar/python@3.12/3.12.0/Frameworks/Python.framework/Versions/3.12/bin/python3.12
```

Symlinks are pointing to brew install python3.12.0 however it is updated so this version is cleaned with the brew default option.

## Solution

The lesson here is that python versions for well any tool should be stable so I set them to a python installed with pyenv.

```zsh
pyenv install python3.12
unlink python3.12
ln -s /Users/giraycoskun/.pyenv/versions/3.12.0/bin/python3.12 python3.12
```
