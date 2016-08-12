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

java语句要用分号；结尾, 用{}表示一个代码块, import语句也需要分号;。

java程序以类的形式出现，类名单词首字母大写。

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

    int <variable> = <value>

变量需要先申明类型,然后再初始化, 最后才能使用.

最好逐一申明每个变量.

变量的申明最好靠近第一次使用的地方.

java不对局部变量做默认初始化。

### 常量:

    final int <VAR> = <val>

使用final修饰的是常量，只能被赋值一次。

    static final int <VAR> = <val>

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

    enum <enum_name> { val1, val2, ..., valN };

申明枚举类型

    <enum_name> <variable> = <enum_name>.varX

## 数组

数组就是一个容器，存储相同数据类型的集合。

数组大小不能改变，只能改变数组元素的大小。

### 一维数组

申明数组两种方法：

    int[] array;
    int array[];

使用new初始化数组：

需要用new创建一个数组,n可以是变量,也可以是0.

数字数组初始化为0,布尔类型初始化为false，对象类型初始化为null（包括String类型）。

    int[] array =  new int[n];

直接初始化数组：

    int[] array = {<val1>, <val2>, ...};

创建并初始化匿名数组,可以直接将匿名数组赋值给别的数组:

    new int[] {<val1>, <val2>, ...};

用for访问数组元素，下标从0开始,下标不能越界:

    for (int i = 0; i < n; i++)
        array[i] = <value>;

使用for each访问数组元素：

    for (int <variable> : array)
        System.out.println(<variable>)

length函数求数组长度：

    array.length

数组拷贝：

将一个数组变量拷贝给另一个数组变量，两个变量引用同一个数组,

也就是说任意改变一个元素的值，另一个数组的对应元素值也改变。

    int[] array1 = array;

将一个数组所有值拷贝给一个新数组：

java.util.Arrays.copyOf()仅仅是把一个数组的所有值拷贝给另一个数组。

    int[] array1 = Arrays.copyOf(array, array.length);

数组排序：

    Arrays.sort(array); / 优化的快速排序 /

### 多维数组：

申明二维数组：

    double[][] arrays;

用new初始化数组：

    double[][] arrays = new double[m][n];

直接初始化：

    double[][] arrays = {｛...｝，｛...｝, ...}；

访问数组元素：

    for (double[] row : arrays)
        for (double col : row)
            System.out.println(col)

参考java.util.Arrays类。

## 字符串(java.lang.String)：

java字符串就是unicode字符序列。

任何一个java对象都可以转换成字符串。

java没有字符串类型，而是用标准库中预定义的类Spring。

每个用双引号""括起来的字符串都是Spring类的一个实例。

不能修改java字符串中的字符，所以String类对象是不可变字符串。

子串:

String类的substring方法可以获取子串

    String greeting = "hello";
    String s = greeting.substring(0, 3);

substring(start, end)，下标从0开始，从start到end，但是不包括end。

拼接:

java可以用+连接两个字符串。

    String expletive = "Expletive";
    String PG13 = "deleted";
    String message = expletive + PG13;

字符串比较:

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

String类的方法:

参考java.lang.String。

### 用StringBuilder构建字符串:

构建一个空字符串构建器:

    StringBuilder builder = new StringBuilder();

修改内容:

    builder.append(String str)
    builder.append(char c)
    builder.delete(int startIndex, int endIndex)
    builder.insert(int offset, String str)
    builder.insert(int offset, Char c)

构建新字符串：

    String completeString = builder.toString();

参考 java.lang.StringBuilder 类的方法。

### 用StringBuffer构建字符串缓冲区

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

### 文件输入（写）：

    PrintWriter out = new PrintWriter(“myfile.txt”));

## java控制流

由{}括起来的若干简单语句构成块作用域。

不能在嵌套的两个块中申明同名的变量。

### if条件语句

条件语句if - else if - else:

    if (condition)
    {
        statement；
    }; / if 只有一条语句，{}可以省略 /

    if (condition)
    {
        statement;
    }
    else
    {
        statement;
    }; / else与最近的if构成一组 /

    if(condition)
    {
        statement;
    }
    else if (condition)
    {
        statement;
    }
    else
    {
        expression;
    };

### switch条件语句

条件语句switch-case, variable只能是 byte， short， int，char的常量表达式或枚举常量，也可以是字符串字面量。

default不管在哪里都是最后运行。

从第一个匹配的case开始执行，直到遇到break停止。

编译时加javac -Xlint:fallthrough会给出没有break的警告。

不提倡使用switch-case语句。

    switch (variable)
    {
        case value1:
            statement1;
            break;
        …
        case valueN:
            statementN;
            break;
        default:
            statement;
            break;
    }

### while循环语句

循环语句while,条件为真进入循环。

    while (condition)
    {
        statement;
    }

### do while循环语句

循环语句do – while,先执行一次，再判断条件为真，进入循环。

    do
    {
        statement;
    }
    while (condition)

### for循环语句

