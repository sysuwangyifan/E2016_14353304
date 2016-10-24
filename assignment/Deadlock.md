#Deadlock
###1.死锁产生时的截图
![](http://a3.qpic.cn/psb?/V131oSoG3VPBEM/0ZmMrdqJ0ZLSlHDcnr*JqeeeY3k4q.iypFKu6UF3B8o!/b/dNoAAAAAAAAA&bo=GQFgAQAAAAADB1s!&rf=viewer_4)
###2.产生死锁的四个条件
* 互斥条件：一个资源每次只能被一个进程使用
* 请求与保持条件：一个进程因请求资源而阻塞时，自己获得的资源保持不放
* 不可剥夺条件:进程已获得的资源，在末使用完之前，不能强行剥夺
* 循环等待条件:若干进程之间形成一种头尾相接的循环等待资源关系

###3.对本次实验产生死锁的解释
在A，B两个类中都包含有两个成员函数，都被关键字synchronized修饰，在成员函数methodA（）和methodB（）中都有调用另一个类中的last（）函数。Java代码中的a.method(b)和b.method(a)是产生死锁的关键，当两个函数调用同时进入本身所拥有的method()函数而并未开始调用另一个类的对象中的last函数时，对于对象a来说由于对象b已经进入了Class B的函数method（）中，此时由于synchronized的存在对象b中的last（）函数不可用，因此a.method(b)被阻塞，而b.method(a)也因为同样的原因被阻塞，此时两个函数调用均被阻塞，于是死锁产生了。