---
layout: post
title: Tutorial 1 位运算
tags: Algorithm_Primary
date: 2024-3-27
---



# Tutorial 1 位运算

概念：位运算就是基于整数的二进制表示进行的运算

# 基础知识

一个int整型数据宽度为32位，即由32位二进制表示  

| 31 | 30 | …… | 1 | 0 |
| --- | --- | --- | --- | --- |

➡️说明int可表示个数 $2^{32}$ （42亿多个）

➡️int是有符号整型，可表示的范围为 $-2^{31} $ ~  $2^{31}$-1 ，二进制的最高位(第31位)为`符号位`

| 31(符号位) | 30 | …… | 1 | 0 |
| --- | --- | --- | --- | --- |
- 符号位为`0`时 —— `非负` ，数的大小就是0~30位二进制数的大小
- 符号位为`1`时 —— `负` ，数的大小时`0~30位取反`再`+1`

如果是无符号整型，那么可以表示的范围就是 0 ~ $2^{32}$-1

# 代码实现

打印二进制 —— Print_Binary

```c
//头文件

#include <stdio.h>
#include <limits.h>
//INT_MAX是定义在<limits.h>头文件中的常量，表示int类型的最大值

```

```c
//print是用于实现二进制打印的函数

void print(int n) {
    for (int i = 31; i >= 0; i--) {
        if ((n & (1 << i)) != 0) {
            printf("1");
        }
        else {
            printf("0");
        }
        //简化：printf("%c",(n & (1 << i)) == 0 ? '0' : '1');
        // **n & (1 << i)) == 0** 是用于检查n的第i位是否为0
    }
    printf("\n");
}
```

```c
//main函数
int main() {

    int num = 10; // 例如，要打印数字10的二进制表示
    print(num);
    printf("Integer max value is :  %d\n", INT_MAX);
    //INT_MAX是定义在<limits.h>头文件中的常量，表示int类型的最大值

    printf("==================\n");

    //左移 <<
    num = 567;
    print(num);
    print(num << 1);
    print(num << 2);
    print(num << 5);

    printf("==================\n");

    //相反数
    num = 10;
    int num1 = -10;
    int num2 = ~num + 1;
    //相反数在二进制中相当于按位取反再加1
    print(num);
    print(num1);
    print(num2);

    printf("%d\n",num);
    printf("%d\n", num1);
    printf("%d\n", num2);

    printf("---------------\n");

    //最小负数的相反数为它本身
    num = INT_MAX;
    int num3 = ~num + 1;
    print(num);
    print(num3);
    printf("%d\n", num);
    printf("%d\n", num3);

    printf("---------------\n");

    //0的相反数为0
    num = 0;
    int num4 = ~num + 1;
    print(num);
    print(num4);
    printf("%d\n", num);
    printf("%d\n", num4);

    printf("==================\n");

    //按位与_& 按位或_| 按位异或_^
    num1 = 15462819;
    num2 = 46852192;
    print(num1);
    print(num2);
    printf("---------------\n");
    print(num1 & num2);
    print(num1 | num2);
    print(num1 ^ num2);

    printf("==================\n");

    //右移  >>
    /*
    在Java中， >> 运算符对有符号整数执行带符号右移操作，符号位被用来填充左边的空位。
    在C语言中， >> 运算符的行为取决于被操作的数是有符号整数还是无符号整数。
                对于有符号整数，它执行带符号右移操作；对于无符号整数，它执行无符号右移操作
    */

    num = INT_MAX;
    num1 = INT_MIN;
    print(num);
    print(num >> 5);
    print(num1);
    print(num1 >> 5);
    //print(num >>> 5);
    //在C语言中并没有类似于Java中的>>>运算符
    //在Java中>>>是无符号右移运算符；>>是带符号右移运算符

    return 0;
}
```