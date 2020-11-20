# Java 修饰符
Java语言提供了很多修饰符，主要分为以下两类：

* 访问修饰符
* 非访问修饰符

修饰符用来定义类、方法或者变量，通常放在语句的最前端。我们通过下面的例子来说明：
```java
public class ClassName {
   // ...
}
private boolean myFlag;
static final double weeks = 9.5;
protected static final int BOXWIDTH = 42;
public static void main(String[] arguments) {
   // 方法体
}
```
## 访问控制修饰符
Java中，可以使用访问控制符来保护对类、变量、方法和构造方法的访问。Java 支持 4 种不同的访问权限。

* **default** (即默认，什么也不写）: 在同一包内可见，不使用任何修饰符。使用对象：类、接口、变量、方法。

* **private** : 在同一类内可见。使用对象：变量、方法。 注意：*不能修饰类（外部类）*

* **public** : 对所有类可见。使用对象：类、接口、变量、方法

* **protected** : 对同一包内的类和所有子类可见。使用对象：变量、方法。 注意：*不能修饰类（外部类）*。

我们可以通过以下表来说明访问权限：

**访问控制**
修饰符 | 当前类 | 同一包内 | 子孙类(同一包) | 子孙类(不同包) | 其他包
-- | -- | -- | -- | -- | -- |
public | Y | Y | Y | Y | Y
protected | Y | Y |	Y |	Y/N | N
default |	Y |	Y |	Y |	N |	N
private |	Y |	N |	N |	N |	N

