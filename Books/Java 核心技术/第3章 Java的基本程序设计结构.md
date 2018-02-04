
- 一个简单的 Java 应用程序
- 注释
- 数据结构
- 变量
- 运算符
- 字符串
- 输入输出
- 控制流
- 大数值
- 数组

## 一个简单的 Java 应用程序
```
public class FirstSample{
    public static void main(String[] args){
        System.out.println("We will not use 'Hello world!'");
    }
}
```
## 注释

Java 中的三种注释方式：
- `//`
- `/* xxx */`
- `/* xxx
    * xxx
    */`

## 数据结构

- 基本数据类型
  - 整型
    - int，   4字节
    - short， 2字节
    - long，  8字节
    - byte，  1字节
  - 浮点
    - float， 4字节
    - double，8字节
  - 字符型
    - char
  - 布尔型
    - boolean

## 变量

在 Java 中，每一个变量属于一种类型（type）。

### 变量的声明
- double salary;
- int vacationDays;

声明一个变量之后，必须用赋值语句对变量进行显示初始化，未被初始化的变量不能使用。

### 变量初始化
- 声明时，同时初始化
```
int vacationDays = 12;
```
- 先声明，后初始化
```
int vacationDays;
vacationDays = 12;
```
### 常量

Java 中，是使用关键字 final 指示常量。

- 普通常量
```
...
final double CM_PER_INCH = 2.54;
...
```

- 类常量
```
public class Constants{
    public static final double CM_PER_INCH = 2.54;
    ....
}
```


## 运算符

- 算数运算符
  - `+` `-` `*` `/` `%`
- 二元算数符
  - `+=` `-=` `*=` `%=`
- 自增或自减运算符
  - `++` `--`
- 关系运算符 与 boolean 运算符
  - `==` `!=` `<` `>` `<=` `>=`
  - `&&` `||` `!`
- 三元运算符
  - `?:`
- 位运算符
  - `&`(与) `|`(或) `^`(异或) `~`(非)
  - `>>` `<<`
  - `>>>`

## 字符串

从概念上讲，Java 字符串就是Unicode 字符序列。Java 没有内置的字符串类型，而是在标准Java类库中提供了一个预定于类，叫做 String 。

每个用双引号括起来的字符串都是一个 String 类的实例。
```
String e = "";
String greeting = "Hello";
```

### 字符串的构建

采用字符串连接的方式来构建字符串，每次都会构建一个新的String对象，非常耗时，效率比较低。

而使用 StringBuilder 类来构建就可以避免上面所述的这些问题。
```java
StringBuilder builder = new StringBuilder();
builder.append(ch);
builder.append(str);
String completedString = builder.toString();
```

### 字符串常用 API 方法
java.lang.string 1.0
- char charAt(int index)
- int codePointAt(int index)
- int offsetByCodePoints(int startIndex, int cpCount)
- int compareTo(String other)
- int endsWith(String suffix)
- boolean equals(Object other)
- boolean equalsIgnoreCase(String other)
- int indexOf(String str)
- int indexOf(String str, int fromIndex)
- int indexOf(int cp)
- int indexOf(int cp, int fromIndex)
- int lastIndexOf(String str)
- int lastIndexOf(String str, int fromIndex)
- int lastIndexOf(int cp)
- int lastIndexOf(int cp, int fromIndex)
- int length()
- String replace(CharSwquence oldString, CharSwquence newString)
- boolean startsWith(String suffix)
- String subString(int beginIndex)
- String subString(int beginIndex, int endIndex)
- String toLowerCase()
- String toUpperCase()
- String trim()



## 输入输出

- 标准输入输出
- 文件输入与输出

## 控制流

- 块作用域
- 条件语句
- 循环
- 多重选择
- 中断控制流程语句

## 大数值

java.math 包中有两个类： BigInterger 和 BigDecimal。 如果Java 提供的基本的整数和浮点数精度不能满足需求，就可以使用这两个类来处理：
- BigInterger 能够实现任意精度的整数运算
- BigDecimal 能够实现任意精度的浮点数运算

将普通数值转为大数值
```
BigInteger a = BigInteger.valueOf(1000);
```
### BigInterger 常用 API
- BigInteger add(BigInteger other)
- BigInteger subtract(BigInteger other)
- BigInteger multiply(BigInteger other)
- BigInteger divide(BigInteger other)
- BigInteger mod(BigInteger other)

### BigDecimal 常用  API
- BigDecimal add(BigDecimal other)
- BigDecimal subtract(BigDecimal other)
- BigDecimal multiply(BigDecimal other)
- BigDecimal divide(BigDecimal other)
- BigDecimal mod(BigDecimal other)

## 数组

数组，是一种用来存储同一类型值的集合的数据结构。

```
int[] a;
int a[];
int[] a = new int[100];
String[] names = new String[10];
```

初始化：
```
int[] small = {2,3,4,5,5,77,8,9};
int[] small = new int[] {2,3,4,5,5,77,8,9};
```

java.util 包中提供了 Arrays 类，该类提供了一些常用的方法可以对数组进行各种操作。

### java.util.Arrays 常用 API
- static String toString(type[] a)
- static type copyOf(type[] a, int length)
- static type copyOfRange(type[] a, int start, int end)
- static void sort(type[] a)
- static int binarySearch(type[] a, type v)
- static int  binarySearch(type[] a, int start, int end, type v)
- static void fill(type[] a, type v)
- static boolean equals(type[] a, type[] b)



.
