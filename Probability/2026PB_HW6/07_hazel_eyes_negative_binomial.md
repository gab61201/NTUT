# Problem 7 / 第 7 題

## 📖 Original Text / 原文

Suppose that 20% of a group of people have hazel eyes. What is the probability that the eighth passenger boarding a plane is the third one having hazel eyes? Assume that passengers boarding the plane form a randomly chosen group.

## 🇹🇼 Chinese Translation / 中文翻譯

假設一個群體中有 20% 的人有淡褐色眼睛。請問第八位登機的乘客正好是第三位有淡褐色眼睛的乘客的機率是多少？假設登機的乘客是從該群體中隨機選取的。

## 💡 Detailed Explanation / 詳細解釋

### 1. 這是什麼分佈？為什麼？

此題屬於**負二項分佈 (Negative Binomial Distribution)**。我們可以這樣判斷：

- 每一位乘客要麼有淡褐色眼睛（成功，機率 $p = 0.20$），要麼沒有（失敗，機率 $1-p = 0.80$）
- 每次觀察（登機）是獨立的伯努利試驗 (Bernoulli trial)
- 我們關心的是：**第 $r$ 次成功發生在第 $x$ 次試驗時** — 這就是負二項分佈的典型場景

具體來說，題目問的是：第 3 個成功（第三位淡褐色眼睛乘客）發生在第 8 次試驗（第八位登機乘客）的機率。

> 這裡使用負二項分佈的「試驗次數」版本：$X \sim \text{NB}(r, p)$，其中 $r=3$ 是目標成功次數，$p=0.20$ 是每次試驗的成功機率，而 $X$ 代表達到第 $r$ 次成功所需要的總試驗次數。

### 2. 關鍵參數拆解

| 參數 | 符號 | 數值 | 意義 |
|------|------|------|------|
| 成功機率 | $p$ | $0.20$ | 隨機選一人有淡褐色眼睛的機率 |
| 目標成功次數 | $r$ | $3$ | 我們想要觀察到的淡褐色眼睛乘客人數 |
| 總試驗次數 | $x$ | $8$ | 第 8 位乘客登機時 |
| 注意 | — | — | 第 8 位乘客**就是**第 3 位成功者 |

### 3. 解題思路提示（不給完整答案）

- 負二項分佈的機率質量函數 (PMF) 形式為：
  $$P(X = x) = \binom{x-1}{r-1} p^r (1-p)^{x-r}, \quad x = r, r+1, r+2, \ldots$$

- 解讀公式：在前 $x-1$ 次試驗中，必須恰好有 $r-1$ 次成功（排列方式有 $\binom{x-1}{r-1}$ 種），然後第 $x$ 次試驗必須是成功（機率 $p$）

- 代入 $r=3$、$p=0.20$、$x=8$ 即可求出答案

- 思考檢查：如果第八位是第三位成功者，那麼在前七位乘客中，必須恰好有兩位有淡褐色眼睛，而第八位也必須有淡褐色眼睛。這跟組合數學的推理一致嗎？

## 🔢 Derivation Process / 推導過程

### Step 1: Identify the Distribution and Parameters

We are asked: what is the probability that the **8th** passenger boarding is the **3rd** one with hazel eyes?

- Success = passenger has hazel eyes, $p = 0.20$
- Failure = passenger does not have hazel eyes, $1-p = 0.80$
- We want the $r$-th success ($r=3$) to occur on trial $x=8$
- This is a **Negative Binomial** distribution (trials-until-$r$-successes version)

Let $X \sim \text{NB}(r=3,\; p=0.20)$ be the trial number on which the 3rd success occurs.

### Step 2: Write the PMF

The probability mass function of the Negative Binomial (trials version) is:

$$P(X = x) = \binom{x-1}{r-1}\, p^r\, (1-p)^{x-r}, \qquad x = r, r+1, r+2, \ldots$$

**Interpretation:** Among the first $x-1$ trials, there must be exactly $r-1$ successes (arranged in $\binom{x-1}{r-1}$ ways), and then the $x$-th trial must be a success (probability $p$).

### Step 3: Substitute the Values

Substitute $r = 3$, $p = 0.20$, $x = 8$:

$$P(X = 8) = \binom{8-1}{3-1}\, (0.20)^3\, (0.80)^{8-3}$$

$$P(X = 8) = \binom{7}{2}\, (0.20)^3\, (0.80)^5$$

### Step 4: Compute Each Component

- Binomial coefficient: $\displaystyle \binom{7}{2} = \frac{7 \times 6}{2 \times 1} = 21$
- $(0.20)^3 = 0.008$
- $(0.80)^5 = 0.32768$

### Step 5: Multiply

$$P(X = 8) = 21 \times 0.008 \times 0.32768$$

$$P(X = 8) = 21 \times 0.00262144 = 0.05505024$$

### Step 6: Final Answer

$$\boxed{P(\text{8th passenger is the 3rd with hazel eyes}) \approx 0.0551}$$
