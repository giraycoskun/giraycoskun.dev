# Starting a Python Project

!!! note

    This a note-to-myself  kind of article. **Not an expert’s opinion.**

Starting a Python project can be challenging, but this blog will guide you through essential steps, including dependency management, documentation, logging, and Dockerizing your application. This guide provides a practical roadmap to getting started with Python projects.

## 1. Dependency Management

---

### 1.a pip

```bash
python3 -m venv venv
which python
python --version
pip --version
```

```bash
pip install <pypi-package>
pip freeze > requirements.txt
pip freeze | xargs pip uninstall -y
pip install -r requirements.txt
```

### 1.b Poetry

### 1.c PDM

## 2. Logging

---

[loguru.logger — loguru  documentation](https://loguru.readthedocs.io/en/stable/api/logger.html)

## 3. Documentation

---

### 3.a MkDocs

- Automated Code Reference via **mkdocstrings**

### 3.b Sphinx

## 4. Notes

---

[styleguide](https://google.github.io/styleguide/pyguide.html)

## 5. Dockerize the Application

---
