# 第十一章 抽象类

> 问：什么是抽象类？
>
> 答：包含抽象方法的类叫做抽象类


* 背景：因为子类不听话，强制子类重写父类方法

* 作用: 抽象的本质是为了规范继承，为了继承而存在。

***

### 抽象类规则：
1. 抽象类不能被实例化，不能创建对象
2. 抽象类有构造器，方便子类继承
3. 抽象类可以有属性，抽象方法，也可以有非抽象方法
4. 含有抽象方法的类一定是抽象类
5. 如果一个类继承于一个抽象类，则子类必须实现父类的抽象方法
6. 使用abstract 修饰class

+ 不能与private、final、static关键字一起使用

### 抽象方法规则：
1. 抽象方法必须存在于抽象类中;
2. 抽象方法没有方法体，连{}花括号都没有；
3. 抽象方法必须为public或者protected（因为如果为private，则不能被子类继承，子类便无法实现该方法），缺省情况下默认为public。

***    

   
### 抽象类定义：

```java
// 定义抽象类
abstract class E{

    private String name;
    private String address;
    private int number;

    // 在抽象类中定义抽象方法
    public abstract void run();

}


// 继承E 抽象类
class Dur extends E{

    //必须重新E 抽象类的run方法
    @Override
    public void run(){

    }
}
```
   
   
   
   