# Ubuntu base cmd
---
## 1 Ubuntu systeam basic tips
---

    入门linux的同志，刚开始最迫切想知道的，大概一个是中文输入法，另一个就是怎么安装软件。本文主要讲一下LINUX安装软件方面的特点。
### 1. 1 apt-get update和upgrade的区别
```
    
     在windows下安装软件，我们只需要有EXE文件，然后双击，下一步直接OK就可以了。但在LINUX下，不是这样的。每个LINUX的发行版，比如UBUNTU，都会维护一个自己的软件仓库，我们常用的几乎所有软件都在这里面。这里面的软件绝对安全，而且绝对的能正常安装。

那我们要怎么安装呢？在UBUNTU下，我们维护一个源列表，源列表里面都是一些网址信息，这每一条网址就是一个源，这个地址指向的数据标识着这台源服务器上有哪些软件可以安装使用。
sudo gedit /etc/apt/sources.list
在这个文件里加入或者注释（加#）掉一些源后，保存。这时候，我们的源列表里指向的软件就会增加或减少一部分。

接一下要做的就是：
sudo apt-get update
这个命令，会访问源列表里的每个网址，并读取软件列表，然后保存在本地电脑。我们在新立得软件包管理器里看到的软件列表，都是通过update命令更新的。

update后，可能需要upgrade一下。
sudo apt-get upgrade

这个命令，会把本地已安装的软件，与刚下载的软件列表里对应软件进行对比，如果发现已安装的软件版本太低，就会提示你更新。如果你的软件都是最新版本，会提示：
升级了 0 个软件包，新安装了 0 个软件包，要卸载 0 个软件包，有 0 个软件包未被升级。
总而言之，update是更新软件列表，upgrade是更新软件。

ref:https://www.cnblogs.com/fenglongyu/p/8654991.html
```
### 1.2  /etc/apt/sources.list  &   /etc/apt/sources.list.d
```
         /etc/apt/sources.list  : Ubuntu  system source 
         /etc/apt/sources.list.d  :  other source    such as:       .../ros-latest.list     
         
```
### 1.3 source cmd
```
每次启动新的shell时，如果将ROS环境变量自动添加到bash会话中，将很方便：
echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc
~/.bashrc

for just one time :
source /opt/ros/melodic/setup.bash
```
### 1.4

## 2. install Ubuntu
---
### 2.1 install

### 2.2 update and setting 

## 3. install chinese(simple)
---


