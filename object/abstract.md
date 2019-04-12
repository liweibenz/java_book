# 第十一章 抽象


    抽象的本质是为了规范继承
    
### 作用：只是为了继承类，不能创建对象

* 抽象类不能被实例化
* 抽象类有构造器，方便子类继承
* 抽象类可以有属性，可以有抽象方法，也可以非抽象方法
* 含有抽象方法的类一定是抽象类
* 抽象类作为基类，所有继承了抽象类的子类必须重写抽象方法

目的是为了让子类继承，利用多态参数，实现调用子类下的方法



## 抽象方法

    什么是抽象方法？
    答：抽象方法必须存在于抽象类中;
    抽象方法没有方法体，连{}花括号都没有；
    
   作用：强制使用多态参数
   
   正好与final相反，final就是为了不继承
   
   
   
## 定义

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
   
   
   
   