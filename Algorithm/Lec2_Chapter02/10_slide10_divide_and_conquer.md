# Slide 10 — Divide-and-Conquer Approach (分治法)

## 📖 Original Text / 原文

---

**Divide-and-Conquer Approach**

1. **Divide**: breaking it into subproblems that are themselves smaller instances of the same type of problem
2. **Conquer**: recursively solving these subproblems
3. **Combine**: combine the solutions to the subproblems into the solution for the original problem

## 🇹🇼 Chinese Translation / 中文翻譯

**分治策略**

1. **分解（Divide）**：將問題分解為若干個較小的子問題，這些子問題是同一類問題的小規模實例
2. **解決（Conquer）**：遞迴地解決這些子問題
3. **合併（Combine）**：將子問題的解合併為原問題的解

## 💡 Detailed Explanation / 詳細解釋

**分治法（Divide-and-Conquer）**是演算法設計中最重要且最廣泛使用的策略之一：

| 步驟 | 說明 | 時間表示 |
|------|------|---------|
| Divide | 將問題拆分為 $b$ 個子問題 | $D(n)$ |
| Conquer | 遞迴解決 $a$ 個子問題 | $a \cdot T(n/b)$ |
| Combine | 合併子問題的答案 | $C(n)$ |

**遞迴式通式**：

$$T(n) = aT\left(\frac{n}{b}\right) + D(n) + C(n)$$

**經典範例**：
- 歸併排序（Merge Sort）— 本章重點
- 快速排序（Quick Sort）
- 二分搜尋（Binary Search）
- 最大子陣列問題（Maximum Subarray）
