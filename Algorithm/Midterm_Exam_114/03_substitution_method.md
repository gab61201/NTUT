# Problem 3 / 第三題

## 📖 Original Text / 原文

Use the substitution method to prove that the recurrence

$$T(n) = T(n-1) + \Theta(n)$$

has the solution $T(n) = \Theta(n^2)$.

---

## 🇹🇼 Chinese Translation / 中文翻譯

使用代入法（substitution method）證明遞迴關係式

$$T(n) = T(n-1) + \Theta(n)$$

的解為 $T(n) = \Theta(n^2)$。

---

## 💡 Detailed Explanation / 詳細解釋

代入法（Substitution Method）是求解遞迴式的三大方法之一（另外兩種是遞迴樹法與主定理）。其核心思路分為三個步驟：

1. **猜測（Guess）** — 根據直覺或遞迴樹，猜測解的漸近上界或下界形式。
2. **代入（Substitute）** — 將猜測代入原遞迴式，利用數學歸納法驗證不等式是否成立。
3. **調整（Adjust）** — 若代入後不等式不成立，則調整猜測中的常數或低階項，使不等式成立。

本題中，我們觀察到 $T(n) = T(n-1) + \Theta(n)$ 表示每一層遞迴增加一個 $\Theta(n)$ 的開銷，共遞迴 $n$ 層，因此總成本類似於等差級數求和：

$$1 + 2 + 3 + \cdots + n = \frac{n(n+1)}{2} = \Theta(n^2)$$

這提供了我們猜測 $T(n) = \Theta(n^2)$ 的直覺依據。

要證明 $\Theta(n^2)$，必須同時證明：
- **上界**：$T(n) = O(n^2)$，即存在常數 $c > 0$，使得 $T(n) \leq c \cdot n^2$
- **下界**：$T(n) = \Omega(n^2)$，即存在常數 $c > 0$，使得 $T(n) \geq c \cdot n^2$

兩者結合即得 $T(n) = \Theta(n^2)$。

---

## 🔢 Derivation Process / 推導過程

### 步驟一：處理 $\Theta(n)$ 項

由於 $\Theta(n)$ 表示存在正常數 $k_1, k_2$，使得對於足夠大的 $n$ 有：

$$k_1 n \leq f(n) \leq k_2 n$$

其中 $f(n)$ 為遞迴式中的非遞迴項。我們將上界與下界分別證明。

---

### 步驟二：證明上界 $T(n) = O(n^2)$

**猜測**：存在常數 $c > 0$，使得對於所有 $n \geq n_0$，有 $T(n) \leq c \cdot n^2$。

**歸納假設**：假設對於所有 $m < n$，$T(m) \leq c \cdot m^2$ 成立。

**代入遞迴式**：

$$\begin{aligned}
T(n) &= T(n-1) + f(n) \\
&\leq c(n-1)^2 + k_2 n && \text{（歸納假設 + } f(n) \leq k_2 n \text{）} \\
&= c(n^2 - 2n + 1) + k_2 n \\
&= c n^2 - 2cn + c + k_2 n \\
&= c n^2 - (2c - k_2)n + c
\end{aligned}$$

要使 $T(n) \leq c n^2$，只需：

$$-(2c - k_2)n + c \leq 0$$

即：

$$(2c - k_2)n \geq c$$

當我們選擇 $c \geq k_2$ 時，$2c - k_2 \geq c > 0$，因此：

$$(2c - k_2)n \geq c \cdot n \geq c \quad \text{（當 } n \geq 1 \text{ 時）}$$

不等式成立！

**基始條件**：對於 $n = 1$，選取足夠大的 $c$ 使得 $T(1) \leq c \cdot 1^2 = c$。

**結論**：$T(n) \leq c \cdot n^2$，即 $T(n) = O(n^2)$。

---

### 步驟三：證明下界 $T(n) = \Omega(n^2)$

**猜測**：存在常數 $c > 0$，使得對於所有 $n \geq n_0$，有 $T(n) \geq c \cdot n^2$。

**歸納假設**：假設對於所有 $m < n$，$T(m) \geq c \cdot m^2$ 成立。

**代入遞迴式**：

$$\begin{aligned}
T(n) &= T(n-1) + f(n) \\
&\geq c(n-1)^2 + k_1 n && \text{（歸納假設 + } f(n) \geq k_1 n \text{）} \\
&= c(n^2 - 2n + 1) + k_1 n \\
&= c n^2 - 2cn + c + k_1 n \\
&= c n^2 - (2c - k_1)n + c
\end{aligned}$$

要使 $T(n) \geq c n^2$，只需：

$$-(2c - k_1)n + c \geq 0$$

即：

$$(2c - k_1)n \leq c$$

這在直接代入時**不一定成立**。此時我們需要**調整猜測**——減去一個低階項：

**調整後的猜測**：$T(n) \geq c \cdot n^2 - d \cdot n$，其中 $d > 0$ 為常數。

**重新代入**：

$$\begin{aligned}
T(n) &\geq c(n-1)^2 - d(n-1) + k_1 n \\
&= c(n^2 - 2n + 1) - dn + d + k_1 n \\
&= c n^2 - 2cn + c - dn + d + k_1 n \\
&= c n^2 - (2c + d - k_1)n + (c + d)
\end{aligned}$$

要使 $T(n) \geq c n^2 - dn$，只需：

$$-(2c + d - k_1)n + (c + d) \geq -dn$$

即：

$$-(2c + d - k_1)n + (c + d) + dn \geq 0$$

$$-(2c - k_1)n + (c + d) \geq 0$$

當我們選擇 $c$ 足夠小使得 $2c \leq k_1$（即 $c \leq k_1/2$），則 $2c - k_1 \leq 0$，故 $-(2c - k_1)n \geq 0$，且 $c + d > 0$，不等式成立！

**基始條件**：對於 $n = 1$，選取適當的 $c, d$ 使得 $T(1) \geq c \cdot 1^2 - d \cdot 1 = c - d$。

**結論**：$T(n) \geq c \cdot n^2 - d \cdot n = \Omega(n^2)$。

---

### 步驟四：綜合結論

由步驟二得 $T(n) = O(n^2)$，由步驟三得 $T(n) = \Omega(n^2)$，因此：

$$\boxed{T(n) = \Theta(n^2)}$$

---

### 📝 關鍵要點 / Key Takeaways

| 要點 | 說明 |
|------|------|
| **猜測形式** | 上界用 $cn^2$，下界用 $cn^2 - dn$（需減去低階項） |
| **為什麼下界需要調整** | 直接猜 $cn^2$ 代入後出現 $-(2c-k_1)n + c \geq 0$，無法保證對所有 $n$ 成立；減去 $dn$ 提供「緩衝空間」 |
| **歸納法的結構** | 基始條件（base case）+ 歸納假設（inductive hypothesis）+ 代入驗證 |
| **$\Theta$ 的意義** | 必須同時證明上界 $O$ 和下界 $\Omega$ |
