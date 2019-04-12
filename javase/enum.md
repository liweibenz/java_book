# 枚举类型


* 历史：枚举是JDK1.5版本新增的特性(泛型、For-each等如今被广泛应用的特性也是由JDK1.5时所新增的)
另外到了JDK1.6后switch语句支持枚举类型。

* 背景：有时候我们需要很多常量来完成工作，一个一个常量写非常麻烦。

* 作用：为了规范常量代码而设计的，一定程度上减少bug，防止字段值被修改


## 枚举类型定义

1. 使用enum关键字声明一个枚举类
2. 内部直接声明常量（变量名需要大写）
```java
enum EnumTest {
    MON, TUE, WED, THU, FRI, SAT, SUN;
}

```



## 枚举应用

枚举支持switch case，
原因：case后面必须放常量




* 枚举默认构造器是私有的
* 不能继承其他类，默认 隐式继承了Enum类
* 枚举类型可以实现接口(对于每个枚举类型的常量都可以实现接口，用的很少)




#### 循环显示枚举
```java
 enum EnumTest {
    MON, TUE, WED, THU, FRI, SAT, SUN;
}
 
   for (EnumTest day : EnumTest.values()) {
            System.out.println(day);
        }
        
        
```

> 可以把 enum 看成是一个普通的 class，它们都可以定义一些属性和方法，
> 不同之处是：enum 不能使用 extends 关键字继承其他类，
> 因为 enum 已经继承了 java.lang.Enum（java是单一继承）。

反编译java class文件

1. javap name.class
2. java -private name.class




