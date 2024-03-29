# 洋葱圈架构

洋葱架构与六边形架构有着相同的思路，它们都通过编写适配器代码将应用核心从对基础设施的关注中解放出来，避免基础设施代码渗透到应用核心之中。这样应用使用的工具和传达机制都可以轻松地替换，可以一定程度地避免技术、工具或者供应商锁定。不同的是洋葱架构还告诉我们，企业应用中存在着不止两个层次，它在业务逻辑中加入了一些在领域驱动设计的过程中被识别出来的层次（Application，Domain Service，Domain model，Infrastructure 等）。另外，它还有着脱离真实基础设施和传达机制应用仍然可以运行的便利，这样可以使用 Mock 代替它们方便测试。

![](https://assets.ng-tech.icu/item/20230418231524.png)

在洋葱架构中，明确规定了依赖的方向：外层依赖内层以及内层对外层无感知。
