# Algorithms Midterm Exam (Take Home 40%) / 演算法期中考（居家作答 40%）

**Due: 2026/05/08**

---

## 📋 Exam Overview / 考題總覽

| Problem | Topic | Key Concept | Link |
|---------|-------|-------------|------|
| **1** | Modified MERGE-SORT | INSERTION-SORT + MERGE-SORT hybrid, asymptotic analysis | [→ 01_modified_mergesort.md](01_modified_mergesort.md) |
| **2** | Binary Search | Recursive pseudocode, recurrence $T(n) = T(n/2) + \Theta(1)$ | [→ 02_binary_search.md](02_binary_search.md) |
| **3** | Substitution Method | Prove $T(n) = T(n-1) + \Theta(n) \Rightarrow \Theta(n^2)$ | [→ 03_substitution_method.md](03_substitution_method.md) |
| **4** | Sorting Algorithm Anatomy | Tight code, constant factors, safety-critical system trade-offs | [→ 04_sorting_algorithm_analysis.md](04_sorting_algorithm_analysis.md) |

> **模板**：每題使用 4-section 結構 📖 原文 → 🇹🇼 中文翻譯 → 💡 詳細解釋 → 🔢 推導過程

---

## 🗺️ Knowledge Structure / 知識結構圖

```
Algorithms Midterm
├── Problem 1: Hybrid Sort Design ─── INSERTION-SORT + MERGE-SORT
│   ├── (a) INSERTION-SORT cost: Θ(nk)
│   ├── (b) Merge cost: Θ(n lg(n/k))
│   ├── (c) Asymptotic equivalence: k = Θ(lg n)
│   └── (d) Practical k selection: constant factors, benchmarking
│
├── Problem 2: Binary Search ─── Divide & Conquer prototype
│   ├── (a) Pseudocode: recursive binary search
│   └── (b) Recurrence: T(n) = T(n/2) + Θ(1) → Θ(log n)
│
├── Problem 3: Substitution Method ─── Proof technique
│   └── T(n) = T(n-1) + Θ(n) → Θ(n²)
│       ├── Upper bound: O(n²) by induction
│       └── Lower bound: Ω(n²) by induction
│
└── Problem 4: Sorting Algorithm Engineering
    ├── (a) Tight code → smaller constant C in Quicksort
    └── (b) Heapsort wins for safety-critical: O(n log n) guarantee + O(1) space
```

---

## 📌 Formula Quick-Reference / 核心公式速查表

| Concept | Formula / Expression |
|---------|---------------------|
| INSERTION-SORT worst-case | $\Theta(m^2)$ for length $m$ |
| MERGE-SORT | $\Theta(n \log n)$ |
| Modified MERGE-SORT | $\Theta(nk + n \lg(n/k))$ |
| Binary Search recurrence | $T(n) = T(n/2) + \Theta(1)$ |
| Master Theorem Case 2 | $T(n) = \Theta(n^{\log_b a} \log n)$ when $f(n) = \Theta(n^{\log_b a})$ |
| Substitution guess | $T(n) \leq cn^2$ (upper bound) |
| Arithmetic series | $\sum_{i=1}^{n} i = \Theta(n^2)$ |
| Quicksort average | $\Theta(n \log n)$ with small constant $C$ |
| Heapsort worst-case | $\Theta(n \log n)$, $O(1)$ extra space |

---

## 📝 Problem Type Index / 題型索引

| Type | Problem | Description |
|------|---------|-------------|
| Asymptotic Analysis | 1(a)(b)(c) | Deriving and simplifying Θ-expressions |
| Parameter Optimization | 1(c)(d) | Finding optimal k in hybrid algorithm |
| Pseudocode Writing | 2(a) | Recursive BINARY-SEARCH |
| Recurrence Solving | 2(b), 3 | Master Theorem + Substitution Method |
| Conceptual Comparison | 4(a)(b) | Tight code, engineering trade-offs |

---

## 📚 Source Material / 原始教材

- **Source**: `Midterm Exam_114 (take home).doc` (38 KB, legacy OLE2 format)
- **Extracted by**: antiword (text), no Equation Editor objects
- **Date**: Spring 2026 (114 學年度)
