# Problem 6 / 第 6 題

## 📖 Original Text / 原文

Suppose that $X$ is a Poisson random variable with $P(X = 1) = P(X = 3)$. Find $P(X = 5)$.

## 🇹🇼 Chinese Translation / 中文翻譯

假設 $X$ 是一個泊松隨機變數，且滿足 $P(X = 1) = P(X = 3)$。求 $P(X = 5)$。

## 💡 Detailed Explanation / 詳細解釋

### （一）本題涉及的機率分佈

本題直接使用 **Poisson 分佈（泊松分佈）**。題目中 $X$ 已明確宣告為 Poisson 隨機變數，但參數 $\lambda$ 未知。本題的核心任務是 **先利用給定的條件反推出 $\lambda$，再代入計算所求機率**。

這是一道「逆向工程」類型的題目——不是直接給你 $\lambda$ 讓你算機率，而是要你先從機率等式中解出 $\lambda$。

### （二）關鍵參數拆解

Poisson 分佈的機率質量函數為：
$$P(X = k) = \frac{e^{-\lambda} \lambda^k}{k!},\quad k = 0, 1, 2, \ldots$$

題目給定條件：
$$P(X = 1) = P(X = 3)$$

代入公式：
$$\frac{e^{-\lambda} \lambda^1}{1!} = \frac{e^{-\lambda} \lambda^3}{3!}$$

兩邊的 $e^{-\lambda}$ 可以消去（因為 $\lambda$ 是實數，$e^{-\lambda} > 0$），得到一個僅含 $\lambda$ 的代數方程。

### （三）解題概念提示

**步驟一：解出 $\lambda$**

從等式出發：
$$\frac{\lambda}{1!} = \frac{\lambda^3}{3!}$$

代入階乘值 $1! = 1$、$3! = 6$：
$$\lambda = \frac{\lambda^3}{6}$$

整理得：
$$\lambda^3 - 6\lambda = 0$$
$$\lambda(\lambda^2 - 6) = 0$$

這給出三個可能的解：$\lambda = 0$、$\lambda = \sqrt{6}$、$\lambda = -\sqrt{6}$。

但 Poisson 分佈的參數 $\lambda$ 必須是 **正實數**（$\lambda > 0$），因此：
$$\lambda = \sqrt{6}$$

（$\lambda = 0$ 會使所有機率集中在 $P(X=0)=1$，不符合 $P(X=1)=P(X=3)$ 的條件；負數則根本不合理。）

**步驟二：代入求 $P(X=5)$**

有了 $\lambda = \sqrt{6}$ 後，直接代入 Poisson 公式：
$$P(X = 5) = \frac{e^{-\sqrt{6}} \cdot (\sqrt{6})^5}{5!}$$

**思考要點：**
- 為什麼 $e^{-\lambda}$ 可以放心地從等式兩邊消去？（指數函數恆正）
- 為什麼 $\lambda = 0$ 被排除？（檢查：若 $\lambda = 0$，則 $P(X=1) = P(X=3) = 0$，形式上滿足等式，但實際上 Poisson 分佈定義中 $\lambda > 0$，且這種 degenerate case 通常不被視為有效的 Poisson 分佈）
- 這題展示了 Poisson 分佈的一個有趣特性：參數 $\lambda$ 並非必須是整數——事實上 $\lambda$ 是「平均發生次數」，可以是任何正實數。
- 如果條件改成 $P(X=2) = P(X=4)$，你會得到什麼 $\lambda$？（練習：$\lambda = \sqrt{12} = 2\sqrt{3}$）

## 🔢 Derivation Process / 推導過程

### Step 1: Write the Given Condition in Terms of the Poisson PMF

Let $X \sim \text{Poisson}(\lambda)$. The PMF is:

$$P(X = k) = \frac{e^{-\lambda} \lambda^k}{k!}, \quad k = 0, 1, 2, \ldots$$

The condition $P(X = 1) = P(X = 3)$ becomes:

$$\frac{e^{-\lambda} \lambda^1}{1!} = \frac{e^{-\lambda} \lambda^3}{3!}$$

### Step 2: Simplify by Canceling Common Factors

Since $e^{-\lambda} > 0$ for all real $\lambda$, we can divide both sides by $e^{-\lambda}$:

$$\frac{\lambda}{1!} = \frac{\lambda^3}{3!}$$

Substitute the factorial values $1! = 1$ and $3! = 6$:

$$\lambda = \frac{\lambda^3}{6}$$

### Step 3: Solve the Algebraic Equation for $\lambda$

Multiply both sides by $6$:

$$6\lambda = \lambda^3$$

Bring all terms to one side:

$$\lambda^3 - 6\lambda = 0$$

Factor out $\lambda$:

$$\lambda(\lambda^2 - 6) = 0$$

This yields three mathematical solutions:

$$\lambda = 0, \quad \lambda = \sqrt{6}, \quad \lambda = -\sqrt{6}$$

### Step 4: Apply Domain Constraints

For a Poisson distribution, the parameter $\lambda$ must be **strictly positive** ($\lambda > 0$), as it represents the expected number of occurrences (a mean rate).

- $\lambda = 0$ is degenerate: it gives $P(X = 0) = 1$ and $P(X = k) = 0$ for all $k \ge 1$, which would make $P(X=1) = P(X=3) = 0$ — technically satisfying the equation but not a meaningful Poisson distribution.
- $\lambda = -\sqrt{6}$ is negative and invalid.

Therefore, the only valid parameter is:

$$\lambda = \sqrt{6} \approx 2.44949$$

### Step 5: Compute $P(X = 5)$ with $\lambda = \sqrt{6}$

Substitute into the Poisson PMF:

$$P(X = 5) = \frac{e^{-\sqrt{6}} \cdot (\sqrt{6})^5}{5!}$$

### Step 6: Simplify the Expression

First, simplify $(\sqrt{6})^5$:

$$(\sqrt{6})^5 = (\sqrt{6})^4 \cdot \sqrt{6} = (6^2) \cdot \sqrt{6} = 36\sqrt{6}$$

And $5! = 120$, so:

$$\frac{(\sqrt{6})^5}{5!} = \frac{36\sqrt{6}}{120} = \frac{3\sqrt{6}}{10}$$

Thus:

$$P(X = 5) = e^{-\sqrt{6}} \cdot \frac{3\sqrt{6}}{10}$$

### Step 7: Numerical Evaluation

Using $\sqrt{6} \approx 2.44949$:

\begin{align*}
e^{-\sqrt{6}} &\approx e^{-2.44949} \approx 0.086294 \\[4pt]
\frac{3\sqrt{6}}{10} &\approx \frac{3 \times 2.44949}{10} \approx 0.734847 \\[4pt]
P(X = 5) &\approx 0.086294 \times 0.734847 \approx 0.06340
\end{align*}

### Step 8: Final Answer

$$\boxed{P(X = 5) = e^{-\sqrt{6}} \cdot \frac{3\sqrt{6}}{10} \approx 0.0634}$$
