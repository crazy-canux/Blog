---
layout: post
title: Java编程
comments: true
date: 2016-04-03 10:49:07
updated:
tags:
- Java
categories:
- Java
permalink:
---

# java概述

Java的三个体系:
1. J2SE: 标准版
2. J2EE: 企业版(包括J2SE)
3. J2ME: 微型版

Java的版本：
1. OpenJDK
2. Oracle JDK
3. IBM JDK

Java的web框架SSH: struts + spring + hibernate。

java的web服务器: tomcat

java命令:
1. java      运行程序
2. javac     编译器
3. jdb       调试器
4. jar       归档工具
5. javadoc   文档工具

java的ide:
1. eclipse(IBM)
2. netbeans(Oracle)

Java的架构：

![pic](/images/java.PNG)

***

# java基本语法

java源程序叫Xxx.java

java是强类型语言。

java大小写敏感。

java使用骆驼命名法，单词首字母大写。

java语句要用分号；结尾, 用{}表示一个代码块。

java程序以类的形式出现，类名单词首字母最好大写。

java源代码文件名要和公共类的名字相同。

java标识符：字母和下划线开头，可以包含数字，不能是关键字。

一个类要独立运行需要main函数。

## java的注释

单行注释:

/          /

多行注释:

/*        */

文档注释:

/**       */

## java关键字

### 数据类型

boolean, int, long, short, byte, float, double, char, class, interface

### 流程控制

if, else, for, do, while, switch, case, default, break, continue, return, try, catch, finally.

### 修饰符

public, protect，private，final，void， static， staticfp， abstract， transient， synchronized， volatile, native,

### 动作相关

package, import, throw, throws, extends, implements, this, super, instanceof, new.

### 保留字

true, false, null, goto, const.

## 数据类型

java有8种基本数据类型

### 整数类型

1. byte 1 字节

2. short 2字节

3. int 4字节

4. long 8字节，后缀为L

byte可以转换成short, short可以转换成int, int可以转换成long.

int和long都可以转换成浮点型.

### 浮点类型

1. float  4字节

2. double  8字节，后缀为F

float可以转换成double类型.

三个表示出错和溢出的浮点数:

正无穷

负无穷

NaN

### 字符类型

1. char 表示单个字符

char类型可以转换成int类型.

### 布尔型：

1. Boolean 两个值true和false表示真和假。

在java中整形值和布尔值不能转换。


### 进制：

前缀0b表示二进制

前缀0表示八进制

前缀0x表示十六进制

### 变量

type var = val

变量需要先申明类型,然后再初始化, 最后才能使用.

最好逐一申明每个变量.

变量的申明最好靠近第一次使用的地方.

### 常量:

final type CON = val

使用final修饰的是常量，只能被赋值一次。

static final CON = val

在一个类的多个方法中使用的是类常量，使用static final修饰。

类常量定义位于main方法外部。

## java运算符

### 算术运算

> +

> -

> *

> /    当除法两个操作数都是整数时结果是整数，否则是浮点数。

> &    求余数

### 自增运算/自减运算

>> ++n/--n    当前表达式n的值就要加1。

>> n++/n--    当前表达式n的值不变，下一个表达式n的值加1。

### 赋值运算

>> =

>> +=

>> -=

>> *=

>> /=

>> &=

### 关系运算

>> ==

>> !=

>> <

>> >

>> <=

>> >=

>> instanceof(检查是否是类的对象）

### 逻辑运算(boolean运算符)

>> && (AND短路)

>> || (OR短路)

>> ! (NOT)

### 位运算

>> & (AND)

>> | (OR)

>> ^ (XOR)

>> ~ (非)

>> a<<b (a左移b位),地位补0。

>> a>>b (a右移b位)，高位是符号位。

>> >>> (无符号右移，高位始终补0)

### 三目运算：

>> x?y:z

## 枚举类型

变量的值只在一个有限的集合内，可以定义枚举类型。

定义枚举类型:

>> enum type_name { val1, val2, ..., valN };

申明枚举类型

>> type_name name = type_name.varX

## 数组： 就是一个容器，相同数据类型的集合。

元素类型［］   数组名   =   new   元素类型［数组长度］；
元素类型［］   数组名   =   new   元素类型［］｛val1，...}；
元素类型［］   数组名   =   ｛val1， …};
数组默认初始化值为0或false 或 '\u0000'
array.length   #求数组长度。

二维数组：
int[][] array = new int[2][3];

int[][] array = new int[2][];
array[0] = new int[1];
array[1] = new int[2];

int[][] array = new {｛1｝，｛2，3｝}；

