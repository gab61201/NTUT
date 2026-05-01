# 03. Efficiency of an Algorithm

> **Slide 4**

---

## 📖 Original Text / 原文

Efficiency of an algorithm

- Time (speed) and space (memory).
- Some problems do not have efficient solution yet (hard problems).

---

## 🇹🇼 Chinese Translation / 中文翻譯

**演算法的效率**

- 時間（速度）與空間（記憶體）。
- 有些問題目前還沒有高效的解法（難題）。

---

## 💡 Detailed Explanation / 詳細解釋

### 1. 時間效率（Time Efficiency）

時間效率指演算法執行所需的時間，通常用**時間複雜度**（time complexity）來衡量：

| 複雜度 | 名稱 | 範例 |
|:---|:---|:---|
| $O(1)$ | 常數時間 | 陣列索引存取 |
| $O(\log n)$ | 對數時間 | 二分搜尋 |
| $O(n)$ | 線性時間 | 線性搜尋 |
| $O(n \log n)$ | 線性對數時間 | 合併排序、快速排序 |
| $O(n^2)$ | 二次時間 | 氣泡排序 |
| $O(2^n)$ | 指數時間 | 遞迴費氏數列 |
| $O(n!)$ | 階乘時間 | 暴力排列組合 |

### 2. 空間效率（Space Efficiency）

空間效率指演算法執行所需的記憶體空間，通常用**空間複雜度**（space complexity）來衡量。

### 3. 難題（Hard Problems）

有些問題目前尚未找到高效解法：

- **旅行推銷員問題（TSP）**：尋找最短路徑訪問所有城市。暴力解法需要 $O(n!)$ 時間。
- **背包問題（Knapsack）**：在容量限制下選擇價值最高的物品組合。
- **圖著色問題（Graph Coloring）**：用最少的顏色為圖著色，使得相鄰節點顏色不同。

這些問題屬於**NP-hard** 或 **NP-complete** 類別，目前已知沒有多項式時間的解法。

### 4. 處理難題的策略

| 策略 | 說明 |
|:---|:---|
| 近似演算法（Approximation） | 求得接近最佳解的解法 |
| 啟發式方法（Heuristic） | 基於經驗規則的快速解法 |
| 隨機化演算法（Randomized） | 引入隨機性的解法 |
| 限制問題規模 | 在小規模輸入上求精確解 |
