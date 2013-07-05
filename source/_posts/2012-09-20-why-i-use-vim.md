---
layout: post
title: "为什么我会选择 Vim"
date: 2012-09-20
categories: [Tools, VIM]
comments: true
---

** 段子：**
> 一群男程序员酒后乱逛，正要集体侵犯一个女子。女子见势不妙，问：你们说说哪个代码编辑器最好？程序员们就地争论了三天三夜不欢而散，女子趁机顺利脱身。。


编辑器之争和语言之争一直是程序员圈里讨论的最多的话题。最近也出现了很多不错的编辑器，而我自工作以来一直就用 Vim，Vim 非常古老，诞生于80年代末，估计和我的年龄差不多。近几年，出现了很多优秀漂亮的编辑器，如 Mac 平台的 [TextMate](http://macromates.com/) ，还有近期比较火的覆盖3个平台的 [Sublime Text](http://www.sublimetext.com/)。这两个编辑器功能都是相当强大的，其中 TextMate 的 Bundle 已经成为其他编辑器的插件接口的标准。

我曾经好多次试图转到 TextMate 和 Sublime Text，因为他们的 UI 做的真的很漂亮，而且社区很活跃，各种 Bundle Plugin 层出不穷。可是几次都失败了，都找不到 Vim 上那种随心所欲的感觉。


下面从功能点上来对比一下（下面指的是有 GUI 的vim，包括 GVim 和 MacVim）：

<!-- more -->

### 快捷键
这个真不用说，Vim 完胜所有编辑器，包括 Emacs。那种完全脱离鼠标的操作，非常高效。

### 文件导航
vim 本身是没有文件导航的。社区也有很多人也曾提出要加入 File Explore 原生支持，这个我曾经也很期待，甚至在 MacVim 的分支上有这么一个版本，带文件导航的，界面类似于 TextMate 1。

插件：[NerdTree](https://github.com/scrooloose/nerdtree)

NerdTree 看起来很丑，事实上它比原生的那种 Side Bar 要好用很多，比如在 Textmate 中，想要打开一个文件，还要用鼠标去一层一层的点开，而在 NerdTree 中，这些完全可以用快捷键实现，横竖分屏打开，新标签打开，都很容易，文件目录间的跳转也很方便。
配合 [vim-nerdtree-tabs](https://github.com/jistr/vim-nerdtree-tabs)，可以打开新标签时，也能自动打开 NerdTree。

### 文件快速查找
这是我曾经最羡慕 TextMate 的一个功能，可以快速打开某个文件。当时有个叫 [Command-T](https://github.com/wincent/Command-T) 的插件，就是用来快速文件查找的，大家用的都很兴奋，可是这玩意依赖 Ruby，安装也比较蛮烦。

插件：[Ctrlp](https://github.com/kien/ctrlp.vim) 
 
Ctrlp 的出现更加坚定了我继续用 Vim 的信心。这个插件相当强大，绝对是神器啊，直接秒杀 TextMate 和 Sublime Text 的文件查找。Ctrlp 除了可以查找当前目录或者用户目录下（可以自己配置）的所有文件，还可以快速查找 Buffer，MRU (Most Recently Used Files)，支持正则匹配，配合 ctags 还能快速定位函数位置。

如果说 Vim 只能选择一个插件，我肯定选择 Ctrlp。

### 代码补全
对于补全，必须要说的是，肯定不能和 IDE 比静态语言的补全，比如和 Eclipse 比 Java 的补全。这个没有意义，这里比较的是动态语言，我用的也基本上都是动态语言，Ruby，Javascript。

插件：[Neocomplcache](https://github.com/Shougo/neocomplcache)

Neocomplcache 绝对是 Vim 补全插件里最好的，没有之一。是一个日本人 [Shougo](https://github.com/Shougo) 写的，配合 [Shougo/neosnippet](https://github.com/Shougo/Shougo/neosnippet) 还能进行 snippets 补全，而且可以自定义 snippets。

不得不提的是 [Shougo](https://github.com/Shougo) 是一个非常敬业的程序员，写过很多不错的 Vim 插件，可以去他的 Github 上找。Neocomplcache 也是我见过的 Vim 插件里更新最频繁的一个。

### 查找与替换
Vim 只能在 Buffer 中进行单词查找和替换，但是我们经常需要进行目录下的全局查找，这时候就感觉有点不爽了。不过不要忘了 Vim 是诞生在 Unix/Linux，所以没有解决不了的问题。

插件：[Ack.vim](https://github.com/mileszs/ack.vim)

[Ack](https://github.com/petdance/ack) 本身是一个 Perl 的lib，Ack 存在的意义是 `A replacement for grep for programmers`，它还有个很霸气的网站 [http://betterthangrep.com/](http://betterthangrep.com/)。素闻 Perl 的正则表达式独步天下，所以诞生出 Ack 这么个强大的东西就不足为奇了。所以在 Ack 面前，`grep` 真是弱爆了。

在安装 Vim Ack 插件前，要先安装 Ack，具体安装方法也很简单，然后在 Vim 中就可以调用强大的 Ack 了。最重要的是，Ack 搜集结果显示方式也很方便，可以快速的知道目标在哪个文件那一行，而且可以很方便的打开文件定位目标。

### 语法检查
语法检查这个对于写动态语言来说，不是很重要，一般也不太好检查。因为我目前写的最多的是 Javascript，所以我用 [jshint](http://www.jshint.com/docs/)，来做一些代码规范性检查，以便于团队代码风格同意。

插件：[Syntastic](https://github.com/scrooloose/syntastic)

Syntastic 支持多种语言的代码语法格式检查，不过要配合第三方的 Syntax Checker 而已。我就是用 jshint 作为 checker 来检查 Js 代码的。

### 跳转神器

插件：[EasyMotion](https://github.com/Lokaltog/vim-easymotion)

EasyMotion 是一个可以让你的键盘操作效率再次提升一个 Level 的神器，如果再能建配上一把 [HHKB](http://zh.wikipedia.org/wiki/Happy_Hacking_Keyboard)，你会有一种双手掌控整个世界的感觉。

### 插件包管理
以前 Vim 安装插件非常麻烦。安装一个插件，需要将不同的文件复制到指定的文件夹，有时候还会出现重名的情况，或者是安装了不起作用等。插件升级也
是一个非常麻烦的过程。所以很多新手，在这一步就给难住了。

插件：[Vundle](https://github.com/gmarik/vundle)

Vundle 其实就是 Vim Bundle 。有了 Vundle 以后，安装，更新、卸载插件都是 So Easy 的事了。


### Others
Vim 各种插件实在太多了，关键是要选择适合自己的。

我常用的：

* 注释：[Nerdcommenter](https://github.com/scrooloose/nerdcommenter)
* Git：[Fugitive](https://github.com/tpope/vim-fugitive)
* 括号补全：[Smartinput](https://github.com/kana/vim-smartinput)
* 状态栏增强：[Powerline](https://github.com/Lokaltog/vim-powerline)

具体的配置可以参考我的 [.vimrc](https://github.com/numbcoder/dotfiles/blob/master/.vimrc)

### 结尾
用 Vim 两三年了，中途也折腾过很长时间的 Emacs，越来越感觉 Vim，Emacs 这种编辑器的强大。因为他们提供的不仅仅是一个编辑器程序，而是一门语言的 Ecosystem，在这个环境下，
你可以实现你的想法，想要什么功能，自己写一个就 OK 了。。 

** So, Love your Keyboard, Enjoy Coding! **
