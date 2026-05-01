# 05. P, NP, and NP-Complete Problems

> **Slide 6**

---

## 📖 Original Text / 原文

---

P, NP, and NP-complete problems

- Class P: decision problems (contrast to optimization problem) that are solvable in polynomial time, i.e. O(nk), a.k.a. tractable
- Class NP (Nondeterministic Polynomial): decision problems that are verifiable in polynomial time if you are given a certificate of a solution. (P  NP)
- Class NP-complete
  - a subset of NP, whose status is unknown
  - no polynomial-time algorithm has yet been discovered
  - nor has anyone yet been able to prove that no polynomial-time algorithm can exist for any one of them
  - at least as hard as any problem in NP
- The relationship between P, NP, and NPC
  - https://ycc.idv.tw/algorithm-complexity-theory.html

---

## 🇹🇼 Chinese Translation / 中文翻譯

**P、NP 與 NP-Complete 問題**

- **類別 P**：決策問題（與最佳化問題相對），可在多項式時間內求解，即 $O(n^k)$，稱為可處理的（tractable）。
- **類別 NP**（非確定性多項式時間）：決策問題，若給定解的證明（certificate），可在多項式時間內驗證該解是否正確。（$P \subseteq NP$）
- **類別 NP-Complete**（NP 完全）：
  - NP 的一個子集，其地位尚不清楚
  - 至今尚未發現任何多項式時間演算法
  - 也尚未有人能證明不存在多項式時間演算法
  - 至少與 NP 中任何問題一樣困難
- P、NP 與 NPC 的關係
  - https://ycc.idv.tw/algorithm-complexity-theory.html

---

## 💡 Detailed Explanation / 詳細解釋

### 三大複雜度類別的對比

| 類別 | 定義 | 關鍵特性 |
|------|------|----------|
| **P** | 可在多項式時間內**求解**的決策問題 | 高效可解，稱為「可處理」 |
| **NP** | 給定 certificate 後可在多項式時間內**驗證**的問題 | 包含 P，範圍更廣 |
| **NP-Complete** | 同時是 NP 問題且是 NP 中最難的 | 若任一 NPC 問題 ∈ P，則 P = NP |

### 關鍵概念解析

#### 1. 決策問題 vs. 最佳化問題

- **決策問題**：答案是「是」或「否」。例如：「是否存在一條路徑長度 ≤ K？」
- **最佳化問題**：尋求最佳值。例如：「最短路徑長度是多少？」

> 注意：P 和 NP 的定義基於決策問題，但許多最佳化問題的決策版本也屬於這些類別。

#### 2. 為什麼 $P \subseteq NP$？

如果一個問題可以在多項式時間內求解，自然也可以在多項式時間內驗證（直接跑演算法即可）。因此 P 是 NP 的子集。

#### 3. NP-Complete 的「完全」意味著什麼？

- **NP-Hard**：至少與 NP 中任何問題一樣困難（可能不在 NP 內）。
- **NP-Complete**：同時是 NP 問題且 NP-Hard。
- 重要性質：若任一 NP-Complete 問題被證明有 $O(n^k)$ 的解法，則所有 NP 問題都有多項式時間解法。

#### 4. P vs NP 問題

- 這是千禧年七大難題之一，解答者可得 100 萬美元獎金。
- 多數學者相信 $P \neq NP$，但至今無人能證明。
- 若 $P = NP$，將徹底改變密碼學、優化、人工智慧等領域。
