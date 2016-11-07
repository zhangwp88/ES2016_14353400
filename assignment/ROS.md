# Lab5 ROS  
<hr>  
## ROS简介  
* **ROS**：Robot operation system， 一套框架，底层提供硬件驱动，软件层面支持通用的文件格式。我们可以在Ubuntu中使用它的仿真功能。  

<hr>  

## 安装ROS 
注：Ubuntu系统为14.04 （安装过程忘记截图了...）  
参考网址：[http://wiki.ros.org/jade/Installation/Ubuntu](http://wiki.ros.org/jade/Installation/Ubuntu "安装教程")  
参考网址（中文版）：[http://wiki.ros.org/cn/jade/Installation/Ubuntu](http://wiki.ros.org/cn/jade/Installation/Ubuntu "安装教程（中文版）")  

* 配置过程 ：  
一步一步跟着教程走就可以了：  
1.配置 Ubuntu 软件仓库  
默认就是允许 "restricted"、"universe" 和 "multiverse"这三种安装模式，所以不需要更改。  
2.添加 sources.list  
    sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'  
3.添加 keys  
    sudo apt-key adv --keyserver hkp://pool.sks-keyservers.net --recv-key 0xB01FA116  
4.安装  
先执行`sudo apt-get update`  
安装桌面完整版：  
![桌面完整版](http://i.imgur.com/WwjdiN7.png)  
5.初始化 rosdep  
    sudo rosdep init  
    rosdep update  
6.环境配置  
    echo "source /opt/ros/jade/setup.bash" >> ~/.bashrc 
    source ~/.bashrc  
7.安装 rosinstall  
    sudo apt-get install python-rosinstall  
8.最后一步，获取安装包源码  
    apt-get source ros-jade-laser-pipeline  
前面都很顺利，最后一步的时候出错了，错误信息如下：  
![错误提示](http://v1.freep.cn/3tb_161107190313b81e512293.png)  
根据TA的提示，使用蓝灯翻墙、换源都不行，所以只能做到这一步了，没办法安装cartographer  

<hr>  

## 实验感想  
* 本次实验的任务是配置ROS，基本上按照网上的教程走一遍就行了，安装过程还挺久的，除了最后一步失败之外都很顺利。到现在都不知道最后一步失败应该怎么解决，TA们没有给出解决方法，在网上也没有查到相关的资料，所有教程关于最后一步的描述都是一笔带过，好像不会出现什么问题那样。所以就止步于此，不继续安装cartographer了，因为不知道会有什么影响。ROS安装配置好之后也不知道怎么使用，等以后要用到的时候再慢慢研究~  


