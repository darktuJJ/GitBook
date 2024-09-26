---
description: 了解保护 GYD 收益分配流程的安全措施
---

# 安全性

储备收益的分配是一个对安全要求很高的流程。因此，实施了以下安全措施：

1. 链下程序没有能力自行触发收益的发放。相反，链下程序（由链上的 Distribution Submitter EOA 表示）只能将待处理的分配提交到链上的中间合约（DistributionManager）。如果没有进一步的操作，这次提交不会产生任何效果。
2. 要发放 GYD，待处理的分配必须由一个被称为分配执行者（Distribution Executor）的特定可信方进行确认。可信方调用 DistributionManager 的 `executeDistribution()` 方法（无需传递参数）。DistributionManager 是唯一有权从 GydDistributor 触发分配的地址，而 GydDistributor 是系统中唯一能够铸造新 GYD 的地址。
   * 目前，可信方是由 Gyroscope Foundation 控制的多重签名账户。
   * 将来，可信方将成为去中心化治理系统的一部分。
3. 待处理的分配可以公开查看，并且设置了时间锁：提交与分配执行之间必须至少间隔 5 分钟（参见 `DistributionManager.minExecutionDelay()`）；否则，执行将失败。这样做的目的是为审核提供一个受保护的时间窗口，并在提交密钥被泄露的情况下防止时机敏感的攻击。
4. GydDistributor 存储了一个场所白名单，只有白名单中的场所才可能接收收益发放。此白名单只能通过治理进行修改。
5. 对 GydDistributor 的调用始终发生在以太坊上，新的 GYD 也总是在以太坊上铸造。为了将收益分配到其他链上的场所，GydDistributor 会使用 Chainlink CCIP 内部处理跨链桥接。桥接过程的另一端由 L2Distributor 合约覆盖，该合约没有任何铸造 GYD 的能力。

该系统还实施了多种完整性检查，以防范可能试图制造过量收益发放的未知攻击向量。具体来说：

* 每次分配最多可以发放不超过 GYD 总供应量的 1%（参见 `GydDistributor.maxRate()`）。
* 在规定的时间间隔内，最多只能对同一场所进行一次分配（参见 `GydDistributor.minimumDistributionInterval()`）。在系统启动时，该间隔将设置为 1 小时；中期将设置为 24 小时。
* 对于 sGYD，流（参见下文）的参数不能出现异常情况；具体而言，流必须至少分配 1 GYD，时间框架必须在 1 小时到 5 年之间，并且最多只能有 10 个活跃或待处理的流。

sGYD 可以通过协议治理进行升级。Distributor 和 L2Distributor 合约不可升级。所有这些合约都遵循基于角色的访问控制模型，由治理系统担任管理员。

