1.下列哪个关键字用于表示方法不需要返回值?()

A.public 

B.stati

C.void

D. return

2.下列选项中，属于Java基本数据类型的是()
A.Integer 

B.Float

C.String

D. byte

3.假设inta=5;，表达式 +ta*2的值是()

A.10

B.11

C.12
0.14

4.阅读下列程序，下列选项中描述正确的是()

```java
class Vehicle{
    void run(){
        System.out.println("Vehicle is running");
    }

}
class Car extends Vehicle{
    void run(){
        System.out.println("Car is runing");
    }
}
public class Main{
    public static void main(String[] args){
        Vehicle v=new Vehicle();
        Car C=new Car();
        v.run();
        c.run();
        v=c;
        v.run();
    }
}
```


A.输出三次"Vehicle is running"

B、输出三次"Car is running”

C.输出"Vehicle is running”,然后输出两次"Car is running

D.输出“Car is running"，然后输出两次"Vehicle is running

5.关于 Java 抽象类，下列描述正确的是()
B、抽象类中必须包含抽象方法A.抽象类可以被实例化C.子类继承抽象类后必须实现抽象方法D,一个类只能继承一个抽象类
6.Java 中用于捕获异常的代码块是()
A.throw
B，throws
D. finally
C.catch
7.以下哪个 String类的方法用于获取字符串的长度?()
A.length

B.size()

D.getSize()

C.count()

8.String s="HelloWorld";s.index0f("World”)返回的值是()
A.5
B.6

C.7

D.-1
9.在Java中，使用哪个接口来实现对象的排序?()

A.Iterable

B.omparable

C.Comparator

D.Serializable

10.如果在使用BufferedReader读取文件时遇到文件末尾，其readLine()方法会返回()

A.空字符串(””)

B.nul1

C.EOF

D.0

二、填空题:(共 10题，每题2分，共20分)
1.Java 中使用关键字来声明类的继承关系。

2.在Java 中，所有类的根类是____

3.Java 中的接口使用关键字进行声明。
4.用________修饰的成员变量，只能在类的内部和子类中访问。

5.知 String str="apple banana orange”,执行 str.split("“)后,返回的是一个长度为___________的字符串数组。
6.Java 中用于将基本类型转换为字符串的方法是______________

7.Java 中用于存放具有唯一性的元素的集合类型是_____________
8.在 Java GUI 编程中，键盘按下所触发的事件是______________

9.Java 中的I0流按照数据传输方向可以分为输入流和______________

10.使用线程池时，可以通过submit()方法提交_______任务。

三、程序阅读题
1.阅读以下程序，输出结果是什么?

```Java
public class Testl {. public static void main(string []args) {
    int a=10;
    a+=5;
    System.out.printin(a);
输出结果是:
```

2.阅读以下程序，输出结果是什么?public 

```java
public class Test2 {
    public static void main(String[]] args) {
        int[] arr = {2, 4, 6, 8, 10);
                     int result = 1;
                     for (int num : arr) {
                         result *= num;
                     }                        System.out.printin(result);
                     }
                    }
```

3.阅读以下程序，输出结果是什么?public 

```java
class Test3 {
    public static void main (String [] args){
     		 
        String str1 = "java";
        String str2 = "java";
        System,out.printin(str1.equals(str2));
        System.out.printin(str1.equalslgnoreCase(str2));
    }
}
```

输出结果是:

4.阅读以下程序，输出结果是什么?
输出结果是:

```java
import java.util.*;
public class ExceptionTest {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        try {
			int num = scanner.nextint();
            System.out.printin("输入的是:“+num);
                               } catch (inputMismatchExceptlon e) {
                                   System.out.printin("输入的不是整数!");
                               }
                               }
                               }
```

如果从键盘输入字符串"abc"，则程序的输出结果是:

5.阅读以下程序，输出结果是什么?

```java
class A 
{A(){
System.out.print("A");
    }
    }
class B extends A {
    B(){
System.out.print("B");
    }
public static void main(String[] args) {
    new B();
}
}
输出结果是:
```

6.阅读以下程序，输出结果是什么?

```java
class Parent {
    public void show() {
        System.out.println("Parent");
    }
}
class Child extends Parent {
    @Override 
    public void show() {
        System.out.println("child");
    }
}
public class Test {
    public static void main(String[] args) {
        Parent p = new Child();
        p.show();
    }
}
```

输出结果是:
