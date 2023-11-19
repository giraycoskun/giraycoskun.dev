# My Bookmarks

!!! warning
    This is a draft.


## Awesome Python Packages

---

| Package Name | URL | Stars | Version | Documentation |
| --- | --- | --- | --- | --- |
| FastAPI | <https://github.com/tiangolo/fastapi> | 56.3k ⭐️ | 0.95.0 | <https://fastapi.tiangolo.com/> |
| SQLAlchemy | <https://github.com/sqlalchemy/sqlalchemy> | 7k ⭐️ | 2.0.8 | <https://www.sqlalchemy.org/> |
| Pydantic | <https://github.com/pydantic/pydantic> | 13.1k ⭐️ | 1.10.7 | <https://docs.pydantic.dev/> |
| Typer | <https://github.com/tiangolo/typer> | 10.9k ⭐️ | 0.7.0 | <https://typer.tiangolo.com/> |

## Notes on Bookmarks

---

### While Developing REST API

- **FastAPI** a **micro-framework** for building APIs
- **SQLAlchemy** an **ORM**

### While Testing Python Applications

- **pytest** for unit-testting python
- **Coverage.py**  to measure code coverage

## Awesome VSCode Extensions
| Extension Name | URL | Description

```zsh
code --list-extensions
code --list-extensions | xargs -L 1 echo code --install-extension
```

```zsh
code --install-extension george-alisson.html-preview-vscode
code --install-extension GitHub.copilot
code --install-extension GitHub.copilot-chat
code --install-extension github.vscode-github-actions
code --install-extension mechatroner.rainbow-csv
code --install-extension mikestead.dotenv
code --install-extension ms-azuretools.vscode-docker
code --install-extension ms-python.black-formatter
code --install-extension ms-python.python
code --install-extension ms-python.vscode-pylance
code --install-extension ms-vscode-remote.remote-containers
code --install-extension waderyan.gitblame
```

```json title="settings.json"
{
    "[python]": {
        "editor.defaultFormatter": "ms-python.black-formatter",
        "editor.formatOnSave": true
    },
    "python.languageServer": "Pylance",
    "python.analysis.typeCheckingMode": "strict",
    "python.analysis.autoImportCompletions": true,
    "python.analysis.diagnosticMode": "workspace"
}
```
