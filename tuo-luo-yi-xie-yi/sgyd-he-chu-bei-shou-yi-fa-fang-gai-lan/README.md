---
description: sGYD（储蓄型 GYD）和收益发放概述
---

# sGYD 和储备收益发放概览

_免责声明：_&#x20;

_以下关于sGYD和Reserve收益发放的信息仅供参考，不应被视为财务建议。用户在与sGYD进行交互之前，应进行深入研究并咨询财务、法律和技术顾问。每位参与者有责任了解sGYD的风险，并遵守其所在司法管辖区的所有适用法律和法规。sGYD在美国、英国和其他特定司法管辖区不可用。更多信息请参阅服务条款。_

**sGYD 和储备收益发放**

支持 GYD 稳定币的储备资产可以为其基础资产产生收益。由于 GYD 和 Gyroscope 协议是去中心化的，这些收益会保留在协议内。协议的设计使得大部分收益可以发放给在以下两类场所中质押 GYD 的用户：

1. GYD 的收益型代币 sGYD
2. GYD 与其他资产交易的某些流动性池，储备收益以新铸造的 GYD 形式发放给用户。

### 通过 sGYD 赚取储备收益

**sGYD** 是 GYD 稳定币的收益型代币，遵循标准的收益型保险库设计（ERC4626）。这意味着用户可以随时将 GYD 存入或从 sGYD 中取出，并且在 GYD 存入 sGYD 期间将产生收益。sGYD不采用rebase机制（即不会重新调整余额），而是通过存取款汇率的自动增长来反映发放给 sGYD 持有者的收益。随着时间的推移，sGYD 的存取汇率会自动上升，反映已发放的收益。sGYD 可在无需许可的情况下进行转移。

用户可以通过两种方式与 sGYD 进行交互：

1. **直接链上交互**：通过 ERC4626 标准的函数与 sGYD 交互。
2. **前端 UI 交互**：通过像 gyro.finance 上托管的用户界面进行交互，受限于适用的使用条款和服务条款（请参阅上方免责声明）。

关于sGYD收益如何精确计算和发放的详细信息，请参见下文。

### 在 GYD 池中作为流动性提供者（LP）赚取储备收益

持有包含 GYD 的 AMM 池份额的流动性提供者，可以在其持有的 GYD 部分上赚取储备收益。为此，他们需要将其 LP 份额存入相应的 Balancer gauge。这可以直接在链上完成，或者通过任何支持的前端，例如 gyro.finance 上托管的用户界面或 balancer.fi 上的用户界面。对于支持的资金池，GYD 会像 BAL 奖励一样累积为奖励代币，奖励可以随时领取。

并非所有 GYD 池都有资格参与这样的储备收益发放（请参阅下方的“支持场所”）。合资格的资金池集合由协议治理决定。

下方将提供有关资金池收益的具体计算和发放方式的详细信息。

{% content-ref url="shou-yi-fa-fang-guo-cheng.md" %}
[shou-yi-fa-fang-guo-cheng.md](shou-yi-fa-fang-guo-cheng.md)
{% endcontent-ref %}

{% content-ref url="an-quan-xing.md" %}
[an-quan-xing.md](an-quan-xing.md)
{% endcontent-ref %}

{% content-ref url="../shen-ji-bao-gao-1.md" %}
[shen-ji-bao-gao-1.md](../shen-ji-bao-gao-1.md)
{% endcontent-ref %}

{% content-ref url="feng-xian.md" %}
[feng-xian.md](feng-xian.md)
{% endcontent-ref %}

