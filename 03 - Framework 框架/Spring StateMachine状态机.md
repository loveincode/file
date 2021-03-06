# 什么是状态机：

就是一组状态，各个状态之间，依据一定的条件（如输入一个  1  或者是  0），存在一定的转换，（从状态X转换到状态Y）它有一个起始状态和若干终结状态，从起始状态开始，根据输入的串转换状态，直到所有的输入的被状态机处理，看看追最后停留的状态是否为终结状态，是的话就说这个串符合这个状态机规则，或者说被这个状态机接受！
流程可能是瞬间的动作经历很多步骤，比如“登录”流程，点击“登录”按钮之后，会有验证帐号、密码、验证码的诸多流程，但是都是在点击登录按钮的瞬间，逐一完成。
而状态机表示的都是一个已经完成的状态，每一个环节都是可以独立存在的。

有限状态机是一种用来进行对象行为建模的工具，其作用主要是描述 **对象在它的生命周期内所经历的状态序列，以及如何响应来自外界的各种事件**。
在
电商场景（订单、物流、售后）、
社交（IM消息投递）、
分布式集群管理（分布式计算平台任务编排）等场景都有大规模的使用。

状态机的要素
状态机可归纳为4个要素，即现态、条件、动作、次态。“现态”和“条件”是因，“动作”和“次态”是果。详解如下：
* 现态：是指当前所处的状态。
* 条件：又称为“事件”。当一个条件被满足，将会触发一个动作，或者执行一次状态的迁移。
* 动作：条件满足后执行的动作。动作执行完毕后，可以迁移到新的状态，也可以仍旧保持原状态。动作不是必需的，当条件满足后，也可以不执行任何动作，直接迁移到新状态。
* 次态：条件满足后要迁往的新状态。“次态”是相对于“现态”而言的，“次态”一旦被激活，就转变成新的“现态”了。

状态机动作类型
进入动作（entry action）：在进入状态时进行
退出动作：在退出状态时进行
输入动作：依赖于当前状态和输入条件进行
转移动作：在进行特定转移时进行

有限状态机是一种对象行为建模工具，适用对象有一个明确并且复杂的生命流（一般而言三个以上状态），并且在状态变迁存在不同的触发条件以及处理行为。
从我个人的使用经验上，使用状态机来管理对象生命流的好处更多体现在代码的可维护性、可测试性上，明确的状态条件、原子的响应动作、事件驱动迁移目标状态，对于流程复杂易变的业务场景能大大减轻维护和测试的难度。

```java
public enum States {
	  UNPAID,                 // 待支付
    WAITING_FOR_RECEIVE,    // 待收货
    DONE                    // 结束
}

public enum Events {
	  PAY,        // 支付
    RECEIVE     // 收货
}
```
其中共有三个状态（待支付、待收货、结束）以及两个引起状态迁移的事件（支付、收货），
其中支付事件PAY会触发状态从待支付UNPAID状态到待收货WAITING_FOR_RECEIVE状态的迁移，
而收货事件RECEIVE会触发状态从待收货WAITING_FOR_RECEIVE状态到结束DONE状态的迁移。


* 定义状态和事件枚举
* 为状态机定义使用的所有状态以及初始状态
* 为状态机定义状态的迁移动作
* 为状态机指定监听处理器



1. 易于使用的扁平单级状态机，用于简单的使用案例。
2. 分层状态机结构，以简化复杂的状态配置。
3. 状态机区域提供更复杂的状态配置。
4. 使用触发器，转换，警卫和操作。
5. 键入安全配置适配器。
6. 生成器模式，用于在Spring Application上下文之外使用的简单实例化通常用例的食谱
7. 基于Zookeeper的分布式状态机
8. 状态机事件监听器。
9. UML Eclipse Papyrus建模。
10. 将计算机配置存储在永久存储中。
11. Spring IOC集成将bean与状态机关联起来。

状态机引擎选型 https://segmentfault.com/a/1190000009906317
