# 行动分级

治理中采取的某些行动比其他行动更具影响力和风险。

为了反映这些不同的重要性，每个可以通过治理调用的功能都会被分配一个级别。目前，实施的级别包括：

| Tier                | Description                      |
| ------------------- | -------------------------------- |
| 低级（LOW）             | 小规模治理支出，微调                       |
| 中级（MEDIUM）          | 可能间接影响安全的参数/系统组件更改               |
| 高级（HIGH）            | 可能直接影响安全的参数/系统组件更改               |
| 核心（CORE）            | 影响整个系统的更改/本质上是升级                 |
| 高资金库（HIGH-TREASURY) | 类似于高级更改，但即使升级被禁用也不受影响。适用于大规模财政支出 |

一个级别包含以下信息：

* **proposalThreshold**：提出提案所需的最小投票权
* **quorum**：提案通过所需的最低法定人数
* **voteThreshold**：提案通过所需的最小赞成票比例
* **timeLockDuration**：时间锁的持续时间
* **proposalLength**：提案的长度
* **actionLevel**：该行动的“影响力”程度

分配级别是通过实现 **ITierStrategy** 完成的，具体取决于调用的功能。已实现的策略包括：

* **StaticTierStrategy**：无论参数如何，始终返回相同的级别。
* **SimpleThresholdStrategy**：根据某个参数是否超过给定的阈值来返回级别。
* **SetVaultFeesStrategy**：与 SimpleThresholdStrategy 类似，但比较两个参数与阈值的关系。
* **SetSystemParamsStrategy**：类似于 SimpleThresholdStrategy，但比较结构体中的多个字段与多个阈值。
* **SetAddressStrategy**：根据地址参数返回不同的级别。用于 **GyroConfig.setAddress**，该功能有权替换系统的某些部分。
