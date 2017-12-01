# 编程风格

收集一下有关编程风格的一些连接，后续再整理。

1. [http://www.lihaoyi.com/post/StrategicScalaStylePrincipleofLeastPower.html](http://www.lihaoyi.com/post/StrategicScalaStylePrincipleofLeastPower.html)
2. [http://www.lihaoyi.com/post/StrategicScalaStyleConcisenessNames.html](http://www.lihaoyi.com/post/StrategicScalaStyleConcisenessNames.html)
3. [http://www.lihaoyi.com/post/StrategicScalaStylePracticalTypeSafety.html](http://www.lihaoyi.com/post/StrategicScalaStylePracticalTypeSafety.html)
4. [http://www.lihaoyi.com/post/StrategicScalaStyleDesigningDatatypes.html](http://www.lihaoyi.com/post/StrategicScalaStyleDesigningDatatypes.html)
5. [http://www.lihaoyi.com/post/OldDesignPatternsinScala.html](http://www.lihaoyi.com/post/OldDesignPatternsinScala.html)
6. [http://www.lihaoyi.com/post/ImplicitDesignPatternsinScala.html](http://www.lihaoyi.com/post/ImplicitDesignPatternsinScala.html)
7. [http://www.lihaoyi.com/post/WhatsFunctionalProgrammingAllAbout.html](http://www.lihaoyi.com/post/WhatsFunctionalProgrammingAllAbout.html)
8. [http://twitter.github.io/effectivescala/](http://twitter.github.io/effectivescala/)

## 理念：强度最小化 Least Power

尽可能采用强度最小化的特性来达成目标，够用就行，避免使用复杂的、高级的特性。原因有三：

1. 任何 时候，复杂性都是你的敌人。
2. Scala是强类型的，重构的成本较低，你尽可以在需要的时候进行重构。
3. 因此，我们无需过渡设计，够用就行。在需要时再进行重构。

### 不可变性Immutability vs 可变性 Mutability

1. 尽可能使用 imutabe的数据类型 和 val，避免使用mutable数据类型和var。在很多的场合，var、mutable是邪恶的。
2. 如果非要使用mutable/var，你应该有非用不可的原因
   1. 为了性能
   2. 建模现实中确实是变化的对象。（Actor也是mutable的）
3. 如果非要使用mutable/var，尽可能将其限定在很小的范围内，避免在一个大的Scope中使用可变性。
4. 避免双重可变。`var myList = mutable.Buffer[Int]()`
5. 即使对数据库Entity，虽然它是可变化的，但你可以将变化留给数据库管理，在程序中仍然使用不可变的ViewObject。（erlang中专门引入了数据存储来解决可变性，在程序代码中仍然只能使用immutable的数据类型）

### 公开的接口、函数

1. 首先，最简单的接口、函数应尽量使用标准的数据类型。（无额外类型依赖）
2. 其次，避免调用者实例化自定义类型（暴露接口而不是具体实现，使用工厂方法而不是构造函数）。
3. 再次避，免需要调用者实现、继承你的接口

### 数据类型

1. 尽量使用标准的数据类型、集合。
2. 最小化参数，如果只依赖一个工厂方法，无需传递整个的工厂。如果只需要依赖对象的某个字段，无需传递整个对象。
3. 使用 Case Class 来传递多个字段值
4. 如果要传递多个泛化的类型，尽可能使用Sealed Trait
5. 上述方式不满足时，才使用其他的类型

### 异常处理

1. 如果只有一个可能的错误，可以使用Option来表示。
2. 如果只有确定有限的几个错误，可以使用 Sealed Trait
3. 其他情况下，才使用Exception
4. 任何情况下，不要使用 error flag。

### 处理异步结果

1. 能够返回同步结果的，避免使用异步
2. 使用 `Future[T]`
3. 最后的选择，才选择回调模式。





