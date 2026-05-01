# Problem 1 / 第一題

## 📖 Original Text / 原文

Consider a modification to MERGE-SORT in which $n/k$ sublists of length $k$ are sorted using INSERTION-SORT and then merged using the standard merging mechanism, where $k$ is a value to be determined.

a) Show that the $n/k$ sublists, each of length $k$, can be sorted by INSERTION-SORT in $\Theta(nk)$ worst-case time.

b) Show that the sublists can be merged in $\Theta(n\lg(n/k))$ worst-case time.

c) Given that the modified algorithm runs in $\Theta(nk + n\lg(n/k))$ worst-case time, what is the largest asymptotic value of $k$ as a function of $n$ for which the modified algorithm has the same asymptotic running time as standard MERGE-SORT?

d) How should $k$ be chosen in practice?

---

## 🇹🇼 Chinese Translation / 中文翻譯

考慮對 MERGE-SORT 的一種改良：將 $n$ 個元素分成 $n/k$ 個子清單，每個子清單長度為 $k$，先使用 INSERTION-SORT 將這些子清單排序，然後使用標準的合併機制將它們合併，其中 $k$ 是一個待定值。

a) 證明：$n/k$ 個子清單（每個長度為 $k$）可以由 INSERTION-SORT 在 $\Theta(nk)$ 最壞情況時間內完成排序。

b) 證明：這些子清單可以在 $\Theta(n\lg(n/k))$ 最壞情況時間內合併完成。

c) 已知改良演算法的最壞情況執行時間為 $\Theta(nk + n\lg(n/k))$，求 $k$ 作為 $n$ 的函數的最大漸進值，使得改良演算法與標準 MERGE-SORT 具有相同的漸近執行時間。

d) 在實務上應該如何選擇 $k$？

---

## 💡 Detailed Explanation / 詳細解釋

### 整體思路

這是一個「混合排序演算法」：在 MERGE-SORT 的框架下，**不**再將陣列拆到只剩 1 個元素，而是拆到每個子陣列長度為 $k$ 時，改用 INSERTION-SORT 來排序這些小子陣列，再依照 MERGE-SORT 的方式逐層合併。

這種做法的直觀想法是：**INSERTION-SORT 在小陣列上表現更好**（常數較小、記憶體存取連續、無遞迴開銷），因此可以用它來取代 MERGE-SORT 的底層遞迴，以改善實際執行速度。

---

### (a) INSERTION-SORT 排序 $n/k$ 個子清單

INSERTION-SORT 對長度為 $m$ 的陣列，最壞情況時間為 $\Theta(m^2)$。

每個子清單長度為 $k$，所以排序一個子清單需要 $\Theta(k^2)$。

共有 $n/k$ 個子清單，且彼此獨立排序，所以總時間為：

$$\frac{n}{k} \times \Theta(k^2) = \Theta(nk)$$

---

### (b) 合併 $n/k$ 個已排序子清單

合併階段使用標準 MERGE-SORT 的合併機制，即「逐層兩兩合併」。

初始有 $n/k$ 個已排序子清單，每次合併將清單數量减半，直到只剩一個完整排序的陣列。合併的層數為：

$$\lg\left(\frac{n}{k}\right)$$

每一層中，所有 $n$ 個元素都會被遍歷一次（合併操作的總工作量等於總元素數），因此每一層的時間為 $\Theta(n)$。

總合併時間：

$$\Theta(n) \times \lg\left(\frac{n}{k}\right) = \Theta\left(n\lg\frac{n}{k}\right)$$

---

### (c) 求最大的 $k$ 使改良演算法仍為 $\Theta(n\lg n)$

標準 MERGE-SORT 的執行時間為 $\Theta(n\lg n)$。

改良演算法的執行時間為：

$$\Theta(nk + n\lg(n/k))$$

利用對數性質展開：

$$n\lg\left(\frac{n}{k}\right) = n(\lg n - \lg k) = n\lg n - n\lg k$$

因此總時間：

$$nk + n\lg n - n\lg k$$

要讓它等於 $\Theta(n\lg n)$，必須確保 $nk$ 項**不超過** $n\lg n$ 的量級，即：

$$nk = O(n\lg n)$$

兩邊除以 $n$：

$$k = O(\lg n)$$

**驗證**：當 $k = \Theta(\lg n)$ 時，

- $nk = \Theta(n\lg n)$
- $n\lg k = n\lg(\lg n) = o(n\lg n)$（因為 $\lg(\lg n)$ 增長遠慢於 $\lg n$）
- 總時間 $= \Theta(n\lg n) + \Theta(n\lg n) - o(n\lg n) = \Theta(n\lg n)$ ✓

因此，$k$ 作為 $n$ 的函數的**最大漸進值為** $\Theta(\lg n)$。

---

### (d) 實務上如何選擇 $k$？

在實務上，$k$ 應選擇為**一個小常數**（例如 $7$ 到 $15$ 之間），而不是讓 $k$ 隨 $n$ 增長。原因如下：

