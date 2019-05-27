---
title: Ubuntu 18.04 LTS 美化
date: 2019-05-20 21:21:07
tags: ['Ubuntu','Linux','GNOME']
categories: GNOME
---

这篇文章是美化`Ubuntu 18.04 LTS`的一篇教程，其中有一些步骤不必全部照做，只是我个人喜好

<!-- more -->

## [](#记住Ubuntu打开终端的快捷键：Ctrl-Alt-T，因为接下来有可能会把Ubuntu左侧启动器隐藏掉，只能用快捷键开终端 "*记住Ubuntu打开终端的快捷键：Ctrl+Alt+T，因为接下来有可能会把Ubuntu左侧启动器隐藏掉，只能用快捷键开终端")\*记住Ubuntu打开终端的快捷键：`Ctrl+Alt+T`，因为接下来有可能会把Ubuntu左侧启动器隐藏掉，只能用快捷键开终端

## [](#记住sudo命令的作用：用管理员权限运行接下来的命令，如果当前终端没有输过密码的话会让你输密码（会隐藏的，放心不会被别人看到） "*记住sudo命令的作用：用管理员权限运行接下来的命令，如果当前终端没有输过密码的话会让你输密码（会隐藏的，放心不会被别人看到）")\*记住`sudo`命令的作用：用管理员权限运行接下来的命令，如果当前终端没有输过密码的话会让你输密码（会隐藏的，放心不会被别人看到）

## [](#安装GNOME优化工具（常用）：终端输入 "*安装GNOME优化工具（常用）：终端输入")\*安装GNOME优化工具（常用）：终端输入

`sudo apt-get install gnome-tweak-tool`

## [](#美化终端 "美化终端")美化终端

[传送](https://zimocp.github.io/2019/04/17/Ubuntu-18-04-LTS-%E7%BE%8E%E5%8C%96-%E7%BB%88%E7%AB%AF-Oh-my-zsh/)

## [](#美化界面 "美化界面")美化界面

[仿Windows 10](https://zimocp.github.io/2019/04/17/Ubuntu-18-04-LTS-%E7%BE%8E%E5%8C%96-%E4%BB%BFWindows/)，  
[仿Mac OS X](https://zimocp.github.io/2019/04/19/Ubuntu-18-04-LTS-%E7%BE%8E%E5%8C%96-%E4%BB%BFMac-OS-X/)  

## [](#更改开机样式 "更改开机样式")更改开机样式

### [](#更改GNU-Grub背景（jl紫难受的很） "更改GNU Grub背景（jl紫难受的很）")更改GNU Grub背景（jl紫难受的很）

首先准备一张图片，最好是PNG格式的，然后把他复制到`/boot/grub/`  
你会发现你在“文件”里找不到/boot，那就终端输入 `sudo cp '/你/的/图片/的/路径/和文件名' /boot/grub/`  
接下来改一改grub的分辨率，  
**注意：可能会修改炸，修改前先备份：`sudo cp /etc/default/grub /etc/default/BeiFen-grub`**  
终端输入  
`sudo gedit /etc/default/grub`  
输完密码就会出来一个类似Windows记事本的东西，按`Ctrl+F`搜索`GRUB_GFXMODE`，找不到就自己添加一行进去，将其更改为  
`GRUB_GFXMODE=你的分辨率x你的分辨率（例如1920x1080）`  
最后重新生成Grub的设置就好啦，终端输入  
`update-grub`

### [](#更改启动时界面 "更改启动时界面")更改启动时界面

如果你想要很炫酷的样子，可以去[GNOME-Look.org](https://www.gnome-look.org/browse/cat/108/)或者[百度搜索`Ubuntu 18.04 Plymouth主题`](https://www.baidu.com/s?wd=Ubuntu%2018.04%20Plymouth%E4%B8%BB%E9%A2%98)  
如果你喜欢Ubuntu原本的样子只是讨厌jl紫背景色，修改Plymouth主题就好了  
终端输入`sudo nautilus /usr/share/plymouth`可以用管理员权限打开Plymouth文件夹  
你会看到里面有个themes文件夹，**先备份再修改**  
进入themes文件夹再进里面的ubuntu-logo文件夹，打开`ubuntu-logo.script`，`Ctrl+F`搜索`Window.SetBackgroundTopColor`然后按回车  
你会看到有`Window.SetBackgroundTopColor`（渐变色顶端）和`Window.SetBackgroundBottomColor`（渐变色底端）  
把它们括号里面的三个值（RGB）改成你想要的颜色就好了，我是用全0.00（也就是黑色）

## [](#更改登录界面背景 "更改登录界面背景")更改登录界面背景

找到一张背景，将他移动到系统背景文件夹（建议不要放在自己用户的主文件夹，有可能会读不到），终端输入  
`sudo cp '/你/的/图片/的/路径/和文件名' /usr/share/backgrounds/`  
然后修改配置，  
**先备份再修改，`sudo cp /etc/alternatives/gdm3.css /etc/alternatives/BeiFen-gdm3.css`**  
终端输入  
`sudo gedit /etc/alternatives/gdm3.css`  
`Ctrl+F`搜索`lockDialogGroup`，默认代码是  

```css
#lockDialogGroup {  
 background: #2c001e url(resource:///org/gnome/shell/theme/noise-texture.png);  
 background-repeat: repeat;   
}  
```

修改为

```css
#lockDialogGroup {
    background: #2c001e url(file:///你/的/图片/的/路径/和文件名);
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center;
}

```

保存重启就ok了

## [](#GNOME插件安装（先装好gnome-tweaks） "GNOME插件安装（先装好gnome-tweaks）")GNOME插件安装（先装好gnome-tweaks）

### [](#安装软件包 "安装软件包")安装软件包

终端输入  
`sudo apt-get install chrome-gnome-extension`  
（这只是包名，其实里面即支持Chrome也有Firefox）

### [](#浏览器安装插件 "浏览器安装插件")浏览器安装插件

##### [](#Firefox "Firefox")Firefox

[火狐插件商店搜索](https://addons.mozilla.org/)`GNOME Shell integration`

##### [](#Chrome "Chrome")Chrome

百度一下，自行搞定（毕竟我没操作过）

### [](#食用方法 "食用方法")食用方法

点击插件图标会打开网站，自己搜索我相信你会用的

### [](#推荐插件 "推荐插件")推荐插件

##### [](#Top-bar-script-executer "Top bar script executer")[Top bar script executer](https://extensions.gnome.org/extension/1154/top-bar-script-executor/)

顶栏快捷方式运行自定义命令

##### [](#Keys-indicator "Keys indicator")[Keys indicator](https://extensions.gnome.org/extension/1154/top-bar-script-executor/)

顶栏显示当前按下了`Caps Lock, Num Lock, Ctrl, Shift, Alt`中的哪些键

##### [](#Hide-activities-button "Hide activities button")[Hide activities button](https://extensions.gnome.org/extension/1128/hide-activities-button/)

隐藏顶栏活动按钮

##### [](#Launch "Launch")[Launch](https://extensions.gnome.org/extension/999/launch/)

替换顶栏活动按钮为所有应用程序（9个点）

##### [](#Hide-top-bar "Hide top bar")[Hide top bar](https://extensions.gnome.org/extension/545/hide-top-bar/)

自动隐藏顶栏

##### [](#No-title-bar "No title bar")[No title bar](https://extensions.gnome.org/extension/1267/no-title-bar/)

直接将应用的标题栏和顶栏结合为一体，窗口操作按钮也被放在顶栏上，有些像Unity，节省空间（建议与Hide activities button合用）