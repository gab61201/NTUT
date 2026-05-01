# Slide 06 — Analysis of Insertion Sort (cont'd)

## 📖 Original Text / 原文

---

**Analysis of Insertion Sort cont'd**

When $t_j = j$ for $j = 2, 3, \ldots, n$.

$$\sum_{j=2}^{n} j = \frac{n(n+1)}{2} - 1$$

and

$$\sum_{j=2}^{n} (j-1) = \frac{n(n-1)}{2}$$

## 🇹🇼 Chinese Translation / 中文翻譯

**插入排序分析（續）**

當 $t_j = j$ 對於 $j = 2, 3, \ldots, n$ 時。

$$\sum_{j=2}^{n} j = \frac{n(n+1)}{2} - 1$$

且

$$\sum_{j=2}^{n} (j-1) = \frac{n(n-1)}{2}$$

## 💡 Detailed Explanation / 詳細解釋

這張投影片計算了**最壞情況**下的求和公式。當陣列完全逆序時，$t_j = j$（每個元素必須與所有已排序元素比較）：

## 🔢 Derivation Process / 推導過程

**公式 1**：$\sum_{j=2}^{n} j$

$$\sum_{j=2}^{n} j = \sum_{j=1}^{n} j - 1 = \frac{n(n+1)}{2} - 1$$

**公式 2**：$\sum_{j=2}^{n} (j-1)$

$$\sum_{j=2}^{n} (j-1) = 1 + 2 + \cdots + (n-1) = \frac{n(n-1)}{2}$$

將這些代入總執行時間：

$$T(n) = an^2 + bn + c$$

其中 $a, b, c$ 是由 $c_1, c_2, \ldots, c_8$ 組合而成的常數。因此最壞情況時間複雜度為 $\Theta(n^2)$。
