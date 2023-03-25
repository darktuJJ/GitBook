---
description: 在DSM定义的价格范围内集中流动性
---

# GYD交易池

### 概述

在陀螺仪协议中，GYD交易池将流动性集中在一个范围内，该范围遵循DSM设定的铸币和赎回报价。

在储备金健康的情况下，GYD交易池的流动性集中在一个狭窄的范围区间内。如果储备金受到冲击引发 DSM 设定新的赎回价格，这个价格区间将会扩大。值得注意的是，**GYD交易池的流动性设定是非常有弹性的，因为**：

* GYD交易池是**冗余的**（提供多条不同的Gyro稳定币出入路径 ）。
* GYD交易池彼此**独立**（例如，如果其中一个资产配对失败，剩余的SAMM交易池仍然可以正常运作，不像Curve的单一池子）。

### GYD交易池赎回曲线示意

下图中所示的是GYD交易池赎回曲线，参考的是50-50 Uniswap池子的示例：

{% embed url="https://2063019688-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MU527HCtxlYaQoNazhF%2Fuploads%2FTXFFIZZ0G8SZks2SLRbx%2FGraph%201%20v3%20(1).png?alt=media&token=b86991ab-f819-400b-9f03-ad62a168d856" %}

GYD交易池设计包含了优化的联合曲线和虚拟储备机制。详情参考Github上的[这几篇论文](https://github.com/gyrostable/technical-papers/tree/main/E-CLP)
