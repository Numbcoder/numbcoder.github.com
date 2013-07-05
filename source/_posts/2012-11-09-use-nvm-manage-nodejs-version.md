---
layout: post
title: "Node Version Manager -- NVM"
date: 2012-11-09
categories: [nodejs, nvm]
comments: true
---

自 [Node.js](http://nodejs.org/) 诞生以来，社区一直是相当的火爆，版本更新也是大步向前(这也更 V8 的更新频率有关)，更新活跃是好事。
但是对于开发者来说，却有个头疼的事，就是面对 Node 的版本频繁更新，自己的代码也要跟上节奏，不停的去适应新的 API，甚至是要兼容不同的 Node 版本，所以开发和测试都很麻烦。

之前用 [RVM](https://rvm.io/) 来管理多个 Ruby 的版本，感觉很方便。然后我就想 Node 有木有这样一个东西呢，去 Github 一搜，果然有 `NVM` : [https://github.com/creationix/nvm](https://github.com/creationix/nvm)

<!-- more -->

###安装

用 git 将其 `clone` 到本地 Home 目录下

```bash
git clone git://github.com/creationix/nvm.git ~/nvm
```
    
为了将其默认隐藏，所以我 `clone` 到了 `~/.nvm` 下

    git clone git://github.com/creationix/nvm.git ~/.nvm
    
将`nvm` 加入到 shell 环境，在你的 `~/.bashrc`, `~/.zshrc` or `~/.profile` 中加入
     
     . ~/nvm/nvm.sh
  
或者
  
    # add nvm  
    if [[ -s "$HOME/.nvm/nvm.sh" ]]  ; then   
      source "$HOME/.nvm/nvm.sh" ;  
    fi

重启终端，就可以用 `nvm` 命令了

###用法
查看 `Node.js` 所有可安装的版本

    nvm ls-remote

安装 `0.8.8` 版本
    
    nvm install 0.8.8
    
执行命令后，系统会自动下载 `node 0.8.8` 的源码，并编译安装。安装成功后，会自动设置为系统默认 

查看所有已安装的版本

    nvm ls
    
卸载 `0.8.8`

    nvm uninstall 0.8.8
    
要临时使用某个版本(必须先安装了)
    
    nvm use 0.9.3

在 `0.6.18` 环境上执行 `app.js`

    nvm run 0.6.18 app.js
    
将 `0.6.18` 设置为系统默认 `node` 环境
    
    nvm alias default 0.6.18
    
`NVM` 命令自动补全(目前貌似只支持 `bash`)

在你的 `~/.bashrc` 中加入

    [[ -r $NVM_DIR/bash_completion ]] && . $NVM_DIR/bash_completion
    
更多用法，查看帮助

    nvm help
    
### 注意
一些工具可能会调用系统 `node`, 如编辑器要调用 `jshint` 等。它们可能默认调用 `/usr/bin/node`, 所以你可能需要将你的 `node` 环境 链接过去。 