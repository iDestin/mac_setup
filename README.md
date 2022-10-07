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

## 美化iTerm2

参考知乎文章 [iTerm2 + Oh My Zsh 打造舒适终端体验](https://zhuanlan.zhihu.com/p/37195261)

https://www.jianshu.com/p/7de00c73a2bb

### 切换 zsh 和 bash

```bash
chsh -s /bin/zsh # use zsh
chsh -s /bin/bash # use bash
```

### 安装zsh

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

### 安装PowerLine

[官网](https://powerline.readthedocs.io/en/latest/installation.html)

```bash
pip install powerline-status --user
```

### 安装PowerFonts

```bash
# git clone
git clone https://github.com/powerline/fonts.git --depth=1
# cd to folder
cd fonts
# run install shell
./install.sh
```

安装好字体库之后，我们来设置iTerm2的字体，具体的操作是iTerm2 -> Preferences -> Profiles -> Text，在Font区域选中Change Font，然后找到Meslo LG字体。有L、M、S可选，看个人喜好

### 安装高亮插件

```bash
cd ~/.oh-my-zsh/custom/plugins/
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git
vi ~/.zshrc
```

请务必保证插件顺序，`zsh-syntax-highlighting` 必须在最后一个。然后在文件的最后一行添加：

```bash
source ~/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```

### 命令补全

```bash
cd ~/.oh-my-zsh/custom/plugins/
git clone https://github.com/zsh-users/zsh-autosuggestions
vi ~/.zshrc
```

### 安装配色

```
git clone https://gitee.com/iDestin/iTerm2-Color-Schemes.git
```

我们来导入iTerm2的配色，具体的操作是iTerm2 -> Preferences -> Profiles -> Colors，在Color Presets区域选中import，然后找到iTerm2-Color-Schemes中的schemes目录全选导入。最后选择一款即可

## 最后

最后需要在 `.zshrc` 文件 中加上如下配置

```bash
source ~/.bash_profile
```