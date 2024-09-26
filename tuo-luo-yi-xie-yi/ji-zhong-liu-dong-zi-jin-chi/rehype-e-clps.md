---
description: 可以说，这些 E-CLP 将不对称的集中流动性与向借贷市场的自动再抵押相结合，是资本效率最高的资金池。
---

# Rehype E-CLPs

<figure><img src="../../.gitbook/assets/Boosted-E-CLPs (1).gif" alt=""><figcaption><p>Rehype 资金池将多个收益来源合并为一个资金池。</p></figcaption></figure>

### Rehype E-CLP 简介

Gyroscope 的 Rehype 资金池通过将不对称集中流动性与自动再抵押（rehypothecation）到借贷协议相结合，双重提升了资本效率，从而增加了流动性提供者（LP）的收益。这种设计允许 LP 在多个收益来源中获取收益，包括集中流动性的交易收益、借贷收益以及代币激励市场的收益，形成三重收益。

Rehype 资金池通过直接在资金池资产层面引入借贷存款（如 Aave 上的 aUSDC）来实现这一点，借贷存款和基础资产之间的转换由前端和智能订单路由（SOR）处理。Gyroscope 的 Rehype 资金池避免了“池上池”架构的复杂性，在智能合约层面不引入任何超出 E-CLP 的额外复杂性，而是将复杂性处理放在更灵活的 SOR 和前端设计层。这使得 Rehype 资金池相比其他资金池设计更安全，因为其继承了 E-CLP 的安全记录，仅增加了 Aave 相关的风险。

Rehype 资金池将多个收益来源合并为一种形式，LP 通过持有资金池份额，不仅能获取收益，还能将其作为有效的抵押品用于其他协议。同时，这些资金池中的再抵押过程透明且由用户控制，这与传统金融中常见的复杂再抵押实践形成对比，避免了相关问题。

<figure><img src="../../.gitbook/assets/image (6) (1).png" alt=""><figcaption><p>Rehype 池将众多收益来源合而为一</p></figcaption></figure>

### GYD 和 Rehype 资金池

GYD Rehype 资金池促进了为去中心化稳定币扩展更具风险调整能力的收益来源，特别是在一个由中心化参与者日益主导的市场中。Rehype 资金池通过将去中心化的收益来源层层叠加，消除了机会成本，从而降低了 GYD 流动性的资本成本。这种设计使得 GYD 在保持去中心化的同时，能够通过更高效的方式获取稳定收益，增强其在市场中的竞争力。

### Rehype E-CLP 风险

使用 Rehype E-CLP 存在一定风险，包括 E-CLP 本身的风险（智能合约风险、策略风险和不利选择风险）以及再抵押（rehypothecation）风险（如 Aave 的相关风险）。值得注意的是，Rehype 资金池采用简单、模块化的设计，旨在尽量减少智能合约风险，并且不会为再抵押引入新的智能合约代码。

**再抵押风险：**

进入 Rehype 资金池后，流动性提供者（LPers）承诺将其 LP 资产部署到借贷协议（如 Aave）。像 Aave 这样的借贷协议具有其自身的风险，包括：

* **智能合约风险**
* **流动性风险**
* **破产风险**
* **预言机风险**
* **治理风险**

借贷协议在不同链上的部署风险也可能有所不同。例如，Aave 在某条链上的流动性水平会影响流动性提供者将其资产提取为基础资产的能力，尽管提取为 Aave 存款代币不受此影响。

和 DeFi 中的每一个创新项目一样，用户应自行进行研究，并评估相关 Aave 借贷市场的风险性。Rehype 资金池确保所有操作在链上完全透明，并赋予用户对其策略选择的控制权。
