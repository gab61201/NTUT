# Problem 1: Modified MERGE-SORT / 改良合併排序法

---

## 📖 Original Text / 原文

Consider a modification to MERGE-SORT in which $n/k$ sublists of length $k$ are sorted using INSERTION-SORT and then merged using the standard merging mechanism, where $k$ is a value to be determined.

**(a)** Show that the $n/k$ sublists, each of length $k$, can be sorted by INSERTION-SORT in $\Theta(nk)$ worst-case time.

**(b)** Show that the sublists can be merged in $\Theta(n \lg (n/k))$ worst-case time.

**(c)** Given that the modified algorithm runs in $\Theta(nk + n \lg (n/k))$ worst-case time, what is the largest asymptotic value of $k$ as a function of $n$ for which the modified algorithm has the same asymptotic running time as standard MERGE-SORT?

**(d)** How should $k$ be chosen in practice?

---

## 🇹🇼 Chinese Translation / 中文翻譯

考慮對 MERGE-SORT 進行修改：將 $n/k$ 個長度為 $k$ 的子串列用 INSERTION-SORT 排序，然後使用標準的合併機制進行合併，其中 $k$ 是一個待定的值。

**(a)** 證明 $n/k$ 個長度各為 $k$ 的子串列，可以在最壞情況下以 $\Theta(nk)$ 的時間用 INSERTION-SORT 完成排序。

**(b)** 證明這些子串列可以在最壞情況下以 $\Theta(n \lg (n/k))$ 的時間完成合併。

**(c)** 已知修改後的演算法在最壞情況下的執行時間為 $\Theta(nk + n \lg (n/k))$，請問 $k$ (作為 $n$ 的函數) 的最大漸近值為何，才能使修改後的演算法與標準 MERGE-SORT 具有相同的漸近執行時間？

**(d)** 在實務上應如何選擇 $k$？

---

## 💡 Detailed Explanation / 詳細解釋

### (1) 涉及的演算法概念

本題將兩個經典排序演算法結合：
- **INSERTION-SORT**：對於長度為 $m$ 的陣列，最壞情況時間複雜度為 $\Theta(m^2)$。它對於**小規模**資料非常高效，因為常數因子小、無遞迴開銷。
- **MERGE-SORT**：標準的分治法排序，時間複雜度 $\Theta(n \log n)$。核心操作是合併（merge）兩個已排序的子陣列。

關鍵洞察：當 $k$ 很小時，INSERTION-SORT 的 $k^2$ 成本可控；當 $k$ 很大時，MERGE-SORT 本身的遞迴樹深度變淺（因為子串列較少）。

### (2) 關鍵參數分析

| 參數 | 意義 |
|------|------|
| $n$ | 總元素數量 |
| $k$ | 每個子串列的長度（待定參數） |
| $n/k$ | 子串列的數量 |
| $\Theta(nk)$ | INSERTION-SORT 階段的總成本 |
| $\Theta(n \lg (n/k))$ | 合併階段的總成本 |

### (3) 解題思路提示

**(a) INSERTION-SORT 階段：**
- 每個子串列長度為 $k$，INSERTION-SORT 的最壞情況為 $\Theta(k^2)$
- 共有 $n/k$ 個子串列
- 總成本：$(n/k) \cdot \Theta(k^2) = \Theta(nk)$
- 思路：直接相乘即可，不需要合併的遞迴分析

**(b) 合併階段：**
- 合併 $n/k$ 個已排序的子串列，每個長度為 $k$
- 將此過程視為一棵合併樹：樹的高度為 $\lg(n/k)$（因為每次合併將子串列數量減半）
- 每一層合併處理 $n$ 個元素，成本 $\Theta(n)$
- 總成本：$\Theta(n) \cdot \lg(n/k) = \Theta(n \lg (n/k))$
- 思路：類似標準 MERGE-SORT 的分析，但葉節點數量不同

**(c) 漸近等價條件：**
- 需要 $\Theta(nk + n \lg (n/k)) = \Theta(n \lg n)$
- 即 $nk$ 項不能主導 $n \lg n$，同時 $n \lg(n/k)$ 需要等價於 $n \lg n$
- 從 $n \lg(n/k)$ 項：當 $k = \Theta(\lg n)$ 時，$\lg(n/k) = \lg n - \lg k \approx \lg n$（因為 $\lg k = o(\lg n)$）
- 從 $nk$ 項：$nk = n \cdot \Theta(\lg n) = \Theta(n \lg n)$，恰好匹配
- 思路：分別分析兩項對 $n \lg n$ 的影響，找出 $k$ 的最大漸近階

