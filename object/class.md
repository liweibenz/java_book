
# 类和类之间的关系

背景：

类和类之间有几种关系
1. 依赖关系
2. 关联关系
3. 继承关系
4. 实现关系


1.1 依赖关系

* 一个类充当另一个类的形式参数，一个类使用另一个类
* 临时性，关系比较弱，
* 只在一个方法内使用

2.1 关联关系
* 源于依赖关系
* 有时候需要经常性使用一个类的属性，就把这个类定义为关联关系
* 一个类作为一个类的属性
* 在类中声明，类型所有方法都可使用这个类的属性



关联关系的方向
1. 单向关系
2. 双向关联



关联关系的多重性
1. 一对一（变量）
2. 一对多（数组）


关联关系的特殊情况
1. 对于关联关系的类声明，可以在声明的时候进行初始化，叫组合关系
2. 在使用之前进行初始化，叫聚合关系






八，访问权限

1. 包

+ 类似操作系统的文件夹，提供独立的命名空间

作用：
1.1 可以将相关的类组织在一起
1.2 提供独立命名空间，解决命名冲突
1.3 包可以提供访问权限的控制

1.4 包的声明方式
对于一个java文件，第一行都会指明当类所在的包，子包用点分割
package com.test;

全限定名：是一个真实的名字，包.子包.类名

包的级别
第一级别：按照项目类型划分，com cn 互联网，org 政府，
第二级别：公司名
第三级别：项目名称
第四级别：功能模块名称

2. 引用包中的类

import 关键字

规则:
对于包内的类，可以使用简单名称，直接访问即可
对于包外的类，可以使用全限定名（只用一次），或者使用import（经常用）
import 会增加编译时间，不会增加执行时间，因为导入时在编译期间完成的
可以有多个import，在package下面，在class上面

import 包.指定类名
import 包.*  导入包下所有类，不包含子包的类

java.lang包 会被自动导入




import static 关键字

导入类中声明的静态成员，导入之后，就像在自己的代码中定义了变量一样







三、访问权限修饰符

4种访问权限修饰符

|修饰符|权限|修饰|
| --- | --- | --- |
|public|公共，任意访问| 类，接口，属性，方法，构造器|
|protected||属性，方法|
|default|只能在同包中访问|类，接口，属性，方法|
|private|只有在本类中访问|属性，方法|





构造器的访问权限





# 第九章 面向对象特征

* 概述背景：OOP

## 1. 封装

> 含义：隐藏具体实现的细节，只提供给外界调用的统一接口
> * 保护数据的安全性
> * 方便调用者调用（封装核心思想）
> 将成员变量使用private 修饰
> 使用 get方法访问，set访问设置，进行统一出入口
>


## 2. 继承
> 
> 1. 使用继承实现代码的重用性，相当于设计的时候，将公共类的的部分放到父类中，其他子类继承父类
> 2. 让子类继承父类，（private，构造器不继承，其他都继承）


继承效果：子类具有父类下的所有成员，

隐式继承：默认所有类继承object类

显示继承：使用extends关键字，一个类只能继承一个父类

```java
class Fruit{
    //水果父类
}

class Apple extends Fruit{
    //使用extends 继承父类
}
```

操作符：instanceof

对象 instanceof 父类

作用：判断对象是不是由某个类产生的
Apple apple = new Apple();
System.out.println(apple instanceof Apple);




重写（覆盖）

如果子类认为父类下的方法不够用、不适合，这时候子类可以自己实现这个方法，叫做重写

"当调用子类下的方法（重写后的方法）如果有重写调用子类的方法，如果没有调用父类的方法"

% 在子类下创建了跟父类一样的，方法名，参数，返回值，

jdk1.5 之后：
参数有泛型，可擦除类型
返回值，返回不同的类型  可替换类型




##### 6.成员变量的隐藏


属性---"重写"

如果在父类中声明了一个成员变量，在子类中也声明一个"同名"的变量，

形式：只要名称相同就是隐藏，无论类型是否相同，都会隐藏，
建议：不用使用这个功能，代码可读性查


##### 7.构造器的继承

* 7.1 继承中的构造器：构造器不是类的成员，所以不能被继承，但是可以被调用
* 7.2 调用父类构造器的时候使用super关键字调用，
* 7.2 创建子类对象的时候，一定会先运行父类构造器，相等于创建了匿名父类对象
* 7.3 super 必须放在第一行，放到下面父类构造器就会覆盖子类的内容

- supue关键字
* 继承关系中，代表父类的引用
* 1. 放在子类构造器中，放在第一行，用于调用父类构造器
* 2. super.成员变量名，在子类中引用父类的成员变量（注意权限）
* 3. super.成员方法名，在子类中引用父类的成员方法（注意权限）



##### 8. final 关键字

* 一个类不希望有子类，不希望被继承

可以修饰，
变量：不能被修改，
方法：不能被重写，
类：不能被继承

一个类被final修饰了，这个类下面的所有方法不能被重写，不能被继承


###### 9. 引用类型直接转换

* 引用类型，如果毫无关系的用户类根本无法转换

* 有继承关系的类型，如果有父子关系，继承的时候，从父类型


* 父类对象 = 子类对象（自动转换）向上造型

* 子类对象 = 父类对象（强制转换，有要求的）向下造型


父类引用子类对象
父类 aa = new 子类;

编译期：检查是否有语法错误，如果没有就将其翻译成字节码文件。即.class文件。
运行期：java虚拟机分配内存，解释执行字节码文件。
 





## 3. 多态


###### 就是一种对外表现的形式，内在具有多种具体的实现

* java 多态方式
1. 方法重载：方法
2. 方法重写
3. 多态参数：运行期的对象实现的

1、 继承

2、 子类重写父类方法

3、 父类引用指向子类对象



#### 父类引用指向子类对象 #####

父类 aa = new 子类;


    = 左边是编译器，直接创建的类型

    = 右边是运行期，真正要创建的对象


编译器：属性，静态成员（看向父类）
运行期：方法（看向子类）

java 父类引用指向子类对象时，成员变量的编译和运行都是看左边，而方法编译看左边，运行看右边。 





编译期：检查是否有语法错误，如果没有就将其翻译成字节码文件。即.class文件。
运行期：java虚拟机分配内存，解释执行字节码文件。

java编译时会做一些优化操作。第一行，因为是两个常量做运算，那么他们的结果就是确定的，
即num1的值是确定的。所以在编译时，编译器就会直接算出num1的值。第二行则不会，
java在运行时期才为变量分配内存空间。







##### 3.2 多态参数

    对于父类引用子类对象的间接使用
    将形式参数定义一个父类
    
    
在方法中将形参定义成父类类型，子类需要重新父类下的方法，程序调用时
可以将
    
   



















