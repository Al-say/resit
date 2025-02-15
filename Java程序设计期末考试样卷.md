# 一、选择题（每题2分，共20分）

1. 下面4种类型的文件中（）可以在Java虚拟机中运行。
   A. .java
   B. .jre
   C. .exe
   D. .class

```answer

```

2. 下列选项中，不属于基本数据类型的是（）
   A. String
   B. short
   C. boolean
   D. char

```answer

```

3. 假设int x=2，三元表达式x>0?x+1:5（）
   A. 0
   B. 2
   C. 3
   D. 5

```answer

```

4. 阅读下列程序：
```java
class Person {
    void say() {
        System.out.println("hello");
    }
}

class Example {
    public static void main(String[] args) {
        Person p2 = new Person();
        Person p1 = new Person();
        p2.say();
        p1.say();
        p2 = null;
        p2.say();
    }
}
```
下列选项中描述正确的是（）
A. 输出1个hello
B. 输出2个hello后会抛出异常
C. 输出3个hello后会抛出异常
D. 不会输出hello，直接抛出异常

```answer

```

5. 下列关于继承的描述中，错误的是（）
   A. Java中一个类只能有一个直接父类
   B. 多个类可以继承一个父类
   C. 一个类可以派生出很多个类
   D. Java是支持多继承的

```answer

```

6. 在异常处理时，释放资源关闭文件一般在()语句块内完成。
   A. try
   B. catch
   C. finally
   D. throw

```answer

```

7. 以下关于String类的常见操作中，哪个是方法会返回指定字符ch在字符串中最后一次出现位置的索引（）
   A. indexOf(int ch)
   B. lastIndexOf(int ch)
   C. indexOf(String str)
   D. lastIndexOf(String str)

```answer

```

8. String s="Computer"；则s.substring(3,4)返回的字符串是（）
   A. u
   B. ut
   C. p
   D. pu

```answer

```

9. 使用Iterator时，判断是否存在下一个元素可以使用（）方法。
   A. hasNext()
   B. hash()
   C. hasPrevious()
   D. next()

```answer

```

10. 下列选项中，FileWriter类中read()方法读取到流末尾的返回值是（）
    A. 0
    B. -1
    C. 1
    D. 无返回值

```answer

```

## 二、填空题（每题2分，共20分）

1. 类封装时会使用________关键字将类中的属性私有化。

```answer

```

2. ________关键字可用于修饰类、变量和方法，它有"无法改变的"或者"最终"的含义。

```answer

```

3. 异常分为两种，分别是________和编译时异常。

```answer

```

4. ___________关键字修饰的变量可以直接通过类名进行访问。

```answer

```

5. 已知strb为StringBuffer的一个实例，且strb.toString()的值为"abcdefg"，则执行strb.reverse()后，strb.toString()的值为________。

```answer

```

6. Java中的boolean基本数据类型只有2个值，分别是_______和false。

```answer

```

7. Map集合中的元素都是成对出现的，并且都是以Key（键）、________的映射关系存在。

```answer

```

8. 在图形用户界面编程中，鼠标按下按钮所触发的事件是_______________。

```answer

```

9. Java中的I/O流，按照传输数据的不同，可分为字节流和________。

```answer

```

10. 在Thread类中，提供了一个________方法用于启动新线程。

```answer

```

## 三、程序阅读题（每题5分，共30分）

1. 阅读下列程序，写出输出结果：
```java
class Test {
    public static void main(String[] args) {
        int a = 21;
        int b = 5;
        System.out.print(a >= b);
    }
}
```

```java
输出结果：

```

2. 阅读下列程序，写出输出结果：
```java
public class Test {
    public static void main(String[] args) {
        int[] intArray = {1,2,3,4,5,6};
        int s = 0;
        for(int i = 0; i < intArray.length; i++)
            s += intArray[i];
        System.out.println(s);
    }
}
```

```java
输出结果：

```

3. 阅读下列程序，写出输出结果：
```java
public class Test {
    public static void main(String[] args) {
        String str1 = "Hello";
        String str2 = "Hel" + "lo";
        System.out.println(str1 == str2);
        System.out.println(str1.equals(str2));
    }
}
```

```java
输出结果：

```

4. 阅读下列程序，如果从键盘上输入16 4，请写出程序的输出结果：
```java
import java.util.Scanner;
public class ExceptionTest {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int a = scanner.nextInt();
        int b = scanner.nextInt();
        try {
            System.out.print(a/b);
        } catch(ArithmeticException e) {
            System.out.print(5);
        } finally {
            System.out.println(0);
        }
    }
}
```

```java
输出结果：

```

5. 阅读下列程序，写出输出结果：
```java
class Father {
    Father() {
        System.out.println("Father");
    }
}

class Son extends Father {
    Son() {
        System.out.println("Son");
    }
    public static void main(String[] args) {
        new Son();
    }
}
```

```java
输出结果：

```

6. 阅读下列程序，写出输出结果：
```java
class Father {
    public void fun() {
        System.out.println("Father");
    }
}

class Son extends Father {
    public void fun() {
        System.out.println("Son");
    }
}

public class Test {
    public static void main(String[] args) {
        Father f = new Son();
        f.fun();
    }
}
```

```java
输出结果：

```

## 四、程序设计题（每题6分，共30分）

1. 定义一个接口Readable，包含方法getTitle()用于获取阅读材料标题。（6分）

```java
// 在此处编写代码

```

2. 封装一个图书类Book，实现Readable接口，包含成员变量title和author，并实现接口中的方法，重写toString方法。（6分）

```java
// 在此处编写代码

```

3. 封装一个杂志类Magazine，实现Readable接口，包含成员变量title和issueNumber，并实现接口中的方法，重写toString方法。（6分）

```java
// 在此处编写代码

```

4. 封装图书馆类Library，包含方法addReadable(Readable readable)用于添加阅读材料到图书馆，和displayReadables()用于展示图书馆中所有阅读材料信息。（6分）

```java
// 在此处编写代码

```

5. 创建测试类LibraryTest，在图书馆中添加两本图书，例如"红楼梦"（作者：曹雪芹）和"平凡的世界"（作者：路遥），然后再添加两本杂志，例如"读者"（刊号：62-1190/Z）和"软件"（刊号：12-1151/TP）。最后，展示图书馆中所有图书和杂志的信息。（6分）

```java
// 在此处编写代码