1. **INSERTION-SORT 的常數因子小**：在小陣列上，INSERTION-SORT 的簡單結構使得其每步操作的成本遠小於 MERGE-SORT 的遞迴呼叫與記憶體配置。

2. **更好的快取局部性 (Cache Locality)**：INSERTION-SORT 使用陣列內部的資料移動，對 CPU 快取更友好。

3. **減少遞迴深度**：讓 $k$ 為常數意味著遞迴樹的深度減少 $\Theta(\lg k) = O(1)$ 層，減少了函數呼叫的開銷。

4. **真實世界的實作**：Python 的 `sorted()` / `list.sort()` 使用的 **Timsort**、Java 的 `Arrays.sort()`（物件陣列版）都採用了類似的策略——當子陣列小於某個閾值（通常為 7 左右）時改用 INSERTION-SORT。

5. **若 $k$ 太大**：INSERTION-SORT 的 $\Theta(k^2)$ 會開始主導整體時間，反而變慢。

---

## 🔢 Derivation Process / 推導過程

### 部分 (a) 的推導

$$
\begin{aligned}
\text{INSERTION-SORT 對長度 } k \text{ 的陣列} &\Rightarrow \Theta(k^2) \text{ 最壞情況} \\
\text{共有 } \frac{n}{k} \text{ 個子清單} &\Rightarrow \text{彼此獨立} \\
\text{總時間} &= \frac{n}{k} \times \Theta(k^2) \\
&= \Theta\left(\frac{n \cdot k^2}{k}\right) \\
&= \boxed{\Theta(nk)}
\end{aligned}
$$

---

### 部分 (b) 的推導

$$
\begin{aligned}
\text{初始已排序子清單數} &= \frac{n}{k} \\
\text{合併層數} &= \lg\left(\frac{n}{k}\right) \\
\text{每層處理的元素數} &= n \quad \text{（所有元素都要合併一次）} \\
\text{每層時間} &= \Theta(n) \\
\text{總合併時間} &= \Theta(n) \times \lg\left(\frac{n}{k}\right) \\
&= \boxed{\Theta\left(n\lg\frac{n}{k}\right)}
\end{aligned}
$$

---

### 部分 (c) 的完整推導

**目標**：求最大的 $k(n)$ 使得改良演算法與標準 MERGE-SORT 具有相同的漸近時間。

標準 MERGE-SORT 時間：

$$T_{\text{standard}} = \Theta(n\lg n)$$

改良演算法時間：

$$T_{\text{modified}} = \Theta(nk + n\lg(n/k))$$

展開對數項：

$$n\lg\left(\frac{n}{k}\right) = n(\lg n - \lg k) = n\lg n - n\lg k$$

代入：

$$T_{\text{modified}} = \Theta(nk + n\lg n - n\lg k)$$

要滿足 $T_{\text{modified}} = \Theta(n\lg n)$，需要：

$$nk + n\lg n - n\lg k = \Theta(n\lg n)$$

重組：

$$n\lg n + (nk - n\lg k) = \Theta(n\lg n)$$

這要求括號內的項不超過 $n\lg n$ 的量級：

$$nk - n\lg k = O(n\lg n)$$

由於 $nk \ge n\lg k$ 當 $k \ge 1$（因為 $k \ge \lg k$ 對所有 $k \ge 1$ 成立），主要限制來自 $nk$：

$$nk = O(n\lg n) \Rightarrow \boxed{k = O(\lg n)}$$

**嚴格驗證 $k = \Theta(\lg n)$ 確實可行**：

設 $k = c \cdot \lg n$（$c$ 為常數）：

$$
\begin{aligned}
nk &= c \cdot n\lg n = \Theta(n\lg n) \\
n\lg k &= n\lg(c \cdot \lg n) = n(\lg c + \lg\lg n) = O(n\lg\lg n) = o(n\lg n) \\
T_{\text{modified}} &= \Theta(n\lg n) + \Theta(n\lg n) - o(n\lg n) \\
&= \Theta(n\lg n) \qquad \blacksquare
\end{aligned}
$$

**關鍵不等式**：$\lg(\lg n) = o(\lg n)$，即 $\lg\lg n$ 的增長速度遠慢於 $\lg n$。

---

### 部分 (d) 的實務分析

| 考量因素 | 說明 |
|---------|------|
| INSERTION-SORT 的優勢範圍 | 陣列越小越明顯（通常 $k \le 15$） |
| 最佳 $k$ 值 | 實務上約為 $7 \sim 15$，取決於硬體 |
| Timsort 預設值 | Python 使用 $k = 32$（minrun 計算） |
| Java 預設值 | 物件陣列排序使用 $k = 7$ |
| 理論上限 vs 實務 | 理論上 $k = \Theta(\lg n)$，但實務上 $k$ 為常數 |

**結論**：實務上 $k$ 應選為一個**小常數**，讓 INSERTION-SORT 在其最擅長的短陣列上發揮，同時不影響 MERGE-SORT 的漸近效率。
