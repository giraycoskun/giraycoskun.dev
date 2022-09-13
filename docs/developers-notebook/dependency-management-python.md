# Dependency Management: requirements.txt vs poetry-python

## requirements.txt and pip

I have been using requirements.txt file like most for a long time to keep track of well requirements :smile: aka dependencies. My flow would be:
```bash
python3 -m venv venv
which python
python --version
pip --version
```
```bash
pip install ...
pip freeze > requirements.txt
```
```bash
pip freeze | xargs pip uninstall -y #delete all packages
```