循环语句for,init最先执行且只执行一次，condition为真进入循环，执行statement1，然后再执行statement，最后在condition-statement1-statement之间循环。

for循环体内申明和定义的变量不能在外部使用，除非在外部申明和定义。

    for (init; condition; statement) {
        statement1;
    }

### 中断控制流程语句

break语句:

只能用于循环语句，跳出循环，不能用于选择语句。

continue语句：

只能用于循环语句，继续下一次循环，不能用于选择语句。

带标签的break语句：

标签放在希望跳出的最外层循环/选择块 之前， 标签需要紧跟一个冒号。

带标签的break语句可以用于任何语句。

    label:
    {
        ...
        break label;
    }

***

# 函数：

函数也叫方法。

一种特殊函数，如果函数没有返回值，用修饰符void代替返回值。

    <decorate>... <type> <function_name>(<type> <argument>, ...)
    {
        statements;
        return <value>;
    }

***

# 面向对象

类是构造对象的模板或蓝图，由类构造对象的过程称为创建类的实例。

对象的三个主要特征：
1. 对象的行为
2. 对象的状态
3. 对象的标识

类之间的关系：
1. 依赖
2. 聚合
3. 继承

对象变量并没有实际包含一个对象，仅仅引用一个对象。

使用预定义类,java自带几千个类：

    <object-type> <object-name> = new <object>()

自定义类：

包含三个部分，域（field），构造器（constructor），方法（method）。

    class ClassName
    {
        field1
        field2
        ...
        constructor1
        constructor2
        ...
        method1
        method2
        ...
    }

一般的一个类放到一个java文件中。

编译时编译main函数所在的文件即可，会自动编译包含的类的源文件。

## filed(域)

如果所有构造器方法都希望赋予相同的值，可以直接在申明时给域赋值。

域中的所有数据最好都是private。

    private type name;

常量域：

可以将实例域定义为final,构造器必须初始化这个域,并且不能再修改。

    private final type name;
    public final type name;

静态域：

用static修饰的是静态域,静态域属于类，不属于任何对象，是唯一的。

    private static type name;
    ClassName.name; # 通过类来访问

静态常量：

static和final修饰的是静态常量

    private static final type name = value;
    ClassName.name; # 可以通过类来访问

初始化块：

在域中放初始化块，只要构造类对象就会在运行构造器方法之前运行初始化块。

    {
        var = val;
        ...
    }

    / 静态初始化块 /
    static
    {
        var = val;
        ...
    }

## method（方法）

java中所有的方法都要在类的内部定义。

对域进行读取的方法叫域访问器，用getFunction（）表示。

对域进行设置的方法叫域更改器，用setFunction（）表示。

方法的参数有显示参数和隐式参数，类对象（实例）就是隐式参数，用关键字this表示。

    public type name(arguments)
    {
        ...
    }

静态方法：

静态方法就是不面向对象的方法，也就是没有隐式参数this。

静态方法只能访问自身类中的静态域,不能访问非静态域。

    public static type name(arguments)
    {
        ...
    }
    ClassName.name(arguments); # 用类名来调用

方法参数：

java方法参数是值调用，不是引用调用。

一个方法不可能修改一个基本数据类型的参数的值。

一个方法可以改变一个对象参数的状态。

一个方法不能让对象参数引用一个新的对象。

参数数量可变的方法：


## constructor（构造器）

1. 构造器与类同名
2. 每个类可以有多个构造器
3. 构造器可以有任意个参数
4. 构造器没有返回值
5. 构造器总是随new一起调用
6. 不要在构造器中定义与域重名的局部变量

重载：

多个构造器方法名字相同，参数不同，构成重载，编译器自动找匹配的构造器方法执行，找不到就编译错误。

推荐在构造器方法中对域进行初始化，避免使用默认的初始化。

当类没有提供任何构造器，系统会默认提供一个无参数的构造器，如果有至少一个构造器，而且没有提供无参数构造器，就不能用无参数的构造器初始化对象。

构造器方法的参数：

    / 在前面加个a和域区分开 /
    public ConstructorName(type aName)
    {
        ...
    }

    / 和域同名，但是引用域需要加this区别 /
    public ConstructorName(type name)
    {
        this.name = name;
    }

    / 一个构造器方法内部调用另外的构造器方法 /
    public ConstructorName(type name)
    {
        this("other argument", name);
    }

## 封装

一个源文件只能包含一个public修饰的公有类，而且文件名要和这个类同名。

编译器找到一个以上的类就报错，因为类必须是唯一的。

编译器还会查看源文件，如果比类文件新就会自动编译源文件。

编译器查找类的顺序：
1. java.lang包，默认导入的包
2. 用import导入的其它包中的公有类
3. 当前包中的公有类，或导入的当前包的非共有类。

类的路径要和包名匹配，需要设置类路径，类路径是所有包含类文件的路径的集合。

jar文件包含多个压缩形式的类文件和子目录。

