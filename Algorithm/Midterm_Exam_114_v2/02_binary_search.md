# Problem 2: Binary Search / 二元搜尋

---

## 📖 Original Text / 原文

**Recursive algorithm:**

**(a)** Write pseudocode for Binary Search.

**(b)** Write a recurrence for the time complexity $T(n)$ and represent the time complexity using asymptotic notation.

---

## 🇹🇼 Chinese Translation / 中文翻譯

**遞迴演算法：**

**(a)** 寫出二元搜尋 (Binary Search) 的虛擬碼。

**(b)** 寫出時間複雜度 $T(n)$ 的遞迴式，並用漸近符號表示其時間複雜度。

---

## 💡 Detailed Explanation / 詳細解釋

### (1) 涉及的演算法概念

**Binary Search（二元搜尋）** 是一種在**已排序**陣列中尋找目標值的分治法（divide-and-conquer）演算法。

核心思想：每次將搜尋範圍減半。
1. 比較目標值與陣列中間元素
2. 若相等 → 找到目標
3. 若目標較小 → 在左半部繼續搜尋
4. 若目標較大 → 在右半部繼續搜尋
5. 若搜尋範圍為空 → 目標不存在

這是最經典的 $O(\log n)$ 演算法，也是分治策略的入門範例。

### (2) 關鍵參數分析

| 概念 | 說明 |
|------|------|
| 輸入 | 已排序陣列 $A[1..n]$ 和目標值 $x$ |
| 每次遞迴 | 搜尋範圍減半：$n \to n/2$ |
| 基底情況 | 找到目標（$A[mid] = x$）或範圍為空（不存在） |
| 遞迴深度 | $\lfloor \log_2 n \rfloor$ |

### (3) 解題思路提示

**(a) 虛擬碼撰寫：**
- 參考 CLRS 風格的 pseudocode 格式
- 需包含：函數簽名 (BINARY-SEARCH(A, low, high, x))、基底情況、遞迴情況、回傳值（索引或 NIL）
- 注意陣列的邊界處理：使用 `low` 和 `high` 作為搜尋範圍的指標
- 使用 `⌊(low + high) / 2⌋` 計算中間位置

**(b) 遞迴式與漸近分析：**
- 每次遞迴呼叫將問題規模減半，且除了遞迴呼叫外只做常數時間的工作（比較 + 計算中間點）
- 遞迴式：$T(n) = T(n/2) + \Theta(1)$
- 使用 **Master Theorem**（主定理）：Case 2，$a = 1$，$b = 2$，$f(n) = \Theta(1) = \Theta(n^{\log_2 1}) = \Theta(n^0) = \Theta(1)$
- 結論：$T(n) = \Theta(\log n)$
- 另一種方法：直接展開遞迴式，$T(n) = T(n/2) + c = T(n/4) + 2c = \dots$，經過 $\log_2 n$ 步後到達基底情況，總成本 $\Theta(\log n)$

---

## 🔢 Derivation Process / 推導過程

### (a) 虛擬碼推導

Binary Search 的遞迴結構如下：

- **輸入**：已排序陣列 $A[low..high]$ 和目標值 $x$
- **基底情況 1**：$low > high$ → 搜尋範圍為空，目標不存在，回傳 NIL
- **基底情況 2**：$A[mid] = x$ → 找到目標，回傳 $mid$
- **遞迴情況**：
  - 若 $x < A[mid]$ → 目標在左半部，遞迴搜尋 $A[low..mid-1]$
  - 若 $x > A[mid]$ → 目標在右半部，遞迴搜尋 $A[mid+1..high]$

$$
\text{BINARY-SEARCH}(A, low, high, x):
\quad
\begin{cases}
\text{NIL}, & \text{if } low > high \\[6pt]
mid, & \text{if } A[mid] = x \\[6pt]
\text{BINARY-SEARCH}(A, low, mid-1, x), & \text{if } x < A[mid] \\[6pt]
\text{BINARY-SEARCH}(A, mid+1, high, x), & \text{if } x > A[mid]
\end{cases}
$$

其中 $mid = \left\lfloor \dfrac{low + high}{2} \right\rfloor$，初始呼叫為 BINARY-SEARCH$(A, 1, n, x)$。

---

### (b) 遞迴式推導與求解

每次遞迴呼叫將問題規模減半（$n \to n/2$），加上常數時間的比較與中點計算：

$$T(n) = T\left(\frac{n}{2}\right) + \Theta(1)$$

**方法一：Master Theorem（主定理）**

主定理形式：$T(n) = a \cdot T(n/b) + f(n)$

此處 $a = 1$，$b = 2$，$f(n) = \Theta(1)$。

計算 $\log_b a = \log_2 1 = 0$。

比較 $f(n)$ 與 $n^{\log_b a} = n^0 = \Theta(1)$：

$$f(n) = \Theta(1) = \Theta(n^{\log_b a})$$

符合 **Case 2**：$f(n) = \Theta(n^{\log_b a})$，因此：

$$T(n) = \Theta(n^{\log_b a} \cdot \log n) = \Theta(1 \cdot \log n) = \Theta(\log n)$$

**方法二：展開法（直接代入）**

將遞迴式展開：

$$
\begin{aligned}
T(n) &= T(n/2) + c \\
     &= T(n/4) + c + c = T(n/4) + 2c \\
     &= T(n/8) + 3c \\
     &= \cdots \\
     &= T(1) + c \cdot \log_2 n
\end{aligned}
$$

經過 $\log_2 n$ 次展開後，問題規模降至 1（基底情況）。$T(1) = \Theta(1)$。

$$\boxed{T(n) = \Theta(\log n)}$$
