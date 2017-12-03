### 如何学习Scala

Scala是JVM上的一门语言，集合了很多的语言特性，结合了OOP、FP等编程特性，可以与Java语言（准）无缝对接，在众多的Java系语言中，Scala是历史悠久（相比Groovy、Kotlin、Ceylon、Fantom等），而又是有良好生态、发展活跃的一个语言。

我经常给Java程序员推荐学习和使用Scala：

> 我最早也是通过C、C++进入到程序员世界的，后面了解到FP，以及受部分LISP的鼓吹者步道，开始学习FP，也是从Haskell入手的。应该说，Hashkell给到了我们一个暂新的思维模式，帮助我们更好的了解了函数式的编程思想。
>
> 不过，真正的对我理解FP起到帮助的是scala，倒不是scala在这一方面更优秀，而是因为scala基于JVM，可以和Java无缝的配合，可以真实的在工程实践中应用。只有真实的工程实践，你写出个几千上万行代码，并且真实的解决一些问题，才能够真实的体会到函数式编程带给你的快乐、痛苦，适应和不适应的地方。而Haskell，则可能难以为你提供这个实践的机会。如果仅仅是做几道算法习题的话，我想，未必能够很好的理解函数式编程。
>
> 所以，如果你目前的工程实践以Java为主的话，那么scala可能会是很好的学习函数式编程的入手语言。其实，不要太理会网上描述的Scala是多么多么的复杂难学，你只要真正的用起来，剩下的只是时间问题：最差的话，你也可以用scala来写java代码，然后在此基础上逐步应用scala的优秀特性尤其是函数式特性，你不会失去太多（IDE支持稍弱、调试稍弱、编译慢），但会得到很多很多。
>
> 在团队中推广scala是一件很困难的事情，我个人是摔过跟头的。对scala最大的障碍其实不是学习，而是一班有一定工作经验的熟悉Java的“资深”程序员或者项目经理，他们其实自己并不怎么写代码了，但却控制着团队的技术选型。如果你没有决定权，你可能无法决定在项目中应用scala，但你至少可以在自己的业余时间，写一些小的工具软件，或者做一些项目外的实验，通过这种方式来学习scala。但读书或者做几道习题是远远不够的。

在网络上，有很多对Scala的复杂性的评价，认为Scala是宇宙中最复杂的语言，在Scala之前，这个语言是C++。 如果一个语言的复杂性超过了C++，那是有多可怕呢？的确，如果论起Scala的复杂性，那可能是恐怖的一面。不过，如果采用了合适的方式来使用Scala，那么Scala也会是很简单的。

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
4. 


