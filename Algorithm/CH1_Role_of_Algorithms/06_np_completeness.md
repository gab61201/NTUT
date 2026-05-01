# 06. NP-Completeness

> **Slide 7**

---

## 📖 Original Text / 原文

NP-completeness

- A decision problem (not an optimization problem) is NP-complete when it is both in NP and NP-hard
  - https://en.wikipedia.org/wiki/NP-completeness
- To become a good algorithm designer, you must understand the rudiments of the theory of NP-completeness. If you can show that the problem is NP-complete, you can instead spend your time developing an efficient (or approximation) algorithm that gives a good, but not the best possible, solution.
- List of NP-complete problems
  - https://en.wikipedia.org/wiki/List_of_NP-complete_problems

---

## 🇹🇼 Chinese Translation / 中文翻譯

**NP-完全性**

- 一個決策問題（非最佳化問題）在同時屬於 NP 且為 NP-hard 時，稱為 NP-完全（NP-complete）
  - https://en.wikipedia.org/wiki/NP-completeness
- 要成為優秀的演算法設計者，你必須了解 NP-完全性理論的基礎。如果你能證明問題是 NP-完全的，你可以將時間花在開發高效的（或近似）演算法上，該演算法能給出良好但非最佳的解。
- NP-完全問題列表
  - https://en.wikipedia.org/wiki/List_of_NP-complete_problems

---

## 💡 Detailed Explanation / 詳細解釋

### NP-Complete 的定義

NP-Complete 問題必須同時滿足兩個條件：

| 條件 | 說明 |
|------|------|
| **屬於 NP** | 給定 certificate 後可在多項式時間內驗證 |
| **NP-Hard** | 至少與 NP 中任何問題一樣困難 |

### 為什麼要理解 NP-Completeness？

- 如果你的問題被證明是 NP-Complete，就不需要繼續尋找「完美解」的多項式時間演算法。
- 應該轉向：
  - **近似演算法**（Approximation Algorithm）：保證解在最佳解的一定比例內
  - **啟發式方法**（Heuristic）：基於經驗規則的快速解法
  - **隨機化演算法**（Randomized Algorithm）：引入隨機性的解法

### 經典 NP-Complete 問題

| 問題 | 說明 |
|------|------|
| **SAT** | 布林公式可满足性問題（第一個被證明的 NP-Complete 問題） |
| **3-SAT** | 三元子句的布林公式可满足性 |
| **Clique** | 圖中是否存在大小為 k 的團 |
| **Independent Set** | 圖中是否存在大小為 k 的獨立集 |
| **Vertex Cover** | 圖中是否存在大小為 k 的頂點覆蓋 |
| **Hamiltonian Cycle** | 圖中是否存在哈密頓回路 |
| **TSP** | 旅行推銷員問題 |
| **Knapsack** | 背包問題（決策版本） |
