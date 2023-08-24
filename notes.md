# Notes for JAVA self-learning

## get started
```java
public class Main {
  public static void main(String[] args) {
    System.out.println("Hello World");
  }
}
```
注意，main 的格式必须遵从两个形式：
> public static void main(String args[])

or

> public static void main(String[] args)

控制台数据作为String数组被读取
可以用args[index]访问


## Java Output

```java
System.out.println("Hello World!"); // System Class
System.out.println("I am learning Java."); // out member, println (print line) method
System.out.println("It is awesome!");
System.out.print("Hello World! "); // does not change line
```
补充其他的print方式
- printf(String format, Object... args) // 指定输出格式 \n %n 换行


## Java Variable
String,int,float,char,boolean
| 常量变量申明 用final 或者 constant
```java
int x = 5, y = 6, z = 50;
System.out.println(x + y + z);
```
### The general rules for naming variables are:

- Names can contain letters, digits, underscores, and dollar signs
- Names must begin with a letter
- Names should start with a lowercase letter and it cannot contain whitespace
- Names can also begin with $ and _ (but we will not use it in this tutorial)
- Names are case sensitive ("myVar" and "myvar" are different variables)
- Reserved words (like Java keywords, such as int or boolean) cannot be used as names
reserved words: goto/const (cannot use)
### more about data types
Data types are divided into two groups:

- Primitive data types - includes byte, short, int, long, float, double, boolean and char
- Non-primitive data types - such as String, Arrays and Classes

### integer variable types

byte 1byte
short 2bytes
int 4bytes (default int)
long 8bytes (specify with L or l)


### declare float and double (also scientific)

float 4bytes
double 8bytes

```java
float f1 = 35e3f; // f as an end
double d1 = 12E4d; // e for secientific d as an end
System.out.println(f1); 
System.out.println(d1);
```
### non-10-based representation

`0b` or `0B` for binary
`0` for octal
`0x` or `0X` for hexadecimal

### java char

Unicode coding scheme

similar to cpp
```java
char myVar1 = 65, myVar2 = 66, myVar3 = 67;
System.out.println(myVar1); // A
System.out.println(myVar2); // B
System.out.println(myVar3); // C
```

### None-primitive dtype
The main difference between primitive and non-primitive data types are:

- Primitive types are predefined (already defined) in Java. Non-primitive types are created by the programmer and is not defined by Java (except for String).
- Non-primitive types can be used to call methods to perform certain operations, while primitive types cannot.
- A primitive type has always a value, while non-primitive types can be null.
- A primitive type starts with a lowercase letter, while non-primitive types starts with an uppercase letter.
- The size of a primitive type depends on the data type, while non-primitive types have all the same size.

### Type casting
2 types: 
1. widening casting (automatic) 
2. narrowing casting (manual)

1. `byte` -> `short` -> `char` -> `int` -> `long` -> `float` -> `double`
2. `double` -> `float` -> `long` -> `int` -> `char` -> `short` -> `byte`

```java
public class Main {
  public static void main(String[] args) {
    int myInt = 9;
    double myDouble = myInt; // Automatic casting: int to double

    System.out.println(myInt);      // Outputs 9
    System.out.println(myDouble);   // Outputs 9.0
  }
}
```
Narrowing casting must be done manually by placing the type in parentheses in front of the value:

```java
public class Main {
  public static void main(String[] args) {
    double mydouble = 9.78d;
    int myInt = (int) mydouble;

  }
}
```

## java operators 
| very similar to c++
&& || !
special ones
&=, |=, ^=

### bit operators
`~` reverse bit by bit
`&` bit and
`|` bit or
`^` bit xor
`\>\>` 


## java Strings
### basics
`String greeting = "Hello"; // double quote`
```java
String txt = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
System.out.println("The length of the txt string is: " + txt.length());
String txt1 = "Hello World";
System.out.println(txt1.toUpperCase());   // Outputs "HELLO WORLD"
System.out.println(txt1.toLowerCase());   // Outputs "hello world"
String txt = "Please locate where 'locate' occurs!";
System.out.println(txt.indexOf("locate")); // Outputs 7
// similarly, method lastIndexOf()
str.trim(); // remove space at the beginning and the end of the string

```
3 classes of String
String, StringBuffer (mutable) and StringBuilder (mutable)
> "" represents empty String instead of null. The latter means no space of memory is allocated.

### String

how to construct
```java
String();
String(String original);
String(StringBuffer buffer);
String(byte[] bytes); //form bytes to String, decode required
String(char[] value, int offset, int length) // creating String obj from char[]
```
### String pool
When initializing Constant String object without using "new"
Then system first search for the object. If found, pass reference. Else, create new object.


### concatenation
+ or concat()
```java
String firstName = "John ";
String lastName = "Doe";
System.out.println(firstName.concat(lastName));
```
### number and String with +
```java
String x = "10";
int y = 20;
String z = x + y;  // z will be 1020 (a String), no error
```
\+ can be used to concat any datatype.
This is because for objects of any kind, java provides a `toString()` method.

### special character
mainly \ escape char

\n
\r carrige return
\t tab
\b Backspace
\f Form Feed

### String comparison
```java
// == can check if the reference is the same
boolean equals(Object anObject); // same content？
boolean euqalsIgnoreCase(Object anObject);
int compareTo(String str); //return value: > (+) < (-) == (0)
// similarly, compareToIgnoreCase(String str)
// pattern
boolean endsWith(String suffix);
boolean startsWith(String prefix);
```
### truncate string
substring & split
```java
String substring(int beginIndex, int endIndex);
// [beginIndex,endIndex)
String[] split(String delimeter); // similar to that of python, return String[]
```

### StringBuffer and StringBuilder
mutable String
>区别在于，前者支持线程同步
```java
StringBuilder();
StringBuilder(CharSequence seq); // include String, StringBuilder and StringBuffer. (difference API)
StringBuilder(int capacity); // capacity specified
StringBuilder(String str)
int capacity(); // return maximum number of char;
// can automatically extend
```
### String append, insert, delete and replace
>append 可连续调用，返回StringBuffer,可追加任意类型数据
```java
StringBuffer insert(int offset, String str);
StringBuffer delete(int start, int end);
StringBuffer replace(int start, int end, String str);
```

## Java Math
useful methods are as follows
```java
Math.max(x,y);
Math.min(x,y);
Math.sqrt(x,y);
Math.abs(x);
Math.random(); // random float number in [0.0,1.0) 
```

## Java If...Else
very similar to those of C++
### if, else, else-if
```java
int time = 22;
if (time < 10) {
  System.out.println("Good morning.");
} else if (time < 18) {
  System.out.println("Good day.");
} else {
  System.out.println("Good evening.");
}
```
### Ternary Operator
> variable = (condition) ? expressionTrue :  expressionFalse;
short-hand for if-else
```java
int time = 20;
String result = (time < 18) ? "Good day." : "Good evening.";
System.out.println(result);
```

### Java Switch
(to be continued)
the result of the expression must be int/byte/short/char/String
## Java While
while or do-while

## Java for loop
> for-each loop: for (type variableName : arrayName) {}
like iterator

## break and continue
break and continue with label
to control which loop to break (by default, the inner most loop)
for example:
```java
label1: for (int x = 0; x < 5; x++) {
  for (int y = 5; y > 0; y--) {
    if (y==x) {
      // jump to outer loop and break
      break label1;
    }
    System.out.printf("(x,y) = (%d,%d)",x,y);
  }
}
```
similar for continue


## Java arrays

### basics
```java
String[] cars; // declare
```
initialize: comma separated list.
```java
String[] cars = {"a","b"}; // static initialize
```

dynamic initialize:
```java
int[] intarr;
intarr = new int[4]; 
// allocate 4 units of space, giving default value of 0
intarr[0] = 1;
intarr[1] = 2;
intarr[2] = 3;
intarr[3] = 4;
```
default value after memory allocation varies from type to type
E.g., boolean-false and null for reference objects


accessing elements: 0-based index

**length of Arr**
```java
String[] cars = {"Volvo", "BMW", "Ford", "Mazda"};
System.out.println(cars.length);
// Outputs 4
```
### interate over an array
```java
String[] cars = {"Volvo", "BMW", "Ford", "Mazda"};
for (int i = 0; i<cars.length; i++) {
  System.out.println(cars[i]);
}
// or
for (String item: cars) {
  System.out.println(item);
}
```

### an example: merging arrays
```java
public class HelloWorld {
    public static void main(String[] args) {
        int[] arr1 = {20,10,50,40,30};
        int[] arr2 = {114,514};
        // static initialization

        int[] result = new int[arr1.length + arr2.length];
        // dynamic . 

        for (int i = 0; i < result.length; i++) {
            if (i<arr1.length) {
                result[i] = arr1[i];
            }
            else {
                result[i] = arr2[i-arr1.length];
            }
        }

        for (int item: result) {
            System.out.println(item);
        }
    }
}
```

### multidimensional Arrays
how to use for each to access multidimensional array?
```java
for (int[] row : intArray) {
  for (int column : row) {
    System.out.print(column);
    System.out.print('\t');
  }
}
System.out.println();
```

## Basics of OOP
### declare a class
> [public] [abstract|final] class className [extends superclassName] [implements interfaceNameList] {}
1. [] means the content can be ignored.
2. superclassName: 父类名. By default, the class inherit from `Object` class
3. implements interfaceNameList,接口列表.

### declare member of class
> [public|protected|private] [static] [final] type variableName;
1. public|protected|private for encapsulate
2. static
3. final, immutable variable

### declare member method/function
> [public|protected|private] [static] [final|abstract] [native] [synchronized] type methodName([para_list]) [throws exceptionList] {}
1. native method:不能跨平台
2. synchronized: 同步，多线程时只能串行执行确保线程安全
3. type: void returns nothing. `return;`

### package
Basically, package -> namespace
> package pkg1.[.pkg2[.pkg3]]
lower case, cannot begin with number
```java
import package1;
```

### encapsulation
private, default, protected and public

### static
execute when the class is loaded for the first time
static code block
static method: have access to static variable and other method

## Object
declaration-instantiate(allocate memory and initialize)
pay attention to "null" obj

### constructor
1. same name as class
2. no return value
3. use together with new


### overload construction method
---
### "this" keyword
- access instance variable
- access instance method
- access other constructor in the class (reduce the number of lines)

## inheritance and polymorphism
[extends superclass]
### access the constructor of superclass
keyword: "super"

example:
```java
package test;

import java.util.Date;

public class Person {
    private String name;
    private int age;
    private Date birthDate;
    
    public Person(String name, int age, Date d) {
        this.name = name;
        this.age = age;
        birthDate = d;
    }

    public Person(String name, int age) {
        this(name,age,new Date());
    }
}
```
*Person.java*

```java
package test;

import java.util.Date;

public class Student extends Person{
    private String school;

    public Student(String name, int age, Date d, String school){
        super(name, age, d); // super must be the first line of constructor
        this.school = school;
    }

    public Student(String name, int age, String school) {
        super(name, age);
        this.school = school;
    }

    /*
     * here is an incorrect example
     * 
     * public Student(String name,  String school) {
     *   this school = school;
     * }
     */
}
```
*Student.java*

super 语句必须位于子类构造方法的第一行

解决第二段代码最后错误的方法有：
1. 在父类中添加默认构造
2. 添加super语句显式调用父类构造
3. 添加this语句显示调用Student类其他构造方法

### 成员变量隐藏和方法覆盖
重名时，子类覆盖父类成员变量，用super关键字可以调用
方法覆盖也是同理的