用classpath当作类路径，linux/unix用冒号：隔开，windows用分号;隔开：

    export CLASSPATH=/class/path:.:/jar/path

    set CLASSPATH=c:\class\path;.;c\jar\path

类设计技巧：
1. 一定要保证数据似有
2. 一定要对数据初始化
3. 不要在类中使用过多的基本类型
4. 不是所有的域都需要独立的域访问器或更改器。
5. 将职责过多的类进行分解。
6. 类名和方法名要能体现职责。

可见性：
1. private, 仅对本类可见
2. public， 对所有类可见
3. protected， 对本包和所有子类可见
4. default,默认不用修饰符就是对本包可见。

## 继承

关键字extends表示继承,java中的所有继承都是公有继承。

已存在的类称为超类，基类，或父类。

新类称为子类，派生类，或孩子类。

    class SubClass extends Class
    {
        ...
    }

在子类中使用super来调用父类的同名的方法

    public type getFunction()
    {
        type var = super.getFunction();
        ...
    }

在子类构造器方法中使用super来调用父类同参数的构造器方法

该语句必须放在构造器的第一句，如果没有显示用super调用，默认调用父类的默认构造器

    public SubClass(arguments)
    {
        super(arguments);
        ...
    }

继承可以是多层继承，由一个公共类派生出来的所有类的集合称为继承层次。

不允许被扩展的类称为final类，用final修饰:

final类中的所有方法(不包括域)自动的成为final方法

    final class SubClass extends ClassName
    {
        ...
    }

类中的特定方法也可以被申明为final，子类就不能覆盖这个方法：

    class ClassName
    {
        ...
        public final type MethodName()
        {
            ...
        }
        ...
    }

将父类转换成子类：

只能在继承层次内进行转换，在转换之前应该使用instanceof检查能否检查。

只有父类转换成子类需要强制转换，子类对象引用父类可以直接引用。

    if (FatherObject instanceof SubClass)
    {
        SubClass = (SubClass) FatherObject;
        ...
    }

抽象类：

用abstract修饰的方法是抽象方法，包含抽象方法的类必须用abstract修饰为抽象类。

最基本的类可以作为抽象类，申明抽象方法，在子类中实现方法。

抽象类不能被实例化，但是可以引用非抽象子类的对象。

    abstract class ClassName
    {
        ...
        public abstract type methodName();
        ...
    }

Object类：

Object类是java中所有类的基类，如果一个类没有用extends明确父类，Object就是它的默认父类。

可以用Object类型的变量引用任何类型对象。

参考java.lang.Object的方法。

## 多态

一个对象变量可以指示多种实际类型的现象被称为多态。

java中的对象变量是多态的。

编译器查看对象的申明类型和方法，列出该类中所有同名方法和父类中同名的public方法，再查看调用方法时提供的类型参数，如果找到完全匹配的就调用这个方法，这个过程叫重载解析。

如果是private方法，static方法，final方法，或者构造器方法，编译器可以准确的知道调用哪个方法，这个过程叫静态绑定。

虚拟机预先为每个类创建一个方法表，列出所有方法的签名和实际调用的方法。

# 包

标准java类库分布在多个包中，包方便类的管理。

使用包要确保类名唯一。

sun建议使用公司域名的逆序作为包名。

使用import导入包：

    import java.util.*;

只能用*导入一个包，不能用java.*导入所有包。

导入多个包，有类在使用时重名，写全路径：

    import java.util.*;
    import java.sql.*;
    java.util.Date deadline = new java.util.Date();
    java.sql.Date today = new java.sql.Date();

使用import导入包中的静态域和静态方法：

    import static java.lang.System.*;
    import static java.lang.System.out;

将类放入包中：

在类的源文件开头添加一行语句,源文件要放到包名对应的目录结构中。

    package package_name;

# 注释

由源文件生成一个html格式的文档。

从下面特性中抽取信息：
1. 包package
2. 公有类与接口
3. 公有的和受保护的构造器及方法
4. 公有的和受保护的域

文档注释方式：

    /**
    * summary, javadoc will automatic detect this line as summary.
    * @param
    * <em>...</em>
    * <code>...</code>
    * <strong>...</strong>
    * <img>...</img>
    * ...
    */

类的注释放在import后面，类定义前面。

方法的注释放到方法前面。

域的注释放到域前面，只需要注释静态常量域。

    import java.util.*;

    /**
     * Class comment
     * @author
     * @version
     * @since
     * @deprecated
     * @see
     * @link
     */
    public Class Comment
    {
        /**
         * Just for public static final field.
         */
        public static final NAME = VALUE;

        /**
         * public Constructor/Method comment
         * @param
         * @return
         * @throws
         */
         public type name(param)
         {
             ...
         }
    }

包注释：

包注释需要在包目录添加单独的文件,有两种方法。

提供一个package.html文件，<body>...</body>之间的会被javadoc提取。

提供一个package-info.java，/**...*/之间的会被javadoc提取。

总注释：

可以为所有源文件提供一个总结性的注释：

提供一个overview.html文件，在<body>...</body>之间的会被javadoc提取。
