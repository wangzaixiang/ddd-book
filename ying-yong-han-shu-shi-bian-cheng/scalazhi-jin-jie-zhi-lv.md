### 进阶之旅

掌握了基本的scala语法，能够用scala来替代java来完成编程，虽然代码的风格还是完全Java化的，但至少可以达到或者接近你之前的编码效率。这其实是一个不难的任务，是所有Java程序员首先要达到的程度。

然后，我们将进一步的熟悉Scala的一些进阶特性，这些特性可以进一步的提升你的代码质量。

1. 使用 expression 来替代 statement。
   在scala中，if, for, match 都是一个expression的。譬如：
   ```scala
   val showFullName = true
   var name: String
   
   // 将 if/else作为 statement使用
   if(showFullName) name = firstName + " " + lastName
   else name = firstName
   
   // 将if/else作为expression使用
   val name = 
      if(showFullName) firstName + " " + lastName
      else firstName
      
   // 将for作为statement使用
   val origin = 0 to 10
   var squres = new Array[Int](10)
   for(i <- origin){
      squares(i) = origin(i) * origin(i)
   } 
   
   // 将for作为表达式使用
   val squares = for(i <- origin) yield origin(i) * origin(i)
   
   // 将match作为statement使用
   val month = 2
   var days: Int
   month match {
   case 1 => days = 31
   case 2 => days = 28
   case 3 => days = 31
   ......
   }
   
   // 将match作为expression使用
   val days = month match {
   case 1 => 31
   case 2 => 28
   ......
   }
   ```
   
   其实，上面的几个例子都有一个共同点，使用expression替 statement后，都消除了var，而使用val替代。这其实是非常关键的一点。记住，**var是邪恶的**，真正的scala世界，不需要var。 
   
2. 学习 Collection API，掌握丰富的集合操作。
   几乎所有的介绍函数式编程的语言，都会包括这样的例子：
   ```scala
   val text = "a long string contains many words"
   val words = text.split("\\s+")
     .map(_.toLowerCase)
     .filter(NON_WORDS.contains(_)==false)
     .groupBy(identity)
     .foreach { case (word, array) =>
        println("$word count:${array.size}")
     }
    ```
  如果使用Java的模式来完成同样的功能，不仅代码量会膨胀很多倍，而且，可读性也会成为一个很大的问题。
  而这也是函数式编程最为擅长的，在上面的例子中，map, filter, groupBy, foreach都是高阶函数，通过这些高阶函数的组合，数据以管道的方式从一个结算传递给另外一个计算，简洁而优美。
  * map operation
     * xs map f
     * xs flatMap f
     * xs collect f
  * iteration
    * xs foreach f
  * filter & subcollections
    * xs.head
    * xs.tail
    * xs.init
    * xs take n
    * xs drop n
    * xs takeWhile p
    * xs dropWhile p
    * xs filter p
    * xs filterNot p
 * test
    * xs forall p
    * xs exists p
    * xs count p
 * Fold Operation
    * xs foldLeft(z)(op)
    * xs foldRight(z)(op)
    * xs reduceLeft op
    * xs reduceRight op
    * xs.sum
    * xs.product
    * xs.min
    * xs.max
 
 scala的进阶之旅，熟练掌握上述的集合操作，并且能够在编程时，熟练的应用，消除一下传统的Java编程方式：
 * 不再需要使用 for 或者 while 等传统的Java模式来处理集合。
 * 不在需要使用 var 乃至 mutable collection来处理集合。
 
 你会感觉到scala的强大、美妙，而且这样编写的代码，不仅简洁、易于阅读，而且，程序的Bug会显著减少，代码一次性正常通过的几率也会大幅度提升。
 
3. 继续学习如下的特性，并在工作中应用，以提高代码的可读性。
  * case class
  *
4. 不要轻易尝试如下特性。这些特性功能很强大，但也是导致scala背负着“宇宙最复杂的语言”的最重要的原因。我的建议是，不充许在应用层中使用，只充许在基础库中出现，并且编程者必需有一定的熟悉度证明。

