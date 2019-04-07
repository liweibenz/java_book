
### 1.一个足球队在寻找年龄在10岁到12岁的小女孩（包括10岁和12岁）加入。编写程序，询问用户的性别（1表示男性，0表示女性）和年龄，然后显示一条消息指出这个人是否可以加入球队，询问10次后，输出满足条件的总人数。

```java
package cn.blk5.day03;

import java.util.Scanner;

public class T1 {
    /**
     * @author: liwei
     * @updateTime: 2019-04-06 22:48
     * @version: 1.0
     * @description: 1.一个足球队在寻找年龄在10岁到12岁的小女孩（包括10岁和12岁）加入。编写程序，
     * 询问用户的性别（1表示男性，0表示女性）和年龄，
     * 然后显示一条消息指出这个人是否可以加入球队，询问10次后，输出满足条件的总人数。
     * <p>
     * 分析需求：
     * 1.判断年龄是否满足10-12岁
     * 2.判断性别是否为女性
     * 3.累计10次，输出总人数
     */
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        byte sum = 0;
        for (int i = 1; i < 11; i++) {
            System.out.println("第" + i + "次输入");
            System.out.print("输入1表示男性，0表示女性\n请输入性别：");
            byte sex = sc.nextByte();
            if (sex == 0) {
                System.out.print("请输入年龄：");
                byte age = sc.nextByte();
                if (age >= 10 && age <= 12) {
                    System.out.println("*****恭喜你可以加入球队*****");
                    sum += 1;
                } else {
                    System.out.println("%%%%%年龄不符合%%%%%%");
                }
            } else {
                System.out.println("%%%%%性别不符合%%%%%%");
            }
        }
        System.out.println("总计符合人数:" + sum + "人");
    }
}


```
### 2.输入3个数，找到最大值和最小值输出

```java
package cn.blk5.day03;

public class T2 {
    /**
     * @author: LIWEI
     * @updateTime: 2019-04-06 23:19
     * @version: 1.0
     * @description: 2.输入3个数，找到最大值和最小值输出
     */
    public static void main(String[] args) {

        int a = 3;
        int b = 55;
        int c = 2;
        int max = 0;
        int min = 0;

        if (Math.max(a, b) > c) {
            max = Math.max(a, b);
        } else {
            max = c;
        }

        if (Math.min(a, b) < c) {
            min = Math.min(a, b);
        } else {
            min = c;
        }

        System.out.println("最大数：" + max);
        System.out.println("最小数：" + min);


    }
}
```

### 3.有四个数字：1、2、3、4，能组成多少个互不相同且无重复数字的三位数？各是多少？
程序分析：可填在百位、十位、个位的数字都是1、2、3、4。组成所有的排列后再去 掉不满足条件的排列。


```java
package cn.blk5.day03;

public class T3 {
    /**
     * @author: LIWEI
     * @updateTime: 2019-04-07 20:41
     * @version: 1.0
     * @description: 3.有四个数字：1、2、3、4，能组成多少个互不相同且无重复数字的三位数？各是多少？
     * 程序分析：可填在百位、十位、个位的数字都是1、2、3、4。组成所有的排列后再去 掉不满足条件的排列。
     */
    public static void main(String[] args) {

        for (int i = 1; i < 5; i++) {
            for (int j = 1; j < 5; j++) {
                for (int k = 1; k < 5; k++) {
                    if (i != j && j != k && k != i) {
                        System.out.print("" + i + j + k+" ");
                        
                    }
                }
            }
        }
    }
}

```

### 4.一个5位数，判断它是不是回文数。
即12321是回文数，个位与万位相同，十位与千位相同。判断更多位数的数字

```java
package cn.blk5.day03;

public class T4 {

    /**
     * @author: LIWEI
     * @updateTime: 2019-04-07 21:10
     * @version: 1.0
     * @description: 4.一个5位数，判断它是不是回文数。即12321是回文数，个位与万位相同，十位与千位相同。判断更多位数的数字
     */
    public static void main(String[] args) {

        int x = 6789876;
        String str = String.valueOf(x);
        boolean flag = false;
        for (int i = 0; i < str.length() / 2; i++) {
            if (str.charAt(i) != str.charAt(str.length() - i - 1)) {
                System.out.println("不是回文数");
                flag = false;
                break;
            } else {
                flag = true;
            }
        }
        if (flag) {
            System.out.println("是回文数");
        }
    }

}
```

### 5.输出10行内容，每行的内容都不一样，第1行一个星号，第2行2个星号⋯

```java
package cn.blk5.day03;

public class T5 {
    /**
     * @author: LIWEI
     * @updateTime: 2019-04-06 23:44
     * @version: 1.0
     * @description: 5. 输出10行内容，每行的内容都不一样，第1行一个星号，第2行2个星号⋯
     */
    public static void main(String[] args) {

        for (int i = 0; i < 10; i++) {
            for (int j = 0; j < i; j++) {
                System.out.print("* ");
            }
            System.out.println();
        }
    }
}
```

### 6.在上面题基础上，打印一个圣诞树

```java
package cn.blk5.day03;

public class T6 {
    /**
     * @author: LIWEI
     * @updateTime: 2019-04-06 23:45
     * @version: 1.0
     * @description: 6.在上面题基础上，打印一个圣诞树
     */
    public static void main(String[] args) {

        for (int i = 1; i <= 9; i++) {

            //控制行输出，控制空格输出
            for (int j = 1; j <= 9 - i; j++) {
                System.out.print(" ");
            }
            //控制列输出，控制*输出
            for (int j = 1; j <= i; j++) {
                System.out.print("* ");
            }
            System.out.println();
        }
    }
}
```


### 7.输出所有的水仙花数（三位数，各位数字的立方和等于自身）

