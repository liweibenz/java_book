
## 什么是变量？

* 是计算机语言中能储存计算结果或表示值的抽象概念
* 变量相当于有名字的容器，该容器用于装载不同类型的数据
* 每一个变量都代表了一小块内存，都有一个内存地址与变量名对象



## 变量有什么用？

> 变量作为程序寻找内存中所存放的数据时的一个标签,它的作用是告诉程序，你应该去内存中的哪个地方寻找接下来要用到的数据。

## 变量分类

按范围分：

* 局部变量
* 成员变量(全局变量)

按数据类型分：
* 基本数据类型变量
* 引用数据类型变量

### 局部变量

> 规则：在方法内声明

声明语法：
```java
//数据类型 变量名 = 变量值;
int a = 3;
```

### 成员变量
> 规则：在类中声明，声明的时候可以不初始化

声明语法
```java
//数据类型 变量名;
int a;
String str;

//数据类型 变量名 = 变量值;
int a = 3;
```



### 常量

> 规则：
> * 使用final关键字修饰
> * 变量名全部大写
> * 变量一旦声明变量值就不能修改

声明语法
```java
final int YY = 5;
```
