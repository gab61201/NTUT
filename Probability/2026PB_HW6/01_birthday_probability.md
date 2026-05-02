# Problem 1 / 第 1 題

## 📖 Original Text / 原文

1. A graduate class consists of six students. What is the probability that exactly three of them are born either in April or in October?

## 🇹🇼 Chinese Translation / 中文翻譯

一個研究生班級有六名學生。請問恰好有三名學生出生在四月或十月的機率是多少？

## 💡 Detailed Explanation / 詳細解釋

### (1) 涉及的機率分佈

本題屬於 **二項分佈（Binomial Distribution）** 的應用。因為：

- 有 $n = 6$ 次獨立試驗（每位學生的出生月份視為一次試驗）
- 每次試驗只有兩種結果：「成功」（出生在四月或十月）或「失敗」（出生在其他月份）
- 每次試驗成功的機率 $p$ 是固定的（假設每個月出生的機率均等）
- 我們關心的是恰好 $k = 3$ 次成功的機率

因此，令隨機變數 $X \sim \text{Binomial}(n, p)$，我們要求 $P(X = 3)$。

### (2) 關鍵參數分析

- **$n = 6$**：班級中的學生總數
- **$k = 3$**：我們感興趣的「成功」次數（恰好三位學生出生在四月或十月）
- **$p$**：一位學生出生在四月或十月的機率。一年有 12 個月，其中四月和十月共 2 個月，所以 $p = \frac{2}{12} = \frac{1}{6}$

### (3) 解題思路提示

二項分佈的機率質量函數（PMF）為：

$$P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}$$

你需要代入 $n = 6$、$k = 3$、$p = \frac{1}{6}$ 來計算答案。

**注意事項**：
- 題目問的是「恰好三位」學生的機率，不是「至少三位」或「最多三位」
- 二項係數 $\binom{6}{3}$ 代表從 6 位學生中選出 3 位「成功者」的方法數
- $p^k = \left(\frac{1}{6}\right)^3$ 代表三位特定學生都在四月或十月出生的機率
- $(1-p)^{n-k} = \left(\frac{5}{6}\right)^3$ 代表另外三位學生都不在四月或十月出生的機率
- 最後把這些部分相乘即可得到最終答案

## 🔢 Derivation Process / 推導過程

### Step 1: Identify the Distribution and Parameters

We have $n = 6$ independent trials (students), each with two outcomes: born in April or October ("success") or not ("failure"). Since births are assumed equally likely across all 12 months:

$$p = \frac{2}{12} = \frac{1}{6}, \quad 1-p = \frac{5}{6}$$

Let $X \sim \text{Binomial}(n=6,\; p=\frac{1}{6})$. We need $P(X = 3)$.

### Step 2: Write the Binomial PMF

$$P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}$$

Substituting $n=6$, $k=3$, $p=\frac{1}{6}$:

$$P(X = 3) = \binom{6}{3} \left(\frac{1}{6}\right)^3 \left(\frac{5}{6}\right)^3$$

### Step 3: Compute the Binomial Coefficient

$$\binom{6}{3} = \frac{6!}{3! \, 3!} = \frac{6 \times 5 \times 4}{3 \times 2 \times 1} = \frac{120}{6} = 20$$

### Step 4: Compute the Powers

$$\left(\frac{1}{6}\right)^3 = \frac{1^3}{6^3} = \frac{1}{216}$$

$$\left(\frac{5}{6}\right)^3 = \frac{5^3}{6^3} = \frac{125}{216}$$

### Step 5: Multiply Everything Together

$$P(X = 3) = 20 \times \frac{1}{216} \times \frac{125}{216} = \frac{20 \times 125}{216 \times 216} = \frac{2500}{46656}$$

### Step 6: Simplify the Fraction

Divide numerator and denominator by 4:

$$P(X = 3) = \frac{2500 \div 4}{46656 \div 4} = \frac{625}{11664}$$

### Step 7: Final Answer

$$\boxed{P(\text{exactly 3 born in April or October}) = \frac{625}{11664} \approx 0.05358}$$
