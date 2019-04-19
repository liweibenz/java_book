# Java日期时间处理类

> Java 8之前的Date(大部分方法已弃用)和Calendar都是线程不安全的，而且使用起来比较麻烦
> 
> Java 8提供了全新的时间日期API

* Instant——代表的是时间戳 时间戳就是计算机读的时间，它是以Unix元年(传统 的设定为UTC时区1970年1月1日午夜时分)开始算起的。

* LocalDate——不包含具体时间的日期
* LocalTime——它代表的是不含日期的时间
* LocalDateTime——它包含了日期及时间，不过还是没有偏移信息或者说时区。

* ZoneId
* ZonedDate -- 包含时区的日期
* ZonedTime -- 包含时区的时间
* ZonedDateTime——这是一个包含时区的完整的日期时间，偏移量是以UTC/格林威治时间为基准的。    
* Duration 用于计算两个"时间"间隔 主要用于以秒和纳秒衡量时间的长短
* Period   用于计算两个"日期"间隔 以年、月或者日的方式对多个时间单位建模   
* DateTimeFormatter  格式化日期

https://cloud.tencent.com/developer/article/1350262
https://cloud.tencent.com/developer/article/1379447
https://cloud.tencent.com/developer/article/1378091



        *** 以下所有代码都可以直接拿到main方法中运行 ***

    
## 1.获取当前日期，时间，日期和时间
```java
// 当前日期
LocalDate d1 = LocalDate.now();
// 当前时间
LocalTime d2 = LocalTime.now();
// 当前日期和时间
LocalDateTime d3 = LocalDateTime.now();

System.out.println(d1);
System.out.println(d2);
System.out.println(d3);

```

输出结果:

```java
今天日期：2019-04-18
当前时间：13:52:57.336
日期时间：2019-04-18T13:52:57.336
```

## 2.获取单独的年月日
```java
// 当前日期
LocalDate d1 = LocalDate.now();
// 获取年
int yaer = d1.getYear();
// 获取月
int month = d1.getMonthValue();
// 获取日
int day = d1.getDayOfMonth();
System.out.println("今天是："+yaer+"年"+month+"月"+day+"日");
```
输出结果：
```java
今天是：2019年4月18日
```

## 3. 计算两个日期差多少年月日




