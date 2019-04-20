# Java日期时间处理类


## 简介
1. java.util.Calendar类是为了替代Date类而出现的。很不幸的是，Calendar类中也有许多缺点。
1. 月份依旧是从0开始计算(不过，至少Calendar 类拿掉了由1900年开始计算年份这一设计)。
2. Calendar类也是可变的，使用起来不安全。
3. 同时存在Date和Calendar这两个类，容易使程序员产生困惑。到底该使用哪一个类呢?
    此外，有的特性只在某一个类有提供，比如用 于以语言无关方式格式化和解析日期或时间的DateFormat方法就只在Date类里有。


## java8 新的日期API介绍


* Instant——代表的是时间戳 时间戳就是计算机读的时间，它是以Unix元年(传统 的设定为UTC时区1970年1月1日午夜时分)开始算起的。
* LocalDate -- 不包含具体时间的日期
* LocalTime -- 它代表的是不含日期的时间
* LocalDateTime -- 它包含了日期及时间，不过还是没有偏移信息或者说时区。
* ZoneId -- 时区信息
* ZonedDate -- 包含时区的日期
* ZonedTime -- 包含时区的时间
* ZonedDateTime -- 这是一个包含时区的完整的日期时间，偏移量是以UTC/格林威治时间为基准的。    
* Duration -- 用于计算两个"时间"间隔 主要用于以秒和纳秒衡量时间的长短
* Period -- 用于计算两个"日期"间隔 以年、月或者日的方式对多个时间单位建模   
* DateTimeFormatter -- 格式化日期

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

## 3. 设置一个日期和时间
```java
//1.1 通过of重载的工厂方法创建

LocalDate ofDate = LocalDate.of(2014, 3, 18);//2014-03-18

LocalTime ofTime = LocalTime.of(13, 45, 20); // 13:45:20

//1.2 使用静态方法parse来创建

LocalDate parseDate = LocalDate.parse("2014-03-18");//2014-03-18

LocalTime parseTime = LocalTime.parse("13:45:20");// 13:45:20
```

## 4. 获取其他时区的日期时间
```java
// 获取美洲 罗萨里奥的时间，直接在now（）写时区，就是获得该时区的日期时间
// 获取时间参见下面时区，第2个知识点
LocalDate date1 =LocalDate.now(ZoneId.of("America/Rosario"));
LocalTime time3 =LocalTime.now(ZoneId.of("America/Rosario"));
LocalDateTime dt2 = LocalDateTime.now(ZoneId.of("America/Rosario"));
System.out.println(date1);
System.out.println(time3);
System.out.println(dt2);
```
输出结果：
```java
2019-04-19
23:00:55.880
2019-04-19T23:00:55.880
```


## 5. 计算两个日期差多少年月日
```java
// 第一种方法
// 获取当前日期
LocalDate today = LocalDate.now();
// 设置出生日期
LocalDate birthDate = LocalDate.of(1949,4,30);
// Period 计算日期的年月日，不能计算相总共差多少月或多少天，结果是xx年xx月xx日
Period p = Period.between(birthDate,today);
System.out.printf("年龄 : %d 年 %d 月 %d 天", p.getYears(), p.getMonths(), p.getDays());
System.out.println();


//第二种，计算差多少天
System.out.println(today.toEpochDay() - birthDate.toEpochDay()+ "天");



// 第三种方式
LocalDateTime d11 = LocalDateTime.of(1949,9,5,19,8,30);
LocalDateTime d12 = LocalDateTime.now();
System.out.println(d11+"与"+d12+"相差："+d11.until(d12,ChronoUnit.YEARS)+"年");
System.out.println(d11+"与"+d12+"相差："+d11.until(d12,ChronoUnit.MONTHS)+"月");
System.out.println(d11+"与"+d12+"相差："+d11.until(d12,ChronoUnit.DAYS)+"日");
System.out.println(d11+"与"+d12+"相差："+d11.until(d12,ChronoUnit.WEEKS)+"周");
System.out.println(d11+"与"+d12+"相差："+d11.until(d12,ChronoUnit.HOURS)+"时");
System.out.println(d11+"与"+d12+"相差："+d11.until(d12,ChronoUnit.MINUTES)+"分");
System.out.println(d11+"与"+d12+"相差："+d11.until(d12,ChronoUnit.SECONDS)+"秒");

```
输出结果：
```java
年龄 : 69 年 11 月 21 天
25557天
1949-09-05T19:08:30与2019-04-20T10:49:31.635相差：69年
1949-09-05T19:08:30与2019-04-20T10:49:31.635相差：835月
1949-09-05T19:08:30与2019-04-20T10:49:31.635相差：25428日
1949-09-05T19:08:30与2019-04-20T11:02:01.302相差：3632周
1949-09-05T19:08:30与2019-04-20T10:49:31.635相差：610287时
1949-09-05T19:08:30与2019-04-20T10:49:31.635相差：36617261分
1949-09-05T19:08:30与2019-04-20T10:49:31.635相差：2197035661秒
```



