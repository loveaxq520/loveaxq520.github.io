# Java 对象和类
![](https://www.runoob.com/wp-content/uploads/2013/12/class-object2020-10-27-dog.png)

通过上图创建一个简单的类来理解下 Java 中类的定义：
```java
public class Dog {
    String breed;
    int size;
    String colour;
    int age;
 
    void eat() {
    }
 
    void run() {
    }
 
    void sleep(){
    }
 
    void name(){
    }
}
```
    一个类可以包含以下类型变量：

* `局部变量`：在方法、构造方法或者语句块中定义的变量被称为局部变量。变量声明和初始化都是在方法中，方法结束后，变量就会自动销毁。
* `成员变量`：成员变量是定义在类中，方法体之外的变量。这种变量在创建对象的时候实例化。成员变量可以被类中方法、构造方法和特定类的语句块访问。
* `类变量`：类变量也声明在类中，方法体之外，但必须声明为 static 类型。

一个类可以拥有多个方法，在上面的例子中：eat()、run()、sleep() 和 name() 都是 Dog 类的方法。

## 构造方法

每个类都有构造方法。如果没有显式地为类定义构造方法，Java 编译器将会为该类提供一个默认构造方法。在创建一个对象的时候，至少要调用一个构造方法。构造方法的名称必须与类同名，一个类可以有多个构造方法。下面是一个构造方法示例:
```java
public class Puppy{
    public Puppy{
    }
    
    public Puppy(String name){
        // 这个构造器仅有一个参数：name
    }
}
```

## 创建对象
对象是根据类创建的。在Java中，使用关键字 new 来创建一个新的对象。创建对象需要以下三步：

* `声明`：声明一个对象，包括对象名称和对象类型。
* `实例化`：使用关键字 new 来创建一个对象。
* `初始化`：使用 new 创建对象时，会调用构造方法初始化对象。

下面是一个创建对象的例子：
```java
public class Puppy{
    public Puppy(String name){
        System.out.println("小狗的名字：" + name);
    }
    public static void main(String[] args){
        //下面的语句将创建一个Puppy对象
        Puppy myPuppy = new Puppy("tommy");
    }
}
```
    小狗的名字：tommy
### 访问实例变量和方法

通过已创建的对象来访问成员变量和成员方法，如下所示：

```java
/* 实例化对象 */
Object referenceVariable = new Constructor();
/* 访问类中的变量 */
referenceVariable.variableName;
/* 访问类中的方法 */
referenceVariable.methodName();
```
## 实例
下面的例子展示如何访问实例变量和调用成员方法：

```java
public class Puppy{
    int puppyAge;
    public Puppy(String name){
        System.out.println("小狗的名字：" + name);
    }
    
    public void setAge(int age){
        puppyAge = age;
    }
    
    public int getAge(){
        System.out.println("小狗的年龄：" + age);
        return puppyAge;
    }
    
    public static void main(String[] args){
        /*创建对象*/
        Puppy myPuppy = new Puppy("tommy");
        /*通过方法来设定age*/
        myPuppy.setAge(2);
        /*通过另一个方法获取age*/
        myPuppy.getAge();
        /*也可以像下面这样访问成员变量*/
        System.out.println("变量值" + myPuppy.puppyAge)
    }
}
```
    小狗的名字：tommy
    小狗的年龄：2
    变量值：2

## 源文件声明规则
当在一个源文件中定义多个类，并且还有import语句和package语句时，要特别注意这些规则。

* 一个源文件中只能有一个 public 类
* 一个源文件可以有多个非 public 类
* 源文件的名称应该和 public 类的类名保持一致。例如：源文件中 public 类的类名是 Employee，那么源文件应该命名为Employee.java。
* 如果一个类定义在某个包中，那么 package 语句应该在源文件的首行。
* 如果源文件包含 import 语句，那么应该放在 package 语句和类定义之间。如果没有 package 语句，那么 import 语句应该在源文件中最前面。
* import 语句和 package 语句对源文件中定义的所有类都有效。在同一源文件中，不能给不同的类不同的包声明。
* 类有若干种访问级别，并且类也分不同的类型：抽象类和 final 类等。

除了上面提到的几种类型，Java 还有一些特殊的类，如：内部类、匿名类。
### 内部类
Java 一个类中可以嵌套另外一个类，语法格式如下：
```java
class OuterClass {   // 外部类
    class NestedClass { // 嵌套类，或称为内部类
    }
}
```
要访问内部类，可以通过创建外部类的对象，然后创建内部类的对象来实现。

    嵌套类有两种类型：

* `非静态内部类`
* `静态内部类`
#### 非静态内部类
非静态内部类是一个类中嵌套着另外一个类。 它有访问外部类成员的权限， 通常被称为内部类。由于内部类嵌套在外部类中，因此必须首先实例化外部类，然后创建内部类的对象来实现。
```java
class OuterClass {
  int x = 10;

  class InnerClass {
    int y = 5;
  }
}

public class MyMainClass {
  public static void main(String[] args) {
    OuterClass myOuter = new OuterClass();
    OuterClass.InnerClass myInner = myOuter.new InnerClass();
    System.out.println(myInner.y + myOuter.x);
  }
}
```
    15

#### 静态内部类
静态内部类可以使用 static 关键字定义，静态内部类我们不需要创建外部类来访问，可以直接访问它：
```java
class OuterClass {
  int x = 10;

  static class InnerClass {
    int y = 5;
  }
}

public class MyMainClass {
  public static void main(String[] args) {
    OuterClass.InnerClass myInner = new OuterClass.InnerClass();
    System.out.println(myInner.y);
  }
}
```
    5
注意：静态内部类无法访问外部类的成员。
#### 从内部类访问外部类成员
内部类一个高级的用法就是可以访问外部类的属性和方法：
```java
class OuterClass {
  int x = 10;

  class InnerClass {
    public int myInnerMethod() {
      return x;
    }
  }
}

public class MyMainClass {
  public static void main(String[] args) {
    OuterClass myOuter = new OuterClass();
    OuterClass.InnerClass myInner = myOuter.new InnerClass();
    System.out.println(myInner.myInnerMethod());
  }
}
```
    10
    
### 匿名类
Java 中可以实现一个类中包含另外一个类，且不需要提供任何的类名直接实例化。主要是用于在我们需要的时候创建一个对象来执行特定的任务，可以使代码更加简洁。匿名类是不能有名字的类，它们不能被引用，只能在创建时用 new 语句来声明它们。

匿名类语法格式：
```java
class outerClass {

    // 定义一个匿名类
    object1 = new Type(parameterList) {
         // 匿名类代码
    };
}
```
以上的代码创建了一个匿名类对象 object1，匿名类是表达式形式定义的，所以末尾以分号 ; 来结束。

匿名类通常继承一个父类或实现一个接口。
![](https://www.runoob.com/wp-content/uploads/2020/06/nm-word-image-145.png)
#### 匿名类继承一个父类
以下实例中，创建了 Polygon 类，该类只有一个方法 display()，AnonymousDemo 类继承了 Polygon 类并重写了 Polygon 类的 display() 方法<:/p>
```java
class Polygon {
   public void display() {
      System.out.println("在 Polygon 类内部");
   }
}

class AnonymousDemo {
   public void createClass() {

      // 创建的匿名类继承了 Polygon 类
      Polygon p1 = new Polygon() {
         public void display() {
            System.out.println("在匿名类内部。");
         }
      };
      p1.display();
   }
}

class Main {
   public static void main(String[] args) {
       AnonymousDemo an = new AnonymousDemo();
       an.createClass();
   }
}
```
执行以上代码，匿名类的对象 p1 会被创建，该对象会调用匿名类的 display() 方法，输出结果为：

    在匿名类内部。
#### 匿名类实现一个接口
以下实例创建的匿名类实现了 Polygon 接口：
```java
interface Polygon {
   public void display();
}

class AnonymousDemo {
   public void createClass() {

      // 匿名类实现一个接口
      Polygon p1 = new Polygon() {
         public void display() {
            System.out.println("在匿名类内部。");
         }
      };
      p1.display();
   }
}

class Main {
   public static void main(String[] args) {
      AnonymousDemo an = new AnonymousDemo();
      an.createClass();
   }
}
```
输出结果为：
    
    在匿名类内部。
