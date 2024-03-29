---
description: 二次方集中流动资金池或2-CLPs
---

# 2-CLPs

## 2-CLPs的说明

**陀螺仪的2-CLPs是将流动性集中在一个定价范围内的AMMs。**一个给定的2-CLP是由定价范围\[α,β]和池子里的两种资产来确定参数的。

给出资金池中实际储备的数量(x,y)和资金池的定价范围\[α,β]，可以计算出偏移量a和b。这些偏移量描述了资金池在真实储备上增加的数量，以形成实现定价范围的虚拟储备。这些资金池使用以下不变因素：(x + a)(y + b) = L^2.

**2-CLPs也可以直观地表示。**下面的概念图显示了一条没有集中流动性的恒定产品曲线，其中两个价格界线被描述为蓝色矩形。2-CLP可以被理解为 "放大 "曲线在价格界线之间的部分。在这里，曲线基本上是 "平坦的"，交易对价格的影响较小。

{% embed url="https://lh3.googleusercontent.com/HiTLnGO8aQoWhypPUi87DmLyJCBsbL2ra71HxO98w2JVsPV1-ZoPKYlp9zskMvxrnHWes5e4RzNhFnDEPgl5eX_NmzvCm88Xq4AO5rm_C6sTnj0YiHevV-d5Sgb-_n1xxFBe4LEBFYtDTAsBfAK6dv8" %}
**显示2-CLPs的流动性集中度的概念性图形**
{% endembed %}

**与 "x \* y = k"（即恒定积或Uniswap v2）的AMMs相比，2-CLP可以更好地利用现有的流动性。**2-CLP不是将流动性分散到理论上可能发生的整个价格范围--"从零到无限"--而是通过增加价格界线来关注小范围的价格，这些界线是通过 "虚拟储备 "来实现的。虚拟储备可以理解为使用标准的无限范围池达到集中流动性头寸的深度所需的储备。

{% embed url="https://2063019688-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MU527HCtxlYaQoNazhF%2Fuploads%2FzHKkA4b9oZOdxn6U0mAe%2F2-clp-v2.gif?alt=media&token=6adaea9d-51c2-478b-9413-78b099189dd5" %}
**2-CLPs的资本效率收益的图形化表示**
{% endembed %}

{% hint style="info" %}
YieldSpace白皮书中首次提出了虚拟储备的概念，Uniswap v3首次提出了集中流动性池的概念。

2-CLPs最好被理解为Uniswap v3的简化设计，是为特定的使用情况量身定做的。为所包含的资产中交易量最大的范围进行专门设计，使资金池具有（1）高资本效率和（2）高气体效率。
{% endhint %}

## 2-CLPs的好处

**2-CLPs有三个主要好处--资本效率、Gas效率和简化的用户体验:**

* **资本效率:** 2-CLPs提高了Balancer生态系统的资本效率。2-CLPs的资本效率可与Balancer池的Uniswap v3相媲美。
* **Gas效率:** 2-CLPs被设计成具有很高的气体效率。2-CLPs采用可有效计算的恒定产品定价公式。2-CLPs也被设计成与Balancer整合。Balancer v2允许以高度Gas效率的方式在几个池子之间组成交易，为Balancer的智能订单路由奠定了基础。
* **用户体验:** 2-CLPs被设计成尽可能简单。2-CLPs设计可以被认为是Uniswap v3的专门变体，因为并不总是需要Uniswap v3的tick系统的全部通用性。这实现了更简单的资金池架构，反映在提供流动性的用户体验上要求简便。

## 2-CLPs的风险

**使用2-CLPs也有一定的风险，包括智能合约风险、策略风险和逆向选择风险。**术语 "无常损失 "有时被用作策略风险和逆向选择风险的总称。

* **智能合约风险:** 与任何智能合约一样，存在一个固有的风险，即利用或错误将存入的资产置于风险之中。这种风险可以通过进行代码审计和测试来减少，但它不能完全被缓解。
* **策略风险:** 通过进入资金池，LPers承诺采用一种做市策略，并反过来采用一种投资组合再平衡规则，从根本上说，这种策略与仅仅持有相关资产或使用不同的再平衡规则具有不同的回报。随着价格的变化，资金池卖出一种资产以换取另一种资产。在一个极端的情况下，两个池子里的资产之间的相对价格会永久地移出价格范围。在这种情况下，资金池只剩下价值较低的资产。

{% hint style="info" %}
对于CLPs来说，这种策略风险可能高于没有集中流动性的资金池，因为该策略允许在资金池的价格范围内的任何价格进行更多的交易。

这是资本效率的副作用，对交易者的价格影响很低。在一个极端的情况下，当其中一个资产的价值归零时，资金池的价值也会归零。通过为资产池的两边选择基本面相关的资产（因为这样相对价格的严重永久性转变的可能性较小，而振荡的可能性较大），以及仔细选择价格范围，可以降低策略风险。
{% endhint %}

* **逆向选择风险:** 在任何AMM资金池中，如果资金池中资产的真实相对市场价格长期波动，LPers会因为逆向选择而产生损失。特别是，资金池会以比真实市场价格更差的价格提供 "陈旧 "的报价。逆向选择的损失将等于套利者将池子里的报价调回与市场其他部分平衡的利润。

{% hint style="info" %}
对于CLPs来说，这种风险可能比没有集中流动性的资金池要高，因为CLP的设计在资金池的价格范围内提供了更深的市场。&#x20;

在价格波动的情况下，更多的套利被启用。然而，如果后来价格恢复到最初的价格，这种损失就不会实现，资金池就会从交易费中获利。
{% endhint %}

## 技术文档

要阅读有关文档和实施的信息，请参见以下资源：

{% content-ref url="../技术文档/" %}
[技术文档](../技术文档/)
{% endcontent-ref %}

