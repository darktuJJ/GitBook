---
description: CLPs是一类AMMs，在规定的范围内为资产交换定价
---

# 集中流动资金池

## 描述：

陀螺仪的 "集中流动性池"（CLPs）是一类自动做市商（AMMs），在规定的范围内为资产交换定价。因此，任何CLP只为限制在这个特定区域的交易活动提供流动性。其目的是为了有效地使用资金池的资本。预计大多数储备资产将被储存在CLPs中。

**这种设计有几个好处--如下所述。CLPs目前是建立在Balancer上的，包括有两个或三个资产的池：**

* **有两种资产的池子：**又称二次方CLPs或[2-CLPs](2-CLPs.md)，以二次方不变曲线命名--类似于Uniswap v3的集中流动性池。但与Uniswap不同的是，2-CLP有效地提供了一个 "单点"，流动性均匀地分布在一个活跃的交易范围内。

{% hint style="info" %}
2-CLPs最好被理解为Uniswap v3的简化设计。针对所含资产的最多交易范围进行专门设计，使资金池具有：

* 高资本效率
* 高GAS效率
* 简单的用户体验
{% endhint %}

{% embed url="https://2063019688-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MU527HCtxlYaQoNazhF%2Fuploads%2FHwUn4OBtNrJvPeelKV1p%2F2-clp-v2.gif?alt=media&token=4e4866b1-49ab-4f08-b4df-9bf6d1170296" %}
**2-CLPs的资本效率收益的图形化表示**
{% endembed %}

* **有三种资产的池子：**又称立方体CLPs或[3-CLPs](3-CLPs.md)，支持三种资产，在功能上最好理解为2-CLPs的延伸。作为一个高层次的总结，它们放大了2-CLPs的好处。

{% hint style="info" %}
思考3-CLPs的一个直观方式是想象一个将两个最具影响力的AMM创新的结合在一起的资金池：多资产池和集中流动性。
{% endhint %}

{% embed url="https://2063019688-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MU527HCtxlYaQoNazhF%2Fuploads%2FiZZZNxilz5dKynNHFEvg%2F3-3CLP%20(1).gif?alt=media&token=9e841166-6d4a-46bb-9f9b-559cad4e91c1" %}
3-CLPs的资本效率收益的程式化代表
{% endembed %}

## CLPs的用户

**利益相关者可以以不同的方式使用陀螺仪CLPs，这是互利的：**

* **陀螺仪储备：**陀螺仪储备资产将被部署到一些CLPs中。部署到CLP的储备资产的费用收入将增加协议抵押率。
* **直接的LPs：**由于CLPs将持有协议资产，它们将可能提供大量的流动性。然而，CLPs也仍然对任何流动性提供者开放。任何直接的LP'ers可以进入引导池，为最常见的交易范围提供深度流动性，交易量（反过来，获得LP费用收入）通过Balancer的智能订单路由进行引导。
*   **互惠互利的循环：**CLPs的两种用途相互受益。

    1. 一旦储备资产被部署，LPers就会从具有高资本效率的实质性引导池中受益。这增加了资金池的活动，从而增加了费用收入。
    2. 陀螺仪协议反过来也会受益，因为CLP LPs的一小部分收入可以通过协议费获得。
    3. LPers和部署的储备资产之间的相互作用创造了规模经济，对资金池活动产生了积极的影响。\


    ****\
    ****

****
