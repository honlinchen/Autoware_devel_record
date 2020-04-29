# Autoware Install

- Autoware安装有官方教程：
[Ref: autowarefoundation官方](https://gitlab.com/autowarefoundation/autoware.ai/autoware/-/wikis/Source-Build)
- 但是作为新手，需要经过以下步骤:<br>
     Steps: install Ubuntu -- Ubuntu setting -- install ROS -- install QT --(install CUDA) -- install Autoware
        
## 1. install Ubuntu 
[Ref](https://www.cnblogs.com/Duane/p/6776302.html) and other blogs.
## 2. Ubuntu setting
[Ref](https://github.com/honlinchen/Autoware_devel_record/blob/master/Ubuntu_base.md)
## 3. install ROS
[Ref](https://github.com/honlinchen/Autoware_devel_record/blob/master/ROS_install.md)
```
Note:
将ROS环境变量自动添加到bash会话中，将很方便：
echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc
~/.bashrc
关于环境变量设置的问题在Ubuntu_base 有详细讲解
```
## 4. install QT

- [Ref blog:](https://blog.csdn.net/luoffy555/article/details/103251712)
```
Note:环境变量
export PATH="/home/chl/Qt5.12.2/5.12.2/gcc_64/bin:$PATH"
export PATH="/home/chl/Qt5.12.2/Tools/QtCreator/bin:$PATH"
根据各类博文，环境设置需要设置Qt gcc与QtCreater环境变量
```

## 5. install Auoware
[Ref: autowarefoundation](https://gitlab.com/autowarefoundation/autoware.ai/autoware/-/wikis/Source-Build)

```
安装autoware时，语句：rosdep update只能执行一次，如果安装不成功，则下次安装的时候跳过这一句。
rosdep update 与ROS安装中的rosdep init是同一个内容。
```

