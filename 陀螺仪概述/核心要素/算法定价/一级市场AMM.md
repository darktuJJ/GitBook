---
description: 稳定币单位的铸造和赎回
---

# 一级市场AMM

### 概述

稳定币单位可以在一级市场（PAMM）上铸造和赎回。

没有中央发行机构，用户可以直接通过完全开放的陀螺仪系统铸造和赎回稳定币，也不存在对手方。

PAMM 的形态（即提供铸币/赎回报价的联合曲线）是基于当前储备率和资金流出的函数。

### PAMM赎回曲线示意

下图中所示的是不同储备率水平下的PAMM赎回曲线与Uniswap50-50流动池的对比：

{% embed url="https://2063019688-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MU527HCtxlYaQoNazhF%2Fuploads%2F1SZSPI7m4l4S9EhenYzb%2FStylized%20PAMM%20Redemption%20Curve%20v3.png?alt=media&token=b35e6caa-2216-4e40-9a2f-43d2cfe3feb8" %}

### 举例和进一步的解释

#### 抵押率接近100%的赎回：

如果稳定币变得抵押不足并开始低于面值交易，赎回曲线就会在1美元附近开始，以便在挂钩周围实现良好的流动性。

#### 抵押率远低于100%的赎回：

如果继续发生赎回，即 "流出 "增加，赎回曲线最终会移动到断路器阶段。在这个断路器上，赎回率下降到实际储备率以下，以确保赎回始终可以进行。

赎回市场的联合曲线提供递减的赎回报价作为断路器。其目的是为了抑制资金出逃和对货币挂钩的攻击，同时使用户能够退出，但奖励那些等待过渡性衰退期过去的用户。

重要的是，即使稳定币持有者决定退出，陀螺仪也提供了押注稳定币会回到其目标价格的合理理由，因为随着资金流出重回到零或储备金恢复（例如通过投资收益），赎回价格会在算法下恢复到锚定价格。

我们会在即将发布的 PAMM 技术论文中对 PAMM 的设计进一步优化并提供更为详尽和正式的描述。目前公布的细节见[<mark style="color:red;">白皮书</mark>](https://gyro.finance/pdfs/Gyroscope\_Lite\_Paper.pdf)第3.1节（铸币曲线）和3.4节（赎回曲线）。
