# ROS install
# 一，官方源
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

# 二，清华源
## 安装步骤
- [blog-1: ROS Melodic 版本安装+将ROS的源设置为国内的源](https://blog.csdn.net/qq_38649880/article/details/99563189)
- 如上文中所写，改用清华源，install过程中的下载速度会极大提升，整个安装过程除了第1，2步换用清华源，setup key 参考[blog-1]外，其他所有步骤均按照下方官方文档！
- [Ref官方文档](http://wiki.ros.org/melodic/Installation/Ubuntu)

## 出现的问题
- 1.sudo rosdep init报错
```
ERROR: cannot download default sources list from:
https://raw.githubusercontent.com/ros/rosdistro/master/rosdep/sources.list.d/20-default.list
Website may be down.
```
查看是否存在/etc/ros/rosdep/sources.list.d/20-default.list文件，不存在则手动添加，参考：</br>
[手动添加20-default.list文件](https://www.jianshu.com/p/bdbfbac69114)
再次执行sudo rosdep init，仍报错，无视报错。

- 2.rosdep update报错
```
reading in sources list data from /etc/ros/rosdep/sources.list.d
ERROR: unable to process source [https://raw.githubusercontent.com/ros/rosdistro/master/rosdep/osx-homebrew.yaml]:
    <urlopen error [Errno 111] Connection refused> (https://raw.githubusercontent.com/ros/rosdistro/master/rosdep/osx-homebrew.yaml)
ERROR: unable to process source [https://raw.githubusercontent.com/ros/rosdistro/master/rosdep/base.yaml]:
    <urlopen error [Errno 111] Connection refused> (https://raw.githubusercontent.com/ros/rosdistro/master/rosdep/base.yaml)
ERROR: unable to process source [https://raw.githubusercontent.com/ros/rosdistro/master/rosdep/python.yaml]:
    <urlopen error [Errno 111] Connection refused> (https://raw.githubusercontent.com/ros/rosdistro/master/rosdep/python.yaml)
ERROR: unable to process source [https://raw.githubusercontent.com/ros/rosdistro/master/rosdep/ruby.yaml]:
    <urlopen error [Errno 111] Connection refused> (https://raw.githubusercontent.com/ros/rosdistro/master/rosdep/ruby.yaml)
Hit https://raw.githubusercontent.com/ros/rosdistro/master/releases/fuerte.yaml
Query rosdistro index https://raw.githubusercontent.com/ros/rosdistro/master/index-v4.yaml
Add distro "ardent"
ERROR: error loading sources list:
    <urlopen error <urlopen error [Errno 111] Connection refused> (https://raw.githubusercontent.com/ros/rosdistro/master/ardent/distribution.yaml)>
```
注意错误类型是“Connection refused”，并不是“time out”(一里面有处理方法)，也不是“error _ssl.c: 或者"urlopen error [SSL: ..."(这种错误参考：https://www.jianshu.com/p/bdbfbac69114 和  https://zhuanlan.zhihu.com/p/77483614)

[Connection refused 处理参考blog](https://blog.csdn.net/mrh1714348719/article/details/103803110)

- 3. 上述两种问题均是由于换 ROS源引发的，但实际使用上，换用源之后的顺畅度大大提升，换源更理想一些。

