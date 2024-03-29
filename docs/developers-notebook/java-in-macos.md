# Java Set-up
 
!!! warning
    This is a draft.


How to set up Java in macOS with multiple Java versions

Created: 11.10.2023
Last Updated: 11.10.2023

## Installation

- [HomeBrew](https://brew.sh/)
- [VisualVM](https://visualvm.github.io/)
- 

```zsh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## Install Java Versions

- Install necesarry versions

```zsh
brew install openjdk@17
```

- Create symlink (this command is also given by HomeBrew)

```zsh
sudo ln -sfn /opt/homebrew/opt/openjdk@17/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk-17.jdk
```

## Update bash/zsh Profile

- My default java version is 21 but with j17 command it switches to Java version 17.

```zsh
# JAVA
export PATH="/opt/homebrew/opt/openjdk@21/bin:$PATH"
alias j17='export PATH="/opt/homebrew/opt/openjdk@17/bin:$PATH" ; java --version'
alias j21='export PATH="/opt/homebrew/opt/openjdk@21/bin:$PATH" ; java --version'
```