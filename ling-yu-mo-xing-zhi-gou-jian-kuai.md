# 领域模型之构建块

领域模型的基本元素包括：

* Entity 是领域模型中最为核心的元素。
  * 实体有唯一标识，可以从外部通过唯一标识进行引用（关联关系）。
  * 实体有状态和生命周期，在整个生命周期中，实体的状态会不断的变更
  * 实体有固有的约束条件，包括：属性的类型、取值范围、唯一性约束、不变量约束。
  * 对实体的变更是通过语义的Command来完成，而非直接对外暴露数据状态的修改。（与之相反，在事务脚本模式中，我们直接修改实体的属性）
  * 实体状态变更时，对外产生Event。其他的领域可以订阅Event，完成包括物化视图的更新、关联实体的状态更新等操作。

* Value Object
  * 实体有一些属性，没有固有的ID，也不需要从外部根据ID仅用引用。如果需要更新时，可以整体值进行替换，那么，这类的数据可以作为Value Object而存在。
  * Value Object也可以作为一个子表而存在。

* Command
  * 对单个实体、或者多个领域实体的语义操作，一个Command的接口契约定义包括：
    * input：最少传入原则，每一个传入的参数都应该是执行当前命令必须的（或至少是依赖的冗余）。对不会被使用到的属性，宁愿多定义一个VO，也不要包括多余的不用的参数。
    * output：根据CQRS原则，Command只返回最少的信息，不要替代Query返回结果。
    * pre-condition：对实体状态的前置检查、对input参数的前置检查
    * post-condition：当前Command执行完成后，应该达成的约束。隐含的，所有的实体不变量、聚合不变量，是全局默认的，无需在每个Command中重复申明。
    * Events。 Command完成后，会产生的事件类型。   

*  Event.
  * Event建模了对实体的更新类操作的结果，可以作为EventSource中的实体存储机制，也可以作为跨实体间的协调、数据一致性的通知机制，也可以作为沟通核心领域逻辑与扩展逻辑的桥梁。
  * Event 有两种传播方式，EventBus vs MessageQueue，EventBus是一种轻量级的，统一进程内、同一事务内的消息传递，用于 aggregation之间的相关实体的数据一致性协作。 MessageQueue是一种重量级的、跨进程乃至跨服务器的，也是夸数据库事务的一种协调机制。通过MQ，来实现最终一致性。
  
* Aggregation（聚合）
  本文中aggregation(聚合)并不完全等同于Eric Evans在《Domain-Driven Design tracking complexity in the heart of software》一书中定义的Aggregation。后续或者可以选择一个更好的名词。  
  





