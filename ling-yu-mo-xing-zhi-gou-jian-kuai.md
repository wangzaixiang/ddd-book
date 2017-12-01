# 领域模型之构建块

![](/assets/ddd-elements.jpeg)领域模型的基本元素包括：

* Entity 是领域模型中最为核心的元素，一个实体是一个有外部唯一标识的、有状态的、有确定生命周期的对象。
  * Command：实体的语义操作，是对业务逻辑的封装，外部客户不能直接修改实体的状态。命令包括原子命令（最小化的操作和复合操作，后者包括对多个原子操作）
  * Query：
  * Event：对实体的原子操作的结果。在EventSource中，这些Event可以直接作为存储。Event可以在当前聚合、当前Package中进行传递，触发
* Value Object
* Aggregations
* Package





