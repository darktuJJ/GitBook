---
description: 探索 sGYD 的内部发放和兑换率机制
---

# sGYD 内部机制

本部分解释 sGYD 的一些内部操作。大多数用户可能不需要关心这些细节；他们可以简单地使用 ERC4626 接口或 UI 与 sGYD 进行交互。例如，`convertToAssets(1e18)` 将返回当前 sGYD/GYD 的兑换率。

发放给 sGYD 的收益存储在名为“stream”的结构中。stream 包含发放的金额以及开始和结束的时间戳。相应的金额在开始和结束时间之间线性发放。可以通过 `streams()` 方法查询所有活跃和待处理的 stream。已过期的 stream 会定期被清理。

sGYD 始终持有存入的 GYD 总量，包括用户存入的部分和 stream 中的部分。如果有活跃的 stream，其中一部分金额被视为待发放（未发放）。这一金额可以通过 `totalPendingAmount()` 方法查询。ERC4626 方法 `totalAssets()` 返回当时可以提取的总金额，等于 `GYD.balanceOf(sGYD) - sGYD.totalPendingAmount()`。兑换率等于 `convertToAssets(ONE) = totalAssets() / totalSupply()`（所有操作均应为 18 位小数的定点数）。