## 字符串(java.lang.String)：

java字符串就是unicode字符序列。

任何一个java对象都可以转换成字符串。

java没有字符串类型，而是用标准库中预定义的类Spring。

每个用双引号""括起来的字符串都是Spring类的一个实例。

不能修改java字符串中的字符，所以String类对象是不可变字符串。

* 子串

String类的substring方法可以获取子串

    String greeting = "hello";
    String s = greeting.substring(0, 3);

substring(start, end)，下标从0开始，从start到end，但是不包括end。

* 拼接

java可以用+连接两个字符串。

    String expletive = "Expletive";
    String PG13 = "deleted";
    String message = expletive + PG13;

* 字符串比较

equals函数比较相等,相等返回true,s和t可以是字符串变量也可以常量:

    s.equals(t)

equalsIgnoreCase函数比较字符串是否相等，不区分大小写：

    s.equalsIgnoreCase(t)

length函数返回字符串长度：

    s.length()

空串：

    if (s.length() == 0)
    if (s.equals(""))

Null:

    if (str == null)

判断一个字符串既不时空串又不是null，先判断是否为null，对null调用方法会出现错误：

    if (str != null && str.length() != 0)

* String类的方法

参考java.lang.String。

* 用StringBuilder构建字符串

构建一个空字符串构建器：

    StringBuilder builder = new StringBuilder();

修改内容：

    builder.append(String str)
    builder.append(char c)
    builder.delete(int startIndex, int endIndex)
    builder.insert(int offset, String str)
    builder.insert(int offset, Char c)

构建新字符串：

    String completeString = builder.toString();

参考 java.lang.StringBuilder 类的方法。

* 用StringBuffer构建字符串缓冲区

参考 java.lang.StringBuffer 类的方法。

## 输入输出：

### 标准输出流：System.out

输出控制流的方法：

    System.out.print();
    System.out.println();

参考 java.io.PrintStream 的方法。

### 标准输入流：System.in

导入Scanner类：

    import java.util.Scanner;

构造Scanner对象，然后和System.in关联：

    Scanner in = new Scanner(System.in);

输入控制流的方法：

    String name = in.nextLine(); / 读取输入的下一行内容 /
    String firstName = in.next(); / 读取输入的下一个单词 /
    int age = in.nextInt(); / 读取一个整数 /
    double number = in.nextDouble(); / 读取一个浮点数 /
    boolean test = in.hasNext(); / 检测输入中是否还有其他单词 /
    boolean test = in.hasNextInt(); / 检测输入中是否还有其他int类型 /
    boolean test = in.hasNextDouble(); / 检测输入中是否还有其他double类型 /

参考 java.util.Scanner 的方法。

### 控制台输入System.console()

返回一个Console类型对象：
 
    Console cons = System.console();

Console类型对象的方法：

    String username = cons.readLine("User name: ");
    char[] password = cons.readPassword("Password: ");

参考 java.io.Console 的方法。

### 文件输出（读）：
Scanner in = new Scanner(Paths.get(“myfile.txt”));
用in读文件即可。

### 文件输入（写）：
PrintWriter out = new PrintWriter(“myfile.txt”));
用out写文件。

## java控制流

条件语句if - else if - else:
if(condition) {
    expression；
}    //if 只有一条语句，{}可以省略

if(condition) {
    expression;
} else {
    expression;
}

if(condition) {
    expression;
} else if {
    expression;
} else {
    expression;
}

条件语句switch – case:
condition 只能是 byte， short， int， char.
default不管在哪里都是最后运行。
switch(condition) {
    case val1:
        expression;
        break;
    …
    case valN:
        expression;
        break;
    default:
        expression;
        break;
}

循环语句while：
条件为真进入循环。
while (condition) {
    expression;
}

循环语句do – while:
先执行一次，再判断条件为真，进入循环。
do {
    expression;
} while (condition)

循环语句for:
init最先执行且只执行一次，condition为真进入循环，执行expression，然后再执行expression1，最后在condition-expression-expression1之间循环。
for (init; condition; expression1) {
    expression;
}

break语句:
只能用于循环语句，跳出循环，不能用于if。

continue语句：
只能用于循环语句，继续下一次循环，不能用于if。


***

# 函数：

格式：
修饰符   返回值类型／void   函数名（参数类型 形式参数1， ...） ｛
    执行语句；
    return   返回值；／ return；（没有返回值可省略）
｝

不能在函数内部定义函数（函数不能嵌套定义）。

函数重载：
函数重载和函数返回值无关，同一个类中的同名函数，在参数个数或类型不完全相同的情况下可以重载。

***

# 面向对象：

