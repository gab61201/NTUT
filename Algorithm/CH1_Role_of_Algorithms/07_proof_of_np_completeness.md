# 07. Proof of NP-Completeness

> **Slide 8**

---

## 📖 Original Text / 原文

Proof of NP-completeness

- NP-completeness is about showing how hard a problem is
- How these new problems are shown to be NP-complete rely on a new technique, called reduction
- Problem Reduction
  - We consider B is an NP-complete problem, A is another problem in NP
  - Suppose that we can show that:
    1. we can transform a problem of B into a problem of A, using polynomial time (B ≤p A), i.e. B is not more than a polynomial factor harder than A
    2. A is at least as hard as B (We can solve B if we can solve A)
  - Then we can conclude A is NP-complete (However, A is NP-hard if A is not a NP problem)

---

## 🇹🇼 Chinese Translation / 中文翻譯

**NP-完全性的證明**

- NP-完全性是用來展示一個問題有多困難
- 這些新問題如何被證明為 NP-完全，依賴於一種稱為「歸約」（reduction）的新技術
- 問題歸約
  - 假設 B 是一個 NP-完全問題，A 是另一個 NP 中的問題
  - 假設我們可以證明：
    1. 我們可以在多項式時間內將 B 的問題轉換為 A 的問題（B ≤p A），即 B 不超過 A 的多項式倍困難
    2. A 至少與 B 一樣困難（如果我們能解 A，就能解 B）
  - 那麼我們可以得出 A 是 NP-完全的（然而，如果 A 不是 NP 問題，則 A 是 NP-hard）

---

## 💡 Detailed Explanation / 詳細解釋

### 什麼是歸約（Reduction）？

歸約是一種將一個問題轉換為另一個問題的技术。如果我們能將已知困難的問題 B 轉換為問題 A，則 A 至少與 B 一樣困難。

**直觀理解**：如果我有一台能解 A 的「魔機」，我就能用它來解 B。因此 A 不比 B 容易。

### 多項式時間歸約 $B \leq_p A$

- 將 B 的輸入轉換為 A 的輸入，轉換過程本身必須在多項式時間內完成
- 這意味著：如果 A 有多項式時間解法，則 B 也有多項式時間解法

### 證明 A 是 NP-Complete 的步驟

| 步驟 | 內容 |
|------|------|
| 1 | 證明 A ∈ NP（可在多項式時間內驗證） |
| 2 | 選擇一個已知的 NP-Complete 問題 B |
| 3 | 證明 $B \leq_p A$（B 可多項式時間歸約到 A） |
| 4 | 結論：A 是 NP-Complete |

### NP-Complete vs NP-Hard

| 類別 | 定義 | 關係 |
|------|------|------|
| **NP-Hard** | 至少與 NP 中任何問題一樣困難 | 不一定在 NP 內 |
| **NP-Complete** | 同時在 NP 內且為 NP-Hard | NP-Complete ⊆ NP-Hard |

### Cook-Levin 定理

- **Stephen Cook (1971)** 和 **Leonid Levin (1973)** 獨立證明了 SAT 是第一個 NP-Complete 問題
- 此後，所有其他 NP-Complete 問題都是透過歸約鏈從 SAT 證明而來
- 歸約具有**傳遞性**：若 $A \leq_p B$ 且 $B \leq_p C$，則 $A \leq_p C$
