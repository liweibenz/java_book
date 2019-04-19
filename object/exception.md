# 第十八章 异常

## 1. 什么是异常：
1. 受检异常：在编译期可以预见的异常，这种异常必须进行异常捕获
2. 运行期异常：可以称为bug，可以处理，也可以不处理
3. 错误，不能捕捉

编译器：执行javac命令 如果受检异常，不捕捉，成绩就会出错
运行期：执行java命令，如果错误会抛出异常

什么是受检异常？
编译期检查不到可能存在的错误，如果运行错误会影响程序运行





## 2. 常见异常类型

* 所有的异常类型，也是继承object类
* 所有的问题，都继承了Throwable类 包含两个子类 error 和 exception 
* exception子类包含"受检异常类"，"运行期异常类"子子类

1. ArithmeticException 数学计算异常 运行期异常
2. IllegalArgumentException 非法参数异常，接收方法参数时
3. ArrayIndexOutOfBoundsException 数组下标越界异常 运行期异常
4. NullPointerException 空指针异常，调用空引用的时候出现，运行期异常
5. ClassNotFoundException 不能加载所需的类
6. NumberFormatException 格式化异常，运行期异常
7. FileNotFoundException 文件找不到异常


3. 异常的处理

* 当异常产生的时候，程序会在异常产生的位置，创建一个关于异常类型的对象，
    对象包含了异常信息，异常堆栈
* 程序出现异常不会终止，程序会从上下文寻找异常的程序，如果成功捕获了异常，继续运行异常
* 如果没有成功捕获，异常"向上传播" 方法a调用了方法b， a称为上，b称为下
* 宗旨：谁调用谁处理

1. 捕获异常
2. 抛出异常


1. 捕获异常语法
```java
        try{
            // 可以能会产生异常的代码段
        }catch (异常类型 参数){
            // 处理异常代码
            
        }catch (异常类型 参数){
            // 处理异常
        }
        
```
    1. try中代码正常运行，不会走catch语句
    2. try中产生了异常，某一个catch捕获了异常，try catch之外的代码正常执行
    3. try中产生了异常，catch没有成功捕获异常，代码不执行，向上抛出
    4. catch可以有多个，从上到下依次匹配，只要匹配成功就不会在匹配了。
    5. 合并异常，当认为多个异常类型可以做到
    6. 有父子关系的异常，一定要让子类异常在上，父类异常在下
           

* 在日常开发中，将异常放在调用端处理异常，不同的调用者处理的方式不同。
* try catch 能捕获的只有运行期异常


2. finally 
* 作用：任何情况下都运行语句，不管程序中是否发生了异常，是否成功的捕获了异常
* 可以组合使用
* try{} catch(){} finally{}       
* try{} finally{}   
* 除非退出虚拟机finally才不会执行

* 【finally使用场景】
    1. 资源被打开之后，占用内存，结束时一定要释放资源
    2. 数据库连接的时候
   
   

## 3. 抛出异常
* 在某个条件符合的时候，使用throw new创建异常对象--抛出异常
* 如果主动抛出异常是在方法中，在方法定义的尾部thr\关键字，异常类型，
    要求调用方法的人必须抛出这种异常
    
【使用】
1. 可以在catch中使用,不掩盖函数定义时异常的出现
```java
	public static void test(){
		try{
			int i =1/0;
		}catch(ArithmeticException e){
			System.out.println("ArithmeticException");
			// 异常设置
			throw new ArithmeticException();
		}
	}


```

2. 直接使用throw 主动抛出使用

主动抛出异常
```java
      Day11 day11 = new Day11();
        day11.regist(-10);
        day11.browse();
    }
    public void regist(int age) {
        if (age > 0) {
            System.out.println("成功注册");
        }else {
            System.out.println("年龄不符合");
            throw new IndexOutOfBoundsException("出错了");
        }
    }

    public void browse() {
        System.out.println("浏览网页");
    }
```


* 强制调用者捕获异常，在方法参数后面添加throws Exception
```java
    public void regist(int age) throws Exception {
        if (age > 0) {
            System.out.println("成功注册");
        }else {
            System.out.println("年龄不符合");
            // 受检异常
            throw new Exception("出错了");
        }
    }
```    


4. 重写

* 子类方法不能抛出比父类更多的受检异常



5. 自定义异常

* 一旦我们的业务非常复杂，自定义一些符合业务需求的异常类型
* 如果希望自定义运行期异常，继承RuntimeException
* 如果希望定义受检异常，继承Exception
* 不管定义什么异常，必须使用Exception结尾

【语法】
class 自定义异常类型 extends Exception{
    // 一般使用写两个构造器，使用方便
    // 一个无参数构造器
    // 一个有参数构造器（错误信息）
}



异常处理情况
1. 继承了exception的类是受检异常
2. 继承了runtimeexcept的类是运行期异常
3. 自定义受检异常，意味着你的方法不负责处理这种异常，而是强制调用者处理
4. 自定义运行期异常，意味着你自己负责处理某一种异常



【异常的优势】
1. 将可以能产生错误的代码分离
2. 可以将异常向上传播，调用者可以根据自己的需求来处理异常
3. 异常类型明确，可以继承，异常分类处理，可以清楚的分出不同异常类型，不同异常类型就可以使用不同的方式处理

    



    
        









