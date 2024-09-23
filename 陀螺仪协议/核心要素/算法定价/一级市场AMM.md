---
description: 通过铸造和赎回稳定币来抵御银行挤兑和脱锚风险。
---

# 动态稳定机制

{% embed url="https://youtu.be/nrdnRNGxv1c" %}

### 概述

在动态稳定机制（DSM）中，稳定币单位可以被铸造和赎回。

这里没有中央发行者。用户可以直接通过去中心化且透明的 Gyroscope 系统铸造和赎回稳定币单位，不存在交易对手。

DSM的形状（即铸造/赎回价格的联合曲线）由当前的储备率和资金流出情况决定。

### DSM赎回曲线示意图

下图展示了在不同储备率水平下的简化 DSM 赎回曲线，并以 50-50 的 Uniswap 池为例进行说明。

{% embed url="https://2063019688-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MU527HCtxlYaQoNazhF%2Fuploads%2FjQGrzaQH1OMUdRT0g0id%2FGraph%202%20v2.png?alt=media&token=c1df3436-1728-49e1-8080-d3adaf4a090e" %}
简化的 DSM 赎回曲线
{% endembed %}

### 示例与进一步解释

#### **接近 100% 抵押的赎回**

如果稳定币变得抵押不足并开始低于面值交易，赎回曲线就会在1美元附近开始，以确保锚定价格附近的良好流动性。

#### **远低于 100% 抵押的赎回**

如果持续发生赎回，即“资金流出”增加，赎回曲线最终会进入“断路器阶段”。在这一断路器下，赎回率将低于实际储备率，使得赎回始终可持续。

在这种情况下，赎回市场的联合曲线提供递减的赎回报价，作为断路器。其目标是抑制银行挤兑和对货币锚定的攻击，同时允许用户退出，但也会奖励那些等待短暂低迷期结束的用户。

重要的是，即使稳定币持有者决定退出，Gyroscope 仍然提供了理性的理由去押注稳定币回归其目标价格。当资金流出回归平衡（趋近于零）或储备通过收益等方式恢复时，赎回价格将自主地回升至锚定价。

DSM的设计在我们的[DSM技术论文](https://github.com/gyrostable/technical-papers/blob/main/P-AMM/P-AMM%20technical%20paper.pdf)（以前称为P-AMM）中得到了充分的说明、正式的描述和优化。
