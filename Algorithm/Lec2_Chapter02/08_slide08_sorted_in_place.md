# Slide 08 — Sorted in Place (就地排序)

## 📖 Original Text / 原文

---

**Sorted in Place**

- The input numbers are rearranged within the array $A$, with at most a constant number of them stored outside the array at any time.
- INSERTION-SORT has the property of sorted in place.

## 🇹🇼 Chinese Translation / 中文翻譯

**就地排序**

- 輸入的數字在陣列 $A$ 內部重新排列，任何時候最多只有常數個數字儲存在陣列外部。
- 插入排序具有就地排序的特性。

## 💡 Detailed Explanation / 詳細解釋

**就地排序（Sorted In Place）**的定義：

- 排序過程中只使用**額外 $O(1)$ 的空間**
- 只有 `key`、`i`、`j` 等常數個變數存放在陣列外
- 所有的元素交換/移動都在原陣列 $A$ 內完成

插入排序的空間複雜度為 $O(1)$，是**就地排序**演算法。

**對比其他排序**：
- 歸併排序（Merge Sort）：需要 $O(n)$ 額外空間 → **不是**就地排序
- 快速排序（Quick Sort）：平均 $O(\log n)$ 堆疊空間 → 可視為就地排序