## 6. 就是两个时间差多少时分秒

```java
// 当前时间
LocalTime t1 = LocalTime.now();
// 设定一个时间
LocalTime t2 = LocalTime.of(23,55,30);

// 获取两个时间差，返回时分秒
Duration du = Duration.between(t1,t2);
System.out.println(du);

// 获取两个时间相差多少秒
System.out.println(t2.toSecondOfDay() - t1.toSecondOfDay()+"秒");
// 获取两个时间相差多少纳秒
System.out.println(t2.toNanoOfDay() - t1.toNanoOfDay() + "纳秒");
System.out.println(t1.until(t2,ChronoUnit.HOURS)+ "时");
System.out.println(t1.until(t2,ChronoUnit.MINUTES)+"分");
System.out.println(t1.until(t2,ChronoUnit.SECONDS)+"秒");
System.out.println(t1.until(t2,ChronoUnit.MILLIS)+"毫秒");
System.out.println(t1.until(t2,ChronoUnit.NANOS)+"纳秒");
```
输出结果：
```java
PT12H46M39.265S
46000秒
45999265000000纳秒
12时
766分
45999秒
45999265毫秒
45999265000000纳秒
```


## 7. 日期，时间，周，加减运算
```java
/**
 * 增加日期时间：plus
 * 减少日期时间：minus
 * 设置日期时间：with
 * 这些用法都类似，plusYears,minusYears,withYear 
 */

//String dateTime = LocalDateTime.now().format(DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss"));
LocalDateTime dateTime = LocalDateTime.of(2018,05,05,11,11,11);
System.out.println("原始时间："+dateTime);

// plusYears(x) 加x年
System.out.println("增加1年："+dateTime.plusYears(1));

// plusMonths(x) 加x月
System.out.println("增加1月："+dateTime.plusMonths(1));

// plusYears(x) 加x日
System.out.println("增加100天："+dateTime.plusDays(100));

// plusWeeks(x) 增加x周
System.out.println("增加10周"+ dateTime.plusWeeks(10));

// plusHours(x) 加x时
System.out.println("增加5小时："+dateTime.plusHours(5));

// plusMinutes(x) 加x分
System.out.println("增加20分钟："+dateTime.plusMinutes(20));

// plusSeconds(x) 加x秒
System.out.println("增加30秒："+dateTime.plusSeconds(30));

// minus 时间做减法运算
// minusYears(x)  减x年
System.out.println("减3年："+dateTime.minusYears(3));

//minusHours(x)   减10小时
System.out.println(dateTime.minusHours(10));

// minusWeeks(5) 减5周
System.out.println("向前5周："+dateTime.minusWeeks(5));


// with 将当前日期修改成 xxxx年xx月xx日 x时x分x秒
// withMonth 将当期日期中的月份修改成9月
System.out.println(dateTime.withMonth(9));

// withMonth 将当期日期中的日修改成20日
System.out.println(dateTime.withDayOfMonth(20));

// 两个日期比较，返回true/false
System.out.println(dateTime.equals(LocalDateTime.now()));


```












# 时区

## 1. 获取当前系统时区
```java
ZoneId zone = ZoneId.systemDefault();
System.out.println(zone);
```
输出结果：
```java
Asia/Shanghai
```      


## 2. 获取所有可用时区

> ZoneId.getAvailableZoneIds()方法，返回所有可用时区
> 
>  ZoneId：地区ID都为“{区域}/{城市}”的格式，这些地区集合的设定都由英特网编号分配机构（IANA）的时区数据库提供

```java
for (String availableZoneId : ZoneId.getAvailableZoneIds()) {
    System.out.println(availableZoneId);
}
```     
部分输出结果：
```java
Asia/Aden
Europe/Tiraspol
Atlantic/Cape_Verde
Asia/Yekaterinburg
America/Louisville
Pacific/Johnston
Pacific/Chatham
Europe/Ljubljana
America/Sao_Paulo
Asia/Jayapura
America/Curacao
Asia/Dushanbe
America/Guyana
America/Guayaquil
America/Martinique
Portugal
Europe/Berlin
Europe/Moscow
Europe/Chisinau
America/Puerto_Rico
America/Rankin_Inlet
Pacific/Ponape
Europe/Stockholm
Europe/Budapest
America/Argentina/Jujuy
Australia/Eucla
Asia/Shanghai
Universal
Europe/Zagreb
America/Port_of_Spain
Europe/Helsinki
Asia/Beirut
Asia/Tel_Aviv
Pacific/Bougainville
US/Central
Africa/Sao_Tome
Indian/Chagos
America/Cayenne
Asia/Yakutsk
Pacific/Galapagos
Australia/North
Europe/Paris
Africa/Ndjamena
Pacific/Fiji
America/Rainy_River
``` 
  
## 3. 设置时区

```java
// 设置时区为：美国/加拉加斯
ZoneId zoneId = ZoneId.of("America/Caracas");
LocalDateTime dateTime1 = LocalDateTime.now(zoneId);
System.out.println(dateTime1);
```



