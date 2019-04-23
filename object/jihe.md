# 第二十章 集合


## 1. 数据结构

> 什么是数据？计算机中存储的元素
>
> 什么是结构？数据与数据之间的关系

计算机常用数据与数据之间的关系
* 点状存储
* 线性存储
* 树状存储
* 网状存储

数据结构两个层次
1. 逻辑结构：强调元素之间的关系
    1. 线性结构
    2. 树型结构
    3. 图状结构
    4. 集合结构
2. 物理结构：数据在计算机内存真实的存储结构
    1. 顺序存储（连续）
    2. 链表存储（不连续）
    
***
    
常用的几种数据结构：
1. 数组（线性存储）又叫顺序线性表
2. 链表（线性存储）
3. 堆栈（线性存储）（受限的线性存储）
4. 队列（受限的线性存储）
5. 树
6. hash表
  
***
  
一、数组
1. 数组
- 【定义】使用一组地址连续的存储单元，依次存储
- 【访问】通过内存首地址+偏移量（n*size）就能得到数组中元素的位置
- 【应用】java中的数组是静态数组，是使用一组地址连续的存储单元
    无法修改数组的原因：无法判断连续的地址后面有没有内存空间。
- 【缺点】插入和删除元素效率低
- 【优点】随机访问效率高
2. 动态数组
- 【扩容】在原来的静态数组的基础上形成一个新数组，扩容原数组空间/2
- 【特点】效率低
- 【java】java中ArrayList就是动态数组



二、链表

1. 链表
- 【定义】是线性的，是逻辑上连续存储，可以物理上不存储
- 【缺点】随机访问性比数组差，每次访问都从第一个元素（首地址）开始访问
- 【优点】对元素插入和删除效率比数组高
- 【元素结构】每个元素分为两部分 前面是"数据域" 后面是"指针域" 存储下一个元素的地址

2. 双向链表
- 【元素结构】{（上一个元素地址）（数据域）（下一个元素地址）}
- 【优点】随机访问块
- 【缺点】占用空间大，每次操作是两倍的工作量

3. 环形链表
- 首元素指针，指向，尾元素地址
- 尾元素地址，指向，首元素指针

三、栈
- 【定义】线性存储，受限的线性表，只有一个口，出入数据
- 【栈顶】数据的出入口
- 【栈底】第一个进入的元素所在的位置
- 【规则】后进先出 LIFO
- 【应用】
    1. 方法的调用：目的为了接住返回值
    2. 异常的向上传播：
    
    
四、队列
- 【定义】线性存储，为了表达元素和元素之间的关系，受限的线性表
- 【队头】第一个进入的元素 （出）
- 【队尾】最后一个进入的元素 （入）
- 【规则】先进先出 FIFO
- 【应用】处理多线程
- 【双端队列】两端可以同时出入元素，添加和删除元素的是需要维护两个队列表


五、树
- 【定义】由节点集合连接每对节点的有向边集组成
- 【根节点】
- 【节点】同级别的叫兄弟

- 【二叉树】每个节点（除叶子节点以外）都只有不超过两个子节点（可以是0-2个）
- 【满二叉树】每个节点（除叶子节点以外）都有两个子节点
- 【满二叉树编号规则】，从上到下，从左到右

- 【完全二叉树】当一个

- 【遍历树】对树种所有节点进行访问
    - 广度遍历：一层一层遍历，应用抓取大量数据
    - 深度遍历：从上向下，向深度遍历，很精确的数据

- 【二叉树遍历规则】
    * 先序遍历：先根-->左-->右
    * 中序遍历：先左-->根-->右
    * 后序遍历：先左-->右-->根  
    
六、hash表

- 【定义】希望将一个数据存储到内存中一组有序的存储单元
- 【规则】按照哈希规则进行存储
- 【hash函数】
- 【优点】当我们访问元素的时候，都可以是常数时间复杂度


***


2）查询和排序

* 查找：顺序查询 二分查找 分块查找
* 排序：冒泡、选择、插入、希尔、快速、归并

1. 冒泡排序
2. 选择排序
3. 插入排序
4. 希尔排序：改进版插入排序，最小增量排序
    每次分组插入排序，排序过程中index不变，排序完在组合起来
    
    * 增量设置原则，从大到小，每次取一半





## 2. 集合

> 什么是集合
>
> 一个容纳多个元素的容器,一个标准

集合有什么用？



