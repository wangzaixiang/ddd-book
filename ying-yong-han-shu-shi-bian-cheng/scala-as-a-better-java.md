### Scala as the better Java

Scala是复杂的，不过，我们可以先把Scala来做一个更好的Java来使用。使用Java的编程思路，但改变为Scala的语法，来替代Java编程。

对于Java程序员来说，转型到使用Scala来进行开发，这是非常重要的一步，可能会不太习惯，但应该可以很快的进行转变，因为，大部分的Java语言结构，在Scala中都有相似的语法。

* 使用 object 来替代 Java 的static。在scala中，没有static,将static的方法、变量定义在 object 中。
* 使用 trait 来替代 Java interface
* 使用 Scala的异常处理模式来替代Java的try/catch。
* Scala中，在类定义中，直接申明构造参数，而无需申明独立的构造方法。
* 使用 while 来替代传统的循环。（或者for）
* 使用 `Boolean/Byte/Char/Short/Int/Long/Float/Double`等类型来替代 `boolean/byte/char/short/int/long/float/double` 等基础类型。
* 使用 `Array[Byte]` 来替代 `byte[]`
* 在scala中，使用`array(idx)` 来替代java版本的`array[idx]`
* 使用 match 来替代 Java的 switch。
* 熟悉 Scala 的替代变量声明、方法定义的语法。
* Scala中缺少enum, @annotation的申明的支持。如果需要枚举、标注，需要在Java中定义，然后在scala中使用。

大部分的Java语法都可以简单的映射为Scala，这里列出一些需要关注的点：

1. instanceof 与 强制类型转换。
   ```scala
   if( obj.isInstanceOf[String] ) {
      val str = obj.asInstanceOf[String]
   }

   ```
2. break. scala中没有break关键字，虽然可以使用`scala.util.control.Breaks`替代，但尽量避免使用。
3. return的使用。 在scala中尽量避免使用 return 提前从方法中返回。必要的时候采用 if/else 进行处理。
4. scala没有 `?:` 三元操作符，需要用 `if else`替代。

综上，你不需要太多的学习scala，就可以简单的使用scala的语法 + java的编程模式，来开始尝试编写代码。即使这样，你可以尝试享受scala的优点：

* 使用scala的类型推理机制，少一些类型申明，让代码更简洁。
* 少使用`;`作为代码的分隔，让代码更加简洁

简洁的代码除了让你少敲代码之外，还可以让你的代码更好阅读。








