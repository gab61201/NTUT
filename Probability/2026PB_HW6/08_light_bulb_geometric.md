# Problem 8 / 第 8 題

## 📖 Original Text / 原文

The probability is $p$ that a randomly chosen light bulb is defective. We screw a bulb into a lamp and switch on the current. If the bulb works, we stop; otherwise, we try another and continue until a good bulb is found. What is the probability that at least $n$ bulbs are required?

## 🇹🇼 Chinese Translation / 中文翻譯

一個隨機選取的燈泡有瑕疵的機率為 $p$。我們將一個燈泡裝入燈座並接通電源。如果燈泡能正常運作，我們就停止；否則，我們換另一個燈泡繼續嘗試，直到找到一個好的燈泡為止。請問至少需要 $n$ 個燈泡的機率是多少？

## 💡 Detailed Explanation / 詳細解釋

### 1. 這是什麼分佈？為什麼？

此題屬於**幾何分佈 (Geometric Distribution)**。判斷方式如下：

- 每次插入一個燈泡是一個伯努利試驗：要麼是好燈泡（成功，機率 $1-p$），要麼是瑕疵燈泡（失敗，機率 $p$）
- 我們重複試驗直到**第一次成功**（找到第一個好燈泡）為止
- 幾何分佈描述的就是：為了得到第一次成功，需要進行的試驗次數

> 令 $X$ = 找到第一個好燈泡所需的燈泡總數。則 $X \sim \text{Geometric}(1-p)$，其中成功機率為 $1-p$（好燈泡的機率）。

### 2. 關鍵參數拆解

| 參數 | 符號 | 數值 | 意義 |
|------|------|------|------|
| 瑕疵機率 | $p$ | 給定（一般形式） | 隨機選一個燈泡有瑕疵的機率 |
| 成功機率 | $q = 1-p$ | — | 隨機選一個燈泡是好的機率 |
| 隨機變數 | $X$ | — | 直到找到好燈泡所需的總燈泡數 |
| 問題所求 | $P(X \geq n)$ | — | **至少**需要 $n$ 個燈泡的機率 |

### 3. 解題思路提示（不給完整答案）

- 幾何分佈的 PMF 為：
  $$P(X = k) = (1-q)^{k-1} q = p^{k-1}(1-p), \quad k = 1, 2, 3, \ldots$$
  其中 $k$ 是總試驗次數，$q = 1-p$ 是成功機率

- 題目問的是 $P(X \geq n)$，即至少需要 $n$ 個燈泡。這等價於：**前 $n-1$ 個燈泡全都是瑕疵的**

- 因為前 $n-1$ 個燈泡全部瑕疵時，我們必定需要至少第 $n$ 個燈泡。所以：
  $$P(X \geq n) = P(\text{前 } n-1 \text{ 個燈泡全部瑕疵})$$

- 每個燈泡獨立地有機率 $p$ 是瑕疵的，因此前 $n-1$ 個全部瑕疵的機率可以直接用乘法原理計算

- 另一種思路：$P(X \geq n) = 1 - P(X < n) = 1 - \sum_{k=1}^{n-1} P(X = k)$，但前面提到的互補事件方法更直接

- 思考：如果 $n=1$，$P(X \geq 1)$ 應該是多少？這可以幫助你驗證公式的合理性

## 🔢 Derivation Process / 推導過程

### Step 1: Identify the Distribution and Parameters

- Let $p$ be the probability a bulb is **defective** (given parameter)
- Then probability a bulb is **good** = $1-p$
- We stop when we find the **first good bulb**
- Let $X$ = number of bulbs tried until (and including) the first good bulb
- $X \sim \text{Geometric}(1-p)$, where "success" = finding a good bulb

### Step 2: Write the Relevant Probability

We need $P(X \geq n)$, the probability that **at least $n$ bulbs are required**.

The event "$X \geq n$" means the first $n-1$ bulbs are **all defective**. If any of the first $n-1$ bulbs were good, we would have stopped earlier, and fewer than $n$ bulbs would be needed.

Since each bulb is independent:

$$P(X \geq n) = P(\text{first } n-1 \text{ bulbs are all defective})$$

### Step 3: Compute Using Independence

Each bulb is independently defective with probability $p$. Therefore:

$$P(X \geq n) = \underbrace{p \times p \times \cdots \times p}_{n-1 \text{ times}} = p^{\,n-1}$$

### Step 4: Verify with the PMF (Alternative Method)

The Geometric PMF is:

$$P(X = k) = p^{\,k-1}(1-p), \qquad k = 1, 2, 3, \ldots$$

Then:

$$P(X \geq n) = \sum_{k=n}^{\infty} p^{\,k-1}(1-p) = (1-p)\,p^{\,n-1}\sum_{j=0}^{\infty} p^{\,j} = (1-p)\,p^{\,n-1} \cdot \frac{1}{1-p} = p^{\,n-1}$$

Both methods agree.

### Step 5: Sanity Check

- If $n=1$: $P(X \geq 1) = p^0 = 1$. ✓ (At least 1 bulb is always required.)
- If $p=0$ (no defective bulbs): $P(X \geq n) = 0$ for $n \geq 2$, meaning we always find a good bulb on the first try. ✓
- If $p=1$ (all bulbs defective): $P(X \geq n) = 1$ for all $n$, meaning we never find a good bulb. ✓

### Step 6: Final Answer

$$\boxed{P(\text{at least } n \text{ bulbs are required}) = p^{\,n-1}}$$
