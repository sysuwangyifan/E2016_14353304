# DOl开发环境配置实验报告
**14353304 王一凡 14M3  2016-10-9**
## DOL 框架描述

分布式操作层（系统）是一个软件开发框架，主要用于并行应用的开发，它允许特定的基于Kahn网络模型的应用进行计算和功能仿真，此外它提供了一个XML的规范格式来描述多处理器上并行应用的实现。

## DOL 安装笔记
###安装一些必要的环境
* sudo apt-get update 
* sudo apt-get install ant
* sudo apt-get install openjdk-7-jdk
* sudo apt-get install unzip

安装 openjdk-7-jdk 或者是  openjdk-8-jdk ，我安装了 openjdk-7-jdk但不能用，之后就安装了 openjdk-8-jdk；

安装过程中命令行显示的内容较多，此处贴出最后一句命令的部分显示结果：

![photo1](http://a3.qpic.cn/psb?/V131oSoG3VPBEM/93phNFeEVD11i3xXRCZNX2LlQ5cT7L.cNlzu2RXUPqg!/m/dAoBAAAAAAAA&bo=gQI2AgAAAAADB5U!&rf=photolist)

###解压文件

将dolethz.zip解压到 dol文件夹中

* sudo mkdir dol  
* sudo unzip dol_ethz.zip -d dol

解压systemc

* sudo tar -zxvf systemc-2.3.1.tgz  

编译systemc

* cd systemc-2.3.1
* sudo mkdir objdir （新建临时文件夹objdir）
* cd objdir
* sudo ../configure CXX=g++ --disable-async-updates (运行configure)

运行configure的结果如下图：

![photo2](http://a3.qpic.cn/psb?/V131oSoG3VPBEM/.s*k9JrUhRMlTyo5rH3P3VAQ5erwy1Awa*v3Z*62.as!/b/dHwBAAAAAAAA&bo=gQL3AAAAAAADAFE!&rf=viewer_4)

紧接着

* suodo make install

sysytemc编译完之后文件目录如下：

![photo3](http://a1.qpic.cn/psb?/V131oSoG3VPBEM/s3X6fG7v5o6ac8sMU5tlKm3pO5b2fbxlEloBiIUKy5s!/b/dHcBAAAAAAAA&bo=YQJeAAAAAAADABg!&rf=viewer_4)

记录当前工作路径

* sudo pwd

结果如下：

![photo4](http://a3.qpic.cn/psb?/V131oSoG3VPBEM/bX.9mLqT5i2hpdWfcWGj37TsONDj0DTnyrclLljGSHU!/b/dHABAAAAAAAA&bo=3gElAAAAAAADAN8!&rf=viewer_4)

进入刚刚dol的文件夹,修改build_zip.xml文件
找到下面这段话，就是说上面编译的systemc位置在哪里：
`<property name="systemc.inc" value="YYY/include"/>`
`<property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>`
把YYY改成上面pwd的文件路径结果；

编译dol文件

* sudo ant -f build_zip.xml all

结果如下图：

![photo5](http://a3.qpic.cn/psb?/V131oSoG3VPBEM/NYueXNwqMXz4X6jITLt4kUX0bHvJZ7tSG2Z49*skpKY!/b/dI8AAAAAAAAA&bo=8QFRAQAAAAADAIU!&rf=viewer_4)

接着可以试试运行第一个例子,进入build/bin/mian路径下

* cd build/bin/main

然后运行第一个例子

* ant -f runexample.xml -Dnumber=1

结果如下：

![photo6](http://a2.qpic.cn/psb?/V131oSoG3VPBEM/G7UmNIgASQMCL6R12joSW3lnoIIvDPZ7vCj0hUBq6ms!/b/dNwAAAAAAAAA&bo=YAG8AQAAAAADAPk!&rf=viewer_4)

##实验感想

整个实验中并没用遇到大的问题，一切似乎都是顺利的，直到最后一步运行测试样例1出现了问题，信息提示说是找不到javac的编译器，我对这些其实是不太了解的，后来知道可以重装了jdk，因为我一开始装的是openjdk-7-jdk
所以我还是重新装了它，但是问题依然没有解决，后来在网上看到有不同的版本就尝试装了openjdk-8-jdk，问题就得到了解决。

 