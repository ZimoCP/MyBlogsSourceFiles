---
title: Ubuntu 18.04 LTS 美化 - 仿Mac OS X
date: 2019-05-20 21:25:42
tags: ['Ubuntu','Linux','GNOME','Mac OS','OSX']
categories: 'GNOME'
---

效果图  
![](/images/Ubuntu-18-04-LTS-美化-仿Mac-OS-X/mac-os-x-like-ubuntu.png)

<!-- more -->

**请先去看[这里](https://zimocp.github.io/2019/04/17/Ubuntu-18-04-LTS-%E7%BE%8E%E5%8C%96/)，特别是第八步（GNOME插件安装）**

## [](#安装GNOME-Tweaks "安装GNOME Tweaks")安装GNOME Tweaks

见上文链接

## [](#添加软件源 "添加软件源")添加软件源

终端输入  
`sudo add-apt-repository ppa:noobslab/macbuntu`

## [](#Dock "Dock")Dock

Dock作为Mac的灵魂肯定要第一个讲。  
对于Dock有3种方案：Docky, Plank和Dash to Dock。

### [](#安装 "安装")安装

#### [](#Docky "Docky")Docky

耗能较大，空间较多，功能较多，易崩溃（毕竟一个Dock耗能再多也比GNOME默认的Dash少。。。）  
![docky](/images/Ubuntu-18-04-LTS-美化-仿Mac-OS-X/docky.png)  
安装：终端输入`sudo apt-get install docky`

#### [](#Plank "Plank")Plank

耗能很少，空间少，功能有限，简洁的一匹，几乎不崩溃（推荐，如果只想要一个单纯的Dock就选这个好了）  
![plank](/images/Ubuntu-18-04-LTS-美化-仿Mac-OS-X/plank.png)  
安装：终端输入`sudo apt-get install plank`

#### [](#Dash-to-Dock "Dash to Dock")Dash to Dock

GNOME插件，耗能咕咕咕，bug多，功能有限，几乎不崩溃（不推荐，但是有自适应透明度、配合GNOME原生应用程序菜单）  
效果图没有  
[安装](https://extensions.gnome.org/extension/307/dash-to-dock/)

### [](#推荐主题（仅推荐，并不一定仿Mac） "推荐主题（仅推荐，并不一定仿Mac）")推荐主题（仅推荐，并不一定仿Mac）

#### [](#Docky：EnigmoDarky "Docky：EnigmoDarky")Docky：EnigmoDarky

[下载](/upload/Ubuntu-18-04-LTS-美化-仿Mac-OS-X/EnigmoDarky.tar)  
安装方法：找到Docky第一个按钮左键（或在Docky部件和各种程序之间会由一个分割线，右键它，点击设置），`主题`的后面有`安装`，点击后选择下下来的tar压缩包即可  
食用方法：做完上一步之后就不用我说了吧？

#### [](#Plank：Frost，Mac-OS-Themes，MacBuntu的Plank主题 "Plank：Frost，Mac OS Themes，MacBuntu的Plank主题")Plank：Frost，Mac OS Themes，MacBuntu的Plank主题

[下载Frost](/upload/Ubuntu-18-04-LTS-美化-仿Mac-OS-X/frost-plank-theme-2.2.1.zip)，[下载Mac OS Themes](/upload/Ubuntu-18-04-LTS-美化-仿Mac-OS-X/plank-macOS-Themes-Pack.zip)  
安装方法：  
Frost：在解压后的文件夹里找到名为`Frost`的文件夹，将他复制到`~/.local/share/plank/themes`里（没有就创建）  
Mac OS Themes：解压后进入文件夹，你会看到一大堆主题，根据名字复制你需要的文件夹到`~/.local/share/plank/themes`里（没有就创建）  
MacBuntu：见下文  
食用方法：在Plank上`Ctrl+右键`，点击`首选项`，然后就不用我说了吧？

### [](#隐藏原Dash "隐藏原Dash")隐藏原Dash

（打算使用Dash to Dock作为Dock的跳过此步）  
见上文安装`Dash to Dock`  
安装好之后进入GNOME Tweaks，进入左侧栏`插件`，将Dash to Dock打开（开了以后可以试试关了它，如果发现没有变回Ubuntu默认dash，那么就一直把他关着好了）  
点击Dash to Dock的设置按钮，打开`自动隐藏`，把两个开关都关掉，你会发现你找不到Dash了

### [](#启动Dock "启动Dock")启动Dock

（打算使用Dash to Dock作为Dock的跳过此步）  
按下`Alt+F2`，输入`docky`（或`plank`），回车

### [](#Dock开机启动 "Dock开机启动")Dock开机启动

（打算使用Dash to Dock作为Dock的跳过此步）  
打开GNOME Tweaks，左侧栏进入开机启动程序，

### [](#隐藏Docky最左侧的图标 "隐藏Docky最左侧的图标")隐藏Docky最左侧的图标

（不使用Docky作为Dock的跳过此步）  
终端输入，安装Gconf编辑器  
`sudo apt-get install gconf-editor`  
打开gconf（`配置编辑器`），按照图中的样子打开  
![docky](/images/Ubuntu-18-04-LTS-美化-仿Mac-OS-X/gconfEditorDockyIcon.png)  
将右侧的`ShowDockyItem`取消勾选，关掉gconf就生效了

## [](#Launchpad "Launchpad")Launchpad

Slingscold是一个比GNOME原生启动器轻量的多的多的多的全屏启动器，虽然不是很像Mac但是是最好的选择了

### [](#安装-1 "安装")安装

终端输入  
`sudo apt-get install slingscold`

### [](#将Slingscold固定在Dock上 "将Slingscold固定在Dock上")将Slingscold固定在Dock上

Dash to Dock：打开`所有应用程序`，然后拖到Dock就好了  
Docky & Plank：进入文件夹`/usr/share/applications`，找到`Slingscold`，拖到Dock上就好了

## [](#Spotlight "Spotlight")Spotlight

Spotlight是在Mac上很nb的一个神奇搜索功能，虽然Linux下没有完全替代品，但是Albert仿的很不错。

### [](#安装-2 "安装")安装

终端输入  
`sudo apt-get install albert`

### [](#配置 "配置")配置

进入Launchpad，打开Albert，之后按`Alt+Q`（默认快捷键）打开它  
你会发现它右上角有个小小的、旋转的设置按钮，点进去  
在`Generals`里可以修改快捷键、各种设置等  
建议修改为图中样式（快捷键可以自己设）  
![albert](/images/Ubuntu-18-04-LTS-美化-仿Mac-OS-X/albertSet1.png)  
Plugins是各种功能的设置，建议不要打开浏览器收藏（`... Bookmarks`）功能，有可能导致浏览器中无法使用收藏  
顺便给出会话管理（`System`）功能、网页搜索功能（`WebSearch`）的建议设置  
![albert](/images/Ubuntu-18-04-LTS-美化-仿Mac-OS-X/albertSet2.png)  
![albert](/images/Ubuntu-18-04-LTS-美化-仿Mac-OS-X/albertSet3.png)

### [](#固定到顶栏 "固定到顶栏")固定到顶栏

见文首链接，安装插件`Top bar script executor`  
进入它的设置，点击下面按钮`Add`，设为图中设置后按OK  
![albert](/images/Ubuntu-18-04-LTS-美化-仿Mac-OS-X/topBarExecute.png)  
接下来关掉它的设置，按`Alt+F2`，输入`r`回车重新启动GNOME Shell  
重启好了之后你就会发现上面有了一个搜索按钮

## [](#主题和图标 "主题和图标")主题和图标

终端输入  
`sudo apt-get install macbuntu-os-icons-v1804 macbuntu-os-ithemes-v1804 macbuntu-os-plank-theme-v1804`  
就会安装Macbuntu的主题、图标和Plank主题  
Plank主题参照上文配置  
打开GNOME Tweaks，将左侧栏`外观`中的`应用程序` `光标` `图标`设成Macbuntu的  
推荐主题是MacBuntu-OS11或MacBuntu-OS-MJ

## [](#启动、登录界面 "启动、登录界面")启动、登录界面

### [](#添加软件源-1 "添加软件源")添加软件源

终端输入  
`sudo add-apt-repository ppa:noobslab/themes`

### [](#启动界面 "启动界面")启动界面

看起来差不多这个样子  
![](/images/Ubuntu-18-04-LTS-美化-仿Mac-OS-X/boot.jpg)  
安装：终端输入  
`sudo apt-get install macbuntu-os-bscreen-lts-v7`  
想恢复成原来的？  
`sudo apt-get autoremove macbuntu-os-bscreen-lts-v7`（暴力卸载解决一切问题。。。）

### [](#登录界面（有风险，需谨慎） "登录界面（有风险，需谨慎）")登录界面（有风险，需谨慎）

看起来差不多这个样子  
![](/images/Ubuntu-18-04-LTS-美化-仿Mac-OS-X/log.jpg)  
安装：终端输入  
`sudo apt-get install macbuntu-os-lightdm-lts-v7`  
想恢复？同样暴力卸载。。。  
`sudo apt-get autoremove macbuntu-os-lightdm-lts-v7`

## [](#壁纸 "壁纸")壁纸

[下载Mac OS X Mojave的壁纸](/uploads/Ubuntu-18-04-LTS-美化-仿Mac-OS-X/All-Mojave-Wallpapers.zip)  
对着图片右键，点击`设为壁纸`即可