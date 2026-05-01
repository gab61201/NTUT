# Slide 07 — Best and Worst Case Analysis (最佳與最壞情況分析)

## 📖 Original Text / 原文

---

**Analysis of Insertion Sort**

- If the array is already sorted, $t_j = 1$ for $j = 2, 3, \ldots, n$, and the best-case running time is $an + b$.
- If the array is in reverse sorted order, then we must compare each element $A[j]$ with each element in the entire sorted subarray, and so $t_j = j$ for $j = 2, 3, \ldots, n$, the worst case running time is $an^2 + bn + c$.

## 🇹🇼 Chinese Translation / 中文翻譯

**插入排序分析**

- 如果陣列已經排序完成，$t_j = 1$ 對於 $j = 2, 3, \ldots, n$，最佳情況執行時間為 $an + b$。
- 如果陣列是完全逆序排列，則必須將每個元素 $A[j]$ 與整個已排序子陣列中的每個元素比較，因此 $t_j = j$ 對於 $j = 2, 3, \ldots, n$，最壞情況執行時間為 $an^2 + bn + c$。

## 💡 Detailed Explanation / 詳細解釋

| 情況 | 條件 | $t_j$ | 時間複雜度 |
|------|------|-------|-----------|
| **最佳情況** | 陣列已排序 | $t_j = 1$ | $\Theta(n)$ |
| **最壞情況** | 陣列完全逆序 | $t_j = j$ | $\Theta(n^2)$ |

**最佳情況**：when $t_j = 1$，while 迴圈每次只執行一次測試就失敗（$A[i] \leq$ key），總共只需線性時間。

**最壞情況**：when $t_j = j$，每個元素都要和前面所有已排序元素比較，總比較次數為 $\frac{n(n-1)}{2}$，因此是 $\Theta(n^2)$。

**重要觀念**：演算法分析通常關注**最壞情況**（worst-case），因為它提供了執行時間的上界保證。
