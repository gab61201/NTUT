# Problem 5 / 第 5 題

## 📖 Original Text / 原文

On average, there are three misprints in every $10$ pages of a particular book. If every chapter of the book contains $35$ pages, what is the probability (by using Poisson model approximation) that Chapters 1 and 5 have $10$ misprints each?

## 🇹🇼 Chinese Translation / 中文翻譯

平均而言，某本書每 $10$ 頁中有三個印刷錯誤。如果該書的每一章包含 $35$ 頁，則使用泊松模型近似，求第一章和第五章各有 $10$ 個印刷錯誤的機率為何？

## 💡 Detailed Explanation / 詳細解釋

### （一）本題涉及的機率分佈

本題使用 **Poisson 分佈（泊松分佈）** 來建模印刷錯誤的發生次數。Poisson 分佈特別適合描述「在一定時間或空間範圍內，稀有事件發生的次數」，而印刷錯誤正是這類典型的「稀有事件」——每一頁出現錯誤的機率很小，但頁數夠多時會呈現一定的規律。

### （二）關鍵參數拆解

- **給定比率**：每 $10$ 頁有 $3$ 個錯誤，即錯誤率為 $0.3$ 個/頁
- **每一章的頁數**：$35$ 頁
- **每一章的 Poisson 參數**：
  $$\lambda_{\text{chapter}} = 35 \times \frac{3}{10} = 35 \times 0.3 = 10.5$$

  這表示：在一章（35 頁）中，平均預期會出現 $10.5$ 個印刷錯誤。

- **題目所求**：第一章和第五章「各有 $10$ 個錯誤」的機率。

### （三）解題概念提示

這題有兩個關鍵層次需要注意：

**層次一：單一章節的機率**

設 $X$ 為某一章中的印刷錯誤數量，則：
$$X \sim \text{Poisson}(\lambda = 10.5)$$
$$P(X = 10) = \frac{e^{-10.5} \cdot 10.5^{10}}{10!}$$

**層次二：兩個獨立章節的聯合機率**

題目問的是 Chapter 1 和 Chapter 5 **各有** 10 個錯誤的機率。假設各章的錯誤數量是相互獨立的（這在 Poisson 模型中是很自然的假設——印刷錯誤在不同章節之間獨立發生），則：

$$P(\text{Ch1} = 10 \ \text{and} \ \text{Ch5} = 10) = P(X_1 = 10) \times P(X_5 = 10) = \big[P(X = 10)\big]^2$$

**思考要點：**
- 為什麼要把「每 10 頁 3 個錯誤」換算成「每 35 頁的 $\lambda$」？（單位的統一）
- 為什麼兩個章節的機率可以直接相乘？（獨立性假設 —— Poisson 過程的無記憶性和獨立增量性質）
- 如果題目問的是「Chapter 1 或 Chapter 5」而非「Chapter 1 和 Chapter 5」，計算方式會有什麼不同？（提示：聯集 vs. 交集）
- 為什麼 $E[X] = 10.5$ 而題目問的是 $X = 10$？這告訴我們什麼？（機率最大的點未必等於期望值，但 $k=10$ 和 $k=10.5$ 附近的值機率很高）

## 🔢 Derivation Process / 推導過程

### Step 1: Determine the Rate Parameter per Page

The book averages $3$ misprints per $10$ pages. Therefore, the misprint rate per page is:

$$\lambda_{\text{per page}} = \frac{3}{10} = 0.3$$

### Step 2: Scale to a Chapter of 35 Pages

Each chapter contains $35$ pages. Under the Poisson model (constant rate, independent occurrences), the parameter for one chapter is:

$$\lambda_{\text{chapter}} = 35 \times 0.3 = 10.5$$

Thus, for any given chapter $i$, the number of misprints follows:

$$X_i \sim \text{Poisson}(\lambda = 10.5)$$

### Step 3: Write the Probability for One Chapter

The PMF for exactly $10$ misprints in one chapter is:

$$P(X_i = 10) = \frac{e^{-10.5} \cdot 10.5^{10}}{10!}$$

### Step 4: Compute the Numerical Value of $P(X = 10)$

We compute $10.5^{10} / 10!$ term-by-term as a product of ratios:

\begin{align*}
\frac{10.5^{10}}{10!} &= \frac{10.5}{1} \times \frac{10.5}{2} \times \frac{10.5}{3} \times \cdots \times \frac{10.5}{10} \\[4pt]
&= 10.5 \times 5.25 \times 3.5 \times 2.625 \times 2.1 \times 1.75 \times 1.5 \times 1.3125 \times 1.1667 \times 1.05 \\[4pt]
&\approx 4488.8
\end{align*}

Now $e^{-10.5} \approx 2.754 \times 10^{-5}$ (since $e^{10.5} \approx 36315$).

$$P(X = 10) = e^{-10.5} \times \frac{10.5^{10}}{10!} \approx 2.754 \times 10^{-5} \times 4488.8 \approx 0.1236$$

### Step 5: Apply Independence of Chapters

Chapters 1 and 5 are independent. The joint probability of both having exactly $10$ misprints is the product of the individual probabilities:

\begin{align*}
P(\text{Ch1} = 10 \text{ and } \text{Ch5} = 10) &= P(X_1 = 10) \times P(X_5 = 10) \\[4pt]
&= \big[P(X = 10)\big]^2
\end{align*}

### Step 6: Compute the Final Result

$$P(\text{Ch1} = 10 \text{ and } \text{Ch5} = 10) = (0.1236)^2 \approx 0.01528$$

### Step 7: Final Answer

$$\boxed{\left[\frac{e^{-10.5} \cdot 10.5^{10}}{10!}\right]^2 \approx 0.0153}$$
