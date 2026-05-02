# Problem 4 / 第 4 題

## 📖 Original Text / 原文

Suppose that $2.5\%$ of the population of a town are illegal immigrants. Find the probability using Poisson random variable approximation that, in a theater of this town with $80$ random viewers, there are at least two illegal immigrants.

## 🇹🇼 Chinese Translation / 中文翻譯

假設某個城鎮有 $2.5\%$ 的人口是非法移民。在一間電影院中，隨機選取 $80$ 位觀眾，使用泊松隨機變數近似法，求其中至少有兩位非法移民的機率。

## 💡 Detailed Explanation / 詳細解釋

### （一）本題涉及的機率分佈

本題的核心是 **Poisson 分佈（泊松分佈）**。題目明確要求「使用泊松隨機變數近似法」，但背後實際上涉及的是從 **Binomial 分佈到 Poisson 分佈的近似**。

原本的問題情境是：從一個「非法移民比例為 $p = 0.025$」的母體中，隨機抽取 $n = 80$ 位觀眾，計算其中非法移民人數的機率。這實際上是一個典型的 **二項分佈（Binomial distribution）** 問題，即 $X \sim \text{Binomial}(n=80,\ p=0.025)$。

然而，當 $n$ 很大、$p$ 很小（$n \to \infty$ 且 $p \to 0$，而 $np$ 保持在一個適中的常數）時，二項分佈可以用 Poisson 分佈來近似，這就是著名的 **Poisson 極限定理（Law of Rare Events）**。

### （二）關鍵參數拆解

- **$n = 80$**：樣本大小（電影院觀眾數）
- **$p = 0.025 = 2.5\%$**：每位觀眾是非法移民的機率（單次試驗成功機率）
- **$\lambda = np = 80 \times 0.025 = 2$**：Poisson 分佈的參數（即期望值），代表這 80 位觀眾中，非法移民的「平均人數」
- **題目所求**：$P(X \ge 2)$，即至少有 2 位非法移民的機率

因此，近似的 Poisson 隨機變數為：
$$X \sim \text{Poisson}(\lambda = 2)$$

其機率質量函數為：
$$P(X = k) = \frac{e^{-\lambda} \lambda^k}{k!},\quad k = 0, 1, 2, \ldots$$

### （三）解題概念提示

要計算「至少兩位」非法移民的機率 $P(X \ge 2)$，直接計算無窮級數並不實際。標準技巧是使用 **補集法（complement rule）**：

$$P(X \ge 2) = 1 - P(X \le 1) = 1 - \big[P(X=0) + P(X=1)\big]$$

也就是說，你只需要計算 **沒有人是非法移民** 以及 **恰好有一人是非法移民** 這兩種情況的機率，然後用 1 減去它們的和即可。

**思考要點：**
- Poisson 分佈中 $\lambda = 2$ 時，$P(X=0)$ 和 $P(X=1)$ 分別是多少？
- 為什麼 $n=80$、$p=0.025$ 的情況適合用 Poisson 近似？（提示：$n$ 足夠大、$p$ 足夠小、$np$ 適中）
- 如果不用近似而用精確的二項分佈計算，結果會有多接近？

## 🔢 Derivation Process / 推導過程

### Step 1: Identify the Distribution and Parameters

The problem describes a binomial scenario: $n = 80$ independent trials (viewers), each with success probability $p = 0.025$ (being an illegal immigrant). The exact distribution is:

$$X_{\text{binomial}} \sim \text{Binomial}(n = 80,\ p = 0.025)$$

We approximate using the **Poisson distribution** with parameter:

$$\lambda = np = 80 \times 0.025 = 2$$

So our working distribution is:

$$X \sim \text{Poisson}(\lambda = 2)$$

### Step 2: Apply the Complement Rule

We want $P(X \ge 2)$. Rather than summing an infinite series, we use the complement:

$$P(X \ge 2) = 1 - P(X \le 1) = 1 - \big[P(X = 0) + P(X = 1)\big]$$

### Step 3: Compute $P(X = 0)$

Using the Poisson PMF $P(X = k) = \dfrac{e^{-\lambda} \lambda^k}{k!}$:

$$P(X = 0) = \frac{e^{-2} \cdot 2^0}{0!} = e^{-2}$$

### Step 4: Compute $P(X = 1)$

$$P(X = 1) = \frac{e^{-2} \cdot 2^1}{1!} = 2e^{-2}$$

### Step 5: Assemble the Final Probability

\begin{align*}
P(X \ge 2) &= 1 - \big(e^{-2} + 2e^{-2}\big) \\
&= 1 - 3e^{-2}
\end{align*}

### Step 6: Numerical Approximation

Using $e^{-2} \approx 0.135335$:

\begin{align*}
P(X \ge 2) &= 1 - 3(0.135335) \\
&= 1 - 0.406005 \\
&= 0.593995 \\
&\approx 0.5940
\end{align*}

### Step 7: Comparison with Exact Binomial (Optional)

For verification, the exact binomial probability is:

$$P_{\text{binomial}}(X \ge 2) = 1 - (0.975)^{80} - 80 \cdot (0.025) \cdot (0.975)^{79}$$

This evaluates to approximately $0.5947$, confirming the Poisson approximation is very close (error $\approx 0.0007$), which is expected since $n$ is large, $p$ is small, and $\lambda = 2$ is moderate.

### Step 8: Final Answer

$$\boxed{P(X \ge 2) = 1 - 3e^{-2} \approx 0.5940}$$
