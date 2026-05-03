# Problem 5 / 第 5 題

## 📖 Original Text / 原文

On average, there are three misprints in every 10 pages of a particular book. If every chapter of the book contains 35 pages, what is the probability (by using Poisson model approximation) that Chapters 1 and 5 have 10 misprints each?

## 🇹🇼 Chinese Translation / 中文翻譯

某本書平均每 10 頁有 3 個印刷錯誤。如果書中每一章有 35 頁，使用卜瓦松模型近似法，求第 1 章和第 5 章各有 10 個印刷錯誤的機率為何？

## 💡 Detailed Explanation / 詳細解釋

### (1) 涉及的機率分佈

本題使用 **卜瓦松分佈（Poisson Distribution）** 來建模印刷錯誤的出現次數。印刷錯誤在頁面中隨機且獨立地出現，且平均發生率固定，這正是卜瓦松過程的典型應用場景。

由於題目指定「卜瓦松模型近似」，我們假設每一章的錯誤數服從 $\text{Poisson}(\lambda)$，其中 $\lambda$ 為該章節的期望錯誤數。第 1 章和第 5 章相互獨立，因此聯合機率為各自機率的乘積。

### (2) 關鍵參數分析

| 參數 | 符號 | 數值 | 說明 |
|------|------|------|------|
| 基準率 | — | 3 錯誤 / 10 頁 | 已知的平均錯誤率 |
| 每章頁數 | — | 35 頁 | 每章固定頁數 |
| 每章期望錯誤數 | $\lambda$ | $3 \times \frac{35}{10} = 10.5$ | 比例換算 |
| 第 1 章錯誤數 | $X_1$ | $\sim \text{Poisson}(10.5)$ | 第 1 章的卜瓦松隨機變數 |
| 第 5 章錯誤數 | $X_5$ | $\sim \text{Poisson}(10.5)$ | 第 5 章的卜瓦松隨機變數 |
| 目標機率 | — | $P(X_1 = 10 \text{ 且 } X_5 = 10)$ | 兩章各有恰好 10 個錯誤 |

- 從「每 10 頁 3 個錯誤」推算每章 35 頁的 $\lambda$：$\lambda = 3 \times \frac{35}{10} = 3 \times 3.5 = 10.5$。
- $X_1$ 與 $X_5$ 是獨立同分佈（i.i.d.）的隨機變數。

### (3) 解題思路提示

- **第一步**：確定每章的卜瓦松參數 $\lambda = 10.5$。
- **第二步**：利用卜瓦松 PMF 寫出單章恰好有 10 個錯誤的機率：

$$P(X = 10) = \frac{e^{-10.5} \cdot (10.5)^{10}}{10!}$$

- **第三步**：由於第 1 章和第 5 章相互獨立（兩章印刷錯誤互不影響），聯合機率為：

$$P(X_1 = 10,\ X_5 = 10) = P(X_1 = 10) \cdot P(X_5 = 10) = \left[ \frac{e^{-10.5} \cdot (10.5)^{10}}{10!} \right]^2$$

> 💡 **提示**：$10.5^{10}$ 和 $10!$ 的計算較為繁瑣，建議使用計算機或逐步化簡。注意指數項 $e^{-10.5} \times e^{-10.5} = e^{-21}$，可合併化簡。此機率非常小，符合直覺（每章期望約 10.5 個錯誤，恰好 10 個不算太稀有，但兩章同時恰好 10 個的機率會顯著降低）。

## 🔢 Derivation Process / 推導過程

### 步驟 1：計算每章的卜瓦松參數 $\lambda$

已知基準率為每 10 頁有 3 個印刷錯誤，每章有 35 頁。依比例換算：

$$\lambda = 3 \times \frac{35}{10} = 3 \times 3.5 = 10.5$$

因此，第 1 章的錯誤數 $X_1 \sim \text{Poisson}(10.5)$，第 5 章的錯誤數 $X_5 \sim \text{Poisson}(10.5)$，且兩章相互獨立。

### 步驟 2：寫出單章恰好 10 個錯誤的機率

卜瓦松 PMF：

$$P(X = k) = \frac{e^{-\lambda} \lambda^k}{k!}$$

代入 $k = 10$、$\lambda = 10.5$：

$$P(X = 10) = \frac{e^{-10.5} \cdot (10.5)^{10}}{10!}$$

### 步驟 3：利用獨立性計算聯合機率

由於 $X_1$ 與 $X_5$ 相互獨立：

$$
\begin{aligned}
P(X_1 = 10,\ X_5 = 10) &= P(X_1 = 10) \cdot P(X_5 = 10) \\
&= \left[ \frac{e^{-10.5} \cdot (10.5)^{10}}{10!} \right]^2
\end{aligned}
$$

### 步驟 4：數值計算

先計算各分量：

- $e^{-10.5} \approx 2.75364 \times 10^{-5}$
- $(10.5)^{10} = 10.5^{10} \approx 1.62889 \times 10^{10}$
- $10! = 3,628,800 = 3.6288 \times 10^6$

計算單章機率：

$$
\begin{aligned}
P(X = 10) &= \frac{2.75364 \times 10^{-5} \times 1.62889 \times 10^{10}}{3.6288 \times 10^6} \\[6pt]
&= \frac{4.4851 \times 10^5}{3.6288 \times 10^6} \\[6pt]
&= 0.12360
\end{aligned}
$$

計算聯合機率：

$$
\begin{aligned}
P(X_1 = 10,\ X_5 = 10) &= (0.12360)^2 \\
&= 0.01527696
\end{aligned}
$$

### 📦 最終答案

$$
\boxed{P(\text{第 1 章與第 5 章各有 10 個錯誤}) \approx 0.01528}
$$

> 即：第 1 章和第 5 章各有恰好 10 個印刷錯誤的機率約為 **1.53%**。
