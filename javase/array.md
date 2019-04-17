# Java数组

> 什么是数组？
>
> 答：用来存储一组固定长度和相同类型元素的数据称为数组
>


> 数组的作用？
> 
> 用来快速读取一组相同类型的数据
>


## 一、规则：
1. 数组长度一旦确定不可变
2. 数组中必须是相同数据类型的元素
3. 数据元素索引，下标从0开始，从左向右数
4. 数组是引用数据类型，数据存在堆内存中

优点：
* 逆序访问数组foreach做不到
* 访问数组中一部分元素做不到
* 在遍历数组元素时，希望修改元素数据做不到


## 二、声明


#### 1. 数组声明和初始化

* 静态声明：声明的时候直接初始化数据
* 动态声明：声明的时候指定数组长度


```java

// 静态声明
int[] arr = {1,2,3,4,5};

// 动态声明
int[] arr = new int[10];

```
 
#### 2.数组内存结构

* 数组属于引用类型，数据存在堆内存中，数组内存地址存到栈内存中
* 数组对象中最后一个元素，存储的length（数组长度）


#### 3.数组访问及遍历

3.1 for循环

```java
// 普通循环
int[] arr = {3,6,1,3,8,9,22,-45,77,-80};
for (int i = 0; i < arr.length; i++) {
    System.out.println(arr[i]);
}
```

3.2 增强for循环


```java
int[] arr = {1, 2, 3, 4};
for (int i : arr) {
    System.out.println(i);
}
```        

数组默认值：
* 整形数组：默认值是0
* 浮点数类型：默认值是0.9
* 字符类型：默认值'\u0000'
* boolean类型：默认值false
* 引用类型：默认值是null（String[] s = new String[3] --> null,null,null）



#### 4.数组修改

```java
 // 修改元素
 // 数组下标 = 值
 arr[0] = 100;


// 普通循环
int[] arr = {3,6,1,3,8,9,22,-45,77,-80};
// 修改元素
arr[0] = 100;
for (int i = 0; i < arr.length; i++) {
    System.out.println(arr[i]);
}

```




#### 5.数组排序


* 选择排序

核心思想：假定一个最大或最小值，每次选择一个最大或最小放到数组前面，找到就位置交换
```java
// 标准选择排序
int[] arr = {993, 6, 11, 3, 78, 9, 22, -45, 77, -80};
for (int i = 0; i < arr.length - 1; i++) {
    int a = arr[i];
    for (int j = i + 1; j < arr.length; j++) {
        if (arr[i] > arr[j]) {
            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
        }
    }
    System.out.println(Arrays.toString(arr));
}


// 优化选择排序
for (int i = 0; i < arr.length - 1; i++) {
    int min_index = i;
    for (int j = i + 1; j < arr.length; j++) {
        if (arr[i] > arr[j]) {
            // 找最小值索引
            min_index = j;
        }
    }
    // 找到最小值索引之后再交换位置
    int temp = arr[i];
    arr[i] = arr[min_index];
    arr[min_index] = temp;
    System.out.println(Arrays.toString(arr));
}
        
```        



* 冒泡排序
核心思想：两两进行比较，如果不符合（最大或最小）就交换位置

```java

boolean flag = true;
for (int i = 0; i < arr.length; i++) {
    for (int j = 0; j < arr.length - i - 1; j++) {
        if (arr[j] > arr[j + 1]) {
            int temp = arr[j];
            arr[j] = arr[j + 1];
            arr[j + 1] = temp;
            flag = false;
        }
    }
    if (flag) {
        break;
    }
}
System.out.println(Arrays.toString(arr));
```





#### 6. Arrays工具类

1. sort/parallelSort 排序


作用：原地排序，就是在原来的数组上进行排序，原数组发生变化

也可以选择区间进行排序，指定起始index

```java
int[] arr = {993, 6, 11, 3, 78, 9, 22, -45, 77, -80};
Arrays.sort(arr);
System.out.println(Arrays.toString(arr));

// 区间排序
Arrays.sort(arr,3,8);
System.out.println(Arrays.toString(arr));
```

parallelSort：jdk1.8之后的新特效，并行排序，利用多核cpu的性能


2. binarySearch 折半查找（必须是排好序的数组）

返回值：排序后的索引位置,如果找不到就随机返回一个负数

```java
int[] arr = {993, 6, 11, 3, 78, 9, 22, -45, 77, -80};
Arrays.sort(arr);
int a = Arrays.binarySearch(arr,9);
System.out.println(a);
```
3. equals 判断两个数组长度和内容是否一致

返回值：Boolean类型
```java
int[] arr = {993, 6, 11, 3, 78, 9, 22, -45, 77, -80};
int[] arr1 = {993, 6, 11, 3, 78, 9, 22, -45, 77, -80};
System.out.println(Arrays.equals(arr,arr1));
```


4. fill 填充数组

也可以指定起始索引位置

```java
int[] arr = new int[6];
Arrays.fill(arr,3);
System.out.println(Arrays.toString(arr));
```

5. toString 转换字符串

上面的例子都是用toString打印数组的



#### 7. 数组复制

三种方式：
1. System.arraycopy();
* 第一个参数：源数组
* 第二个参数：复制开始的位置
* 第三个参数：目标数组
* 第四个参数：复制开始的位置
* 第五个参数：复制长度

```java
int[] arr = {3,4,5,6,7,8,3,2,2};
int[] rra = new int[6];
System.arraycopy(arr,0,rra,0,5);
System.out.println(Arrays.toString(rra));
```


2. Arrays.copyOf()

如果下表越界，不会报错，使用默认值进行填充


返回值：就是复制的数组
```java
int[] arr = {3,4,5,6,7,8,3,2,2};
int[] rra = Arrays.copyOf(arr,3);
System.out.println(Arrays.toString(rra));

//返回：
[3, 4, 5]
```

3. 数组对象.clone()

直接克隆一个数组

```java
int[] arr = {3,4,5,6,7,8,3,2,2};
int[] rra = arr.clone();
System.out.println(Arrays.toString(rra));

```

    三种数组复制的共同点都属于浅拷贝
    
    浅拷贝：只对当前的数组对象进行拷贝            
           基本类型的 数据：在堆中复制一个新“数组”对象。新对象中的基本类型相当于复制过来一份。
		   引用类型的数据： 在堆中复制一个新“数组”对象。但是只复制 这一层对象。
		   只拷贝第一层拷贝
	一般深拷贝：
	
	
	彻底深拷贝：彻底深拷贝是在成功 clone 个对象之后，此对象与母对象在任何引用路径上都不存在共享的实例对象，
	           但是引用路径递归越深，则越接近JVM底层对象，且发现彻底深拷贝实现难度越大
	           
	           
	           若想实现深拷贝，需要重写clone对象
	           
	           
	           	   
		 
		 
		   
		   
		   
		   
		   
		   

    






## 时间复杂度

1. 没有for循环：O(1) 最好
2. 一层for循环: O(n) 次好
3. 二层for循环：O(n^2) 次次次




