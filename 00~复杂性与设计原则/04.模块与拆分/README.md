# 模块化设计

管理软件复杂性最重要的技术之一就是设计系统，以便开发人员在任何给定时间只需要面对整体复杂性的一小部分。这种方法称为模块化设计。在模块化设计中，软件系统被分解为相对独立的模块集合。模块可以采用多种形式，例如类，子系统或服务。在理想的世界中，每个模块都将完全独立于其他模块：开发人员可以在任何模块中工作，而无需了解任何其他模块。在这个世界上，系统的复杂性就是最糟糕的模块的复杂性。

不幸的是，这种理想是无法实现的。模块必须通过调用彼此的函数或方法来协同工作。结果，模块必须相互了解。模块之间将存在依赖关系：如果一个模块发生更改，则可能需要更改其他模块以进行匹配。例如，方法的参数在方法与调用该方法的任何代码之间创建依赖关系。如果必需的参数更改，则必须修改该方法的所有调用以符合新的签名。依赖关系可以采用许多其他形式，并且它们可能非常微妙。模块化设计的目标是最大程度地减少模块之间的依赖性。

为了管理依赖关系，我们将每个模块分为两个部分：接口和实现。接口包含使用其他模块的开发人员必须知道的所有内容，才能使用给定的模块。通常，接口描述模块做什么，而不描述模块如何做。该实现由执行接口所承诺的代码组成。在特定模块中工作的开发人员必须了解该模块的接口和实现，以及由给定模块调用的任何其他模块的接口。除了正在使用的模块以外，开发人员无需了解其他模块的实现。

考虑一个实现平衡树的模块。该模块可能包含复杂的代码，以确保树保持平衡。但是，此复杂性对于模块用户而言是不可见的。用户可以看到一个相对简单的接口，用于调用在树中插入，删除和获取节点的操作。要调用插入操作，调用者只需提供新节点的键和值即可。遍历树和拆分节点的机制在接口中不可见。

# Links

- [《软件设计的哲学》中文翻译 A Philosophy of Software Design](https://github.com/xulongfei/A-Philosophy-of-Software-Design-zh)
