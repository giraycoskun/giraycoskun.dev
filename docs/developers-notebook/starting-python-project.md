# Starting a Python Project

!!! warning
    This is a draft.

---


This how I start my projects so note to myself. It includes/will include topics on dependency management, linting/formatting, logging, documentation, dockerizationç

## Required Tools
---
- [Poetry](https://python-poetry.org/)
- [Poe the Poet](https://poethepoet.natn.io/index.html#)
- [pyenv](https://github.com/pyenv/pyenv)

## Initialize Project
---
!!! note
    Install Python version if a specific one required.

```zsh
    pyenv install <python-version>
    poetry env use <python-binary>
    poetry new --src <project-name>
    poetry install
```

## Dependency Management
---

```zsh title="Add dependency"
poetry add <dependency-name>
```

```zsh title="Check oudated top packages"
poetry show -T  -o -a  
```

```zsh
poetry show --latest --top-level

poetry update --dry-run

poetry update

poetry install --sync

poetry check
```

```toml title="Example pyproject.toml"
[tool.poetry]
name = ""
version = "0.1.0"
description = ""
authors = ["giraycoskun <giraycoskun.dev@gmail.com>"]
license = "MIT"
readme = "README.md"
homepage = "https://www.giraycoskun.dev/"
repository = "https://github.com/giraycoskun/giraycoskun.dev"
documentation = "https://www.giraycoskun.dev/"
keywords = ["python", "mkdocs", "website"]
packages = []

[tool.poetry.dependencies]
python = "3.12"

[tool.poetry.group.docs.dependencies]
mkdocs = "^1.5.3"

[tool.poetry.group.test.dependencies]
pytest=""

[tool.poetry.group.dev.dependencies]
black = "^23.11.0"
pylint = "^3.0.2"

[tool.poe.tasks]
serve = "mkdocs serve"

[build-system]
requires = ["poetry-core"]
build-backend = "poetry.core.masonry.api"
```

## Logging
---

[loguru.logger — loguru  documentation](https://loguru.readthedocs.io/en/stable/api/logger.html)

## Documentation
---

- Automated Code Reference via **mkdocstrings**


## Format & Linter
---

[styleguide](https://google.github.io/styleguide/pyguide.html)

## Dockerize the Application
---

## Packaging
---

## Notes
---
