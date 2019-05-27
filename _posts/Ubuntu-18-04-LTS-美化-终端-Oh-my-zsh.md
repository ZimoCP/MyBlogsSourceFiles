---
title: 'Ubuntu 18.04 LTS 美化 - 终端 Oh-my-zsh '
date: 2019-05-20 21:24:03
tags: ['Ubuntu','Linux','Zsh','Terminal','Oh my Zsh']
categories: 'Zsh'
---

效果图

![Ubuntu Oh-my-Zsh](/images/Ubuntu-18-04-LTS-美化-终端-Oh-my-zsh/ubuntu-oh-my-zsh.png)

<!-- more -->

## [](#安装Zsh，终端输入 "安装Zsh，终端输入")安装Zsh，终端输入

`sudo apt-get install zsh`

## [](#将Zsh设为默认终端 "将Zsh设为默认终端")将Zsh设为默认终端

`chsh -s $(which zsh)`  
恢复为bash：`chsh -s /bin/bash`

## [](#不要着急注销重新登录，Zsh配置超级狗蛋，先装好Oh-my-zsh，终端输入 "不要着急注销重新登录，Zsh配置超级狗蛋，先装好Oh-my-zsh，终端输入")**不要着急注销重新登录，Zsh配置超级狗蛋，先装好Oh-my-zsh**，终端输入

1.  curl方式  
    `sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"`
2.  wget方式  
    `wget https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O - | sh`  
    装好后注销重新登录，再打开终端，可以发现终端前面是个箭头了

## [](#配置Zsh "配置Zsh")配置Zsh

**Home和End键可能会失效，那么就用`Ctrl+A`和`Ctrl+E`**  
但我个人认为默认主题不太好看，我最喜欢Agnoster（当然你可以用其他的主题，百度一下就好了）

### [](#Agnoster主题配置 "Agnoster主题配置")Agnoster主题配置

进入主文件夹，按`Ctrl+H`显示隐藏文件，打开`.zshrc`  
Gedit里按`Ctrl+F`搜索`ZSH_THEME`，等号后面的值改为`agnoster`  
重开终端就会发现有一些颜色了，并且字体咕咕咕。。。。

因为Agnoster用了Powerline字体，通常直接apt安装就好了，终端输入  
`sudo apt-get install fonts-powerline`  
重启终端，如果还是不行，那只好[去Github下载](https://github.com/powerline/fonts)（我就不讲了，自己看文档吧。。。）

### [](#配置插件 "配置插件")配置插件

推荐插件：wd, zsh-autosuggestions, zsh-syntax-highlighting

##### [](#wd "wd")wd

*   用途：终端中快速跳转到常用的文件夹
*   安装：按照前文方法打开`.zshrc`，搜索`plugins`，在后括号`)`前面加上`wd`（一定要有空格！），重启终端即可
*   食用方法：终端中用`cd`进入你想要设置的文件夹，输入`wd add 你想要的名字`，以后就可以用`wd 你设置的名字`来快速打开了

##### [](#zsh-autosuggestions "zsh-autosuggestions")zsh-autosuggestions

*   用途：自动补全，来源是终端食用历史
*   安装：终端输入  
    `git clone https://github.com/zsh-users/zsh-autosuggestions ~/.zsh/zsh-autosuggestions`  
    然后打开`.zshrc`，在最后添加一句`source ~/.zsh/zsh-autosuggestions/zsh-autosuggestions.zsh`
*   食用方法：终端里输入命令，如果有历史匹配的话后面会显示灰色（？）的字（提示），可以按`→`或`End`补全

##### [](#zsh-syntax-highlighting "zsh-syntax-highlighting")zsh-syntax-highlighting

*   用途：高亮，对的是绿色，错的是红色粗体，路径是白色下划线
*   安装：终端输入  
    `git clone https://github.com/zsh-users/zsh-syntax-highlighting.git`  
    然后打开`.zshrc`，在最后添加一句`source ./zsh-syntax-highlighting/zsh-syntax-highlighting.zsh`
*   食用方法：这个不用说了吧？

### [](#调整终端配色 "调整终端配色")调整终端配色

打开终端，界面上右键，点击`配置文件首选项`  
然后点击上面一栏中的`颜色`，自己调一调吧