# Problem 2 / 第二題

## 📖 Original Text / 原文

**2. Recursive algorithm:**

**(a)** Write pseudocode for Binary Search.

**(b)** Write a recurrence for the time complexity $T(n)$ and represent the time complexity using asymptotic notation.

---

## 🇹🇼 Chinese Translation / 中文翻譯

**2. 遞迴演算法：**

**(a)** 寫出二元搜尋（Binary Search）的虛擬碼。

**(b)** 寫出時間複雜度 $T(n)$ 的遞迴式，並用漸近符號表示時間複雜度。

**(a) 二元搜尋虛擬碼：**

```
BINARY-SEARCH(A, target, low, high)
    if low > high
        return -1
    mid ← ⌊(low + high) / 2⌋
    if A[mid] = target
        return mid
    else if A[mid] > target
        return BINARY-SEARCH(A, target, low, mid - 1)
    else
        return BINARY-SEARCH(A, target, mid + 1, high)
```

**(b) 遞迴式：**

$$
T(n) = T(n/2) + \Theta(1)
$$

---

## 💡 Detailed Explanation / 詳細解釋

### 二元搜尋（Binary Search）

二元搜尋是一種在**已排序陣列**中尋找目標值的經典演算法。它的核心思想是每次將搜尋範圍縮小一半：

1. **比較中點元素**：取搜尋範圍的中間位置，將目標值與該位置的值比較。
2. **排除一半**：
   - 如果目標值**等於**中點值，搜尋成功，回傳索引。
   - 如果目標值**小於**中點值，目標值一定在左半邊，繼續搜尋左半邊。
   - 如果目標值**大於**中點值，目標值一定在右半邊，繼續搜尋右半邊。
3. **遞迴終止**：當搜尋範圍為空（`low > high`）時，表示目標值不存在於陣列中，回傳 $-1$。

### 時間複雜度直觀理解

每執行一次遞迴，搜尋範圍從 $n$ 個元素縮減到 $n/2$ 個元素。因此，最多只需要 $\lg n$ 次遞迴就能將範圍縮小到 $1$（或 $0$）。每次遞迴本身只需要常數時間 $\Theta(1)$ 來計算中點和比較。

---

## 🔢 Derivation Process / 推導過程

### 步驟 1：建立遞迴式

在每次遞迴呼叫中：
- 計算中點 `mid` 和進行比較操作：**$\Theta(1)$**（常數時間）。
- 最多遞迴呼叫一次，問題規模縮減為原來的一半：**$T(n/2)$**。

因此遞迴式為：

$$
T(n) = T(n/2) + \Theta(1)
$$

基例（base case）：當 $n = 1$ 時，$T(1) = \Theta(1)$。

### 步驟 2：使用遞迴樹法求解

展開遞迴式，觀察遞迴樹的結構：

$$
\begin{aligned}
T(n) &= T(n/2) + c \\
&= \big(T(n/4) + c\big) + c = T(n/4) + 2c \\
&= \big(T(n/8) + c\big) + 2c = T(n/8) + 3c \\
&\;\;\vdots \\
&= T(n/2^k) + k \cdot c
\end{aligned}
$$

### 步驟 3：確定遞迴深度

遞迴在 $n/2^k = 1$ 時終止，即：

$$
n/2^k = 1 \implies 2^k = n \implies k = \lg n
$$

### 步驟 4：代入求解

將 $k = \lg n$ 代入：

$$
\begin{aligned}
T(n) &= T(1) + c \cdot \lg n \\
&= \Theta(1) + c \cdot \lg n \\
&= \Theta(\lg n)
\end{aligned}
$$

### 步驟 5：使用主定理（Master Theorem）驗證

遞迴式 $T(n) = aT(n/b) + f(n)$ 中：

- $a = 1$（每次產生 1 個子問題）
- $b = 2$（問題規模除以 2）
- $f(n) = \Theta(1) = \Theta(n^0)$

計算 $\log_b a = \log_2 1 = 0$。

由於 $f(n) = \Theta(n^{\log_b a}) = \Theta(n^0) = \Theta(1)$，符合主定理的 **Case 2**：

$$
T(n) = \Theta(n^{\log_b a} \cdot \lg n) = \Theta(n^0 \cdot \lg n) = \Theta(\lg n)
$$

### 📌 結論

二元搜尋的時間複雜度為：

$$
\boxed{T(n) = \Theta(\lg n)}
$$
