---
description: 在 PAMM 定义的价格范围内集中流动性
---

# 二级市场AMM

### 概述

在陀螺仪协议中，二级市场AMM将流动性集中在一个范围内，该范围遵循一级市场AMM设定的铸币和赎回报价。

在储备金健康的情况下，SAMM 的流动性集中在一个狭窄的区间内。如果储备金受到冲击引发 PAMM 设定新的赎回价格，这个区间就会扩大。值得注意的是，SAMM 的流动性设定是非常有弹性的，因为：

* SAMMs是冗余的（提供多条不同的Gyro稳定币出入路径 ）。
* SAMMs是相互独立的（例如，如果交易对中的资产崩溃，剩余的 SAMM 池仍然可以运作，这与使用一个共同的Curve池不同）。

### SAMM赎回曲线示意

下图中所示的是 SAMM 赎回曲线与Uniswap50-50流动池的对比：

![SAMMs 将流动性集中在 PAMM 的价格范围内 (这里模拟了在冲击环境下PAMM改变形态).](<../../../.gitbook/assets/Graph 6 v2.png>)

SAMM 设计包含了优化的联合曲线和虚拟储备机制。我们会在即将发布的 SAMM 技术论文中对其进一步优化并提供详尽、正式的描述。更多细节暂时可见[<mark style="color:red;">白皮书</mark>](https://gyro.finance/pdfs/Gyroscope\_Lite\_Paper.pdf)第3.5节。
