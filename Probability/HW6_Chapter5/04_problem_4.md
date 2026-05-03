# Problem 4 / 第 4 題

## 📖 Original Text / 原文

Suppose that 2.5% of the population of a town are illegal immigrants. Find the probability using Poisson random variable approximation that, in a theater of this town with 80 random viewers, there are at least two illegal immigrants.

## 🇹🇼 Chinese Translation / 中文翻譯

假設某個城鎮中有 2.5% 的人口為非法移民。在一間有 80 位隨機觀眾的劇院中，使用卜瓦松隨機變數近似法，求其中至少有兩位非法移民的機率。

## 💡 Detailed Explanation / 詳細解釋

### (1) 涉及的機率分佈

本題要求使用 **卜瓦松近似（Poisson Approximation）**。原始情境是一個二項分佈問題：從城鎮中隨機抽取 $n = 80$ 位觀眾，每位觀眾是非法移民的機率為 $p = 0.025$（即 2.5%）。令 $X$ 表示這 80 人中非法移民的人數，則 $X \sim \text{Binomial}(n=80,\ p=0.025)$。

然而，當 $n$ 夠大且 $p$ 夠小時，二項分佈 $\text{Binomial}(n, p)$ 可以用卜瓦松分佈 $\text{Poisson}(\lambda)$ 來近似，其中 $\lambda = np$。這正是本題的核心技巧。

### (2) 關鍵參數分析

| 參數 | 符號 | 數值 | 說明 |
|------|------|------|------|
| 樣本數 | $n$ | 80 | 劇院中的觀眾人數 |
| 成功機率 | $p$ | 0.025 | 單一觀眾為非法移民的機率 |
| 卜瓦松參數 | $\lambda$ | $np = 80 \times 0.025 = 2$ | 期望非法移民人數 |
| 目標 | — | $P(X \geq 2)$ | 至少有兩位非法移民 |

由於 $n=80$ 不算極大、$p=0.025$ 也不算極小，使用卜瓦松近似會有一定誤差，但本題明確要求使用此方法。

### (3) 解題思路提示

- **第一步**：計算 $\lambda = np = 2$，因此 $X \stackrel{\text{approx}}{\sim} \text{Poisson}(\lambda = 2)$。
- **第二步**：將「至少兩位」轉換為補集運算：$P(X \geq 2) = 1 - P(X = 0) - P(X = 1)$。
- **第三步**：利用卜瓦松機率質量函數（PMF）：

$$P(X = k) = \frac{e^{-\lambda} \lambda^k}{k!}$$

分別計算 $P(X=0)$ 和 $P(X=1)$：

$$P(X = 0) = \frac{e^{-2} \cdot 2^0}{0!} = e^{-2}$$

$$P(X = 1) = \frac{e^{-2} \cdot 2^1}{1!} = 2e^{-2}$$

- **第四步**：代入補集公式：$P(X \geq 2) = 1 - e^{-2} - 2e^{-2} = 1 - 3e^{-2}$。

> 💡 **提示**：$e^{-2} \approx 0.1353$，可進一步計算數值結果。注意，若用精確的二項分佈計算，結果會略有不同，但本題指定使用卜瓦松近似，請務必遵循題意。

## 🔢 Derivation Process / 推導過程

### 步驟 1：確定卜瓦松參數 $\lambda$

原始情境為二項分佈 $X \sim \text{Binomial}(n=80,\ p=0.025)$。根據卜瓦松近似，當 $n$ 夠大且 $p$ 夠小時：

$$\lambda = np = 80 \times 0.025 = 2$$

因此 $X \stackrel{\text{approx}}{\sim} \text{Poisson}(\lambda = 2)$。

### 步驟 2：轉換為補集機率

「至少兩位非法移民」即 $X \geq 2$。利用補集運算：

$$P(X \geq 2) = 1 - P(X = 0) - P(X = 1)$$

### 步驟 3：代入卜瓦松 PMF

卜瓦松分佈的機率質量函數（PMF）為：

$$P(X = k) = \frac{e^{-\lambda} \lambda^k}{k!}$$

分別計算 $k = 0$ 與 $k = 1$：

$$
\begin{aligned}
P(X = 0) &= \frac{e^{-2} \cdot 2^0}{0!} = e^{-2} \\[6pt]
P(X = 1) &= \frac{e^{-2} \cdot 2^1}{1!} = 2e^{-2}
\end{aligned}
$$

### 步驟 4：合併計算

$$
\begin{aligned}
P(X \geq 2) &= 1 - P(X = 0) - P(X = 1) \\
&= 1 - e^{-2} - 2e^{-2} \\
&= 1 - 3e^{-2}
\end{aligned}
$$

### 步驟 5：數值代入

查表或計算 $e^{-2}$ 的近似值：

$$e^{-2} \approx 0.135335$$

代入：

$$
\begin{aligned}
P(X \geq 2) &= 1 - 3 \times 0.135335 \\
&= 1 - 0.406006 \\
&= 0.593994
\end{aligned}
$$

### 📦 最終答案

$$
\boxed{P(X \geq 2) \approx 0.5940}
$$

> 即：在 80 位隨機觀眾中，至少有兩位非法移民的機率約為 **59.40%**。