1. Collection 主接口
    下面有两个子接口 Set，List
    * List 第二级别子接口（有序，不唯一元素，可以重复）
        * ArrayList： 实现类（使用动态数组的形式存储，动态数组扩容ArrayList是通过原始容量*3/2+1）
        * LinkedList：实现类（使用链表的形式存储）
        * Vector：实现类
    * Set  第二级别子接口（无序，元素唯一，不能重复）
        * HashSet：实现类
        * TreeSet：实现类
    
    
  

 
    
    
2. Map 接口，是以键值对形式存储数据

3. Collection接口不能实例化对象，需要实现类实现接口


```java

        // 创建一个集合对象
        Collection<Integer> c = new ArrayList<Integer>();
        Collection<Integer> c1 = new ArrayList<Integer>();

        // 1.add方法，向集合中添加元素，添加成功返回true，否则返回false
        // 如果有重复元素，则添加失败，返回false
        c.add(123);
        // c.forEach(System.out::println);

        // 2.addAll方法，添加集合对象，将一个集合对象添加到一个集合中
        // 返回值，当前集合发生变化的时候， 就会返回tru，否则返回false，如果一个都不进去才会返回false
        c1.addAll(c);
        //c1.forEach(System.out::println);

        // 3.size 返回集合中元素个数
        // 判断一个集合类型是不是为空，尽量不要用对象 != null
        //System.out.println(c1);

        // 4.isEmpty 判断集合是否为空
        // System.out.println(c.isEmpty());

        // 5.contains判断是否包含某一个对象
        //c.contains(123);

        // 6.containsAll判断c集合中否是包含c2集合的所有元素 ????
        //System.out.println(c.containsAll(c1));

        // 7.remove 删除一个元素,返回true，否则返回false
        //System.out.println(c.remove(555));

        // 8.removeAll 删除集合对象，与另外一个集合对象，如果重复的，就删除自己集合中的元素

        c1.add(999);
//        System.out.println("c集合删除之前"+c);
//        System.out.println("c1集合删除之前"+c1);
//        c1.removeAll(c);
//        System.out.println("c集合删除之后"+c);
//        System.out.println("c1集合删除之后"+c1);

        // 9.removeIf 按条件删除集合元素

//        c.removeIf((Integer y)->y>5);
//        for (Integer integer : c) {
//            System.out.println(integer);
//
//        }

        // 9. retainAll 两个集合对比，保留交集

        //c.retainAll(c1);


        // 10. 循环显示集合对象 c.forEach(System.out::println);
        // c.forEach(System.out::println);

        // 11. clear 清空集合中所有元素
//        c.clear();
//        c1.clear();

        // 12. toArray 将集合对象转换成数组，用集合对象去接
//        Object[] r = c.toArray();
//        System.out.println(Arrays.toString(r));


        // 13.c.toArray(arr)  将集合对象转换成数组，放到一个声明好的数组中
     

//        c1.removeIf((Integer a) -> {
//            return a > 6;
//        });
//        c1.removeIf((Integer a) -> a > 6);
        // c1.forEach(System.out::println);

        Integer[] arr = new Integer[c1.size()];
        c1.toArray(arr);
        System.out.println(Arrays.toString(arr));


        // 5种集合的遍历
        /**
         * 1.Iterable接口（1.8之前）
         * next 获取下一个元素
         * hasnext 判断是否还有下一元素
         * remove 删除刚刚调用next方法的最后一个next元素
         * Iterator迭代器会存储集合中的元素,如果next获取不到元素就会报错
         * 迭代器是一次性的
         */

        Iterator<Integer> it = c1.iterator();
        while (it.hasNext()) {
            System.out.print(it.next()+" ");
        }


        /**
         * 2.Iterable接口（jdk 1.8之后）
         *
         */
        Iterator<Integer> it=c.iterator();
        it.forEachRemaining(System.out::println);

        // 3.增强for循环
        for (Integer integer : arr) {
            System.out.println(integer);
        }

        // 4.forEach方法
        c1.forEach(System.out::println);


        // 5.使用聚合操作
        System.out.println("---------");
        c1.stream().forEach(System.out::print);

```



## Set子接口

* HashSet：注重于元素不可重复，
    * LinkedHashSet 继承HashSet类，底层使用双向链表存储
    * 
    
* TreeSet
    * SortedSet ：必须排序,放入就排序了
        * NavigableSet 是对SortedSet父类的扩展


很多方法跟list差不多



## Queue队列，跟list和set子接口平级

* 多线程处理并发
* 继承collection父街口

* 阻塞型队列
* 非阻塞型队列       
 
