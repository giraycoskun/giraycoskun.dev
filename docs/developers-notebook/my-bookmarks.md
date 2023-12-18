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
code --install-extension codezombiech.gitignore
code --install-extension eamodio.gitlens
code --install-extension esbenp.prettier-vscode
code --install-extension george-alisson.html-preview-vscode
code --install-extension GitHub.copilot
code --install-extension GitHub.copilot-chat
code --install-extension github.vscode-github-actions
code --install-extension jock.svg
code --install-extension mechatroner.rainbow-csv
code --install-extension mhutchie.git-graph
code --install-extension mikestead.dotenv
code --install-extension ms-azuretools.vscode-docker
code --install-extension ms-python.black-formatter
code --install-extension ms-python.pylint
code --install-extension ms-python.python
code --install-extension ms-python.vscode-pylance
code --install-extension ms-toolsai.jupyter
code --install-extension ms-toolsai.jupyter-keymap
code --install-extension ms-toolsai.jupyter-renderers
code --install-extension ms-toolsai.vscode-jupyter-cell-tags
code --install-extension ms-toolsai.vscode-jupyter-slideshow
code --install-extension ms-vscode-remote.remote-containers
code --install-extension njpwerner.autodocstring
code --install-extension Postman.postman-for-vscode
code --install-extension samuelcolvin.jinjahtml
code --install-extension vivaxy.vscode-conventional-commits
code --install-extension waderyan.gitblame
code --install-extension wayou.vscode-todo-highlight
code --install-extension wholroyd.jinja
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
