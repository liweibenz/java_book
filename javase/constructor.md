
# JAVA构造器

<font color=#0099ff size=5 face="黑体">1.什么是构造器</font><br>

<table><tr><td bgcolor=#708090>
<font color=#FFD700 size=8 ><p align="center">构造器是一类特殊的成员方法</p></font>
</td></tr></table>


<font color=#0099ff size=5 face="黑体">2.构造器作用</font><br>

1. 主要作用是借助new关键字用来对新创建对象进行初始化工作
2. 第二个作用是，创建对象时进行初始化数据

<font color=#0099ff size=5 face="黑体">3.构造器特点</font><br>
1. 和类同名2
2. 没有返回方法
3. 除了上述两点外，在语法结构上与一般对方法相同


<font color=#0099ff size=5 face="黑体">4.构造器规则</font><br>

1. <font color=red>构造器可以重载</font><br>
2. <font color=red>构造器不能被继承</font><br>
3. 如果没有声明构造器，编译器就灰自动创建一个默认无参的构造器
4. 如果定义了带参数的构造器，编译器就不会为创建默认无参的构造器
5. 如果没有定义无参的构造器，企图调用无参构造器创建对象，编译器就会报错

<font color=#0099ff size=5 face="黑体">5.构造方法实例化类对象格式</font><br>



类名 对象名 = new 构造方法()
类名 对象名 = new 构造方法(实际参数)





new关键字是运行时动态分配内存的
1. 为对象分配内存空间
    1. 如果是字符就分配16位的内存空间
    2. 如果是整型就分配32位的内存空空
    3. 如果是引用数据类型分配32位的地址空间
2. 引起对象构造方法的调用
3. 为对象返回一个引用地址