```java
package cn.blk5.day03;

public class T7 {
    /**
     * @author: LIWEI
     * @updateTime: 2019-04-07 17:53
     * @version: 1.0
     * @description: 7.输出所有的水仙花数（三位数，各位数字的立方和等于自身）
     */
    public static void main(String[] args) {

        for (int i = 100; i < 1000; i++) {
            int a = i / 100 % 10;
            int b = i / 10 % 10;
            int c = i % 10;
            if (i == (Math.pow(a, 3) + Math.pow(b, 3) + Math.pow(c, 3))) {
                System.out.println(i);
            }
        }

    }
}
```

### 8.输出9 * 9乘法表。（for   while）

```java
package cn.blk5.day03;

public class T8 {
    /**
     * @author: LIWEI
     * @updateTime: 2019-04-06 23:30
     * @version: 1.0
     * @description: 8.输出9 * 9乘法表。（for   while）
     */
    public static void main(String[] args) {
        // for 99乘法表
        for (int i = 1; i < 10; i++) {
            for (int j = 1; j <= i; j++) {
                System.out.print(i + "x" + j + "=" + i * j + " ");
            }
            System.out.println();
        }

        // while 99乘法表
        int i = 1;
        while (i < 10) {
            int j = 1;
            while (j <= i) {
                System.out.print(i + "x" + j + "=" + i * j + " ");
                j++;
            }
            i++;
            System.out.println();
        }
    }
}
```

### 9.Random r=new Random();r.nextInt(10)可以随机输出0到9之间的数字。
通过输入猜随机产生的数字是什么。记录猜错的次数，如果错误超过3次，则退出，
并输出“小笨蛋。。。”，如果3次之内猜对了，则输出“真聪明”

```java
package cn.blk5.day03;

import java.util.Random;
import java.util.Scanner;

public class T9 {
    /**
     * @author: LIWEI
     * @updateTime: 2019-04-07 14:01
     * @version: 1.0
     * @description: 9.Random r=new Random();r.nextInt(10)可以随机输出0到9之间的数字。
     * 通过输入猜随机产生的数字是什么。记录猜错的次数，如果错误超过3次，则退出，
     * 并输出“小笨蛋。。。”，如果3次之内猜对了，则输出“真聪明”
     */
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);
        Random r = new Random();

        boolean flag = true;
        int yy = 0;
        while (flag) {
            System.out.println("*****请输入一个数*****");
            int ran = r.nextInt(10);
            System.out.println(ran);
            int num = sc.nextInt();
            if (num != ran) {
                yy++;
            } else {
                yy--;
            }

            switch (yy) {
                case 3:
                    System.out.println("错误超过" + yy + "次，小笨蛋");
                    flag = false;
                    break;
                case -3:
                    System.out.println("真聪明");
                    flag = false;
                    break;
                default:
            }
        }
    }
}
```

### 10.输出100以内的素数

```java
package cn.blk5.day03;

public class T10 {
    /**
     * @author: LIWEI
     * @updateTime: 2019-04-06 23:56
     * @version: 1.0
     * @description: 10.输出100以内的素数
     * 只能被1和自己整数的数称为质数，又称素数
     */
    public static void main(String[] args) {

        for (int i = 3; i < 100; i++) {
            boolean flag = true;
            for (int j = 2; j < i / 2 + 1; j++) {
                if (i % j == 0) {
                    flag = false;
                    break;
                }
            }
            if (flag) {
                System.out.println(i);
            }
        }
    }
}
```

### 11.假设一年期定期利率为3.25%，计算一下需要过多少年，一万元的一年定期存款连本带息能翻番？


```java
package cn.blk5.day03;

import com.sun.tools.internal.xjc.reader.dtd.bindinfo.BIAttribute;

import java.math.BigDecimal;

public class T11 {
    /**
     * @author: LIWEI
     * @updateTime: 2019-04-07 14:49
     * @version: 1.0
     * @description: 11.假设一年期定期利率为3.25%，计算一下需要过多少年，一万元的一年定期存款连本带息能翻番？
     */
    public static void main(String[] args) {

        int i = 1;
        BigDecimal totalInterest = new BigDecimal(0);
        BigDecimal principal = new BigDecimal(10000);
        BigDecimal interest = new BigDecimal(0.0325);
        while (i >= 1) {
            // 计算总利息= 本金*利息
            totalInterest = totalInterest.add(principal.multiply(interest));
            // 判断本金+利息是否翻倍
            int a = totalInterest.add(principal).compareTo(new BigDecimal(20000));
            // 计算一共收入多少钱 总利息 + 本金
            BigDecimal total = totalInterest.add(principal);

            if (a == 1) {
                System.out.println("需要" + i + "年");
                System.out.println("总利息：" + totalInterest.setScale(4, BigDecimal.ROUND_HALF_UP));
                System.out.println("总收入：" + total.setScale(4, BigDecimal.ROUND_HALF_UP));
                break;
            }
            i++;
        }


    }
}
```

### 12.一球从100米高度自由落下，每次落地后反跳回原高度的一半；再落下，求它在第10次落地时，共经过多少米？第10次反弹多高？

```java
package cn.blk5.day03;

public class T12 {
    /**
     * @author: LIWEI
     * @updateTime: 2019-04-07 16:58
     * @version: 1.0
     * @description: 12.一球从100米高度自由落下，每次落地后反跳回原高度的一半；
     * 再落下，求它在第10次落地时，共经过多少米？第10次反弹多高？
     */
    public static void main(String[] args) {

        double b = 100;
        double total = 0;
        for (int i = 1; i < 11; i++) {
            double a = b /= 2;
            total += a;
            if (i == 10) {
                System.out.println("第" + i + "次反弹：" + a + "米");
            }
        }
        System.out.println("共经过：" + total + "米");
    }
}
```

































