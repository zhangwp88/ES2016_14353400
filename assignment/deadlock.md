# Lab4 Deadlock  
<hr>  
## 代码部分 
* class A 和 class B ：  
![代码1](http://i.imgur.com/WdVdCF5.png)  
可以看到，在类A中调用了类B的方法；在类B中调用了类A的方法。
并且两个类都有关键字synchronized修饰 :  
（1）当它用来修饰一个方法或者一个代码块的时候，能够保证在同一时刻最多只有一个线程执行该段代码。  
（2）当一个线程访问object的一个synchronized同步代码块或同步方法时，其他线程对object中所有其它synchronized同步代码块或同步方法的访问将被阻塞。  
  
* 主类 ：  
![代码2](http://i.imgur.com/aQsC1gv.png)  
我修改了bat文件，可以通过输入改变count的值 ：  
![代码3](http://i.imgur.com/lV1yEfy.png)  

<hr>  

## 执行部分 
* 运行过程截图 ：  
（1）count=2000 发生死锁  
![2000](http://i.imgur.com/Hp6IJYa.png)  
![2000死锁](http://i.imgur.com/4qIxeVu.png)  
（2）count=10000 发生死锁  
![10000](http://i.imgur.com/2aiFR6Q.png)  
![10000死锁](http://i.imgur.com/zy6hrri.png)  
（3）count=20000 发生死锁  
![20000](http://i.imgur.com/6dpgW15.png)  
![20000死锁](http://i.imgur.com/96nO79K.png)  
（4）count=30000 不发生死锁  
![30000](http://i.imgur.com/9iT0XqA.png)  
![30000不死锁](http://i.imgur.com/rRVlDKs.png)   
可以看到，在第几次发生死锁是随机的，是否发生死锁也是随机的，通过修改count的值，可能会使其发生死锁，但同一个count产生的结果也可能是不一样的。

<hr>  

## 实验感想  
* 什么是死锁：死锁就是两个或者多个进程，互相请求对方占有的资源。 
 
* 产生死锁的4个必要条件：  
互斥条件：一个资源每次只能被一个进程使用  
请求与保持条件：一个进程因请求资源而阻塞时，对已获得的资源保持不放  
不剥夺条件：进程已获得的资源，在末使用完之前，不能强行剥夺  
循环等待条件：若干进程之间形成一种头尾相接的循环等待资源关系  

* 对上述程序产生死锁的解释：  
![分析](http://i.imgur.com/0jnNDu5.png)  
如上图所示，Deadlock主类中有两条可以随时间执行的过程，一条是构造函数中的：当count--等待时间到了之后，会执行“a.methodA(b)”；一条是线程t的执行过程：当t.start()之后，线程t就被插入到调度队列里，当调度到他的时候（由操作系统决定的），就跑run()里面的代码，而run()里面的代码为“b.methodB(a)”。如果时机把握得好，a必须等待b执行完才能继续，而b也必须等待a执行完才能继续，那么就产生了死锁。（class A 和 class B 都是 synchronized ）  
通俗点来讲，如果线程1锁住了A，然后尝试对B进行加锁，同时线程2已经锁住了B，接着尝试对A进行加锁，这时死锁就发生了。线程1永远得不到B，线程2也永远得不到A，并且它们永远也不会知道发生了这样的事情。为了得到彼此的对象（A和B），它们将永远阻塞下去。这种情况就是一个死锁。  
