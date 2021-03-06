# 第十九章 泛型

* 背景：在jdk1.5之前没有泛型，为了让集合能够处理各种类型数据，而产生了泛型
    在jdk1.5之后出现了泛型，引用了C++的泛型
    1.5之前 list集合可以放入object

> 什么时候定义泛型类？
> 
> 当类中要操作的引用数据类型不确定的时候,适合定义泛型类型


原生类型：1.5以前用object解决
泛型类型：1.5以后出现的    
    
    
* 作用：
    1. 创建对象的时候声明泛型，    
    2. 方法定义的时候，声明形式参数
    3. 【本质】将所操作的数据类型指定一个参数类型，也被称为：参数化类型
    * 解决了元素安全的问题
    * 解决了元素取出，不需要强制转换的问题
    
* 使用范围：
    1. 接口
    2. 类
    3. 方法

    
* 语法
```java

List<String> list = new ArrayList<String>();

```      
    
  
List接口
ArrayList实现类

* add 添加元素
* get 获取元素    




* 语法：
```java
    //泛型定义在接口上   
interface Inter<T>
{
    void show(T t);
}
```    

对于泛型来说，在使用的时候，如果没有提供<> 叫原生泛型
如果提供了<> 叫参数化类型

* 原生类型与参数化类型转换
    * 原生类型直接赋予泛型类型，不可以
    * 泛型类型赋予原生类型，可以
    
### 应用
1. 创建对象的 容器类
2. 充当形式参数

一、泛类型应用

```java

package cn.blk5.Day12;

// 1.	定义一个泛型类盒子Box<T>,属性width和height, 调用验证可支持Integer,Double,String等等类型。（也就是能够放入到box中的内容都必须是指定的类型）

/**
 *
 * @author: LIWEI
 * @updateTime: 2019-04-19 08:43
 * @version: 1.0
 * @description: 泛型类 测试
 *
 */

class Box<T>{

    private T width;
    private T height;

    public T getWidth() {
        return width;
    }

    public void setWidth(T width) {
        this.width = width;
    }

    public T getHeight() {
        return height;
    }

    public void setHeight(T height) {
        this.height = height;
    }
}

public class Day12_class {



    public static void main(String[] args) {

        // 创建一个box对象
        Box box = new Box();
        // 创建一个Interger对象
        Box<Integer> aa = new Box<Integer>();
        Box<String> bb = new Box();
        box.setHeight("88888");
        box.setWidth(9999);

        aa.setHeight(5555);
        bb.setHeight("44");
        System.out.println(aa.getHeight());
        System.out.println(bb.getHeight());
        
        System.out.println("高度："+box.getHeight()+ "宽度："+box.getWidth());
        
    }
}

```

二、泛方法
```java
package cn.blk5.Day12;
/**
 *
 * @author: LIWEI
 * @updateTime: 2019-04-19 09:02
 * @version: 1.0
 * @description:  非泛型类中定义泛型方法
 *
 */
public class Day12_method {

    // 泛型方法，在返回类型前面使用泛型字母
    public static <T>  void test1(T t){
        // 传入任何基本类型的数据都可以输出
        System.out.println(t);
    }

    public static void main(String[] args) {

        test1("asdfasdfasfd");
        test1(4.345);
        test1(false);
        test1(55534.34534534F);

    }
}
```

三、泛接口
```java








```











    
### 自定义泛型

语法
1. class 类名<大写字母 E [extends 父类]》>
    可以是E类型，包含父类的类型
2. E：代表一种抽象类型，可以任意定义，下面是习惯性命名方式
T：tyep
E：element
K：key
V：value    



### 泛型继承

1. 当定了一个类型，如果这类型有父类型，那么这个
2. 泛型类型不保持原有的继承关系
3. 可以多继承List<? extends X&Y> 代表同时继承



### 泛型通配符

1. 无界通配符：?  定义 List<?>
2. 上限通配符：List<? extends X>  可以接收E类型或者E的子类型--写父类-带子类
3. 下限通配符：List<? super X>    可以接收E类型或者E的父类型--写子类-带父类

   

### 泛型擦除

* 背景：java中的泛型是仿照C++的泛型，在编译期过后，运行时素有的泛型参数会丢失
    编译期取的元素类型，取泛型擦除之后的类型
   
        C++泛型在编译期和运行期都有效



1. 关于重载方法中的泛型




2. 关于方法重写-泛型规则
    1. 参数：要求参数类型一样，如果泛型类型擦除之后一样也可以
    2. 如果父类擦除后跟子类一样，算是重载
    3. 如果子类擦除后跟父类一样，报错，不算重载


    
    
    

