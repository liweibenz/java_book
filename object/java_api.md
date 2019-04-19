# 第十七章 Java常用API


## 1.Math 数学计算

* 在java.lang包中

1. // 产生0-1的随机数，包含0，不包含1
     System.out.println(Math.random());
2. 
3. ceil 向上取整  ceil(4.8)  // 返回 5.0
4. floor 向下取整 floor(4.8) // 返回 4.0
   


## 2. Date 日期计算（大部分方法已放弃）





new Date() 获取当前时间


* date.getTime()
距离1970年1月1日 00:00:00 开始到现在的毫秒数

* 日期类型格式化类：SimpleFormatter

年：yyyy
月：MM
日：dd
时：HH （hh：12小时制）
分：mm
秒：ss


* 将date类型转换成字符 format方法

* 将字符串转date类型 parse方法(必须用try 捕获异常)



* 格式化日期 format方法
```java
        Date date = new Date();
        SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        System.out.println(sdf.format(date));

``` 

* 将字符串转成日期格式：parse方法
```java
        Date date = new Date();
        SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        System.out.println(sdf.format(date));

        String dd = "2019-04-17 10:36:00";
        try {
            sdf.parse("2019;04-17 10:36:00");

        } catch (ParseException e) {
            System.out.println("no");

        };
```



## 3. Calendar 日历计算（正在使用的日期处理类）


1. 日期加减



## 4. Random

* 随机产生类，提供很多随机的方法

1. 返回随机数
        Random r = new Random();
        // 返回在int范围内的随机数
        System.out.println(r.nextInt());
        // 返回0-x区间的随机数
        System.out.println(r.nextInt(42));
        
2. 




## 5. Scanner 扫描键盘输入类



## 6. BigInteger 大整数类

* 使用方法加减乘除

1. 
2. 
3. 
4. 

```java
        BigInteger b1 = new BigInteger("88888888888888888888");
        BigInteger b2 = new BigInteger("3453542345234565456");

        // 加法
        System.out.println(b1.add(b2));
        // 减法
        System.out.println(b1.subtract(b2));
        // 乘法
        System.out.println(b1.multiply(b2));
        // 除法
        System.out.println(b1.divide(b2));
        // 取余
        System.out.println(b1.mod(b2));
```
        
        
        
## 7. 国际化

* 背景：当程序中需要使用不同的语言，可以通过国际化进行编码统一，防止乱码

需要使用的类：
1. java.util.Locale 封装了特别国际的语言环境，（CN-zh，US-en 国际-语言）
2. java.util.ResourceBundle 用来加载一个国际语言的资源包

* 【资源】采用properties文件存储资源，需要显示的信息

标记
name="名字"

 
 

* 实现
1. 产生一个资源文件，默认语言资源文件，指定语言的资源文件
    * 默认资源文件，文件名.properties，没有指定locale就会加载这个默认资源文件
    * 指定语言的资源文件： 文件名_zh_CN.properties 
    
2. 通过locale指定资源文件，使用构造器指定 new Locale（语言，国际）两个参数    

3. 通过ResourceBundle调用资源文件中的内容


* 调取资源文件，调用=左边的名字，显示=右边的内容










        




