---
description: 立方体集中流动性池或3-CLPs
---

# 3-CLPs

## 关于3-CLPs的说明

**立方体CLPs，或称3-CLPs，将三种资产的流动性集中在一个定价范围内。**第一个3-CLPs是针对资产池中三对资产的对称价格范围\[α,1/α]而设计的。一个给定的资产池是由定价参数α和组成资产池的三种资产所决定的。

{% hint style="info" %}
给出资金池中真实储备的数量（x,y,z）和资金池的定价参数α，可以计算出偏移量a。这个偏移量描述了资金池在真实储备上增加的数量，以形成实现定价范围的虚拟储备。

对称的3-CLPs使用以下不变式：（x+a）（y+a）（z+a）=L^3
{% endhint %}

就像任何有两个以上资产的 Balancer pool 或 Curve pool 一样，3-CLP中不同资产对之间的价格是相互影响的。例如，如果资产x对资产z进行交易，池子里的资产y对资产z的现货价格就会改变。这意味着，资金池在任何时间点上同时提供的价格组合都受到数学关系的限制。

**由于这种关系，理解3-CLP的多维定价区域需要一些思考。**对于2-CLP，池子的定价界限非常容易理解：它们只是一条线上的价格区间，如下图所示：

{% embed url="https://lh6.googleusercontent.com/GbUtkQtQ-tuoYYkFyDMfDZv3gVtmrDXwxw9TjO74o2uW9N1Laes-2XpOS68S8NIeTtH0V0jry-IRwlmI2I5W36_SxgX_5oImxrsMvyjhwYD50ImQ-UddNM2ua0hq4Bzk26cmEJpfvke-MRBF8N6tp3Q" %}
**2-CLP价格区域的可视化图像**
{% endembed %}

**下面的图形直观地显示了3-CLP的可行定价区域，即3-CLP可能报价的现货价格区域。**这里我们选择了α=0.5，所以池子的价格不会低于0.5或高于2.0。

{% embed url="https://lh6.googleusercontent.com/RBCkNsxzRrF7UbF74qSSNoa99_AjVg2HRyZhJ3xR4WeOjaxGoWxMPuz2vX2W_1gAGqc7LARkrcwjOGyxGMROvcwNpbBFI7PStehE4Aa8IfFgOfubFnDqRUs1gKqzCck7-uj16n7MOfwozAaKxx6EVWA" %}
**3-CLP的可行定价区域的可视化图像**
{% endembed %}

可行定价区域的参数是资产x和y的价格，分别以资产z的单位表示。第三个价格对，x以y的单位表示，是这两个价格的商：px/y=px/z/py/z。在图中，每一种包含的资产都用不同的颜色表示。

线条表示各自的储备资产x、y或z在池中被耗尽的价格组合，阴影区域表示各自的储备资产在池中有正数余额的地方。

所有颜色重叠的区域是可行的定价区域--这些是资金池可以报价的价格组合。在角点，资金池只持有单一资产，三对资产中有两对实现了最小或最大的价格约束（即它们等于α=0.5或1/α=2.0）。

## 3-CLPs的好处

**3-CLPs放大了2-CLPs的好处：**

* **资本效率：**通过将流动性集中在三种资产之间，与类似于2-CLPs的交易对设置相比，3-CLPs通过聚合第三种资产实现了50%的资本效率提升。
* **GAS效率：**三个资产之间的交易相比通过两个不同的2-CLP连接两个交易更省GAS。
* **用户体验：**3-CLPs在结构和用户体验方面仍然比较简便。

{% embed url="https://2063019688-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MU527HCtxlYaQoNazhF%2Fuploads%2FZJMm9nSAJWIU3T74TaWG%2F3-3CLP%20(1).gif?alt=media&token=e3bc2dd9-eb31-4ede-a8ba-2298d7ca6c94" %}
**3-CLPs的资本效率收益的程式化代表**
{% endembed %}

## 3-CLPs的风险

**使用3-CLPs 也有一定的风险，包括以下几点：** （这些风险包括2-CLPs的风险；我们只简单地解释这些风险。更多细节见[2-CLPs部分](2-CLPs.md#2clps-de-feng-xian)。）

* **智能合约风险：**漏洞或错误使存放的资产处于风险之中的风险。
* **策略风险：**集合体所隐含的投资组合策略比不同的策略（如仅仅持有资产）的回报率更差的风险。
* **逆向选择风险：**由于套利者采取陈旧的价格报价，永久性的价格变化意味着对LPers的损失。

**与2-CLP相比，3-CLP中的LPers面临着额外的风险：**

* **资产互动风险：**由于3-CLP包含一个额外的资产，LPers会因为两个额外的价格对而面临策略和逆向选择风险。

{% hint style="info" %}
例如，如果其中一种资产的价格下降到足够低的水平，池子最终将只有那个价值最低的资产（见上图）。这种现象发生在许多多资产AMM中，如Curve稳定币3-pool。就像2池中的策略风险一样，它可以通过选择基本面相连的资产和适当的价格界限来减少。
{% endhint %}

* _请注意，3-CLP的定价区域比其他资金池更复杂；这可能意味着套利者需要更多时间来熟悉资金池的运作，才能顺利运行。_

## 技术规格

要阅读有关数学规范和实施的信息，请参见以下资源：

{% content-ref url="../技术文档.md" %}
[技术文档.md](../技术文档.md)
{% endcontent-ref %}
