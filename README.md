---
cover: >-
  https://docs.gyro.finance/~gitbook/image?url=https%3A%2F%2F3407769812-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-MU527HCtxlYaQoNazhF%252Fuploads%252FYSvrJBGMzQ3jJcoKC1JS%252FDiscord%2520Invite%2520Image.jpg%3Falt%3Dmedia%26token%3De712845c-6789-4613-8054-ba4d158f74f1&width=768&dpr=2&quality=100&sign=837e69a0&sv=1
coverY: 0
---

# tldr: 什么是 Gyroscope

_Gyroscope 的非技术性概述_

Gyroscope 是一个去中心化的稳定币，采用了新颖的全天候稳定币设计，结合了更高效的稳定币流动性池。

### Gyro Dollars（GYD）

Gyroscope 的稳定币 **Gyro Dollars（GYD）**，旨在由一篮子资产完全支撑，并在协议层面内置了创新的风险控制机制。GYD 的设计旨在分离并控制来自各类资产的风险，具体包括：

* **自动化的风险分散规则**
* **优化的铸造和赎回曲线**，指导协议如何使用储备资产来维持稳定
* **全新的弹性预言机和断路器系统**，用于应对压力

GYD 的设计是为了防范持有稳定币的主要风险，通过去中心化、无托管的方式，将风险控制高度自动化。它为稳定币持有者提供了稳健的风险控制层。GYD 致力于成为链上最安全的稳定资产，遵循了这些设计原则。

### E-CLPs

Gyroscope 的 **E-CLPs**（椭圆集中流动性池，Elliptic Concentrated Liquidity Pools）是一种新型的流动性池，能够实现流动性的非对称集中。E-CLPs 沿着椭圆曲线聚焦资产交易。

E-CLPs 相比其他流动性池类型有以下几个优势：

* **效率提升高达 75%**：E-CLPs 比 Stableswap 流动性池高效 75%，极大的提高了流动性提供者（LP）的资本效率。
* **高度可定制**：允许更高的灵活性，流动性不再需要在统一的价格范围内平均分布。
* **无需主动管理**：E-CLPs 不需要主动的头寸管理，并可自动适应收益累积的资产。池部署者在启动时负责校准和设定交易参数。

E-CLPs 将集中流动性打包成一种可定制和被动的形式。

### GYD 和 E-CLPs 的结合

GYD 和 E-CLPs 是相辅相成的。虽然 E-CLPs 在 GYD 之外也有应用场景，但它们之间紧密集成，共同实现以下目标：

* **增强 GYD 的稳定性**：为 GYD 优化的 E-CLP 交易池在锚定价格附近提供更多流动性。这得益于协议的铸造和赎回机制的支持。
* **更高效的抵押品**：使用 LP 份额作为支持 GYD 的更高效的抵押品类别。E-CLPs 被用作储备资产的收益策略。

从长远来看，LST E-CLPs 中的 LP 头寸可以被整合到 GYD 的杠杆机制中。这将允许以 E-CLPs 产生的高效收益型抵押品类型为抵押，**借入 GYD**。

最后，GYD 在启动时配备了一个特殊的\*\*“引导 E-CLP”\*\*，这是在协议层面实现的，为获取 GYD 提供了一种初始的简化方式。这个引导池通过使用 sDAI 作为储备资产进行交换，提供了预设数量的 GYD 可被“铸造”。这为直接用储备资产铸造提供了一种更直接的替代方案，后者是一个复杂的过程，预计未来将由资深的做市商进行。引导池中的 sDAI 储备将在后期转入更广泛的 Gyroscope 储备中。
