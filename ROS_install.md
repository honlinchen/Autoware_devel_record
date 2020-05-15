# ROS install

## 1. install :
- [ROS Melodic 版本安装+将ROS的源设置为国内的源](https://blog.csdn.net/qq_38649880/article/details/99563189)
- 如上文中所写，改用清华源，install过程中的下载速度会极大提升，
- [Ref官方文档](http://wiki.ros.org/melodic/Installation/Ubuntu)
- [Ref blog](https://blog.csdn.net/leonardohaig/article/details/82813738)

## 2. 可能出现的Err

### 2.1  apt-key引发的错误
```
报错时: 
chl@chl:~$ sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
Executing: /tmp/apt-key-gpghome.NfurFOZBUR/gpg.1.sh --keyserver hkp://keyserver.ubuntu.com:80 --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
gpg: key F42ED6FBAB17C654: "Open Robotics <info@osrfoundation.org>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

正确时：
chl@chl:~$ sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 421C365BD9FF1F717815A3895523BAEEB01FA116
Executing: /tmp/apt-key-gpghome.yS6J3IPYF6/gpg.1.sh --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 421C365BD9FF1F717815A3895523BAEEB01FA116
gpg: key 5523BAEEB01FA116: public key "ROS Builder <rosbuild@ros.org>" imported
gpg: Total number processed: 1
gpg:               imported: 1

解决方式：下列两个key，一个出错就换另一个
sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 421C365BD9FF1F717815A3895523BAEEB01FA116
```
### 2.2 连接的问题
```
错误: http://packages.ros.org/ros/ubuntu bionic/main amd64 libgazebo9 amd64 9.0.0+dfsg5-3ubuntu1+ppa2
 无法连接上 117.128.6.20:80 (117.128.6.20)，连接超时
  or
E: 无法下载 http://117.128.6.30/cache/packages.ros.org/ros/ubuntu/pool/main/r/ros-melodic-actionlib-tutorials/ros-melodic-actionlib-tutorials_0.1.11-0bionic.20200320.123237_amd64.deb?ich_args2=506-15114205043928_579e480f33154fd1e38ac2ab38eb1e9e_10001002_9c896c2adec1f3d09032518939a83798_a699ee352b68c54d96d9b2efd5abb6a6  无法连接上 117.128.6.30:80 (117.128.6.30)，连接超时
 
 分析：可能是Ubuntu 源设置的问题，或者网络的问题
 Ubuntu源设置为下图：
 ```
![](https://github.com/honlinchen/Autoware_devel_record/blob/master/md_images/Screenshot%20from%202020-04-15%2021-00-10.png)
        
        apt-key语句执行成功后，下图中的设置会自动完成
![](https://github.com/honlinchen/Autoware_devel_record/blob/master/md_images/Screenshot%20from%202020-04-15%2021-00-22.png)

##  some cmd analyse
```
1. rosdep : tools and other dependencies for building ROS packages
2. sudo rosdep init:  Wrote /etc/ros/rosdep/sources.list.d/20-default.list
   sudo rosdep init  （安装一次后只能运行一次，若重新安装选择跳过或删除该文件，并再次执行此语句）
   rosdep update
3. 构建包所需的依赖 rosinstall:创建和管理你自己的 ROS workspace，还有单独发布的许多的工具。
比如，rosinstall 是一个常用的命令行工具，使你可以通过一个命令为 ROS 包简单地下载许多源码树。



```

- [rosdep update更新不了问题解决——第1步](https://blog.csdn.net/nidie508/article/details/104156378)
- [rosdep update一直timeout的问题——第2步](https://blog.csdn.net/qq_38649880/article/details/87903654)可以
- 上面都设好之后需要多次耐心运行rosdep update ，还是不行的话换个网络再试，还是不行的话，早上早点起来(7-8点)接着试。这个问题没有什么好办法，上面的两步操作可以大大提高成功率。
## wheather succeed

[Ref blog](https://blog.csdn.net/weixin_43288132/article/details/104613544)

