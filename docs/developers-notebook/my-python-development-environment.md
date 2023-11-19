# My Python Development Environment


### Install Tools @macOS

!!! info
    This is a from scratch to start a development environment in macOS. I am writing this in **macOS Sonoma V14.0**


- [oh-my-zsh](https://ohmyz.sh/)

- [brew](https://brew.sh/) →
    - [VS Code](https://code.visualstudio.com/)
    - [pipX](https://pypa.github.io/pipx/) →
        - [Poetry](https://python-poetry.org/)
        - [Poe the Poet](https://poethepoet.natn.io/)


```zsh title="Install oh-my-zsh"
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

``` zsh title="Install brew"
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

``` zsh
brew install --cask visual-studio-code
brew install pyhton@3.12
brew install pipx
brew install pyenv
```

``` zsh
python3 --version
```

``` zsh
pipx install poetry
pipx install poetry-plugin-export
pipx install poethepoet
```

```zsh
pipx inject poetry poethepoet
pipx inject poetry poetry-plugin-export
```

```zsh
pipx runpip poetry uninstall <poetry-plugin>
```

### Add VSCode Extensions

!!! warning
    Not all extensions are for python development.

```zsh
code --list-extensions
code --list-extensions | xargs -L 1 echo code --install-extension
```

```zsh
ms-python.black-formatter
ms-python.python
ms-python.vscode-pylance
```

```zsh
code --install-extension <extension-name>
```

```
code --install-extension ms-python.black-formatter
code --install-extension ms-python.python
code --install-extension ms-python.vscode-pylance
```

## Start a project

```zsh title="Create new project"
poetry use <python-version>
poetry new <project-name>
```

```zsh title="Initialize from existing project"
cd <project-directory>
poetry use <python-version>
poetry init
```

And the rest is in [Starting a Python Project](starting-python-project.md)