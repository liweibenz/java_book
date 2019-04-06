
### 1.一个足球队在寻找年龄在10岁到12岁的小女孩（包括10岁和12岁）加入。编写程序，询问用户的性别（1表示男性，0表示女性）和年龄，然后显示一条消息指出这个人是否可以加入球队，询问10次后，输出满足条件的总人数。

```java
package cn.blk5.day03;

import java.util.Scanner;

public class T1 {
    /**
     * @author: liwei
     * @updateTime: 2019-04-06 22:48
     * @version: 1.0
     * @description: 1.一个足球队在寻找年龄在10岁到12岁的小女孩（包括10岁和12岁）加入。编写程序，询问用户的性别（1表示男性，0表示女性）和年龄，
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

