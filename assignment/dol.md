#DOL实例分析&编程实验报告
##example1
通过修改square.c实现输出结果为相应数字的3次方

	DOL_read((void*)PORT_IN, &i, sizeof(float), p); 
	i = i*i*i;  (将i = i*i; 替换为 i = i*i*i;)    
 	DOL_write((void*)PORT_OUT, &i, sizeof(float), p);
 	p->local->index++;
 
运行结果如下图：

![](http://a1.qpic.cn/psb?/V131oSoG3VPBEM/TSFOZqPKc6AVk7Q2ajJ1Xw3.8Mfv9p.kK5WobsvRuLA!/b/dAsBAAAAAAAA&bo=zAHBAQAAAAADBy8!&rf=viewer_4)

相应的dot图：

![](http://a2.qpic.cn/psb?/V131oSoG3VPBEM/yqhHzQDuM15jB0DiA8P2PA1G3rXCa18pxrQtRfXK7*s!/b/dNwAAAAAAAAA&bo=7QGmAAAAAAADB2g!&rf=viewer_4)


通过修改example2.xml,通过减少square模块的个数，实现输出结果为相应数字的4次方

 	将<variable value="3" name="N">  变为下面
	<variable value="2" name="N">

运行结果如下图：

![](http://a3.qpic.cn/psb?/V131oSoG3VPBEM/9qftVmKaLAQVRstgN7.Q8ZZDetLZtm38viwpMP0ZXaI!/b/dOMAAAAAAAAA&bo=7gG.AQAAAAADB3I!&rf=viewer_4)

相应的dot图：

![](http://a2.qpic.cn/psb?/V131oSoG3VPBEM/XRJXjsVR*IxExNYn3dPaYSvI.GWDizLU3n9Yp5GxY2Y!/b/dAkBAAAAAAAA&bo=PgP0AAAAAAADB.s!&rf=viewer_4)

##实验感想

通过对DOL两个实例的分析，我对它们的结构有了大致的了解，包括不同的模块的作用，它们在代码中基本的构成方式，以及不同的模块之间是如何连接的。实验内容十分简单，但可以让我更加深刻的了解DOL的工作方式，同时对实验一中DOL的编译以及运行等步骤有了一些简单的复习。