> add comment `@Override` before the definition
- 增加程序可读性
- 编译器检查相应方法在父类中是否存在，不存在则报错

覆盖原则
- 覆盖后方法不能比原来有更严格的访问控制
- 覆盖后方法不能比原方法产生更多异常（？） p114?

### polymorphism
1. inheritance
2. override
3. declare dtype <- superclass, instance <- class
定义为父类，实体为子类
多态发生时，java虚拟机运行根据引用变量指向的实例调用方法，而不是根据引用对象本身调用

### instanceof operator
obj instanceof type
子类 instanceof 父类：true
反之则为false.

### 引用类型转换
属于同一棵继承层次树的引用类型才可以相互转换

downcast-not automatic transformation
不明确实例类型时用instanceof检验

### final 关键字
final修饰得到常量
- final修饰的局部变量必须使用之前被赋值一次才能使用
- final修饰的成员变量必须在构造方法或者静态代码块中初始化

final修饰的类不能被继承

final修饰方法不能被子类覆盖

## Abstract class & Interface

### Abstract class
```java

public abstract class Figure {
  public abstract void onDraw();
}

```
只有抽象方法声明，没有实现
> 如果有一个方法被声明为抽象，那相应的类也必须声明为抽象

Here are example of subclass

```java
public class Ellipse extends Figure {
  @Override
  public void onDraw() {
    System.out.println("Draw Ellipse:");
  }
}

public class Triangle extends Figure {
  @Override
  public void onDraw() {
    System.out.println("Draw Triangle:");
  }
}
```

invocation:

```java
public class Helloworld {
  public static void main(String[] args) {
    Figure f1 = new Triangle(); // polymorphism
    f1.onDraw();
  }
}
```

*Abstract class cannot be instantiated.*

### Interface
接口

> 关键词是interface

```java
package xxx;

public interface Figure {
  // 接口中静态成员变量
  String name = "XX"; // 省略public static final 原因后面讲

  void onDraw() ; // 省略public
}
```

> 省略public表示默认访问级别，包内可访问
> 接口中成员均为静态成员，可以省略public static final
> 声明抽象方法，省略了public

调用interface的关键词是implements，注意在java中没有多继承类，但可以多继承接口

```java
package xxx;

import xxx.Figure;

public class Ellipse implements Figure {
  @ Override
  public void onDraw() {
    System.out.println("Ellipse");
  }
}
```


Also, interface cannot be instantiated

多继承：
```java

package xxx;

public interface InterfaceA {
  void methodA();

  void methodB();
}

package xxx;

public interface InterfaceB {
  void methodA();

  void methodB();
}
```

```java
//多继承接口实现代码

package xxx;

import xxx.InterfaceA;
import xxx.InterfaceB;

public class AB extends Object implements InterfaceA, InterfaceB {
  // 多继承的不同接口只需一个implements关键字，然后之后的接口之间用逗号分隔
  @Override
  public void methodA() {}

  @Override
  public void methodB() {}

  @Override
  public void methodC() {}

}
```
#### 接口多继承
由于接口中的方法都是抽象的，继承后什么也不用做
类继承多继承的接口相当于继承每一个子接口中的所有方法，可以看作多层次的封装
```java
// InterfaceA.java
package xxx;

public interface InterfaceA {
  void methodA ();
  void methodB ();
}

// InterfaceB.java

package xxx;

public interface InterfaceB extends InterfaceA{
  @Override 
  void methodB();
  
  void methodC();
}
// 接口之间的继承仍然使用extends

//ABC.java

package xxx;
import xxx.InterfaceB;

public class ABC implements InterfaceB {
  @Override
  methodA();

  @Override
  methodB();

  @Override
  methodC();
}

```

#### Java8: default method and static method

Here is an example
```java
package xxx;

public interface InterfaceA {
  void methodA();
  String methodB();

  // default method
  default int methodC() {return 0;}

  default String methodD() {
    return "默认方法返回字符串"
  }

  static double methodE() {return 0.0;}

}

// ABC.java
package xxx;

import xxx.InterfaceA ;

public class ABC implements InterfaceA {
  @Override
  public void methodA() {}

  @Override
  public String methodB() {return "实现了methodB"};

  @Override
  public int methodC() {return 514;}
} 
// 默认方法可以被选择性覆盖（这里覆盖了C而没有覆盖D）
// 静态方法无需实现，实现类中不能拥有接口中的静态方法

// HelloWorld.java
package xxx;

import xxx.InterfaceA;

public class HelloWorld {
  public static void main(String[] args) {
    InterfaceA abc = new ABC();
    // 声明接口类型，对象是实现类，发生多态

    System.out.println(abc.methodB());
    System.out.println(abc.methodC());
    System.out.println(abc.methodD());
    System.out.println(InterfaceA.methodE()); // 访问了InterfaceA静态方法methodE
  }
}
```

### 抽象类与接口的区别

## 枚举类 Emun
使用枚举可以提高程序可读性！

> Java Enumerate class
> superclass is java.lang.Enum 不需要显式声明
> interface
> cannot be inherited

### 枚举类的声明
> [public] enum className {Constlist}

```java
// WeekDays.java

package xxx;

public enum WeekDays {
  MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY
}

// HelloWorld.java
package xxx;

public class HelloWorld {
  public static void main(String[] args) {
    Weekdays day = Weekdays.FRIDAY;
    System.out.println(day);

  switch (day) {
    case MONDAY:
      System.out.println("Monday");
      break;
    case TUESDAY:
      System.out.println("Tuesday");
      break;
    case WEDNESDAY:
      System.out.println("Wednesday");
      break;
    case THURSDAY:
      System.out.println("Thurday");
      break;
    default: // case FRIDAY 
      System.out.println("Friday");
    }
  }
}
```

> Enumerate Class works well with switch: case clause can directly use Enum Constant without adding Enum Class perfix
> case分支语句应该对应枚举常量个数

### 枚举类的成员变量和方法

```java
package xxx;

public enum WeekDays {
  MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY;


private String name;
private int index;

private static int staticVar = 100;

// override the toString() method in superclass
@Override
public String toString() {
  StringBuilder sb = new StringBuilder();
  sb.append(name);
  sb.append('-');
  sb.append(index);
  return sb.toString(); // 为什么是sb.toString() ? 

}

public String getInfo() {
  return super.toString(); // 调用父类中的toString()方法
}

public static int getStaticVar() {
  return staticVar;
}
}
```
> when adding other members to the Enum Class, the constant list must be the first line of code in the class body
> And the constant list ends with ;

```java

package xxx;

public class HelloWorld {
  public static void main(String[] args) {
    WeekDays day = WeekDays.FRIDAY;

    System.out.println(day); //类内toString方法打印
    System.out.println(day.getInfo()); // 默认toString打印
    System.out.println(Weekdays.getStaticVar());
  }
}
```

### Enum Constructor

可以在上一节的代码中进一步添加构造方法

```java
package xxx;

public enum WeekDays {
  MONDAY("Monday",0), TUESDAY("Tuesday",1), WEDNESDAY("Wednesday",2), THURSDAY("Thursday",3), FRIDAY("Friday",4); // 补充参数表


private String name;
private int index;

private WeekDays(String name,int index) {
  this.name = name;
  this.index = index;
}

private static int staticVar = 100;

// override the toString() method in superclass
@Override
public String toString() {
  StringBuilder sb = new StringBuilder();
  sb.append(name);
  sb.append('-');
  sb.append(index);
  return sb.toString(); // 为什么是sb.toString() ? 

}

public String getInfo() {
  return super.toString(); // 调用父类中的toString()方法
}

public static int getStaticVar() {
  return staticVar;
}
}
```

> 枚举类构造方法一定是私有的方法，以上代码中的private关键字可以省略
> 这也意味着枚举类不允许在外部创建对象
> 添加构造方法后，枚举常量列表也需要修改，初始化调用构造方法

*私有构造方法经常用于单例设计or工厂设计模式，枚举类的设计类似于后者*

### 枚举类常用方法

所有枚举类都继承java.lang.Enum类，其中有一些常用的方法

> `int ordinal()` 返回枚举常量的顺序，根据枚举常量声明的顺序而定，从零开始 index
> `Enum_Type values()` 静态方法，返回一个包含全部枚举常量的数组
> `Enum_Type valueOf(String str)` 静态方法，str是枚举常量对应的字符串，返回一个包含枚举类型的实例（？

使用例
```java
package xxx;

public class Helloworld {
  public static void main(String[] args) {
    WeekDays[] allValues = WeekDays.values();
    for (WeekDays value: allValues) {
      System.out.printf("%d - %s\n", value.ordinal(), value); //回顾一下printf
      // ordinal 获取了当前枚举常量的顺序
    }

    WeekDays day1 = WeekDays.FRIDAY;
    WeekDays day2 = WeekDays.valueOf("FRIDAY");
    //两种方式创建对象

    System.out.println(day1 == WeekDays.FRIDAY);
    System.out.println(day1.equals(WeekDays.FRIDAY));
    System.out.println(day2 == day1);
    //比较结果都为true
  }

}
```
> **注意** java引用类型比较时，有两种比较方法 == 或 equals，前者比较引用是否指向同一个对象，后者比较对象内容是否相同。
> 枚举类中的枚举常量不论何时只有一个实例，因此判断总为true

## Java常用类

### Java根类_Object Class
常用方法有:
> `String toString()` return the String representation of an object
> `boolean equals(Object obj)` indicate equality

这些方法都是需要在子类中进行覆盖的

#### toString 方法
未经过覆写的默认字符串：“类名@对象哈希码”

```java
package xxx;

public class Person {
  String name;
  int age;

  public Person(String name, int age) {
    this.name = name;
    this.age = age;
  }

  @Override
  public String toString() {
    return "Person [name =" + name + ", age" + age + "]"; // 打印过程会调用这一方法
  }
}
```

#### 对象比较方法
需要为比较指定相等的规则，比如说，Person类中比较名字+年龄
> 类似cpp的操作符重载

```java
// 覆写一例
package xxx;

public class Person {
  String name;
  int age;

  public Person(String name, int age) {
    this.name = name;
    this.age = age;
  }

  @Override
  public String toString() {
    return "Person [name =" + name + ", age" + age + "]"; // 打印过程会调用这一方法
  }

  @Override
  public boolean equals(Object otherObject) { // template

    if (otherObject instanceof Person) {
      Person otherPerson = (Person) otherObject; // 判断为实例才能有这一行
      if (this.age == otherPerson.age && this.name.equals(otherPerson.name)) // 这样对吗？
      {
        return true;
      }
    }
  }
}
```

### Wrapper Class 包装类

8种基本数据类型不属于类，不具备对象特征，没有成员变量与方法。java提供了包装类来包装基本数据类型
种类的基本命名特征是大写首字母
除了：`int` - `Integer` 和 `char` - `Character`

#### 数值包装类
including `Byte, Short, Integer, Long, Float, Double`

1. 构造方法
   1. `Integer(int value)` 指定数值构造对象
   2. `Integer(String s)` 指定字符串构造对象，s是十进制字符串表示的数值
2. 共同父类Number，是抽象类，子类必须实现以下方法，以便数值类可以相互转换
   1. `byte byteValue()`
   2. `double doubleValue()`
   3. `float floatValue()`
   4. `int intValue()`
   5. `long longValue()`
   6. `short shortValue()`
3. `int compareTo()` 方法
   1. == return 0
   2. \> return int>0
   3. < return int<0
