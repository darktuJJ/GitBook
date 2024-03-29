---
description: 陀螺仪协议文档
---

# 介绍

{% hint style="info" %}
陀螺仪DAO负责启动陀螺仪系统，并决定有哪些机制应该被纳入最终设计中。本文件描述了FTL实验室通过学术研究和开发制定的理论设计机制

如果文档有任何翻译错误和不清楚的地方，请通过Github向[Gyroscope-CN存储库](https://github.com/darktuJJ/GitBook/tree/Gyroscope-CN)提交合并请求。
{% endhint %}

### 陀螺仪协议

陀螺仪协议的使命是为DeFi建立强大的公共基础设施，其核心部分是一个有充分支撑的稳定币，具有充分的储备支撑和受算法上的价格约束。

* **一个完全支持的稳定币**：陀螺仪稳定币的目标旨在实现100%的长期储备率，即每单位稳定币都有价值1美元的抵押品支持。
* **全天候的储备支撑**：储备金是“一篮子”由协议控制的资产，共同为已发行的稳定币提供抵押。最初，大多数资产将是其他稳定币。储备金的目的是在最大程度上分散DeFi的各种风险，它考虑的不仅仅是价格风险，还包括审查制度、监管、交易对手方、oracle（预言机）和治理风险。
* **受算法上的价格约束**：铸造/赎回稳定币的价格是通过算法设定的，以平衡维持紧密挂钩的目标和面对短期危机时项目的长期生存能力。

{% hint style="info" %}
陀螺仪协议将在以太坊上推出，该协议仍在开发中。有一个建立在[Kovan测试网上的游戏化版本](游戏化测试网/游戏化测试网教程.md)，在各种容易获得的 "级别 "中向用户介绍了核心概念。
{% endhint %}

### 核心稳定性机制

#### 情景A：稳定币的价格高于面值

如果价格上升到挂钩点以上，就可以铸造更多的稳定币并在市场上出售，所得的收益会增加储备，这实际上是一个有上升趋势的封闭的套利循环。为了防止稳定币供应量的过度膨胀，作为对过渡性市场事件（如对另一个稳定币失去信心）的反应，如果资金流入量过大，且稳定币被过度抵押，那么铸造可能会暂时被禁止。

{% hint style="info" %}
这是陀螺仪设计中算法部分的内容：可以预见，以后会通过使用联合曲线衡量资金流入和流出的水平来决定铸造/赎回稳定币的动态铸造费用。
{% endhint %}

#### 情景B：稳定币的价格低于面值

根据储备价值是否覆盖100%的稳定币供应，这种情况的表现是不同的：

* 默认情况下，拥有健康的储备，就会存在与上升期相同的套利循环。稳定币可以在市场上买入，然后用价值1美元的储备资产赎回。正如第一道防线所支持的那样，有充分支撑的[储备设计](陀螺仪协议/核心要素/储备设计.md)，使资产支撑尽可能的强大。
* 如果对储备金有很大的冲击，则存在额外的防线，包括[算法](陀螺仪协议/核心要素/算法定价/)上的价格约束。

### 协议防御线

#### 存在多道防线以维持稳定的系统：

第一道防线是有充分支撑的储备金，储存所有的发行收益，并尽可能地进一步分散DeFi的各种风险，这旨在将全额抵押作为默认情况。有充分支撑的储备是多样化的，不仅仅是针对价格风险，还包括审查制度、监管、交易对手方、oracle（预言机）和治理风险。

{% hint style="info" %}
虽然储备金最初将几乎完全由其他稳定币组成，但在长期内可能会有所变化。只有在其他DeFi系统出现重大问题时，才会对储备金产生巨大的冲击，在这种情况下，陀螺仪将致力于提供最好的解决方案，并防止最坏的结果发生。
{% endhint %}

![](https://2063019688-files.gitbook.io/\~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MU527HCtxlYaQoNazhF%2Fuploads%2FPoCpe2N4EwTMBf5oEH1q%2FVaults%20Graphic%20v2.png?alt=media\&token=afee2403-d4a8-4d16-bc63-003d8356fa07)

**如储备金受到巨大冲击，那么第二道防线，即陀螺仪的算法定价就会接手控制**。如果稳定币单位变得抵押不足，赎回市场的联合曲线提供递减的赎回报价，作为一个断路器来维持一个可持续的系统。这种稳定机制应该会很少需要，但作为一个应急计划而存在，并使用陀螺仪的多市场设计，将流动性集中在稳定币铸币/赎回的联合曲线价格行情中。

降低赎回报价的目的是为了抑制银行挤兑和对货币挂钩的攻击，并以可持续的方式奖励那些等待过渡性低迷期过去的用户。虽然保留了稳定币持有者退出的能力，但重要的是，**陀螺仪提供了押注稳定币回到其目标价格的理由**，因为随着资金流出平衡回到零或储备恢复（例如，通过收益率），赎回价格会以算法方式恢复到挂钩价格。

{% hint style="info" %}
货币挂钩协调博弈的直观性是这样的：\
用户对稳定币的基本价值形成的信念取决于储备的价值以及稳定币被广泛接受和使用的程度。但用户也对其他市场参与者的信念形成了信念（等等），陀螺仪对这些信念进行协调。由于储备金的价值是可以在链上观察到的，以及关于如何使用储备金的规则，然后理性的用户隐含地同意是否攻击或捍卫挂钩，因为他们只有在数量占优的情况下才能获胜，这旨在预防信心危机。
{% endhint %}

**三级防线**包括允许储备金恢复或资产支撑扩大的机制。例如，储备金可以通过拍卖治理代币进行资本重组。事实上，陀螺仪治理被激励在适当的时候这样做，以建立应对冲击的资产缓冲，而不仅仅是作为危机期间的最后防御手段。\
陀螺仪机制还与杠杆贷款机制（如Maker）并肩工作，以增加强稳定性。

### 补充性的基础设施

额外的产品自然而然产生于陀螺仪的设计之下：例如，一个能够承受资产故障的、高流动性的DEX。这种设计可以被概念化为二级市场自动做市商、储备池和外部池的网络将允许有效的交易路由。二级市场的AMM（SAMM）是冗余的、高流动性的陀螺仪稳定币进出路径，而一级市场的AMM（PAMM）是铸币/赎回市场。如需更详细的解释，请阅读[PAMM](陀螺仪协议/核心要素/算法定价/一级市场AMM.md)和[SAMM](陀螺仪协议/核心要素/算法定价/二级市场AMM.md)的描述。

{% embed url="https://2063019688-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MU527HCtxlYaQoNazhF%2Fuploads%2FONC2tLGmZMuoMgcfFB6U%2FSAMM%20and%20Reserve%20Pools%20Graphic%20v2.png?alt=media&token=b35eb699-dad5-43bb-9355-7d3e03b9fd25" %}
