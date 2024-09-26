# 关联 DAO 金库

由于 DeFi 的可组合性，有时一个协议中的操作会直接或间接影响到另一个协议。因此，赋予这些协议在治理过程中发言权是合理的。

在 Gyroscope 的治理系统中，关联 DAO 金库允许治理为其他 DAO 分配投票权。通过调用 `FriendlyDAOVault.updateDAOAndTotalWeight` 来完成这一操作。

每个 DAO 在金库中的成员将拥有金库总投票权的一部分。治理系统可以决定是否将某个 DAO 添加或移除出该金库。

**哪些 DAO 参与其中？**

[Balancer](https://balancer.fi/)、[Aura](https://aura.finance/) 和 [BeethovenX](https://beets.fi/) 的 DAO 将成为关联 DAO 金库的初始成员。
