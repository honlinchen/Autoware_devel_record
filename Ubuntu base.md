# Ubuntu base cmd

## 1 Ubuntu systeam basic tips

basic tips.
    
### 1. 1 apt-get update和upgrade的区别
```
 在windows下安装软件，我们只需要有EXE文件，然后双击，下一步直接OK就可以了。但在LINUX下，不是这样的。每个LINUX的发行版，比如UBUNTU，
 都会维护一个自己的软件仓库，我们常用的几乎所有软件都在这里面。这里面的软件绝对安全，而且绝对的能正常安装.那我们要怎么安装呢？在UBUNTU下，
 我们维护一个源列表，源列表里面都是一些网址信息，这每一条网址就是一个源，这个地址指向的数据标识着这台源服务器上有哪些软件可以安装使用。

        sudo gedit /etc/apt/sources.list
        在这个文件里加入或者注释（加#）掉一些源后，保存。这时候，我们的源列表里指向的软件就会增加或减少一部分。
        
        接一下要做的就是：
        sudo apt-get update
        这个命令，会访问源列表里的每个网址，并读取软件列表，然后保存在本地电脑。我们在新立得软件包管理器里看到的软件列表，都是通过update命令更新的。

        update后，可能需要upgrade一下。
        sudo apt-get upgrade
        
        这个命令，会把本地已安装的软件，与刚下载的软件列表里对应软件进行对比，如果发现已安装的软件版本太低，就会提示你更新。如果你的软件都是最新版本，
        会提示：升级了 0 个软件包，新安装了 0 个软件包，要卸载 0 个软件包，有 0 个软件包未被升级。
        总而言之，update是更新软件列表，upgrade是更新软件。
```
[ref blog:](https://www.cnblogs.com/fenglongyu/p/8654991.html)

### 1.2  /etc/apt/sources.list  与   /etc/apt/sources.list.d的区别

        /etc/apt/sources.list  :            Ubuntu系统的源list
        /etc/apt/sources.list.d/ :       其他源的list， 例如:         /etc/apt/sources.list.d/ros-latest.list     
         
### 1.3 source 命令

        
        echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc
        ~/.bashrc
        
- 环境设置相关变量的存放位置 :<br>
        ROS: source /opt/ros/melodic/setup.bash
        QT: source /etc/profile
        Autoware:cd autoware.ai    source install/setup.bash
        
 - ~/.bashrc 与 profile || setup.bash等的关系<br>
 
       系统开机时会默认执行 ~/.bashrc，其他包含环境设置的文件需要手动source， 在~/.bashrc添加source其他文件的语句，就能默认执行其他文
       件中的环境设置，即每次启动新的shell时，如果将ROS/QT/Autoware环境变量自动添加到bash会话中，将很方便：
        ROS:
        echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc
        ~/.bashrc

        QT:
        echo "source /etc/profile" >> ~/.bashrc
        ~/.bashrc

        Autoware:
        echo "source /home/chl/autoware.ai/install/setup.bash" >> ~/.bashrc
        ~/.bashrc

        写入bashrc的方法还有
        vim ~/.bashrc
        add the sentences: source...

```
Q:添加过多source sentences 到 ./bashrc 可能的影响...?
```

### 1.4

## 2. install Ubuntu

### 2.1 install

### 2.2 Ubuntu update and setting 

- [ref:官方文档](https://help.ubuntu.com/community/Repositories/Ubuntu)
- 更换源为:aliyun
![](https://github.com/honlinchen/Autoware_devel_record/blob/master/md_images/Screenshot%20from%202020-04-15%2021-00-10.png)

## 3. install chinese(simple)
---