实现类（非阻塞型） 
* LinkedList -- 先进先出 -- 队列
* PriorityQueue -- 优先队列 -- 可以实现堆栈的效果，甚至高于堆栈的效果，可以设置优先级
* Deque 双端队列，使用LinkedList 作为实现类
    * Deque<Integer> q4 = new LinkedList<>();
    * 使用LinkedList类实现
    * 使用双向链表实现
    * 可以实现堆栈的功能，单独实现了对于堆栈的方法

* 创建语法：
    * Queue<Integer> q1 = new LinkedList<Integer>();
    * Queue<Integer> q2 = new PriorityQueue<Integer>();


* 方法：
    1. add 添加元素方法
    2. remove() 删除元素方法



## Map接口 跟list，set，Queue一个级别的

* 实现类中存储的是键值对，key-->value
* key不能重复，因为key底层是使用set实现的
* 实现类
    * HashMap
    * LinkedHashMap
    * TreeMap(继承Map)
        * SortedMap（Map）
          1. 另行创建的新街口，必须放入可以排序的元素
          2. 可以对key排序
          3. 
            * NavigableMap（继承SortedMap）
                1. 


语法：
Map<Integer, String> map = new HashMap<>();
1. put 添加元素(只要key相同就会覆盖掉)
map.put(1,"liwei");

2. get(key) 以key获取value
map.get(1);

3. putAll 将另一个map复制到当前map中


4. map.putIfAbsent(3,"999");


5. remove(key) 根据key删除键值对，返回value


5. remove(key,value) 根据 key value为条件删除

6. clear 清空map

7. map.getOrDefault(44,"888") 如果key不存在，就返回默认值

8. size() 返回键值对数量

9. isEmpty() 判断map是否为空


10. map.containsKey(1); 判断是否包含key  返回true/false
        
        
11. map.containsValue("liwei"); 判断是否包含value 返回true/false


12. keySet 获取所有key

13. values() 获取所有value

14. entrySet() 获取所有key value

    返回：[1=liwei, 2=lxw, 3=aaaa]


14. replace 根据key，替换value

15. replace 根据key和value 替换value
    map.replace(2,"lxw","ok");
    
    
16. replaceAll()  函数式接口
    可以实现全局替换

17. computeIfAbsent() 按照规则加入不存在的键值对，如果存在，则不会更新value


18. computeIfPresent() 如果key存在，则按规则替换value


19. compute() 无论key是否存在，都会使用function，计算之后的值替换old，如果不存在，则追加键值对



20. merge() 如果key不存在，则使用参数value当value
            如果key存在，则使用function计算出来的new value来替换原来的oldvalue
            
            


### 遍历map


1. keyset

```java
Set<Integer> s = map.keySet();
s.forEach((k)->{
    System.out.println(k+":"+ map.get(k));
});

```

2. entryset

```java
Set<Map.Entry<Integer,String>> s = map.entrySet();
s.forEach(e-> System.out.println(e.getKey()+"::"+ e.getValue()));

```        


3. forEach

```java
map.forEach((k,v)->System.out.println(k+"-"+v));
```


        



# 面试题

1. ArrayList和LinkedList区别

    1. 都是List的子类
    2. 关于数据结构
        1. ArrayList 基于动态数组的数据结构，当空间不足扩容公式，新容量=(旧容量*3)/2+1
        2. LinkedList基于双向链表的数据结构
    
    3. 关于性能
        1. ArrayList 修改和随机访问效率高，因为LinkedList要移动指针
        2. LinkedList 新增和删除效率高， 因为ArrayList要移动数据
        3. 当数据达到百万级别时，ArrayList增加数据导致空间扩容，会变的异常慢。
    
    4. 关于浪费内存空间
        1. ArrayList的空间浪费主要体现在在list列表的结尾预留一定的容量空间，
        2. LinkedList的空间花费则体现在它的每一个元素都需要消耗相当的空间存储指针
    5. 在1.8中，如果只是new ArrayList(),容量其实是0，当第一次通过add(E e)时，扩充为10
   
2. HashSet和ArrayList区别

    1. 关于父类
        1. HashSet 实现的是Set接口
        2. ArrayList实现的List接口
        3. 而Set和List接口都是继承Collection接口
    2. 关于数据结构
        1. ArrayList 数组存储，有序，元素不唯一
        2. HashSet   存储对象，无序，元素唯一
    
    
  
