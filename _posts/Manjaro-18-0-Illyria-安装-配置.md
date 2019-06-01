---
title: Manjaro 18.0 Illyria 安装&配置
date: 2019-05-22 20:07:02
tags: ['Manjaro','Linux']
categories: 'Manjaro'
---

记录我安装Manjaro的过程以便日后要是硬盘又咕的时候可以更简单的安装&配置

<!--more-->

# 前言（废话）
作为一名蒟蒻，受到巨佬[ZFY](mailto:zhoufangyuantv@outlook.com)的影响，本来是一个[Ubuntu](https://ubuntu.com)的忠实粉丝。  
后来在配置、美化过程中发现坑巨多，而且软件不好找，便虚拟机试了试[Deepin](https://deepin.org)，发现咔咔咔咔。。。而且软件也不多  
后来知道[Arch Linux](https://archlinux.org)有个AUR还有个ArchLinuxCN软件源，于是想试试，翻了一翻[洛咕日报一片安装Arch的教程](https://www.luogu.org/blog/ddsblog/article-001)。。瞬间不想装了。。。  
再后来发现了[Manjaro](https://manjaro.org)，看了看评价还不错（后来食用的时候也觉得很不错），正好移动硬盘刚刚咕掉了，于是保修后就装了Manjaro


# 安装
最开始安装的时候并没有截图，于是接下来的都是虚拟机的截图

## 下载
建议使用[中科大的镜像站](https://mirrors.ustc.edu.cn/manjaro-cd/)，里面有官方维护版本（XFCE,KDE,GNOME和一个命令行在线安装镜像）  
推荐桌面环境：GNOME（最多人用），KDE（我现在在用，Qt开发一定要用这个），MATE（*社区维护*，GNOME2的延续，轻量不难用）  
如果要社区维护（其他桌面环境）的我只知道在[官网上](https://manjaro.org/download/)

## 刻进U盘
当然你也可以让虚拟机挂载你的硬盘来安装（我给同学安装到U盘的时候试了试kvm来装，装到一半就卡炸了）  

Linux: 可以用`SUSE Studio Imagewriter`（我觉得这个软件不用教你们应该也会用）

Windows: [下载USBWriter] 这个软件也不用教

## 进入Live系统
你可以进你电脑的BIOS然后调一调启动顺序（这个只能自己百度，联想、小米是开机狂按F2）  
也可以直接选择启动的硬盘（联想、小米开机狂按F12）  
进入U盘（我那里显示`UEFI Boot Device`）  
接下来会看到一个很好看（？）的GRUB界面  
![](/images/Manjaro-18-0-Illyria-安装-配置/install1.png)  
用`←` `→`和回车改成上图的样子就好了，然后进入`Boot:....`

## 准备安装
静候一会儿，你发现你进入了一个very ok的Live环境  
双击桌面上（GNOME可能在左侧栏上）的`Install Manjaro`  
然后语言选中文，时区/语言地图上点Shanghai，键盘布局就默认  

## 分区
**注意！！建议先在虚拟机里尝试后再实践！！**  
如果觉得自己的硬盘里数据都不要了或备份好了可以直接抹掉整个硬盘安装  

### 自动
如果电脑里装了Windows或者其他系统应该会有一个双系统共存选项  
如果没有系统或移动硬盘就抹掉整块磁盘  
如果还有数据就用手动  
创建分区：点击"空闲空间"然后点`创建`按钮

### 手动：MBR+Legacy（如果安装程序白色部分左上角写着BIOS就用这个）
没有分区表的建立分区表（请先备份数据，会删除所有分区），选MBR  
创建分区：第一个（/boot）512M，第二个（/）开很大很大，最后一个（swap）开内存的两倍（如果不需要休眠功能可以不要这个）  
分区文件系统：第一个（/boot）选fat32，第二个（/）选ext4，第三个（swap）选linuxswap  
挂载点：第一个到/boot，第二个到/，第三个不用  
标记：/boot标记boot，/标记root，swap标记swap  
然后应该是这样的  
![](/images/Manjaro-18-0-Illyria-安装-配置/install2.png)

### 手动：GPT+UEFI（如果安装程序白色部分左上角写着UEFI就用这个）
没有分区表的建立分区表（请先备份数据，会删除所有分区），选GPT
创建分区：第一个（/boot/efi）512M，第二个（/）开很大很大，最后一个（swap）开内存的两倍（如果不需要休眠功能可以不要这个）  
分区文件系统：第一个（/boot/efi）选fat32，第二个（/）选ext4，第三个（swap）选linuxswap  
挂载点：第一个到/boot/efi，第二个到/，第三个不用  
标记：/boot/efi标记esp，/标记root，swap标记swap  
然后应该是这样的  
![](/images/Manjaro-18-0-Illyria-安装-配置/install3.png)

## 结束安装
分完区接下来一路确定就好了，然后静待一会儿后不要重启要继续试用，然后关机，把U盘拔了再开


# 配置
这里说的配置就是配置pacman和一些常用软件

## Pacman

### 切换中国源
终端输入`sudo 你想用的文本编辑器 /etc/pacman-mirrors.conf`  
在最后加上  
```
OnlyCountry = China
```

### 增加ArchLinuxCN源
终端输入`sudo 你想用的文本编辑器 /etc/pacman.conf`  
在最后加上  
```
[archlinuxcn]
SigLevel = Optional TrustedOnly
Server = http://mirrors.ustc.edu.cn/archlinuxcn/$arch

[arch4edu]
SigLevel = Never
Server = http://mirrors.tuna.tsinghua.edu.cn/arch4edu/$arch
```

### 更新、使用中国源
终端输入`sudo pacman -c China`

### 更新系统
终端输入`sudo pacman -Syyu`

### 增加ArchLinuxCN源秘钥
终端输入`sudo pacman -S archlinuxcn-keyring`

### 使用AUR

#### yay（命令行AUR软件包管理器）
终端输入`sudo pacman -S yay`  
以后想要安装AUR里的东东就终端输入`yay 包名`（不要sudo！！）

#### Pamac（图形软件包管理器）
安装（虽然这个好像是自带的）：终端输入  
`sudo pacman -S pamac-gtk`（非KDE）  
`sudo pacman -S pamac-qt`（KDE）

进入Pamac的设置（Gtk:窗口栏三个点里面的选项，KDE/Qt:三条杠），找到AUR，然后勾选第一个，再都选自动更新那个就好了，我相信你会用的

## 常用软件

### 搜狗输入法（不知为何我的KDE配不好这个）
为什么用搜狗的呢？因为好用。。。（真的是Linux下最好用的了）  
终端输入`sudo pacman -S fcitx-sogoupinyin fcitx-im fcitx-configtool`  
终端输入`你的文本编辑器 ~/.xprofile`  
添加内容  
```
export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
export XMODIFIERS="im=fcitx"
```

### IBus（输入法）
当然你也可以直接去看[ArchWiki](https://wiki.archlinux.org/index.php/IBus_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))  
安装（GNOME请将下面`-S`后的第一个`ibus`删掉）：终端输入  
`sudo pacman -S ibus ibus-libpinyin`  
如果KDE的不能用就还要`yay ibus-qt`并且开`qtconfig-qt4`，选择`Interface`，将最底下的`Default Input Method`换成ibus  
GNOME用户装好之后直接开GNOME设置调就好了，我相信你们会的（主要是我没有用GNOME。。。）  
其他用户打开`.xprofile`（没有就新建）加上这么几句  
```
export GTK_IM_MODULE=ibus
export XMODIFIERS=@im=ibus
export QT_IM_MODULE=ibus
ibus-daemon -x -d
```  
然后注销重登桌面就好了

### QQ/TIM
QQ: `yay deepin.com.qq.im`
TIM: `yay deepin.com.qq.office`

### WPS
`sudo pacman -S wps-office ttf-wps-fonts`

### 迅雷
`yay deepin.com.thunderspeed`

### 网易云音乐
`sudo pacman -S netease-cloud-music`

