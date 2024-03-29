# 模块划分

软件设计中最基本的问题之一是：给定两个功能，它们应该在同一位置一起实现，还是应该分开实现？这个问题适用于系统中的所有级别，例如功能，方法，类和服务。例如，应该在提供面向流的文件 I/O 的类中包括缓冲，还是应该在单独的类中？HTTP 请求的解析应该完全在一种方法中实现，还是应该在多个方法（甚至多个类）之间划分？

在决定是合并还是分开时，目标是降低整个系统的复杂性并改善其模块化。看来实现此目标的最佳方法是将系统划分为大量的小组件：组件越小，每个单独的组件可能越简单。但是，细分的行为会带来额外的复杂性，而这在细分之前是不存在的：

- 一些组件的复杂性仅来自组件的数量：组件越多，就越难以追踪所有组件，也就越难在大型集合中找到所需的组件。细分通常会导致更多接口，并且每个新接口都会增加复杂性。
- 细分可能会导致附加代码来管理组件。例如，在细分之前使用单个对象的一段代码现在可能必须管理多个对象。
- 细分产生分离：细分后的组件将比细分前的组件相距更远。例如，在细分之前位于单个类中的方法可能在细分之后位于不同的类中，并且可能在不同的文件中。分离使开发人员更难于同时查看这些组件，甚至很难知道它们的存在。如果组件真正独立，那么分离是好的：它使开发人员可以一次专注于单个组件，而不会被其他组件分散注意力。另一方面，如果组件之间存在依赖性，则分离是不好的：开发人员最终将在组件之间来回翻转。更糟糕的是，他们可能不了解依赖关系，这可能导致错误。
- 细分可能导致重复：细分之前的单个实例中存在的代码可能需要存在于每个细分的组件中。

如果它们紧密相关，则将代码段组合在一起是最有益的。如果各部分无关，则最好分开。以下是两个代码相关的一些提示：

- 他们共享信息；例如，这两段代码都可能取决于特定类型文档的语法。
- 它们一起使用：任何使用其中一段代码的人都可能同时使用另一段代码。这种关系形式只有在双向关系中才具有吸引力。作为反例，磁盘块高速缓存几乎总是包含哈希表，但是哈希表可以在许多不涉及块高速缓存的情况下使用。因此，这些模块应该分开。
- 它们在概念上重叠，因为存在一个简单的更高级别的类别，其中包括这两段代码。例如，搜索子字符串和大小写转换都属于字符串操作类别。流控制和可靠的交付都属于网络通信的范畴。
- 不看其中的一段代码就很难理解。
