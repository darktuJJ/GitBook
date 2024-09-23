---
description: Balancer池LP代币（BPT）定价的方法和实现。
---

# LP份额定价

对于 LP 代币的定价，简单地将池中所有资产的价值相加是不够的，因为这很容易被操纵。相反，需要一个更稳健的流程来计算 LP 代币的价值。

{% hint style="info" %}
关于如何计算 2-CLP、3-CLP 或 E-CLP 的 LP 份额的具体说明，请参见[本技术文件的第 5 节](https://github.com/gyrostable/technical-papers/blob/main/Consolidated%20Price%20Feed%20and%20Circuit%20Breakers/Design%20of%20the%20Consolidated%20Price%20Feed%20and%20Circuit%20Breaker%20System.pdf)。
{% endhint %}

### **示例：恒定乘积池**&#x20;

这个例子展示了应用于恒定乘积池的稳健LP份额定价原则。 对于包含资产1, ..., n的给定恒定乘积Balancer池，定义如下：

$$
\begin{align*}
w_i &= \text{weight of asset } i \\
r_i &= \text{amount (in \# tokens) of asset } i \\
p_i &= \text{price of asset } i \\
S &= \text{total \# LP tokens}
\end{align*}
$$

池的恒定乘积不变量是：

$$
L = \prod_{i=1}^{n} r_i^{w_i}
$$

请注意，数量 _ri_ 可以通过交换轻易被操纵，但乘积 L 则不能。而且，由于我们在其他地方需要资产定价预言机，我们可以假设价格 pi 也不容易被操纵（防止这种情况的控制措施将在其他地方讨论）。

要计算抗操纵的 LP 代币价格，只需用抗操纵变量 wi、pi 和 L/S 来表示 LP 代币的定价就足够了。请注意，虽然 L 和 S 单独可以通过添加或移除流动性来操纵，但只要有适当的会计方法来处理流动性的添加和移除，L/S 就不容易被操纵（详见技术论文第 5.5 节）。



整个池的投资组合价值可以计算为：



$$
\text{Pool value} = L \prod_{i=1}^{n} \left( \frac{p_i}{w_i} \right)^{w_i}
$$

**进而，LP代币价格可以用抗操纵变量表示为：**



$$
p_{LP \, \text{token}} = \frac{\text{Pool value}}{S} = \frac{L}{S} \prod_{i=1}^{n} \left( \frac{p_i}{w_i} \right)^{w_i}
$$



**2-CLP、3-CLP和E-CLP的LP代币定价** CLP的LP份额定价遵循相同的一般原则，在以下技术论文的第5节中有详细描述。

{% embed url="https://github.com/gyrostable/technical-papers/blob/main/Consolidated%20Price%20Feed%20and%20Circuit%20Breakers/Design%20of%20the%20Consolidated%20Price%20Feed%20and%20Circuit%20Breaker%20System.pdf" %}
