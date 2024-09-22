---
description: 如何定价n个资产的恒定乘积池（普通的Balancer池）：
---

# 恒定乘积

对于包含1，..., n个资产的给定Balancer池，定义如下：

&#x20;                           ![](<../../../.gitbook/assets/image (6).png>)

Balancer池的恒定乘积是指：

&#x20;                         ![](<../../../.gitbook/assets/image (9).png>)

请注意，这些金额"𝓇𝒾"易于操纵，但积"k[^1]"则不然。同时，因我们从其它地方获取资产的定价，所以我们可以假设价格"𝓅𝒾"也是不易操纵的(我们会在其他地方讨论防止价格操纵的措施）。

为了制造抗操纵的BPT预言机，只需用抗操纵的变量 $$w_i, p_i, k, S$$.来表达BPT代币的定价。

Balancer池的组合价值可以计算为：

&#x20;                                ![](<../../../.gitbook/assets/image (1) (2).png>)

然后，反过来，BPT价格可以计算为

&#x20;                             ![](<../../../.gitbook/assets/image (3) (1).png>)             &#x20;

[^1]: k
