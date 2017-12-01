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

### 关于依赖注入

1. 能够用直接依赖解决的，直接依赖。
2. 其次，作为参数进行传递
3. 其次，需要传递给多个函数时，可以作为构造参数传递给一个封装的类
4. 其次，使用Abstract Member，在构造时注入
5. 其次，使用implicit参数
6. 其次，使用dynamic variable + Global-States
7. 不要使用 setter 注入

### 关于变量、方法、类的命名约定

理念：应该是面对阅读代码，而非面向编写代码来确定如何命名。

1. 如果作用域范围大，应使用长命名
2. 常用的名称应该简短
3. 有副作用的方法（如果有危险新的话，就更加）需要使用长名称
4. 在特定上下文中，不必要重复上下文的名称
5. 避免使用运算符命名方法。

### 编写类型安全的代码

1. 避免使用null，使用Option\[T\] 替代null。
2. 使用Empty集合来替代null
3. 避免Exception，使用sealed trait来作为返回值
4. 编写无副作用的代码
5. 使用正确的数据类型，不要用String来作为替代类型。 
6. 避免使用反射的方式，来处理代码，这样的代码是无法发现类型错误的，对重构不友好。
7. 如果必要，可以使用Macro来处理动态的类型，同时，获得强类型的支持。

### 避免过程式的写法

1. no return
2. no break
3. no var
4. 使用尾递归来替代循环
5. 使用Expression，避免statement
6. 使用 match 来替代复杂的 if else
7.  使用Pattern Match来处理的匹配逻辑

### 编程风格

1. 善用pipe模式的链式调用风格，每一步操作在一行中完成。
2. 使用private等作用域限定符
3. 使用 NotFatal 来处理异常



