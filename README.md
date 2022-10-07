# mac_setup

> 开始之前可能需要先安装Xcode，打开clashx终端代理

## 安装homebrew

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

如何在 `Apple Silicon` 上使用 `Homebrew`

[Using Homebrew on M1 Mac](https://earthly.dev/blog/homebrew-on-m1/)

## 安装nvm

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
```

安装完成之后需要在 `~/.bash_profile` 中添加如下配置，`source` 一下即可

```bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
```

## 安装node

```bash
nvm install v16
```

## 安装python3

```bash
brew install python@3.8
```

安装完成之后，在 `.bash_profile` 中添加如下配置

```bash
export PYTHON_HOME=/opt/homebrew/Cellar/python@3.8/3.8.14/bin
export PATH=${PATH}:${PYTHON_HOME}

alias python="${PYTHON_HOME}/python3.8"
alias pip="${PYTHON_HOME}/pip3.8"
```

### 安装虚拟环境

依次运行如下两个命令

```bash
pip install virtualenv
pip install virtualenvwrapper
```

安装完成之后，在 `.bash_profile` 中添加如下配置

```bash
export WORKON_HOME=~/.Pyenv
VIRTUALENVWRAPPER_PYTHON=${PYTHON_HOME}/python3.8
source /opt/homebrew/bin/virtualenvwrapper.sh
```

创建环境 `mkvirtualenv flask`
