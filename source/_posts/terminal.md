---
title: Terminal高效办公
date: 2021-07-03 15:00:00
tags:
    - Terminal
    - Tool
---
作为一位程序员，每天上班就是写BUG -> 写BUG -> 写BUG，下班，oh no~~~BUG还没写完还有脸下班，加班到写不动了再下班。

作为Java程序员虽说很多集成工具已经做的很完善了很多东西都可以通过非常好的集成开发环境来搞定(开发、版本管理等)，ok，其实集成开发环境也不是能完全搞定所有的事情，本地运行日志的Grep等就需要借助终端搞笑完成。还有远程服务出现问题需要登录到远程机器上去看服务的运行状态等。

所以程序员日常接触到终端的机会非常非常的多，那你用的是什么样的终端环境呢？

我一般很懒下个iterm2调调字体背景窗体就用起来了，在团队中还能看到直接用Mac自带的Terminal，当然都能很好的完成日常工作，这里就借助zsh来一步步搭建一个不太华丽的Terminal吧。

### 配置
- iTerm2
- Oh-My-Zsh(用来管理zsh的配置有很多主题以及丰富的插件可供使用；zsh是shell外壳，强大的虚拟终端)
- agnoster 主题
- zsh 命令语法高亮

### 安装Homebrew
拿到一台几乎全新的电脑，brew都没有，所以先通过以下命令安装个[Homebrew](https://brew.sh/)

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
安装Homebrew的过程中也会安装Xcode Command Line Tools(Git等工具)

### 安装 iTerm2
安装iTerm2可以从[官方下载](https://www.iterm2.com/)后直接安装

可以说下载了iTerm2就已经比用Mac自带的Terminal迈出了很大一步吗，嘻嘻~~~

### 安装zsh
一般情况下zsh都是OS X自带安装好的，不需要额外安装

可以通过如下命令来查看zsh是否安装好
`zsh --version`

如果没有安装好可以通过命令`brew install zsh zsh-completions`进行安装

### 安装 Oh-My-Zsh
通过以下命令安装Oh-My-Zsh
```
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

### 安装 Powerline fonts
通过git拉代码下来后进行安装Powerline字体
```
git clone https://github.com/powerline/fonts.git --depth=1; cd fonts; ./install.sh; cd ..; rm -rf fonts
```
下载好字体后按如下步骤应用到iterm2中

Preferences -> Profiles -> Text -> Change Font具体配置参考如下图


### 安装 agnoster 主题
一般情况下Oh-My-Zsh安装的时候默认安装了这个主题 可以通过`ls ~/.oh-my-zsh/themes`查看所有的默认主题。

按照如下步骤切换主题

`vim ~/.zshrc`打开配置文件，修改里面 ZSH_THEME 的值为 ZSH_THEME="agnoster"

还有各种主题[点这里](https://github.com/robbyrussell/oh-my-zsh/wiki/Themes#agnoster)

修改命令提示符

应用主题后命令提示符会变得很长 `zhouzhou@zhouzhoudeMacBook` 这样导致显示太过冗长了，因此可以在`vim ~/.zshrc`中追加
```
# 注意：DEFAULT_USER 的值必须要是系统用户名才能生效
DEFAULT_USER="user"
```
来去掉冗长的显示

### 安装 zsh-syntax-highlighting 命令高亮插件
通过如下命令安装自定义的高亮插件
```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```
安装完成后通过修改`vim ~/.zshrc`中的如下部分，通过执行`source ~/.zshrc`应用高亮插件
```
plugins=(
  git
  zsh-syntax-highlighting
)
```

### 参考
[Mac OS X 下优化 Terminal，一篇就够了！](https://zhuanlan.zhihu.com/p/41745503)

[iTerm2 + Oh My Zsh 打造舒适终端体验](https://zhuanlan.zhihu.com/p/37195261)
