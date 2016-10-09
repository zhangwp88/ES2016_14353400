# *DOL配置过程*
## 1.Description（DOL框架描述）
Distributed Operation Layer (DOL):一个软件开发框架，用于编程设计并行应用程序。它由三个部分组成：  
1.DOL应用程序编程接口  
2.DOL功能仿真  
3.DOL映射优化  
（未完待续...）

<hr>

## 2.How to install（DOL安装笔记）
* 安装必要的环境（Ubuntu）  
`$ sudo apt-get update`  
![1](http://i.imgur.com/yU4eDQD.png)  
`$ sudo apt-get install ant`  
![2](http://i.imgur.com/3zQtHxn.png)  
`$ sudo apt-get install openjdk-7-jdk`  
![3](http://i.imgur.com/u8N2gGt.png)  
`sudo apt-get install unzip`  
![4](http://i.imgur.com/oXCADnL.png)  

* 解压文件  
新建dol的文件夹  `$ mkdir dol`  
将dolethz.zip解压到 dol文件夹中  `$ unzip dol_ethz.zip -d dol`  
![5](http://i.imgur.com/1IHapsP.png)  
解压systemc  `$ tar -zxvf systemc-2.3.1.tgz`  
![6](http://i.imgur.com/8O9e7et.png)  
![7](http://i.imgur.com/mvzg6n4.png)  

* 编译systemc  
解压后进入systemc-2.3.1的目录下  `$ cd systemc-2.3.1`  
新建一个临时文件夹objdir  `$ mkdir objdir`  
进入该文件夹objdir  `$ cd objdir`  
运行configure (能根据系统的环境设置一下参数，用于编译)  `$ ../configure CXX=g++ --disable-async-updates`  
![8](http://i.imgur.com/zgj1Lm2.png)  
下图为运行configure之后的截图  
![9](http://i.imgur.com/sucIuDQ.png)  
编译  `$ sudo make install`  
![10](http://i.imgur.com/53InMhw.png)  
编译完后查看文件目录，以及查看当前的工作路径  
`$ cd ..`  
`$ ls`  
`pwd`  
![11](http://i.imgur.com/pnqbDm9.png)  
* 编译dol  
进入刚刚dol的文件夹  `$ cd ../dol`  
修改build_zip.xml文件  
![11.5](http://i.imgur.com/EBFxhXE.png)  
![19](http://i.imgur.com/LhHFNVu.png)  
编译  `$ ant -f build_zip.xml all`  
![14](http://i.imgur.com/H2o2V5A.png)  
（编译成功）
![15](http://i.imgur.com/ETweaHl.png)  
* 运行例子  
进入build/bin/mian路径下  `$ cd build/bin/main`  
运行第一个例子  `$ sudo ant -f runexample.xml -Dnumber=1`  
发现 build failed：  
![16](http://i.imgur.com/VCXWYbq.png)  
找到dol/build/bin/main下的runexample.xml，注释或者删掉几行代码  
![21](http://i.imgur.com/S7zKCrY.png)  
重新运行第一个例子  
![22](http://i.imgur.com/P1orFO0.png)  
成功，并且可以看到  
![23](http://i.imgur.com/idbgWdV.png)  

<hr>

## 3.Experimental experience（实验感想、实验心得）
* 第一次实验主要是配置dol开发环境，操作不是很多，也比较简单，以后的实验应该都要基于这个环境来进行的。刚刚接触dol，不太清楚它有什么用，会在以后的实验过程中逐步地深入地理解dol，并修改完善本文档。  
* 在配置过程中，在修改build_zip.xml文件时，由于自己的粗心大意，systemc的字母“c”被我写成了大写的“C”，如下图所示。之后build failed一直不知道是哪里出错了，于是从头开始检查，花了不少时间。今后在实验过程中一定要多加小心，尽量不犯这种低级错误。  
![13](http://i.imgur.com/vSMp2rY.png)


