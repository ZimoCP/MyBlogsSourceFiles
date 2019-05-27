---
title: Ubuntu 18.04 LTS 美化 - 仿Windows
date: 2019-05-20 21:22:52
tags: ['Ubuntu','Linux','GNOME','Windows']
categories: 'GNOME'
---

效果图

![Ubuntu仿Windows](/images/Ubuntu-18-04-LTS-美化-仿Windows/windows-like-ubuntu.png)  

<!-- more -->

**请先去看[这里](https://zimocp.github.io/2019/04/17/Ubuntu-18-04-LTS-%E7%BE%8E%E5%8C%96/)，特别是第八步（GNOME插件安装）**

## [](#安装GNOME-Tweaks "安装GNOME Tweaks")安装GNOME Tweaks

见上文链接

## [](#安装GNOME插件 "安装GNOME插件")安装GNOME插件

用上文链接方法安装[插件`Dash to Panel`](https://extensions.gnome.org/extension/1160/dash-to-panel/)  
打开GNOME Tweaks（优化），找到左侧栏`扩展`  
将`Dash to panel`打开，你会发现底下有了一条状态+任务栏

## [](#配置插件 "配置插件")配置插件

点击优化->扩展->`Dash to panel`右边开关左边的设置按钮，自己捣鼓一下吧

## [](#安装主题 "安装主题")安装主题

[下载Windows 10主题](/upload/Ubuntu-18-04-LTS-美化-仿Windows/Windows-10-2.1.zip)  
暗色主题我就没有下了，如果想要的话就[去Github下好了](https://github.com/B00merang-Project/Windows-10-Dark)  
下下来之后解压zip（右键点击`解压到此处`），把解压后的文件夹复制到主文件夹`.themes`（没有？先按`Ctrl+H`显示隐藏文件，还没有就新建）  
打开GNOME Tweak，将图中高亮的设置设好  
![](/images/Ubuntu-18-04-LTS-美化-仿Windows/windows-like-ubuntu-3.png)  
接下来你会发现界面变了个样子（虽然我觉得并没有那么像Windows，但是是我找到最像的了）

## [](#安装图标 "安装图标")安装图标

[下载图标](/upload/Ubuntu-18-04-LTS-美化-仿Windows/Windows-10-icon.zip)  
下下来之后解压zip（右键点击`解压到此处`），把解压后的文件夹复制到主文件夹`.icon`（没有？先按`Ctrl+H`显示隐藏文件，还没有就新建）  
打开GNOME Tweak，将图中高亮的设置设好  
![](/images/Ubuntu-18-04-LTS-美化-仿Windows/windows-like-ubuntu-4.png)  
接下来你会发现图标变了个样子  
（Ctrl+C Ctrl+V最好van了）

## [](#设置按Super键（Windows键）打开所有应用程序菜单 "设置按Super键（Windows键）打开所有应用程序菜单")设置按Super键（Windows键）打开`所有应用程序`菜单

终端输入

```
gsettings set org.gnome.mutter overlay-key ''  
gsettings set org.gnome.shell.keybindings toggle-application-view "['Super_L','Super_R']"  
```   
之后按按Super键（左右都试试），哇！   
恢复默认：终端输入  

```
gsettings set org.gnome.mutter overlay-key 'Super_L'  
gsettings set org.gnome.shell.keybindings toggle-application-view "['A']"  
```

## [](#设置左下角图标 "设置左下角图标")设置左下角图标

[Windows7图标（我只在Windows里找到绿的。。。）](/images/Ubuntu-18-04-LTS-美化-仿Windows/windows-7-start-green.png)  
[Windows10的透明背景的图标我乱咔了一个](/images/Ubuntu-18-04-LTS-美化-仿Windows/windows-10-start-green.png)  
下载上面你更喜欢的图标，然后右键左下角9个点图标，点进`Dash to Panel Settings`可以快速进入设置  
进入设置，进入最上面一栏的`行为`，你会在下面看到”显示**应用**图标”，点击左边的设置键，有一个`自定义...图像`，选中你刚下载的那个就OK啦

## [](#背景 "背景")背景

[下载Windows10背景](/images/Ubuntu-18-04-LTS-美化-仿Windows/windows10bckgrd.jpg)  
右键选择`设为背景`即可