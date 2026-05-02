# Problem 2 / 第 2 題

## 📖 Original Text / 原文

2. A certain basketball player makes a successful foul shot with probability 0.45. Determine for what value of $k$, the probability of $k$ baskets in 10 shots is maximum, and then find this maximum probability.

## 🇹🇼 Chinese Translation / 中文翻譯

某位籃球選手罰球命中的機率為 0.45。請判斷在 10 次投籃中，命中 $k$ 球的機率在 $k$ 取何值時達到最大，並求出此最大機率。

## 💡 Detailed Explanation / 詳細解釋

### (1) 涉及的機率分佈

本題同樣屬於 **二項分佈（Binomial Distribution）** 的應用。因為：

- 有 $n = 10$ 次獨立試驗（每次罰球）
- 每次試驗只有兩種結果：「命中」（成功）或「未命中」（失敗）
- 每次命中的機率固定為 $p = 0.45$
- 我們關心的是 $k$ 次成功的機率 $P(X = k)$

令 $X \sim \text{Binomial}(n=10, p=0.45)$，本題要求找出使 $P(X = k)$ 最大化的 $k$ 值，以及對應的最大機率值。

### (2) 關鍵參數分析

- **$n = 10$**：罰球總次數
- **$p = 0.45$**：單次罰球命中的機率
- **目標 $k$**：使 $P(X = k)$ 最大的命中次數（即二項分佈的**眾數 / mode**）

### (3) 解題思路提示

對於二項分佈 $X \sim \text{Binomial}(n, p)$，使 $P(X = k)$ 最大的 $k$ 值（即眾數）有一個簡單的公式：

- 眾數 $\lfloor (n+1)p \rfloor$ 或 $\lceil (n+1)p \rceil - 1$
- 更精確地說，在 $k = \lfloor (n+1)p \rfloor$ 處達到最大值（若 $(n+1)p$ 是整數，則 $k = (n+1)p$ 和 $k = (n+1)p - 1$ 都是眾數）

**步驟提示**：

1. 計算 $(n+1)p = 11 \times 0.45 = 4.95$
2. 因為 $4.95$ 不是整數，取整數部分可得唯一的眾數 $k = \lfloor 4.95 \rfloor = 4$
3. 代入二項分佈 PMF 計算 $P(X = 4) = \binom{10}{4} (0.45)^4 (0.55)^6$
4. 可得最大機率的數值

**注意事項**：
- 本題有兩個問號：先找出 $k$，再計算對應機率
- 可以驗證 $P(X=4)$ 確實大於 $P(X=3)$ 和 $P(X=5)$ 來確認答案正確
- 直觀上，因為 $p=0.45$，10 次中平均命中 $np = 4.5$ 球，所以眾數在 4 附近是合理的

## 🔢 Derivation Process / 推導過程

### Step 1: Identify the Distribution and Parameters

Let $X \sim \text{Binomial}(n=10,\; p=0.45)$ be the number of successful foul shots in 10 attempts. The PMF is:

$$P(X = k) = \binom{10}{k} (0.45)^k (0.55)^{10-k}$$

We need:
1. The value of $k$ that maximizes $P(X = k)$ (the **mode**)
2. The corresponding maximum probability $P(X = k)$

### Step 2: Find the Mode Using the Standard Formula

For a binomial distribution $\text{Binomial}(n, p)$, the mode is given by:

$$k_{\text{mode}} = \lfloor (n+1)p \rfloor$$

when $(n+1)p$ is not an integer. If $(n+1)p$ is an integer, both $k = (n+1)p$ and $k = (n+1)p - 1$ are modes.

Compute:

$$(n+1)p = 11 \times 0.45 = 4.95$$

Since $4.95$ is not an integer:

$$k_{\text{mode}} = \lfloor 4.95 \rfloor = 4$$

### Step 3: Verify with the Ratio Test

To confirm $k=4$ is indeed the mode, use the successive probability ratio:

$$\frac{P(X = k+1)}{P(X = k)} = \frac{n-k}{k+1} \cdot \frac{p}{1-p}$$

For $k = 4$:

$$\frac{P(X = 5)}{P(X = 4)} = \frac{10-4}{4+1} \cdot \frac{0.45}{0.55} = \frac{6}{5} \cdot \frac{0.45}{0.55} = \frac{6}{5} \cdot \frac{9}{11} = \frac{54}{55} \approx 0.9818$$

Since the ratio is less than 1, $P(X = 5) < P(X = 4)$, meaning the probability peaks at $k = 4$ and then decreases. Similarly, for completeness, $k = 3$:

$$\frac{P(X = 4)}{P(X = 3)} = \frac{10-3}{3+1} \cdot \frac{0.45}{0.55} = \frac{7}{4} \cdot \frac{9}{11} = \frac{63}{44} > 1$$

So $P(X = 4) > P(X = 3)$ as well, confirming $k = 4$ is the unique mode.

### Step 4: Compute the Binomial Coefficient

$$\binom{10}{4} = \frac{10!}{4! \, 6!} = \frac{10 \times 9 \times 8 \times 7}{4 \times 3 \times 2 \times 1} = \frac{5040}{24} = 210$$

### Step 5: Compute the Powers

$$(0.45)^4 = 0.45^4 = 0.04100625$$

$$(0.55)^6 = 0.55^6 = 0.027680640625$$

### Step 6: Compute the Maximum Probability

$$P(X = 4) = 210 \times 0.04100625 \times 0.027680640625$$

First multiply $210 \times 0.04100625 = 8.6113125$, then:

$$8.6113125 \times 0.027680640625 \approx 0.238366$$

More precisely:

$$P(X = 4) \approx 0.2384$$

### Step 7: Final Answer

$$\boxed{\begin{aligned} k_{\text{max}} &= 4 \\ P(X = 4) &\approx 0.2384 \end{aligned}}$$

The probability of making exactly 4 baskets in 10 shots is the maximum, at approximately 23.84%.
