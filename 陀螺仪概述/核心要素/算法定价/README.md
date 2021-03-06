---
description: 市场与价格结构
---

# 算法定价

Gyroscope 使用**两种不同的自动化做市商类型**。

* **一级市场自动做市**（PAMM）设计，用于提供稳定币的铸币和赎回报价 （需把标的资产可能受到的冲击纳入计算中）。
* **多个二级市场自动做市**（SAMMs），通过定制 Balancer v2 池，将流动性集中在 PAMM 的价格范围内。

{% hint style="info" %}
**一级市场**和**二级市场**的术语是从传统金融中借用的，一级市场指的是 "发行市场"，二级市场指的是 "交易市场"（例如在ETF中）。
{% endhint %}

### 市场间的相互作用

SAMMs各自将流动性集中在 PAMM 为**储备资产—Gyro稳定币对**提供的价格范围内。它们保证了Gyro稳定币有着高流动性的出入渠道。SAMMs 也是相互独立的：如果一个SAMM中的配对资产崩溃，其余的池仍然可以运作，而不像当前那些只采用一个公共AMM池的设计。SAMMs将形成一个连接池网络的中心，提供高效的交易路径。一些陀螺仪储备金库将把资产部署到增强这个网络的资金池中，其他现有的AMM池将与SAMMs中的交易对相连接。

这种设计的一个特点是，它引入了一个挂钩协调机制。这个机制在促进锚定价格附近流动性的同时，也可以在协调失效时通过一个断路器来抵御投机狙击和挤兑。

{% embed url="https://2063019688-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MU527HCtxlYaQoNazhF%2Fuploads%2F7VmlNzsOSqijj9cjFuLR%2FSAMM%20and%20Reserve%20Pools%20Graphic.png?alt=media&token=829dac44-5425-4491-ba4b-9d12cf798eb3" %}