**(d) 實務選擇：**
- 漸近分析給出 $k = \Theta(\lg n)$，但實務上常數因子很重要
- INSERTION-SORT 在 $k \approx 10 \sim 50$ 時實際效能最佳（快取友好、分支預測好）
- 需要考慮的因素：CPU 快取大小、比較與交換的相對成本、輸入資料的初始有序程度
- 思路：漸近分析提供的是「成長趨勢」，實務上需要通過實驗（benchmarking）來確定最佳 $k$ 值

---

## 🔢 Derivation Process / 推導過程

### (a) INSERTION-SORT 階段：證明 $\Theta(nk)$

INSERTION-SORT 對長度為 $m$ 的陣列，最壞情況時間複雜度為 $\Theta(m^2)$。

對於一個長度為 $k$ 的子串列：

$$T_{\text{IS}}(k) = \Theta(k^2)$$

共有 $\dfrac{n}{k}$ 個這樣的子串列，且彼此獨立排序：

$$T_{\text{total-IS}} = \frac{n}{k} \cdot \Theta(k^2) = \Theta\left(\frac{n}{k} \cdot k^2\right) = \Theta(nk)$$

**證明完成。** 直覺：每個子串列花 $O(k^2)$，$n/k$ 個子串列相乘後 $k$ 項抵銷一個，剩下 $nk$。

---

### (b) 合併階段：證明 $\Theta(n \lg (n/k))$

將 $n/k$ 個已排序子串列合併，使用標準 MERGE-SORT 的合併機制（兩兩合併）。

建立合併樹（merge tree）：
- **葉節點數量**：$n/k$（每個葉節點是一個長度為 $k$ 的已排序子串列）
- **樹的高度**：$\lg(n/k)$（每次合併子串列數量減半）

每一層合併處理所有 $n$ 個元素，成本為 $\Theta(n)$：

$$T_{\text{merge}} = \Theta(n) \cdot \lg\left(\frac{n}{k}\right) = \Theta\left(n \lg \frac{n}{k}\right)$$

**證明完成。** 對比標準 MERGE-SORT：葉節點 $n$ 個（每個元素）→ 高度 $\lg n$；此處葉節點 $n/k$ 個 → 高度 $\lg(n/k)$。

---

### (c) 最大漸近 $k$ 值

總執行時間：

$$T(n) = \Theta(nk + n \lg (n/k))$$

標準 MERGE-SORT 時間：$T_{\text{MS}}(n) = \Theta(n \lg n)$。

要求：$\Theta(nk + n \lg (n/k)) = \Theta(n \lg n)$。

**分析 $n \lg (n/k)$ 項：**

$$n \lg \frac{n}{k} = n(\lg n - \lg k)$$

當 $k$ 為 $n$ 的多項式函數時（如 $k = n^c$），$\lg k = c \lg n$，則：

$$n(\lg n - c \lg n) = n(1-c)\lg n = \Theta(n \lg n) \quad (\text{若 } c < 1)$$

**分析 $nk$ 項：** 必須滿足 $nk = O(n \lg n)$，即 $k = O(\lg n)$。

**合併兩個條件：**
- 從 $n \lg(n/k)$：$k = O(n^{1-\varepsilon})$ for any $\varepsilon > 0$
- 從 $nk$：$k = O(\lg n)$

較嚴格的條件是 $k = O(\lg n)$。

反之，若 $k = \omega(\lg n)$（如 $k = \lg^2 n$），則 $nk = \omega(n \lg n)$，主導整體時間。

$$\boxed{k = \Theta(\lg n)}$$

此時 $nk = \Theta(n \lg n)$，$n \lg(n/k) = n(\lg n - \lg \lg n) = \Theta(n \lg n)$，兩項皆為 $\Theta(n \lg n)$。

---

### (d) 實務上 $k$ 的選擇

漸近分析給出 $k = \Theta(\lg n)$，但實務中考慮**常數因子**：

INSERTION-SORT 的實際執行時間：$c_1 \cdot k^2$
合併的實際執行時間：$c_2 \cdot n \lg(n/k)$

總實際時間：$\dfrac{n}{k} \cdot c_1 k^2 + c_2 \cdot n \lg\dfrac{n}{k} = c_1 nk + c_2 n \lg\dfrac{n}{k}$

通過實驗（benchmarking）測量 $c_1$ 和 $c_2$，找到使總時間最小的 $k$。實務上 $k$ 通常在 **10 到 50** 之間，因為：
- INSERTION-SORT 在小陣列上快取局部性極佳
- 小 $k$ 使合併樹高度接近 $\lg n$，合併成本主導
- 大 $k$ 使 INSERTION-SORT 的 $k^2$ 成本暴增

最終 $k$ 應通過**實證調整 (empirical tuning)** 決定。
