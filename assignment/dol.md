# Lab3 dol实例分析&编程  
<hr>  
## example1  
* 要求：修改example1，使其输出3次方数，tips:修改square.c  
* 实验过程  
修改square.c，将**"i * i"**改为**"i * i * i"**(2次方改成3次方)  
![修改](http://i.imgur.com/maImsOf.png)  
* 实验结果  
![结果](http://i.imgur.com/YscuTbl.png)  
dot截图：  
![ex1dot](http://i.imgur.com/zKWXlw7.png)  

<hr>  

## example2
* 要求：修改example2，让3个square模块变成2个, tips:修改xml的iterator  
* 实验过程  
修改example2.xml，将value由**"3"**改成**"2"**  
![修改](http://i.imgur.com/5bk6t5c.png)  
* 实验结果  
未修改前：（3个square模块，8次方）  
![未修改前](http://i.imgur.com/6jIbFR2.png)  
修改后：（2个square模块，4次方）  
![修改后](http://i.imgur.com/gQqVGJs.png)  
dot截图：  
![ex2dot](http://i.imgur.com/iaRFOsi.png)  

<hr>  

## 实验感想  
本次实验每次修改完代码之后都要重新编译运行，具体操作为：  
    cd dol  
    sudo ant -f build_zip.xml all  
    cd build/bin/main  
    把该目录下runexample.xml第211-218行注释或者删掉（中文系统需要这一步）  
    sudo ant -f runexample.xml -Dnumber=X （X=1或者2）  
一开始做的时候，改完代码就直接执行"sudo ant -f runexample.xml -Dnumber=X"，结果不行，要先编译。而且我的Ubuntu是中文系统，每一次编译完都要去注释掉runexample.xml中的那几行，比较麻烦。不过实验内容倒是挺简单的，一个只需要把平方改成立方；一个只需要把迭代次数从3改成2。关键还是要会分析和理解代码的内容，".c"、".h"、"xml"文件都要看一看，生产者、运算模块、消费者的进程以及通道、连接等的定义都要分析一下，了解数据的变化过程和传递过程。