4. 字符串转换：一些parseXXX()静态方法
   1. `static int parseInt(String s)`转化为有符号10进制整型
   2. `static int parseInt(String s, int radix)`radix 指示基数，此功能在Double，Float中没有
5. 静态`toString`方法
   1. `static String toString(int i)`
   2. `static String toString(int i, int radix)`

数值类的示例代码
```java
package xxx;

public class HelloWorld {
  public static void main(String[] args) {

    Integer objInt = new Integer(90);
    Double objDouble = new Double(90.0);
    Float objFloat = new Float("90.0");
    Long objLong = new Long("90");

    long longvar = objInt.longValue(); // 转化类型

    Float objFloat2 = new Float(100);
    int result = objFloat.compareTo(objFloat2);
    // 比较，result = -1
    int intVar2 = Integer.parseInt("100");
    int intVar3 = Integer.ParseInt("ABC", 16);

    String str1 = Integer.toString(100);
    String str2 = Integer.toString(100, 16);
  }
}
```

#### Character 类

常用方法有
> `Character(char value)` 构造方法
> `Char charValue()` 获取值
> `int compareTo(Character anotherCharacter)` 比较返回int, 相等时返回0

#### Boolean Class
*similar to Char Class*

> `Boolean(boolean value)`
> `Boolean(String s)` s cannot be null. If s is "true" (case insensitive) create true obj., otherwise false.

Boolean.parseBoolean(String s)
作用原理与Boolean类构造方法类似，但是这一方法创建的是boolean 而不是Boolean

#### auto boxing and unboxing (for reference)

auto unboxing ensures direct numerical calculation between numerical Class

auto boxing enables creating Class directly without using constructor

```java

Integer objInt = new Integer(80);
Double objDouble = new Double(90.0);

double sum = objInt + objDouble;

Character objChar = 'C'; // auto boxing

// when defining fuction

public static int display(Integer objInt) {
  System.out.println(objInt);

  //return objInt.intValue(); not necessary anymore
  return objInt; // auto unboxing
}
```

### Math Class
math class is final class

basic methods:

1. double ceil(double a); double floor(double a); int round (float a)
2. min/max(Type a, Type b); four kind of overload
3. abs()
4. basic trigonometric functions and Degree-Radian transform
5. log()
6. sqrt()
7. pow(a,b)
8. random() //return [0,1)
9. constants: PI and E (natural constant)

### Class for large numbers (for reference)
BigInteger and BigDecimal, all inherited from Number Class
Deal with large number

BigInteger: immutable large Integer with arbitrary precision

```java
package xxx;

import java.math.BigInteger;

public class Helloworld {
  public static void main(String[] args) {
    BigInteger number1 = new BigInteger("999999999999999");
    // constructor
    BigInteger number2 = new BigInterer("9999999999999999",16); // the second Integer Indicates the base of the given String

    System.out.println(number1.add(number2));
    System.out.println(number1.subtract(number2));
    System.out.println(number1.mutiply(number2));
    System.out.println(number1.divide(number2));

    //  math operations on BigIntegers
  }
}
```

BigDecimal: immutable 10-based number with arbitrary precision

```java
BigDecimal(BigInteger val);
// transform BigInteger to BigDecimal

BigDecimal(double val);
BigDecimal(int val);
BigDecimal(long val);
BigDecimal(String val);

// algebraic operations are similar to the BigInteger

```

Since these two classes inherited from **Number** class, they can also implement 6 basic functions of Number class.

Use `compareTo(Object obj)` to compare the objects of these two classes.



### Class for date and time



## Inner Classes

nested Classes

Why inner class?
- encapsulation
- offering new **namespace**
- easier access to inner class members

Understand the classification of Inner Classes

*psuedo code*
```java
If (Class name is given) {
  if (scope is the whole outer class) {
    if (instance) {
      a = instance object class;
    }
    else { a = static class; }
  }
  else { a = local class; }

}
else { a = anonymous class; }
```

### **成员内部类**
---
#### **实例成员内部类**
成员内部类可以声明为四种访问级别，而外部类仅可以声明为公有或默认

```java
package xxx;

public class Outer {
  private int x = 10;

  private void print() {
    System.out.println("Testing in progress, outer function invoked");
  }

  public void test() {
    Inner inner = new Inner();

    inner.display(); 

    // call the function of inner class
  }

  class Inner {
    private int x = 5;

    void display() {
      System.out.println(Outer.this.x); // access the member of outer class
      System.out.println(this.x); // access the member of inner class
      System.out.println(x); // same as last line

      Outer.this.print();
      print(); // these two lines are the same, because print is defined only in Outer class
    }
  }
}
```

```java
package test;

public class HelloWorld {
  public static void main(String[] args) {
    Outer outer = new Outer();

    outer.test(); // lower case "outer"

    Outer.Inner inner  = outer.new Inner(); // outer.new Inner();
    inner.display();
    // access inner class directly by ClassName.xxx

  }   
}
```

#### **静态成员内部类**
静态内部类仅可以访问外部类静态对象
```java
package xxx;
public class View {
  private int x = 20;
  private static int staticX = 10; // accessible to inner class

  static class Button {
    void onClick() {
      System.out.println(staticX);
      // System.out.println(x); // compilation error
    }
  }
}
```

```java
package xxx;

public class HelloWorld {
  public static void main(String[] args) {
    View.Button button = new View.Button(); // inner_class.inner_static_class
  }
}
```
### 局部内部类
即在方法体或代码块中定义的内部类
访问级别*default*，不可为静态，可以访问外部类所有成员

```java
package xxx;

public class Outer {
  private value = 10;

  public void add(final int x, int y) {
    int z = 100;

    class Inner {
      void display() {
        int sum = x + y + z + value;
        System.out.println("sum = " + sum);
      }
    }
    // Inner inner = new Inner();
    // inner.display();

    new Inner().display(); //声明了匿名对象，没有为Inner对象分配引用变量名，适用于只调用一次的情况

  }
}
```

``` java
package xxx;

public class HelloWorld {

  public static void main(String[] args) {
    Outer outer = new Outer;
    outer.add(100,300);
  }
}
```
---

### 匿名内部类
本质上是没有名字的局部内部类
*内部类要访问的参数需要声明为final的* (?? 为什么)


```java
package xxx;

public class View {
  
  public void handler(onClickListener listener) {
    listener.onClick();
  }
}
```
```java
package xxx;

public interface onClickListener {
  void onClick();
}
```

```java
package xxx;

public class HelloWorld {
  public static void main() {
    
    View v = new View();
    // 方法参数为匿名内部类
    v.handler(new OnClickListener() {
      @Override
      public void onClick() { System.out.println("实现接口的匿名内部类");}
    }
    );

    Figure f = new Figure() {
      @Override
      public void onDraw() {
        System.out.println("继承类的匿名内部类");
      }
    };

    // 具体类作为内部类
    Person person = new Person("Tong", 18) {
      @Override
      public String toString() {
        return "xxx" ;
      }
    };

    System.out.println(person);
  }
}

```

---
## **Lambda expression** and functional programming

### 实现方法
```java
public static Calculable calculable(char opr) {
  Calculable result;

  if (opr == '+') {
    // lambda expression instead of Calculable interface
    result = (int a, int b) -> {
      return a + b;
    };
  }
  else {
    result = (int a, int b) -> {
      return a - b;
    };
  }
  return result;
}
```
> `(paraList) { // Lambda Block }`
> 
> paraList is similar to that in the interface

### 函数式接口
Lambda实现的接口是函数式接口，只能有一个方法，如果在接口中声明了多个抽象方法，会报错

```java
package xxx;

@FunctionalInterface
public interface Calculable {
  int calculateInt(int a, int b);
}
// still, we can define default and static methods/functions
```

Lambda表达式是匿名方法代码。方法必须声明在类或接口中，对于Lambda，在函数式接口中声明。

### shorthand expression for λ

1. 省略参数类型
2. 省略参数小括号（单一参数）
3. 省略return和大括号（只有一个语句的话）

```java
public static Calculable calculate(int power) {
  Calculate result;

  if (power == 2) {
    result = (int a) -> {
      return a*a;
    };
  } else {
    result = a -> a*a*a; //最简化
  }
  return result;
}
```

### 作为参数使用Lambda表达式

```java
package xxx;

public class HelloWorld{

  public static void main(String[] args) {

    int n1 = 10;
    int n2 = 5;
    display((a, b) -> {
      return a + b;
    }, n1, n2);


    display((a, b) -> a-b, n1, n2);
}
  public static void display(Calculable calc, int n1, int n2) {
    System.out.println(calc.calculateInt(n1, n2));
  }
}
```
---
### 访问变量
成员变量：实例成员变量和静态成员变量。Lambda表达式可以像普通方法一样访问成员变量
>注意：静态方法只能访问静态成员变量
```java
package java.Lambda;

public class LambdaDemo {
    
    private int val = 10;

    private static int staticVal = 5;

    public static Calculable add() {
        Calculable result = (int a, int b) -> {
            staticVal++;
            int c = a + b + staticVal;
            return c;
        };
        return result;
    }

    public Calculable sub() {
        Calculable result = (int a, int b) -> {
            staticVal++;
            this.val++;
            int c = a - b - staticVal - this.val;
            return c;
        };
        return result;
    }
}

```
Lambda捕获的**局部变量**会变为final的，不可以改变

### 方法引用
> `::`operator，不是调用方法
>
> 引用格式：
> `Type::StaticMethod` for static method
> `Instance::InstantMethod` for instant method

*被引用的方法的参数表和返回值类型必须与函数式接口方法的参数列表和方法返回值类型一致* （？）

Examples:
```java
package xxx;

//这是函数式接口的定义
@FunctionalInterface
public interface Calculable{
  int calculateInt(int a, int b);
}
```

```java
package xxx;

public class LambdaDemo {
  public static int add(int a, int b) {
    return a + b;
  }

  public int sub(int a, int b) {
    return a - b;
  }
}
```
```java
package xxx;

public class HelloWorld{

  public static void main(String[] args) {

    int n1 = 10;
    int n2 = 5;

    display(LambdaDemo::add,n1,n2);

    LambdaDemo d = new LambdaDemo();

    display(d::sub,n1,n2);

  }

  public static void display(Calculable calc, int n1, int n2) {
    System.out.println(calc.calculateInt(n1,n2));
    // display中的第一个参数接受Calculable实现对象，Lambda表达式和方法引用，三类对象
    
  }
}

```
---

## **异常处理技巧**

异常类封装为Exception类，此外还有Throwable和Error类；

### Throwable Class methods
```java
String getMessage();
void printStackTrace();
String toString(); // 异常对象的具体描述
```

Throwable 包含Exception和error。
Error 无法避免，包含如虚拟机错误或者内存泄漏等致命问题

Exception类包含受检查异常和运行时异常（Runtime Exception）

### **捕获异常**
try-catch
> ```java
>try{
>  //可能出错语句
>}
>catch (Throwable e) {
>  // 处理异常 e
>}

### Mutiple catch blocks
就是用连续的catch代码块，匹配可能出现的多种Exception
>多个异常之间存在父子类关系时，一般先捕获子类再捕获父类
>一个异常捕获后，后续catch不再执行

一段有关file IO的代码

```java
package xxx;

public class HelloWorld {

  public static void main(String[] args) {
    Date date = readDate();
    System.out.println("Date = " + date); 

  }

