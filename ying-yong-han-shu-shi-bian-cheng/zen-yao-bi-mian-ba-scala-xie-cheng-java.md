# 如何避免将Scala写成Java?

1. 杨博的回答。
2. 北南的回答
   > 链接：[https://www.zhihu.com/question/64568400/answer/222048320](https://www.zhihu.com/question/64568400/answer/222048320)
   >
   > 来源：知乎
   >
   > 这真的是个非常好的问题，我主要从提高开发效率的角度出发，而不是为Functional Programming而Functional Programming。当然，即便你是FP的铁粉，你也会发现它们在绝大多数情况也是不矛盾的。另一方面，Java还是很不错的，但scala可以做的更好。
   >
   > 那我们如何能利用好scala的特性，让程序更简洁高效，而又不损失甚至提供比java还好的易读性呢? 一点小建议，不断补充.
   >
   > 1. 不用var。var是可以被不断修改的，而val是不能被修改的。使用val而不是var能让你的程序更强壮，bug更少，更好调试，更容易测试，在并发条件下，更容易调优而获得更好的性能。数学证明我们不用var是没问题的。  
   > 2. 不用mutable的collection，和var同样的道理。  
   > 3. 不用null，在java中，我们把null当作一个magic value给return回来，等待调用方进一步判断。但这非常容易让你的代码crash，而且你要到处进行判断。在scala中，可以用Option的，可以用Try，scala有好几种类似的结构，大家可以都看看。  
   > 4. 不要使用throw。直接抛出异常是个坏习惯\(我不是说抛异常是个坏习惯，但抛的方法是可以更讲究的\)，而且你在多线程的情况下，你的异常抛给谁？在Scala中，你可以封装你的异常，把它作为一个值来返回，可以看一下Try\[\] ，不是try/catch的try, 是scala.utils.Try，和Option非常像。我不推荐使用Either用来处理成功和失败的混合情况，Left和Right多烧脑。  
   > 5. 不用thread。除非你要玩最底层，从头写个akka或者netty， 我觉得你一般是用不上thread的。actor最好也不用，多用Future来设计你的多线程程序。  
   > 6. case class和match用的好可以让你的程序更易读。极端点你都可以不用if, 但没必要，我主张能用if还是用if， 因为if其实很多时候更高效，更易读。还有scala的各种block是一个值，你可以直接使用，很多java程序员往往一开始不习惯这么干。比如说 val a = if \(isAxxx\) 1 else {......}  
   > 7. 减少继承的层级。弄一大堆trait来mixin，你这是在把scala导向c++。如果你只是像重用代码，可以通过传递一个function，或者纯粹oo的aggregation模式.
   >
   > 其实scala可以非常易读，而且高效。我haskell用的很少，不过道理是相通的，var是最邪恶的。



