# Problem 9 / 第 9 題

## 📖 Original Text / 原文

Suppose that 15% of the population of a town are senior citizens. Let $X$ be the number of nonsenior citizens who enter a mall before the tenth senior citizen arrives. Find the probability mass function of $X$. Assume that each customer who enters the mall is a random person from the entire population.

## 🇹🇼 Chinese Translation / 中文翻譯

假設一個城鎮的人口中有 15% 是老年人。令 $X$ 為在第十位老年人抵達之前進入商場的非老年人人數。請求出 $X$ 的機率質量函數。假設每位進入商場的顧客都是從整個人口中隨機選取的。

## 💡 Detailed Explanation / 詳細解釋

### 1. 這是什麼分佈？為什麼？

此題同樣屬於**負二項分佈 (Negative Binomial Distribution)**，但使用的是「失敗次數」版本。判斷關鍵：

- 每次進入商場的顧客是一個伯努利試驗：是老年人（成功，$p = 0.15$）或非老年人（失敗，$1-p = 0.85$）
- 我們持續觀察直到第 $r = 10$ 次成功（第十位老年人）出現
- 題目問的是在這過程中出現的**失敗次數**（非老年人人數）

> 負二項分佈有兩種常見表述方式：(1) 達到 $r$ 次成功所需的總試驗次數；(2) 達到 $r$ 次成功之前所經歷的失敗次數。本題使用的是第二種。

### 2. 關鍵參數拆解

| 參數 | 符號 | 數值 | 意義 |
|------|------|------|------|
| 成功機率（老年人） | $p$ | $0.15$ | 隨機一人為老年人的機率 |
| 失敗機率（非老年人） | $1-p$ | $0.85$ | 隨機一人為非老年人的機率 |
| 目標成功次數 | $r$ | $10$ | 第十位老年人抵達時停止 |
| 隨機變數 | $X$ | $0, 1, 2, \ldots$ | 停止前出現的非老年人人數 |
| 所求 | PMF | $P(X = k)$ | 非老年人人數恰好為 $k$ 的機率 |

### 3. 解題思路提示（不給完整答案）

- 負二項分佈（失敗次數版本）的機率質量函數 (PMF) 為：
  $$P(X = k) = \binom{k + r - 1}{r - 1} p^r (1-p)^k, \quad k = 0, 1, 2, \ldots$$

- 解讀公式：總共進行了 $k + r$ 次試驗（$k$ 次失敗 + $r$ 次成功），最後一次試驗必須是成功（第十位老年人）。因此在前面 $k + r - 1$ 次試驗中，有 $r-1$ 次成功和 $k$ 次失敗，排列方式有 $\binom{k + r - 1}{r - 1}$ 種

- 代入 $r=10$ 和 $p=0.15$ 即可得到 $X$ 的 PMF

- 另一種等價表達方式（使用 $\binom{k + r - 1}{k}$ 而非 $\binom{k + r - 1}{r - 1}$）：
  $$P(X = k) = \binom{k + 9}{k} (0.15)^{10} (0.85)^k, \quad k = 0, 1, 2, \ldots$$

- 注意：題目只要求寫出機率質量函數（PMF），不需要計算特定數值。答案應為一個以 $k$ 為變數的函數表達式

- 思考檢查：$X$ 的最小可能取值是多少？如果前十位顧客全部都是老年人，$X$ 是多少？這對應 $k=0$ 的情況，公式是否成立？

## 🔢 Derivation Process / 推導過程

### Step 1: Identify the Distribution and Parameters

- Success = a customer is a **senior citizen**, $p = 0.15$
- Failure = a customer is a **non-senior citizen**, $1-p = 0.85$
- We observe customers until the **10th senior citizen** ($r = 10$) arrives
- $X$ = number of non-senior citizens (failures) before the 10th senior citizen

This is a **Negative Binomial** distribution in the "failures-before-$r$-successes" formulation:

$$X \sim \text{NB}(r=10,\; p=0.15) \quad \text{(failures version)}$$

### Step 2: Write the PMF (Failures Version)

In this formulation, we count the number of failures $k$ that occur before the $r$-th success. The total number of trials is $k + r$, and the last trial must be a success.

Among the first $k + r - 1$ trials, there are exactly $r-1$ successes and $k$ failures. The number of ways to arrange them is $\binom{k + r - 1}{r - 1}$ (or equivalently $\binom{k + r - 1}{k}$).

$$P(X = k) = \binom{k + r - 1}{r - 1}\, p^r\, (1-p)^k, \qquad k = 0, 1, 2, \ldots$$

### Step 3: Substitute $r=10$ and $p=0.15$

$$P(X = k) = \binom{k + 10 - 1}{10 - 1}\, (0.15)^{10}\, (0.85)^k$$

$$P(X = k) = \binom{k + 9}{9}\, (0.15)^{10}\, (0.85)^k, \qquad k = 0, 1, 2, \ldots$$

Equivalently, using $\binom{k+9}{k} = \binom{k+9}{9}$:

$$P(X = k) = \binom{k + 9}{k}\, (0.15)^{10}\, (0.85)^k, \qquad k = 0, 1, 2, \ldots$$

### Step 4: Verify Boundary Cases

- **$k = 0$:** The first 10 customers are all senior citizens. $P(X=0) = \binom{9}{9}(0.15)^{10}(0.85)^0 = (0.15)^{10}$. ✓
- **$k$ can be arbitrarily large:** The support is $\{0, 1, 2, \ldots\}$ because in theory, we might need to wait arbitrarily long for the 10th senior citizen. ✓

### Step 5: Final Answer

$$\boxed{P(X = k) = \binom{k + 9}{9}\, (0.15)^{10}\, (0.85)^k, \qquad k = 0, 1, 2, \ldots}$$
