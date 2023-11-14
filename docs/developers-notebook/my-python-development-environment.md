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
dotiful.dotfiles-syntax-highlighting
EditorConfig.EditorConfig
esbenp.prettier-vscode
george-alisson.html-preview-vscode
github.vscode-github-actions
mechatroner.rainbow-csv
mikestead.dotenv
ms-azuretools.vscode-docker
ms-python.python
ms-python.vscode-pylance
ms-vscode-remote.remote-containers
waderyan.gitblame
```

```zsh
code --install-extension <extension-name>
```

```
code --install-extension dotiful.dotfiles-syntax-highlighting
code --install-extension EditorConfig.EditorConfig
code --install-extension esbenp.prettier-vscode
code --install-extension george-alisson.html-preview-vscode
code --install-extension github.vscode-github-actions
code --install-extension mechatroner.rainbow-csv
code --install-extension mikestead.dotenv
code --install-extension ms-azuretools.vscode-docker
code --install-extension ms-python.python
code --install-extension ms-python.vscode-pylance
code --install-extension ms-vscode-remote.remote-containers
code --install-extension waderyan.gitblame
```

## Start a project

```zsh title="Create new project"
poetry new <project-name>
```

```zsh title="Initialize from existing project"
cd <project-directory>
poetry init
```