  public static Date readDate(){

    FileInputStream readfile = null;
    InputStreamReader ir = null;
    BufferReader in = null;

    try {
      readfile = new FileInputStream("readme.txt");
      ir = new InputStreamReader(readfile);
      in = new BufferReader(ir);

      String str = in.readLine();
      if (str == null) {
        return null;
      }

      DateFormat df = new SimpleDateFormat("yyyy-mm-dd");
      Date date = df.parse(str);
      return date;
    }
    catch (FileNotFoundException e) {
      System.out.println("  ");
      e.printStackTrace();
    } 
    catch (IOException e) {
      System.out.println("  ");
      e.printStackTrace();
    }
    catch (ParseException e) {
      System.out.println("  ");
      e.printStackTrace();      
    }
    return null;
  }
}
```
*Besides, we can use nested try-catch blocks. When Exception is raised in inner layer, the inner catch will try to catch the exception first.*

### **多重捕获**
捕获之后的处理相同的话，可以使用多重捕获，使代码更简洁

```java
try {
  //...
} catch (IOException | ParseException e) {
  //...
}
```

use operator `|`

### **资源释放**

1. try-catch-finally
2. Java7 之后的automatic resource management

第一种方法，finally语句块不论是try正常结束还是catch异常结束都会执行finally代码块
在finally代码块中可以关闭一些input stream

> 注意，关闭instream过程也有可能出错，所以需要额外的try-catch来预防错误

第二种方法无需finally，将资源释放的工作完全交给JVM

在`try`语句后面加`(//initialization of resources)`

比如，修改上文的代码示例：
```java
package xxx;

public class HelloWorld {

  public static void main(String[] args) {
    Date date = readDate();
    System.out.println("Date = " + date); 

  }

  public static Date readDate(){


    try (FileInputStream readfile = new FileInputStream("readme.txt");
      InputStreamReader ir = new InputStreamReader(readfile);
      BufferReader in = new BufferReader(ir)) // 用;分隔
      {
      String str = in.readLine();
      if (str == null) {
        return null;
      }

      DateFormat df = new SimpleDateFormat("yyyy-mm-dd");
      Date date = df.parse(str);
      return date;
    }
    catch (FileNotFoundException e) {
      System.out.println("  ");
      e.printStackTrace();
    } 
    catch (IOException e) {
      System.out.println("  ");
      e.printStackTrace();
    }
    catch (ParseException e) {
      System.out.println("  ");
      e.printStackTrace();      
    }
    return null;
  }
}
```
> 使用了*Auto Closable Interface*

### throws 与 声明方法抛出异常

方法后可以选择抛出异常 `[throws ExceptionList]` 使用关键词throws。
方法中可能抛出的异常（除了Error和RuntimeException及其子类外）都需要通过throws语句列出，异常间用`,`分隔

示例：

```java
package xxx;

public class HelloWorld {

  public static void main(String[] args) {

    try{
      Date date = readDate();
      System.out.println("Date = " + date); 
    }
    catch (IOException e) {
      System.out.println("  ");
      e.printStackTrace();
    }
    catch (ParseException e) {
      System.out.println("  ");
      e.printStackTrace();      
    }

  }

  public static Date readDate() throws IOException, ParseException{
    //方法中不捕获，只抛出。捕获交给main处理
    //自动资源管理
    FileInputStream readfile = new FileInputStream("readme.txt");
    InputStreamReader ir = new InputStreamReader(readfile);
    BufferReader in = new BufferReader(ir);
    
    String str = in.readLine();
    if (str == null) {
      return null;
    }

    DateFormat df = new SimpleDateFormat("yyyy-mm-dd");
    Date date = df.parse(str);
    return date;

  }
}
```

### **自定义异常类**
注意需要继承RuntimeException或者其子类
自定义的异常类通常需要提供两个构造方法
```java
package xxx;

public class MyException extends Exception {
  public MyException() {
    
  }// 第一个默认构造，无参，描述信息为空

  public MyException(String message) {
    super(message);
  }// 第二个为字符串参数的构造方法，message即为异常描述信息，可以用getMessage来获取
}
```

### **throw 与 显式抛出异常**
> throw Throwable

示例：
```java
package xxx;

public class HelloWorld {

  public static void main(String[] args) {

    try{
      Date date = readDate();
      System.out.println("Date = " + date); 
    }
    catch (MyExcpetion e) {
      System.out.println("  ");
      e.printStackTrace();
    }// 仅有可能捕捉到MyException
  }

  public static Date readDate() throws MyException{
    
    try(FileInputStream readfile = new FileInputStream("readme.txt");
    InputStreamReader ir = new InputStreamReader(readfile);
    BufferReader in = new BufferReader(ir))
    {
      String str = in.readLine();
      if (str == null) {
        return null;
      }
      DateFormat df = new SimpleDateFormat("yyyy-mm-dd");
      Date date = df.parse(str);
      return date;
    }
    catch (FileNotFoundException e){
      throw new MyException(e.getMessage()); // 主动抛出,可以向上一级系统隐藏异常“FileNotFoundException”
    }
    catch (IOException e){
      throw new MyException(e.getMessage());
    }
    catch (ParseException e) {
      System.out.println("...");
      e.printStackTrace();
    }

    return null;
  }
}
```
---
## **Java container**

### **List**
list包含ArrayList和LinkedList两类接口
list有序，可以重复

list继承自Collection接口
常用方法包括
1. Operation on elements
   1. `get(int index)`
   2. `set(int index, Object obj)`
   3. `add(Object obj)` append to the end of the list
   4. `add(int index, Object obj)` add to specific position
   5. `remove(int index)`
   6. `remove(Object obj)` remove the first occurrence
   7. `clear()` empty the list
2. boolean judgement
   1. `isEmpty()` return true if the list is empty
   2. `contains(Object obj)` return true if the list contains obj
3. access index
   1. `indexOf(Object obj)` return the index of the first occurence. (return -1 if not found) [string `find` in cpp]
   2. `lastIndexOf(Object obj)` return the index of the last occurence. (return -1 if not found) [string `rfind` in cpp]
4. other methods
   1. `iterator()` return an object of iterator to iterate over the list
   2. `size()` return the number of element in the list
   3. `subList(int from, int to)` return a sublist [from,to)

声明集合变量和方法的简单调用
```java
List list = new ArrayList();

String b = "B";

list.add("A");
list.add(b);
list.add("A");
list.add(b);

System.out.println(list.size());
System.out.println(list.lastIndexOf(b));

list.remove(b);
list.set(1,"C");
list.remove(0);
list.clear();

list.add(1); // auto-boxing !
int item = (Integer) list.get(0); // auto-unboxing
```

注意list的实例化过程，使用的是ArrayList类，这是因为List本身是接口，不能实例化
java中任何集合存放的都是对象/引用数据类型.放入基本数据类型时会自动装箱为类，再取出时也为相应对象。

Iterate over the list
use `for`/ enhanced-`for` or `Iterator`

```java
package List;

import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;


public class HelloWorld {
    public static void main(String[] args) {
        List<String> myList = new ArrayList<String>(); // generic type

        String b = "B";
        myList.add("A");
        myList.add(b);
        myList.add("C");
        myList.add(b);
        myList.add("D");
        myList.add("E");

        // Iterate with for
        for (int i = 0; i<myList.size();i++) {
            System.out.printf("%d. %s %n", i, myList.get(i));
        }

        // enhanced-for
        for (Object item: myList) {
            System.out.println(item);
        }

        // iterator
        Iterator it = myList.iterator();
        
        while (it.hasNext()) {
            Object item = it.next(); // transform iterator object to Object Type
            String s = (String) item;
            System.out.println(s); // directly print item is also ok
        }
    }
}
```
> Notice that the iterator points to a header of the List

### **Set集合**
无序，不重复

Methods
1. operation on elements
   1. `add(Object element)` append to the end
   2. `remove(Object element)` 
   3. `clear()`
2. Boolean Judgement
   1. `isEmpty()`
   2. `contains(Object element)` 判断是否有该元素return true/false
3. others
   1. `iterator()`
   2. `size()`

```java
  Set<String> set = new HashSet<String>(); // declare
  
  set.add("A");
  set.add(b);
  set.remove("C"); // 无事发生
  for (Object item: set) {
      System.out.println(item);
  }
```

遍历时同样可以使用增强for和迭代器两种方法，语法与List一致

### **Map集合** 
Map set consists of two types of sets: key and value. Key set is Set Type. No duplicates are allowed
Value set is collection type.

接口的实现类主要是哈希表（HashMap）

Methods:
1. operation on elements
   1. `get(Object key)`
   2. `put(Object key, Object value)`
   3. `remove(Object key)` 移除键值对
   4. `clear()`
2. Boolean judgement
   1. `isEmpty()`
   2. `containsKey(Object key)`
   3. `containsValue(Object value)`
3. View the sets
   1. `keySet()` returns key set
   2. `values()` returns value collection
   3. `size()` returns size of the map (total pairs of Key-value)

```java
Map map = new HashMap();
```

键对应值若不存在，打印出null

遍历Map集合的方法，同样是增强for或者迭代器

```java
package List;

import java.util.Collection;
import java.util.HashMap;
import java.util.Map;
import java.util.Set;
import java.util.Iterator;

public class MapTest {
    public static void main(String[] args) {
        Map map = new HashMap();

        map.put(102,"yhz");
        map.put(103,"awa");
        map.put(105,"hku");

        Set keys = map.keySet();

        for (Object key: keys) {
            System.out.println(key);
            int ikey = (Integer) key;
            String value = (String) map.get(ikey);

            System.out.printf("%d - %s %n", ikey, value);
        }

        Collection values = map.values();
        
        Iterator it = values.iterator();
        while (it.hasNext()) {
            Object item = it.next();
            String s = (String) item;
            System.out.println(s);
        }
    }
}
```


---
## Java generics
泛型
上一节的有一些代码中其实已经添加了泛型，比如

```java
Set<String> set = new HashSet<String>();

// When using iterator, also need to specify generics
Iterator<String> it = set.iterator();
```

有了泛型可以保证从集合中取出的元素一定为String类型

### **自定义泛型类**

```java
// simulate the definition of Queue
package Queue;

import java.util.ArrayList;
import java.util.List;


public class Queue<T> {
    private List<T> items;

    public Queue() {
        this.items = new ArrayList<T>();
    }

    /*
     * 入队方法，没有返回值
    */
    public void queue(T item) {
        this.items.add(item);
    }

    public T dequeue() {
        if (items.isEmpty()) {
            return null;
        }
        else {
            return this.items.remove(0);
        }
    }

    @Override
    public String toString() {
        return items.toString();
    }
}
```

调用如下
```java
package Queue;

public class HelloWorld {
    public static void main(String[] args) {
        Queue<String> genericsQueue = new Queue<String>();

        genericsQueue.queue("A");
        genericsQueue.queue("B");
        genericsQueue.queue("D");
    
        System.out.println(genericsQueue);

        genericsQueue.dequeue();

        System.out.println(genericsQueue);
    }
}
```

### **自定义泛型接口**
代码是很类似的，只是定义并且实现了泛型接口

```java
package Queue;

public interface IQueue<T> {

    public void queue(T item);

    public T dequeue();
    
}
```

```java
package Queue;

import java.util.List;
import java.util.ArrayList;

public class ListQueue<T> implements IQueue<T> {
    
    private List<T> items;

    public ListQueue() {
        this.items = new ArrayList<T> () ;
    }
    
    @Override
    public void queue(T item) {
        this.items.add(item);
    }

    @Override
    public T dequeue() {
        if (items.isEmpty()) {
            return null;
        }
        else {
            return items.remove(0);
        }
    }

    @Override
    public String toString() {
        return items.toString();
    }
}
```

### **泛型方法**
方法中也可以使用泛型

```java
package xxx;

public class HelloWorld {
  public static void main(String[] args) {

    System.out.println(isEquals(new Integer(1), new Integer(5)));

    System.out,println(isEquals(new Double(1.0),new Double(1.0)));

    System.out.println(isEquals(1.0,1.0)); // 发生自动装箱

    System.out.println(isEquals("A","A"));
  }

  public static <T> boolean isEquals(T a, T b) {
    return a.equals(b);
  }
}
```

也可以限定参数为Number类

```java
public static <T extends Number> boolean isEquals(T a, T b){
  return a.equals(b);
}
```

## File Management and IO Stream

### file Management

File Class

In fact, file type is quite like directroy

Methods for use
1. Constructor
   1. `File(String path)`
   2. `File(String path, String name)` 路径+文件名
   3. `File(File dir, String name)` 路径对象+文件名
2. Get File name
   1. `String getName()`
   2. `String getPath()`
   3. `String getAbsolutePath()` 绝对路径
   4. `String getParent()` 上级目录路径
3. File properties
   1. `boolean exists()`
   2. `boolean canWrite()`
   3. `boolean canRead()`
   4. `boolean isFile()`
   5. `boolean isDirectory()`
4. Operation on files
   1. `long lastModified()` 文件最近一次修改时间
   2. `long length()` the byte capacity of the file
   3. `boolean delete()` delete the file, return true if deletion is successful, otherwise false
   4. `boolean renameTo(File dest)` rename the File type file. If successful, return true
5. Directory operation
   1. `boolean makeDir()`
   2. `String[] list()` similar to ls, return all files and directories is the current working directory
   3. `String[] list(FilenameFilter filter)` return the files or directories that satisfy certain filter
   4. `String[] listFiles(FileFilter filter)`

> **about path**
> in unix, linux or macOS /
> in windows \ but \ is a special character
> java supports two types of path formats, but when using\ type `\\`

对目录操作有两个过滤器接口，FileFilter & FilenameFilter

FilenameFilter
`boolean accept(File dir, String name)`

FileFilter
`boolean accept(File pathname)`

```java
package IO;

import java.io.File;
import java.io.FilenameFilter;

public class HelloWorld {
    public static void main(String[] args) {

        File dir = new File(".\\TestDir");

        Filter filter = new Filter("html");

        System.out.println("HTML directory: " + dir);

        String files[] = dir.list(filter);

        for (String fileName: files) {
            File f = new File(dir,fileName);
            // create File object for files/directories in TestDir

            if (f.isFile()) {
                System.out.println("filename: " + f.getName());
                System.out.println("Absolute path: " + f.getAbsolutePath());
                System.out.println("filepath: " + f.getPath());
            } else {
                System.out.println("Child directory" + f);
            }
    }
}
}

// FilenameFilter interface
class Filter implements FilenameFilter{
    String extent;

    Filter(String extent) {
        this.extent = extent;
    }

    @Override
    public boolean accept(File dir, String name) {
        return name.endsWith("."+extent); // test on extent name, recall the String methods
    }
}

```

编程中尽量使用相对路径，"."表示当前目录。".."表示parent directory

这里注意，当前目录是工程的根目录，所以我们需要把TestDir文件夹直接创建在CODE文件夹内才能起作用！！

### Introduction to I/O Stream

java stream: instream, including files, web or keyboard input (std). outstream, including files, web and console (std)

继承层级
1. Stream
   1. Byte Stream
      1. InputStream
         1. FileInputStream
         2. ByteArrayInputStream
         3. PipedInputStream 管道输入，用于线程之间的数据传输
         4. FilterInputStream
            1. BufferedInputStream
            2. DataInputStream
      2. OutputStream
         1. FileOutputStream
         2. ByteArrayOutputStream
         3. PipedOutputStream
         4. FilterOutputStream
            1. BufferedOutputStream
            2. DataOutputStream
   2. Character Stream
      1. Reader
         1. CharArrayReader
         2. FilterReader
         3. PipedReader
         4. BufferedReader
         5. InputStreamReader 字节流转化为字符流
            1. FileReader
      2. Writer
         1. CharArrayWriter
         2. FilterWriter
         3. PipedWriter
         4. BufferedWriter
         5. InputStreamWriter 字节流转化为字符流
            1. FileWriter

### **Byte Stream**

InputStream

methods:
`int read()` read one byte and return from 0-255, return -1 if reaches the end of the stream
`int read(byte b[])` read multiple bytes and put them into b[]. Return the actual number of bytes that are read. 
`int read(byte b[], int off, int len)` read at most len bytes, and store the data to b[], starting form b[off]
`void close()` close the stream after operation

> remember to deal with IOException

OutputStream

methods
`void write(int b)` 将32位int b的8个低位写入输出流，忽略高位
`void write(byte[] b)`
`void write(byte[], int off, int len)`
`void flush()`
`void close`


之前的章节中学过Autoclosable接口，流是实现了这些接口的，可以用之前提到过的自动资源管理技术，在括号中初始化流

FileInputStream 和 FileOutputStream的构造方法如下

1. FileInputStream
   1. `FileInputStream(String name)` name-filename, if the file does not exist, throw FileNotFoundException
   2. `FileInputStream(File file)` Create FileInputStream with File Class Object
2. FileOutputStream
   1. `FileOutputStream(String name)`
   2. `FileOutputStream(String name, boolean append)` if append = true, then append
   3. `FileOutputStream(File file)`
   4. `FileOutputStream(String name, boolean append)`


how to copy a file?
```java
package IO;

import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;


public class FileCopy {
    
    public static void main(String[] args) {
        
        try (FileInputStream in = new FileInputStream("./TestDir/build.txt");
            FileOutputStream out = new FileOutputStream("./TestDir/subDir/build.txt", false)) {
                
                // prepare a buffer, choose the size by your self
                byte[] buffer = new byte[10];
                
                // read in first
                int len = in.read(buffer);

                while (len != -1) {
                    String copyStr = new String(buffer);

                    System.out.println(copyStr);

                    out.write(buffer, 0, len);

                    len = in.read(buffer);
                }
            }
                catch (FileNotFoundException e) {
                    System.out.println(e.getMessage());
            }
                catch (IOException e) {
                    e.printStackTrace();
            }
    }
}
```
可自行选择缓冲区大小，原则是计算机内存足够大时，且选择大内存不影响其他应用运行时，缓冲内存越大越好，因为这样读写效率高

注意参数off `void write(byte[], int off, int len)` 缓冲区b[] 的 index = off 位置开始向out中输入流

Buffered I/O Stream

字节缓冲流：BufferedInputStream and BufferedOutputStream

他们的父类是FilterInputStream，decorator mode of design

Constructors：
1. `BufferedInputStream(InputStream in)` default buffer zone, size 8192
2. `BufferedInputStream(InputStream in, int size)` size is for the size of buffer zone, 2^n. (maximizing efficiency)
3. `BufferedOutputStream(OutputStream out)`
4. `BufferedOutputStream(OutputStream out, int size)`

```java
package IO;

import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.BufferedInputStream;
import java.io.BufferedOutputStream;

public class FileCopy {
    
    public static void main(String[] args) {
        
        try (FileInputStream fis = new FileInputStream("./TestDir/build.txt");
            BufferedInputStream bis = new BufferedInputStream(fis);
            FileOutputStream fos = new FileOutputStream("./TestDir/subDir/build.txt", false)
            BufferedOutputStream bos = new BufferedOutputStream(fos)) {

                long startTime = System.nanoTime();

                
                // prepare a buffer
                byte[] buffer = new byte[1024];
                
                // read in first
                int len = bis.read(buffer);

                while (len != -1) {

                    bos.write(buffer, 0, len);

                    len = bis.read(buffer);
                }

                long elapsedTime = System.nanoTime() -startTime;

                System.out.println(elapsedTime/1000000.0);

            }
                catch (FileNotFoundException e) {
                    System.out.println(e.getMessage());
            }
                catch (IOException e) {
                    e.printStackTrace();
            }
    }
}
```

### **character stream**

1. methods for Reader Class
   1. `int read()` read an character, return 0-65535 (0x00-0xffff)
   2. `int read(char[] cbuf)`
   3. `int read(char[] cbuf, int off, len)`
   4. `void close()`
2. methods for Writer Class
   1. `void write(int c)` 写入c的16个低位
   2. `void write(char[] cbuf)`
   3. `void write(char[] cbuf, int off, int len)`
   4. `void write(String str)` write string to the stream
   5. `void write(String str, int off, len)`
   6. `void flush()` flush the output stream and force to output everything in the buffer zone
   7. `void close()`

注意考虑IOException

FileReader 和 FileWriter 的构造方法

1. `FileReader(String fileName)` 
2. `FileReader(File file)`
3. `FileWriter(String fileName)`
4. `FileWriter(String fileName, boolean append)`
5. `FileWriter(File file)`
6. `FileWriter(File file, boolean append)`
   

Example: Copy file
```java
package IO;

import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;

public class CharacterCopy {
    
    public static void main(String[] args) {

        try (FileReader in = new FileReader("./TestDir/build.txt");
            FileWriter out = new FileWriter("./TestDir/subDir/build.txt")){ 
            
            char[] buffer = new char[10];

            int len = in.read(buffer);

            while (len != -1) {
                String copyStr = new String(buffer);

                System.out.println(copyStr);

                out.write(buffer, 0, len); // buffer 或 copyStr都可以

                len = in.read(buffer);
            }
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        }
        catch (IOException e) {
            e.printStackTrace();
        }

                                         
    }
}

```

使用字符缓冲流和之前的字节缓冲流很相似

1. BufferedReader
   1. `String readLine()`
   2. `BufferedReader(Reader in)` 8192 by default
   3. `BufferedReader(Reader in, int size)`
2. BufferedWriter
   1. `void newLine()`
   2. `BufferedWriter(Writer out)`
   3. `BufferedWriter(Writer out, int size)`


### **字节流转化为字符流**
转换使用`InputStreamReader` and `OutputStreamReader`

Constructor
1. InputStreamReader
   1. `InputStreamReader(InputStream in)` byte->char
   2. `InputStreamReader(InputStream in, String CharsetName)` specify charset, raise UnsupportedEncodingException if the charset is not supported
2. OutputStreamWriter
   1. `OutputStreamWriter(OutputStream out)` byte->char
   2. `OutputStreamWriter(OutputStream out, String CharsetName)`
---

## **Multithreaded Programming**
```java
package Threads;

public class Test1 {
    
    public static void main(String[] args) {
        Thread mainThread = Thread.currentThread();

        System.out.println("Main Thread: " + mainThread.getName());
    }
}
```

### **Create sub-threads**

子线程的执行程序代码是在实现Runnable接口对象中的run()方法中编写的

#### 实现runnable接口

1. `Thread(Runnable target, String name)` target为线程的执行对象，name为线程名
2. `Thread(Runnable target)` 线程名由JVM分配

```java
// 定义自己的子线程

package Threads;

public class Runner implements Runnable{
    
    @Override
    public void run() {
        // Thread body
        for (int i = 0; i < 10; i++) {
            System.out.printf(" %d - %s\n", i, Thread.currentThread().getName());

            try {
            long sleepTime = (long) (1000*Math.random());

            Thread.sleep(sleepTime);

            }
            catch (InterruptedException e) {}
            }
        System.out.println("Finished" + Thread.currentThread().getName());
    }
}
```

这边有两个关于sleep的补充
- `static void sleep(long millis)` 指定毫秒数的休眠
- `static void sleep(long millis, int nanos)` 指定毫秒数+纳秒数

```java
// Test1.java
package Threads;

public class Test1 {
    
    public static void main(String[] args) {
        Thread mainThread = Thread.currentThread();

        System.out.println("Main Thread: " + mainThread.getName());

        Thread t1 = new Thread(new Runner());

        t1.start();

        Thread t2 = new Thread(new Runner(), "MyThread");

        t2.start();
    }
}
```
注意线程的创建和start()的开始

```
Main Thread: main
 0 - Thread-0
 0 - MyThread
 1 - Thread-0
 1 - MyThread
 2 - MyThread
 3 - MyThread
 2 - Thread-0
 4 - MyThread
 3 - Thread-0
 4 - Thread-0
 5 - MyThread
 5 - Thread-0
 6 - Thread-0
 6 - MyThread
 7 - Thread-0
 8 - Thread-0
 7 - MyThread
 8 - MyThread
 9 - Thread-0
FinishedThread-0
 9 - MyThread
FinishedMyThread
```

输出结果表明两个线程之间是交替进行的

#### 继承Thread线程类

只需简单改写*Runner.java*的代码
```java
package Threads;

public class MyThread extends Thread{

    public MyThread() {
      // 线程名将由JVM分配
        super();
    }

    public MyThread(String name) {
        super(name);
    }
    
    @Override
    public void run() {
        // Thread body
        for (int i = 0; i < 10; i++) {
            System.out.printf(" %d - %s\n", i, Thread.currentThread().getName());

            try {
            long sleepTime = (long) (1000*Math.random());

            Thread.sleep(sleepTime);

            }
            catch (InterruptedException e) {}
            }
        System.out.println("Inherited Thread Finished " + Thread.currentThread().getName());
    }    
}

```

#### 使用匿名内部类和Lambda表达式实现线程体

如果线程使用次数不多的话，可以采用上述两种方式

```java
package Threads;

public class Test2 {
    
    public static void main(String[] args) {

        // 匿名内部类
        Thread t1 = new Thread(new Runnable() {
            // code to run

            @Override
            public void run() {
                // Thread body
                for (int i = 0; i < 10; i++) {
                    System.out.printf(" %d - %s\n", i, Thread.currentThread().getName());
        
                    try {
                    long sleepTime = (long) (1000*Math.random());
        
                    Thread.sleep(sleepTime);
        
                    }
                    catch (InterruptedException e) {}
                    }
                System.out.println("Finished " + Thread.currentThread().getName());
            } 
        },"Hello");

        t1.start();

        // Lambda表达式
        Thread t2 = new Thread(() -> {
            
            for (int i = 0; i < 10; i++) {
                System.out.printf(" %d - %s\n", i, Thread.currentThread().getName());
    
                try {
                long sleepTime = (long) (1000*Math.random());
    
                Thread.sleep(sleepTime);
    
                }
                catch (InterruptedException e) {}
                }
            System.out.println("Lambda Thread Finished " + Thread.currentThread().getName());            
        }, "World");

        t2.start();

        // 如果都没有说明线程名，名称会由JVM分配
    }
}
```

*no need to define a Thread File*

### **线程状态**
1. 新建状态 `new` 空线程对象
2. 就绪状态 start() 之后 Runnable 等待CPU调度
3. 运行状态 running, 处于运行状态的线程独占CPU
4. 阻塞状态 blocked
   1. sleep
   2. 被其他线程调用了join
   3. 发出I/O请求，需等待IO完成
   4. 当前进程调用wait(),可用notify或notifyall唤醒
5. 死亡状态 正常退出run()或发生异常导致


### **线程管理**

#### **优先级**
java提供了10种优先级 int 1-10 10最高
以下常量用于表示优先级
MAX_PRIORITY 10
MIN_PRIORITY 1
NORM_PRIORITY 5 //默认

```java
package Threads;

public class ThreadPriority {
    
    public static void main(String[] args) {

        Thread t1 = new Thread(new Runner());

        t1.setPriority(Thread.MAX_PRIORITY);

        t1.start();

        Thread t2 = new Thread(new Runner());

        t2.setPriority(Thread.MIN_PRIORITY);

        t2.start();
    }

}

```

事实上运行时会发现t2有的时候也会先运行，说明影响线程获得CPU时间的因素除了优先级外还有操作系统等

#### **等待线程结束**

当前线程调用另一个线程的join() 如调用t1，则当前线程blocked，等待t1结束。 若结束/超时，原线程回到就绪状态

- `void join()`
- `void join(long millis)` 等待该线程结束的时间最长为millis毫秒 （？）
- `void join(long millis, int nanos)` 毫秒加纳秒

```java
package Threads;

public class Test3 {
    
    static int value = 0; // shared variable
    public static void main(String[] args) throws InterruptedException {
        
        System.out.println("Main Thread initiated");

        Thread t1 = new Thread(() -> {

            System.out.printf(" %s initiated %n", Thread.currentThread().getName());

            for (int i = 0; i < 2; i++) {

                System.out.printf("Run %s %n", Thread.currentThread().getName());

                value++;
            }
            System.out.printf("%s ends %n", Thread.currentThread().getName());
        }, "ThreadA");

        t1.start();
        t1.join();
        
        System.out.println(value);
    }
}

```

若没有t1, 输出的value将为0

#### **线程让步** yield

注意yield方法只会让步给相同或更高优先级的线程

调用也很简单，就是
`Thread.yield();` 放在线程体内

yield方法不能控制时间，所以一般很少使用


#### **线程停止**

通常采用引入结束变量的方式

```java
package Threads;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Test4 {
    
    private static String command = "";

    public static void main(String[] args) {

        Thread t1 = new Thread(() -> {

            while (!command.equalsIgnoreCase("exit")) {

                System.out.println("Processing");

                try {
                    Thread.sleep(10000);
                }
                catch (InterruptedException e) {}

            }

            System.out.println("finished");
        });

        t1.start();

        try (InputStreamReader ir = new InputStreamReader(System.in);
            BufferedReader in = new BufferedReader(ir)) {
                command = in.readLine();
            }
        catch (IOException e) {}
    }
}
```
不推荐使用`stop()` `suspend()` `resume()`

### **线程安全**

#### **临界资源问题**
主要出现在线程之间共享数据的时候 可能会导致共享数据的不一致性

#### **多线程同步**
为了解决临界资源问题，java有互斥机制，使得资源对象在任一时刻仅可以由一个线程访问

1. sychronized方法
在有必要加锁的方法中加上synchronized关键词
```java
package Threads;

public class TicketDB {
    
    private int ticketCount = 5;

    public synchronized int getTicketCount() {
        return ticketCount;
    }

    public synchronized void sellTicket() {
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {}
    
        System.out.printf("%d ticket sold!", ticketCount);
        ticketCount--;
    }

}
```

主线程程序
```java
package Threads;

public class Test5 {
    
    public static void main(String[] args) {

        TicketDB db = new TicketDB();

        Thread t1 = new Thread(() -> {
            while (true) {
                int currTickCount = db.getTicketCount();

                if (currTickCount > 0) {
                    db.sellTicket();
                }
                else {
                    break;
                }
            }
        });

        t1.start();

        Thread t2 = new Thread(() -> {
            while (true) {
                int currTickCount = db.getTicketCount();

                if (currTickCount > 0) {
                    db.sellTicket();
                }
                else {
                    break;
                }
            }
        });

        t2.start();
    }
}
```

2. synchronized语句
主要适用于第三方类，当我们不方便修改其代码的时候
```java
package Threads;

public class Test5_2 {
    
    public static void main() {
        TicketDB db = new TicketDB();

        Thread t1 = new Thread(() -> {
            while (true) {
                synchronized(db) {
                    int currTickCount = db.getTicketCount();

                    if (currTickCount > 0) {
                        db.sellTicket();
                    }
                    else {
                        break;
                    }
                }
            }
        });
        // 只需要用synchronized语句体套住对象就可以了，这种写法不需要修改TicketDB
    }
}

```

### **线程间通信**

methods
1. `void wait()`
2. `void wait(long timeout)`
3. `void wait(long timeout, int nanos)`
4. `void notify()`
5. `void notifyAll()`

以下是一个典型例子，堆栈问题
```java
package Threads;

public class Stack {
    
    private int pointer = 0;
    // 感受一下这个pointer是怎么变化的

    private char[] data = new char[5];

    public synchronized void push(char c) {

        while (pointer == data.length) {
            try {
                //等待，直到有数据出栈
                this.wait();
            } catch (InterruptedException e) { }

        }
        this.notify(); // 一开始写的时候忘记加上这句了，导致只压栈不出栈

        data[pointer] = c;

        pointer++;
    }

    public synchronized char pop() {

        while (pointer == 0) {
            // 注意这边要判断pointer是不是等于0
            // 无数据不出栈
            try {

                this.wait();
            } catch (InterruptedException e) {}
        }

        this.notify();
        pointer--;
        return data[pointer];
    }
}
```
调用如下
```java
package Threads;

public class Test6 {
    
    public static void main(String[] args) {

        Stack stack = new Stack();
        // Two threads manipulate the same stack

        Thread producer = new Thread(() -> {
            char c;
            for (int i = 0; i < 10; i++) {
                c = (char) (Math.random() * 26 + 'A');
                stack.push(c);
                System.out.println("Produce "+ c);

                try { 
                    Thread.sleep((int) Math.random()*1000);
                }
                catch (InterruptedException e) {}
            }
        });

        Thread consumer = new Thread(() -> {
            char c;
            for (int i = 0; i < 10; i++) {
                c = stack.pop();

                System.out.println("Consume " + c) ;

                try {
                    Thread.sleep((int) Math.random()*1000);
                } catch (InterruptedException e) {}
            }
        });

        producer.start();
        consumer.start();
    }
}
```

---

## 网络编程

端口 port 相当于 ip的“分机”号码
TCP/IP port: 16bit integer 0~63335
port with number lower than 1024 are predifined port


### **TCP Sockect低层次网络编程**

Socket Class

constructors:
1. `Socket(InetAddress address, int port)` 指定远程主机ip和端口
2. `Socket(InetAddress address, int port, InetAddress localAddr, int localPort)` 除了远程主机，还指定本地主机ip和端口
3. `Socket(String host, int port)` 指定远程主机名和端口号，ip为null，即送回地址127.0.0.1
4. `Socket(String host, int port, InetAddress localAddr, int localPort)`

Other methods

1. `InputStream getInputStream()` 通过此Socket返回输入流对象
2. `OutputStream getOutputStream()` 输出流
3. `int getPort()`
4. `int getLocalPort()`
5. `InetAddress getInetAddress()`
6. `InetAddress getLocalAddress()`
7. `boolean isClosed()`
8. `boolean isConnected()`
9. `void close()`

Server Socket

constructor:

1. `serverSocket(int port, int maxQueue)` maxQueue 设置连接请求的最大队列长度，默认为50
2. `serverSocket(int port` 连接请求的最大队列长度默认为50
  
other methods

1. `InputStream getInputStream()`
2. `OutputStream getOutputStream()`
3. `boolean isClosed()`
4. `Socket accept()` 此方法在建立链接之前一直阻塞，用于侦听并收到Socket的连接
5. `void close()`

close可以由资源自动管理技术完成

*案例：文件上传工具*

*UploadServer.java*
```java
package Web_Programming_TCP;

import java.io.BufferedInputStream;
import java.io.FileOutputStream;
import java.io.IOException;
import java.net.ServerSocket;
import java.net.Socket;

public class UploadServer {
    
    public static void main(String[] args) {

        System.out.println("Server online!");

        try (ServerSocket server = new ServerSocket(8080);
            // 8080 port
            Socket socket = server.accept();
            // 当前线程阻塞，等待客户端响应
            // 事实上，阻塞主线程并不太好，因为如果在图形界面中，会导致画面卡住，界面操作失效
            // 最好能把这种语句放到子线程中（如何更改呢？）
            BufferedInputStream in = new BufferedInputStream(socket.getInputStream());

            FileOutputStream out = new FileOutputStream("./TestDir/subDir/Test.png")
            )
        {
            byte[] buffer = new byte[1024];

            int len = in.read(buffer);

            while (len != -1) {

                out.write(buffer, 0, len);
                
                len = in.read(buffer);
            }

            System.out.println("RECEIVED");
            
        } catch (IOException e) {
            e.printStackTrace();
        }
    }


}

```

*UploadClient.java*

```java
package Web_Programming_TCP;

import java.io.BufferedInputStream;
import java.io.BufferedOutputStream;
import java.io.FileInputStream;
import java.io.IOException;
import java.net.ConnectException;
import java.net.Socket;

public class UploadClient {
    
    public static void main(String[] args) {

        System.out.println("Clinet online!");
        
        try (//向8080发出请求
                Socket socket = new Socket("127.0.0.1", 8080);
                
                // 由socket获取输出流

                BufferedOutputStream out = new BufferedOutputStream(socket.getOutputStream());

                FileInputStream fin = new FileInputStream("./TestDir/Test.png");

                BufferedInputStream in = new BufferedInputStream(fin)
        )
        {
            byte[] buffer = new byte[1024];

            int len = in.read(buffer);

            while (len != -1) {
                out.write(buffer, 0, len);

                len = in.read(buffer);
            }

            System.out.println("Upload Successful");
            
        } catch (ConnectException e) {
            // TODO: handle exception
            System.out.println("Server Offline");
        }
        catch (IOException e) {
            e.printStackTrace();
        }
    }
}

```

需要在两个不同的**terminal**中分别运行服务器和客户端
注意要先运行服务器端

*案例：聊天工具*

可以实现双向传播
但是服务器端和客户端不能连续发消息，会有一定的问题

```java
package Web_Programming_TCP;

import java.io.BufferedReader;
import java.io.DataInputStream;
import java.io.DataOutputStream;
import java.io.InputStreamReader;
import java.net.ServerSocket;
import java.net.Socket;
import java.time.LocalTime;

public class ChatServer {
    
    public static void main(String[] args) {

        System.out.println("Server Online!");

        Thread t = new Thread(() -> {

            try (
                ServerSocket server = new ServerSocket(8080);

                Socket socket = server.accept(); // 在子线程中，阻塞，等待客户端请求

                DataInputStream in = new DataInputStream(socket.getInputStream());

                DataOutputStream out = new DataOutputStream(socket.getOutputStream());

                BufferedReader keyboardIn = new BufferedReader(new InputStreamReader(System.in)) // 用标准输出流创建缓冲输出流
            )
            {
                while (true) {
                    /*receive message */
                    String str = in.readUTF();

                    System.out.printf(LocalTime.now() + " Clinet: %s %n", str);
                    
                    /*send message */
                    String keyboardInputString = keyboardIn.readLine();

                    if (keyboardInputString.equalsIgnoreCase("bye")) {
                        break;
                    }

                    out.writeUTF(keyboardInputString);
                    
                    out.flush();
                }
                
            } catch (Exception e) {
                // TODO: handle exception
            }
            System.out.println("Server shut down!");
        });

        t.start();

    }
}

```

```java
package Web_Programming_TCP;

import java.io.BufferedReader;
import java.io.DataInputStream;
import java.io.DataOutputStream;
import java.io.InputStreamReader;
import java.net.ConnectException;
import java.net.Socket;
import java.time.LocalTime;

public class ChatClient {
    
    public static void main(String[] args) {
         
        System.out.println("Client online!");

        Thread t = new Thread(() -> {

            try ( // 向127.0.0.1主机8080端口发出请求
                Socket socket = new Socket("127.0.0.1", 8080, null, 0);

                DataInputStream in = new DataInputStream(socket.getInputStream());

                DataOutputStream out = new DataOutputStream(socket.getOutputStream());

                BufferedReader keyboardIn = new BufferedReader(new InputStreamReader(System.in))
            ){
                while (true) {

                    /*send message */
                    String keyboardInputString = keyboardIn.readLine(); // 标准输入

                    if (keyboardInputString.equalsIgnoreCase("bye")) {
                        break;
                    }

                    out.writeUTF(keyboardInputString);
                    
                    out.flush();

                    /*receive message */
                    String str = in.readUTF();

                    System.out.printf(LocalTime.now() + " Server: %s %n", str);
                    
                }
                
            } catch (ConnectException e) {
                System.out.println("Server offline!");
                for (int i = 5; i >= 0; i--) {
                    System.out.print(".");
                    try {
                        Thread.sleep(1000);
                    } catch (InterruptedException e1) {
                    }
                }
            } 
            catch (Exception e) {
            }
            System.out.println("Client shut down!");
        });

        t.start();
                

    }
}

```

### **UDP Sockect低层次网络编程**

无连接，对系统资源要求少，可能会有丢包，不保证数据顺序

但是传输快，实时性高

DatagramSocket类 和 DatagramPacket类

DatagramSocket类constructor
1. `DatagramSocket()`创建数据报对象，并将其绑定到本地主机上的任何可用端口
2. `DatagramSocket(int port)`创建数据报对象，并将其绑定到指定端口
3. `DatagramSocket(int port, InetAddress laddr)`
  
other method:
1. `void send(DatagramPacket p)`
2. `void receive(DatagramPacket p)`
3. `int getPort()`
4. `int getLocalPort()`
5. `InetAddress getInetAddress()` 返回DatagramSocket连接的地址
6. `InetAddress getLocalAddress()` 返回绑定的本地地址
7. `boolean isClosed()`
8. `boolean isConnected()`
9. `void isClosed()`

DatagramPacket类constructor
1. `DatagramPacket(byte[] buf, int length)` buf 是数据包，length是包长度
2. `DatagramPacket(byte[] buf, int length, InetAddress address, int port)`
3. `DatagramPacket(byte[] buf, int offset, int length)`
4. `DatagramPacket(byte[] buf, int offset, int length, InetAddress address, int port)`
   
useful methods
1. `InetAddress getAddress()`
2. `byte[] getData()`
3. `int getLength()` 返回发送或接受到的数据byte[]的长度
4. `int getOffset()`
5. `int getPort()`

重新实现一下上文中的文件传输器
```java

package Web_Programming_UDP;

import java.io.BufferedOutputStream;
import java.io.FileOutputStream;
import java.io.IOException;
import java.net.DatagramPacket;
import java.net.DatagramSocket;

public class UploadServer {
    public static void main(String[] args) {

        System.out.println("Server Online!");

        Thread t = new Thread(()->{

            try (DatagramSocket socket = new DatagramSocket(8080);
                FileOutputStream fout = new FileOutputStream("./TestDir/subDir/Test.png"); // 注意路径不要写错
                BufferedOutputStream out = new BufferedOutputStream(fout);
            ){
                
                byte[] buffer = new byte[1024]; // create buffer zone 

                while (true) {
                    DatagramPacket packet = new DatagramPacket(buffer, buffer.length);

                    socket.receive(packet); // 该方法会导致线程阻塞，所以放在子线程里比较好

                    int len = packet.getLength();

                    if (len == 3) {

                        String flag = new String(buffer, 0 , 3);

                        if (flag.equals("bye")) {
                            break;
                        }
                    }

                    out.write(buffer,0,len);

                }
                System.out.println("received!");
            } catch (IOException e) {
                // TODO: handle exception
                e.printStackTrace();
            }
        });

        t.start();
    }
}

```

```java
package Web_Programming_UDP;

import java.io.BufferedInputStream;
import java.io.FileInputStream;
import java.net.DatagramPacket;
import java.net.DatagramSocket;
import java.net.InetAddress;

public class UploadClient {
    public static void main(String[] args) {

        System.out.println("Client Online!"); 

        try (DatagramSocket socket = new DatagramSocket();
            FileInputStream fin = new FileInputStream("./TestDir/Test.png");
            BufferedInputStream in = new BufferedInputStream(fin); 
        ){
            InetAddress address = InetAddress.getByName("localhost");

            byte[] buffer = new byte[1024];

            int len = in.read(buffer);

            while (len != -1) {

                DatagramPacket packet = new DatagramPacket(buffer, len, address, 8080);

                socket.send(packet);

                len = in.read(buffer);
            }

            DatagramPacket packet = new DatagramPacket("bye".getBytes(), 3, address, 8080); // 结束标志

            socket.send(packet);

            System.out.println("Upload complete!");
            
        } catch (Exception e) {
            // TODO: handle exception
            e.printStackTrace();
        }
    }
}

```

### **数据交换格式、JSON和XML**

json是一种轻量级数据交换格式
json文档的两种结构为对象和数组，对象是“名称-值”对的集合，数组就是一系列元素的集合

```json
{
  "name":"a.htm",
  "size":345,
  "saved":true
}
```

```json
["text","css","html"]
```

因为技术原因，json部分无法调试代码和安装org.json 包 暂时跳过

### **访问互联网资源 URL**

URL的格式
> protocol://resources

使用URL类

constructors
1. `URL(String spec)`
2. `URL(String protocol, String host, String file)`
3. `URL(String protocol, String host, int port, String file)`

常用方法
1. `inputStream openStream()` 打开链接，返回输入流
2. `URLConnection openConnection()`

```java
package Web_Programming_URL;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStream;
import java.io.InputStreamReader;
import java.net.MalformedURLException;
import java.net.URL;

public class Test1 {
    
    public static void main(String[] args) {
        String url = "https://sina.com.cn/";

        URL reqURL;
        try {
            reqURL = new URL(url);
        } catch (MalformedURLException e) {
            return;
        }
        try (//打开网络通信流
            InputStream is = reqURL.openStream(); 
            InputStreamReader isr = new InputStreamReader(is, "utf-8");
            BufferedReader br = new BufferedReader(isr);
        ){
            StringBuilder sb = new StringBuilder();
            String line = br.readLine();

            while (line != null) {
                sb.append(line);
                sb.append("\n");
                line = br.readLine();
            }

            System.out.println(sb);
            
        } catch (IOException e) {
            // TODO: handle exception
        }
    }
}
```
这样就可以“爬取” sina的网页内容了

**使用HttpURLConnection发送GET/POST请求**

```java

URL reqURL = new URL(urlString);
conn = (HttpURLConnection) reqURL.openConnection();
conn.setRequestMethod("POST");

```

案例：downloader
```java
package Web_Programming_URL;

import java.io.BufferedInputStream;
import java.io.BufferedOutputStream;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.InputStream;
import java.io.OutputStream;
import java.net.HttpURLConnection;
import java.net.URL;


public class Downloader {
    private static String urlString = "https//ss0.bdstatic.com/5aV1bjqh_Q23odCf/"+"static/superman/img/logo/bd_;ogo1_31bdc765.png";

    public static void main(String[] args) {
        download();
    }

    private static void download(){
        HttpURLConnection conn = null;

        try {
            URL reqURL = new URL(urlString);

            conn = (HttpURLConnection) reqURL.openConnection();

            try ( InputStream is = conn.getInputStream();
                BufferedInputStream bin = new BufferedInputStream(is);
                OutputStream os = new FileOutputStream("./download.png");
                BufferedOutputStream bout = new BufferedOutputStream(os);
            ){
                byte[] buffer = new byte[1024];

                int byteRead = bin.read(buffer);

                while (byteRead != -1) {
                    bout.write(buffer,0,byteRead);
                    byteRead = bin.read(buffer);
                }
                
            } catch (IOException e){}
            System.out.println("Download complete!");
        } catch (IOException e) {
            // TODO: handle exception
        } finally {
            if (conn != null) {
                conn.disconnect();
            }
        }

    }
}
```
---

## Swing 图形界面编程

### Swing basis

```java
package GUI;

import java.awt.Container;

import javax.swing.JFrame;
import javax.swing.JLabel;

public class SwingDemo1 {
    
    public static void main(String[] args) {
        
        JFrame frame = new JFrame("MyFrame", null);

        JLabel label1 = new JLabel("Hello Swing!");

        Container contentpane = frame.getContentPane();

        contentpane.add(label1);

        frame.setSize(300, 300); // 最后设置大小，设置可见

        frame.setVisible(true);
    }
}
```

> 也可以写一个JFrame的子类，在构造方法中初始化窗口
>

### **事件处理模型**

事件，事件源和事件处理者

事件是用户对界面的操作

事件源是事件发生的场所

事件处理者是事件处理程序

| 事件类型 | 监听接口 | 监听方法 |
| ------- | -------- | ------- |
| Action | ActionListener | `actionPerformed()` |
| Item | ItemListener | `itemStateChanged()` |
| Mouse| MouseListener | `mousePressed()` ... |
...

可以用内部类/匿名内部类 lambda表达式实现事件处理

```java
package GUI;

import java.awt.BorderLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;

public class FrameEffect extends JFrame{
    
    JLabel label1;
    
    public FrameEffect(String title) {

        super(title);

        label1 = new JLabel("Label");

        getContentPane().add(label1, BorderLayout.NORTH); // 布局，枚举变量

        JButton button1 = new JButton("Button1");

        getContentPane().add(button1, BorderLayout.CENTER);

        JButton button2 = new JButton("Button2");

        getContentPane().add(button2, BorderLayout.SOUTH);

        setSize(350, 120);

        setVisible(true);

        button2.addActionListener(new ActionEventHandler());

        button1.addActionListener(new ActionListener() {
            
            @Override
            public void actionPerformed(ActionEvent event) {
                label1.setText("Hello Swing!");
            }
        });
    }

    class ActionEventHandler implements ActionListener {

        @Override
        public void actionPerformed(ActionEvent e) {
            label1.setText("Hello World!");
        }
    }
    
}
```
也可以用Lambda表达式，只需要修改注册事件监听器的代码

```java
button1.addActionListener((event) -> {
    label1.setText("Hello Swing");
});
```
```java
package GUI;

import java.awt.BorderLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;

public class FrameEffect2 extends JFrame implements ActionListener{
    
    JLabel label1;
    
    public FrameEffect2(String title) {

        super(title);

        label1 = new JLabel("Label");

        getContentPane().add(label1, BorderLayout.NORTH); // 布局，枚举变量

        JButton button1 = new JButton("Button1");

        getContentPane().add(button1, BorderLayout.CENTER);

        JButton button2 = new JButton("Button2");

        getContentPane().add(button2, BorderLayout.SOUTH);

        setSize(350, 120);

        setVisible(true);

        button2.addActionListener(this);  // 由于本类调用了ActionListener的接口，这里就是this就可以

        button1.addActionListener((event) -> {
            label1.setText("Hello World");
        });

    }
    @Override
    public void actionPerformed(ActionEvent e) {
        label1.setText("Hello Swing!");
    }    
    // 覆写actionlistener的抽象方法
}

```

如果一个事件监听器接口只有一个抽象方法，则可以使用lambda表达式

**适配器使用**

监听器是接口，适配器是类

只覆盖需要实现的方法，其他方法则不用实现

```java
this.addWindowListener(new WindowAdapter() {

    @override
    public void windowClosing(WindowEvent e) {
        System.exit(0);
    }
})
```

### **布局管理**

`setLayout()`

#### **FlowLayout布局**

主要构造方法
`FlowLayout(int align, int hgap, int vgap)`

align 是对齐方式，是通过FlowLayout常量指定的

CENTER
LEADING
LEFT
RIGHT
TRAILING 结束边对齐

#### **BorderLayout布局**

把容器分为5个区域

主要构造方法
`BorderLayout(int hgap, int vgap)`

向面版容器添加元素的时候用add(), 需要指定约束常量

CENTER
EAST
NORTH
SOUTH
WEST

#### **GridLayout布局**

该布局以网络形式对组件进行摆放

主要构造方法
`GridLayout(int rows, int cols, int hgap, int vgap)`

添加元素的时候，从左到右，从上到下

#### **不使用布局管理器**
`setLayout(null);`

`setLocation(int x, int y)`
`setSize(int width, int height)`
`setBounds(int x, int y, int width, int height)` 设置大小和位置

以下是一个示例
```java
package GUI;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.SwingConstants;

public class Layout extends JFrame {
    
    public Layout(String title) {
        
        super(title);

        setResizable(false);

        getContentPane().setLayout(null);

        JLabel label = new JLabel("label");

        label.setBounds(89, 13, 100, 30);

        label.setHorizontalAlignment(SwingConstants.CENTER); // 标签文本水平居中

        getContentPane().add(label);

        JButton button1 = new JButton("Button1", null);

        button1.setBounds(89, 59, 100, 30);

        getContentPane().add(button1);

        JButton button2 = new JButton("Button2", null);

        button2.setLocation(89, 102);

        button2.setSize(100, 30);

        getContentPane().add(button2);

        setSize(300,200);

        setVisible(true);

        button2.addActionListener((event) -> {
            label.setText("Hello Swing");
        });

        button1.addActionListener((event) -> {
            label.setText("Hello World");
        });
    }
}

// 为什么本例中完全不需要调用ActionListener的接口，也不需要覆盖ActionListener的方法?
```

### **Swing组件**

#### **标签和按钮**

1. `JLabel(String text, Icon icon, int horizontalAlignment)`
   1. icon可以设置图标
   2. 水平对齐方式选用SwingContraints中定义的LEFT/CENTER/RIGHT/LEADING/TRAILING
2. `Jbutton(String text, Icon icon)`

> icon image 有 ImageIcon 类

#### **文本输入组件**
JTextField JPasswordField JTextArea

前两个单行文本，后一个可以输入和显示多列文本

enter时触发ActionEvent事件

`JTextField(String text, int columns)`

`JTextArea(String text, int rows, int columns)`

以下是一个示例

```java
package GUI;

import java.awt.BorderLayout;

import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JPanel;
import javax.swing.JPasswordField;
import javax.swing.JTextArea;
import javax.swing.JTextField;

public class TextArea extends JFrame{
    private JTextField textField;
    private JPasswordField passwordField;

    public TextArea(String title) {
        super(title);

        getContentPane().setLayout(new BorderLayout());

        JPanel panel1 = new JPanel(); // 创建面板，方便布局嵌套

        getContentPane().add(panel1, BorderLayout.NORTH);

        JLabel lbTextFieldLabel = new JLabel("TextField:");

        panel1.add(lbTextFieldLabel);

        textField = new JTextField(12);

        panel1.add(textField);

        JLabel lbPasswordLabel = new JLabel("Password:");

        panel1.add(lbPasswordLabel);

        passwordField = new JPasswordField(12); //?

        panel1.add(passwordField);

        JPanel panel2 = new JPanel();

        getContentPane().add(panel2, BorderLayout.SOUTH); // 嵌套式布局

        JLabel lblTextAreLabel = new JLabel("TextArea:");

        panel2.add(lblTextAreLabel);

        JTextArea textArea = new JTextArea(3, 20);

        panel2.add(textArea);

        pack();
        // 紧凑排列

        setVisible(true);

        textField.addActionListener((event)-> {
            textArea.setText("enter pressed");
        });

    }
    
}

```

#### **复选框和单选按钮**

JCheckBox 和 JRadioButton

`JCheckBox(String text, Icon icon, boolean selected)`

JRadioButton的构造方式是类似的

RadioButton需要创建ButtonGroup以实现互斥选项

以下是一个实现例
```java
package GUI;

import javax.swing.ButtonGroup;
import javax.swing.JCheckBox;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JPanel;
import javax.swing.JRadioButton;

import java.awt.BorderLayout;
import java.awt.Button;
import java.awt.FlowLayout;
import java.awt.event.ItemEvent;
import java.awt.event.ItemListener;

public class Boxes extends JFrame implements ItemListener {
    private JRadioButton radioButton1 = new JRadioButton("Male");
    private JRadioButton radioButton2 = new JRadioButton("Female");
    private JRadioButton radioButton3 = new JRadioButton("Non-Binary");

    public Boxes(String title) {

        super(title);

        getContentPane().setLayout(new BorderLayout());

        JPanel panel1 = new JPanel();
        FlowLayout flowLayout_1 = (FlowLayout) panel1.getLayout();
        flowLayout_1.setAlignment(FlowLayout.LEFT);

        getContentPane().add(panel1);

        JLabel label1 = new JLabel("choose your favourite programming language");
        panel1.add(label1);

        JCheckBox checkBox1 = new JCheckBox("Java");
        panel1.add(checkBox1);

        JCheckBox checkBox2 = new JCheckBox("C++");
        panel1.add(checkBox2);

        JCheckBox checkBox3 = new JCheckBox("Python");

        checkBox3.addActionListener((event) -> {
            System.out.println(checkBox3.isSelected());
        });

        panel1.add(checkBox3);

        JPanel panel2 = new JPanel();
        FlowLayout flowLayout = (FlowLayout) panel2.getLayout();
        flowLayout.setAlignment(FlowLayout.LEFT);
        getContentPane().add(panel2, BorderLayout.SOUTH);

        JLabel label2 = new JLabel("choose your gender");

        panel2.add(label2);

        ButtonGroup buttonGroup = new ButtonGroup();
        panel2.add(radioButton1);
        panel2.add(radioButton2);
        panel2.add(radioButton3);
        
        buttonGroup.add(radioButton1);
        buttonGroup.add(radioButton2);
        buttonGroup.add(radioButton3);

        radioButton1.addItemListener(this);
        radioButton2.addItemListener(this);
        radioButton3.addItemListener(this);

        pack();

        setVisible(true);
    }

    @Override
    public void itemStateChanged(ItemEvent e) {
        if (e.getStateChange() == ItemEvent.SELECTED) {
            JRadioButton button = (JRadioButton) e.getItem();
            System.out.println(button.getName());
        }
    }
}

```

#### **下拉列表**

`JComboBox(Object[] items)`

#### **列表**

`JList(Object[] listData)`

#### **分隔面板**

`JSplitPane(int newOrientation, Component newLeftComponent, Component newRightComponent)`

newOrientation can take: `JSplitPane.HORIZONTAL_SPLIT` & `JSplitPane.VERTICAL_SPLIT`

#### **表格**

`JTable(TableModel dm)`

`JTable(Object[][] rowData, Object[][] columnData)`

`JTable(int row, int col)`

以上部分仅作了解
