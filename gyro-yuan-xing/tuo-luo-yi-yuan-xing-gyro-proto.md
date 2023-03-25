---
description: Gyro Proto是Gyroscope稳定币系统的测试版。
---

# 陀螺仪原型(Gyro Proto)

我可以在哪里使用并测试它？

{% hint style="info" %}
[https://app.gyro.finance/dsm/](https://app.gyro.finance/dsm/)
{% endhint %}

## Gyro Proto实施

Gyro Proto（p-GYD）是Gyroscope稳定币系统的测试版。在完整的Gyroscope在以太坊上推出之前，它以一种保守的形式在Polygon上发布用于测试目的。

在2023年第一季度之后，Proto系统将继续作为测试未来协议更新的平台。用户可以继续使用Proto系统，但将被鼓励在以太坊上的最终协议发布之前撤出资产。

{% embed url="https://lh4.googleusercontent.com/BksD8MLIr3jc5GkDDekDOzJiUtsZ0ocyW4NUTLlxAmnqAmkVndu_pzM4gxcOV3NkzCT2NNcdM72CHEt3xAbPhraPPg4gT8eHH-ztKhWIeMrdbpzvexePgG2NCD_bLXDgszUE6JAfLlkzWuG6E2wnbBHwZAvNLEECkrI2dmwHkeeRgR9Lu4IT7EOO1-vKVg" %}

### Gyro Proto

### 的目标

Gyro Proto发布的目的是在实际环境中测试协议，特别是在生产环境中测试智能合约及其交互。经过测试期后，目标是将经过校准和测试的合约代码交给Gyroscope治理，以便根据其决定启动最终系统。

考虑到目标仅限于一定时期内的代码测试，Gyro Proto在Polygon上被校准为简单易用。这意味着它并非特意针对重要目标（如长期经济韧性）进行校准，并不一定代表完整系统的校准方式。

在Gyro Proto校准中需要强调的一个方面是储备资产的选择。考虑到以下因素，选择了一个简单的储备结构：

1. 在Polygon上可供选择的流动性合理的资产数量有限。
2. 希望在储备中测试2-CLP、3-CLP和E-CLP流动性池。
3. 希望在各种储备比率状态下测试系统。

因此，Gyro Proto的储备使用其他稳定币组成的简单的2-CLP、3-CLP和E-CLP流动性池进行初始化。其中大部分流动性池早先已经被用于CLP测试。最终系统的储备资产选择将受到Gyroscope治理的批准。

储备还启用了少量的WETH。原因是为了使储备比率在短期内波动，以便在更广泛的环境中测试系统功能。虽然在长期内，储备中的稳定币价格可能会偏离1美元，但在短期内这种可能性很小。因此，WETH的包含使得可以在不同的储备比率情况下测试代码。

### 资产上限

Gyro Proto是一个受保护的系统，具有资产上限以限制风险。为了进行测试，单个地址仅能贡献一定数量的资产（10美元）。用户可能可以被加入受保护的白名单以获得更高的资产上限，但对于大多数用户而言，这并不建议，也没有预期的好处。Gyro Proto还设有总资产上限，为10万美元。

### Gyro Proto合约的可升级性

在Gyro Proto中，智能合约首次在真实环境中进行测试。虽然这些合约已经经过审计，但代码漏洞的风险无法完全消除。因此，社区和FTL Labs的开发团队（[更多信息](https://snapshot.org/#/gyrodao.eth/proposal/QmeMYwoCCEhSk8E7BNshU2XeSD91RVdLrkkv3mSV2EApTe)）必须能够迅速解决可能发现的智能合约问题。出于这个原因，FTL Labs将暂时保留对Proto系统参数、协议更新和设计决策的控制权。

在Gyroscope治理启动后，对Gyroscope合约的更新必须由Gyroscope治理执行。这对于将Gyroscope作为去中心化协议推出是非常重要的。

### 使用Gyro Proto的风险

使用Gyro Proto也具有一定的风险，包括以下方面：

* **智能合约风险：**与任何智能合约系统一样，存在潜在风险，即漏洞或错误可能会使承诺的资产面临风险。这种风险可以通过进行代码审计和测试来降低，但无法完全消除。
* **储备资产的风险：**Gyroscope系统是由储备资产支持的，这些资产可能包括其他稳定币、AMM池中的LP份额和其他代币。每种资产都有自己的风险，不能保证Gyroscope储备资产始终具有足够的价值来完全支持系统。例如，在此[文献](https://arxiv.org/abs/2006.12388)中详细描述了稳定币的风险。此外，由于这些资产在Polygon区块链上，因此它们也可能带有从其他链上跨链桥的风险。更多有关LP风险的信息可在CLP文档中找到。尽管这些资产的风险已经被研究过了（例如提供的链接），但是加密货币仍然是一个新兴领域，风险可能尚未完全被理解。如上所述，Gyro Proto将WETH作为储备资产，参与Gyro Proto涉及一定的ETH风险。由于ETH的波动性，系统在测试期间可能会出现储备不足的情况。
* **价格预言机风险：**Gyroscope系统依赖于一套价格预言机系统，以从链外市场导入资产定价信息并从链上市场读取定价信息。有时，这些预言机可能会提供错误信息或被操纵，这可能会导致储备资产的系统损失。例如，这篇[论文](https://arxiv.org/abs/2006.12388)和[预言机系统规范](https://github.com/gyrostable/technical-papers/blob/main/Consolidated%20Price%20Feed%20and%20Circuit%20Breakers/Design%20of%20the%20Consolidated%20Price%20Feed%20and%20Circuit%20Breaker%20System.pdf)进一步描述了预言机风险。虽然Gyroscope设计试图减轻预言机风险，但仍然存在一些残留风险。
* **使用DSM的风险：**DSM定义了系统的货币政策，即如何使用储备资产来维持稳定币的锚定。 DSM的设计旨在在维持锚定的同时，在储备资产遭受冲击且系统处于不足储备的情况下保留储备资产。根据DSM的设计（并且在链上透明），不能保证用户能够在任何时候以接近锚定价格的价值从系统中赎回GYD。除了由于储备资产的波动导致的回撤风险外，DSM可能导致储备价值的额外回撤。 DSM的货币政策旨在在系统不足储备的情况下允许一定程度的接近稳定币锚定的赎回，这将消耗后续赎回所需的整体储备比例。此额外回撤取决于系统在不足储备的情况下经历的流入和流出的水平以及DSM的校准。DSM的设计是由DSM参数界定的，如[DSM技术论文](https://github.com/gyrostable/technical-papers/blob/main/P-AMM/P-AMM%20technical%20paper.pdf)所述。
* **合约升级风险：**由于Gyro Proto合约可升级，因此系统存在升级风险，这意味着智能合约代码可能会随着时间的推移而发生变化。虽然升级旨在解决可能出现的代码漏洞，但是升级也可能引入新的漏洞，导致智能合约风险。
* **区块链基础设施风险：**由于Gyro Proto合约部署在Polygon PoS区块链上，与智能合约的任何交互都会继承Polygon PoS区块链的风险。
* **用户界面和区块链交互风险：**当用户通过Gyro Proto Web用户界面与Gyro Proto系统交互时，他们会面临技术风险。虽然Gyro Proto UI已经经过仔细审查以避免错误和漏洞，但这些不能完全排除。UI错误可能会导致生成不正确的交易，或者UI可能变得不可用。用户自己的IT设置（例如Web浏览器，钱包软件）也可能包含错误和漏洞。

_**以上任何风险都可能导致用户资产的部分或全部丧失。**_

