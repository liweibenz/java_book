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
> 一个容纳多个元素的容器


1. Collection 主接口
    下面有两个子接口 Set，LIst
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
        for (int i = 0; i < 10; i++) {
            c1.add(i);
        }

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
         *
         *
         *
         */

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


























