3. HashSet和HashMap区别
    1. 关于父接口
        1. HashSet实现了Set接口
        2. HashMap实现了Map接口
    2. 关于存储方式
        1. HashSet仅存储对象，不允许有重复的值
        2. HashMap存储键值对，不允许有重复的键，可以有重复的值
    3. 关于添加元素
        1. HashSet通过add()方法添加，当元素值重复时则会立即返回false，如果成功添加的话会返回true
        2. HashMap通过put()方法添加
    4. 关于计算hashcode
        1. HashSet使用成员对象来计算hashcode值，对于两个对象来说hashcode可能相同，
            所以equals()方法用来判断对象的相等性，如果两个对象不同的话，那么返回false 
        2. HashMap中使用键对象来计算hashcode值 








哈希表底层使用的也是数组机制，数组中也存放对象，而这些对象往数组中存放时的位置比较特殊，当需要把这些对象给数组中存放时，那么会根据这些对象的特有数据结合相应的算法，计算出这个对象在数组中的位置，然后把这个对象存放在数组中。而这样的数组就称为哈希数组，即就是哈希表。
当向哈希表中存放元素时，需要根据元素的特有数据结合相应的算法，这个算法其实就是Object类中的hashCode方法。由于任何对象都是Object类的子类，所以任何对象有拥有这个方法。即就是在给哈希表中存放对象时，会调用对象的hashCode方法，算出对象在表中的存放位置，这里需要注意，如果两个对象hashCode方法算出结果一样，这样现象称为哈希冲突，这时会调用对象的equals方法，比较这两个对象是不是同一个对象，如果equals方法返回的是true，那么就不会把第二个对象存放在哈希表中，如果返回的是false，就会把这个值存放在哈希表中。
总结：保证HashSet集合元素的唯一，其实就是根据对象的hashCode和equals方法来决定的。如果我们往集合中存放自定义的对象，那么保证其唯一，就必须复写hashCode和equals方法建立属于当前对象的比较方式。

HashSet它进行储存对象时，先根据对象的hash值来确定它的位置区域，
然后通过equals去和相同hash值的对象去比较，如果为true则不进行储存，如果是false，则进行链式储存。
为什么要这样来进行储存呢？由于HashSet储存的是不同的对象，假设已经有了1000个对象，再添加一个对象，
我们需要比较一千次，极为麻烦，我们可以直接的通过hash值和equals来比较是否对象满足我们相同的条件



## 集合工具类


*. Arrays : 针对数组的一系列操作的工具类
*. Collections：针对集合的工具类


1. Arrays工具类
    1. sort 排序
    2. asList：将数组对象转换成集合对象
    
        Integer[] tt = {1,2,3,4};
        List<Integer> list = Arrays.asList(tt);
        List<Integer>  linew = new ArrayList<Integer>();
        linew.addAll(list);
        linew.add(888);
        
    
2. Collections 很多都是静态方法
    1. sort 排序方法
    2. binarySearch() 二分查找法，查找前需要排序
    3. reverse  集合反转元素
    4. shuffle 洗牌，随机打乱元素的位置
    5. fill    填充元素
    6. max min  查找最大值，最小值
    7. frequency  查找集合中某个元素出现的次数
    8. Collections.replaceAll(linew,888,10000); 替换元素
    

## 聚合操作

1.  什么是聚合操作？对于集合元素，进行一连串的相关操作，跟数据库中聚合函数类似
    java中的聚合操作不一定将多条记录合成一条记录
    
* 【管道】一序列顺序的聚合操作叫做管道，包括多个操作
    一类叫中间操作，一类叫终端操作
    
* 【流】是一个元素序列，聚合操作通过流来进行操作的

2. 聚合操作跟普通的迭代访问区别
    1. 两种操作都可以输出数据源中的元素
    2. 不同：迭代器堆集合进行操作，使用数据源来进行迭代
    3. 不同：聚合操作，使用内部迭代器
    4. 外部迭代器，可以对数据底层元素进行修改操作
    5. 聚合操作是通过流进行运算，不会对源数据修改，相当于复制一份源数据

3. 聚合操作（中间操作）
    1. 过滤数据
       list2.stream().filter(t-> t>5).forEach(System.out::println);
    2. map 映射
    3. distinct 去重
    4. sorted   排序
    5. peek   (返回一个流)  跟foreach实现的功能一样
    6. limit   对集合元素数量的限制，多的元素删除
    7. skip 跳过n元素 n代表跳过n个元素后输出
    
4. 聚合操作（终端操作，最后一次操作）
    1. max 最大值 传比较器
    2. min 最小值
    3. sum 求和
    4. count 统计数量
    5. average 平均数
    6. reduce 合二为一，条件为➕，就是累加
    
    

    








































