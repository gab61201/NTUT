# Algorithms Midterm Exam — 演算法期中考講義

---

## 📋 Course Overview / 課程總覽

| Problem | Topic | Link |
|---------|-------|------|
| **1** | Modified Merge-Sort + Insertion-Sort | [→ 01_modified_merge_sort.md](01_modified_merge_sort.md) |
| **2** | Recursive Binary Search | [→ 02_binary_search.md](02_binary_search.md) |
| **3** | Substitution Method Proof | [→ 03_substitution_method.md](03_substitution_method.md) |
| **4** | Sorting Algorithms Anatomy | [→ 04_sorting_anatomy.md](04_sorting_anatomy.md) |

---

## 🗺️ Knowledge Structure / 知識結構圖

```
演算法期中考
├── 排序演算法 (Sorting Algorithms)
│   ├── Merge-Sort (Θ(n lg n))
│   ├── Insertion-Sort (Θ(n²) worst-case, Θ(k²) on size-k list)
│   ├── Modified Merge-Sort (Θ(nk + n lg(n/k)))
│   │   ├── 排序 n/k 個長度 k 的子列表: Θ(nk)
│   │   ├── 合併子列表: Θ(n lg(n/k))
│   │   └── 最佳 k 值: Θ(lg n)
│   ├── Quicksort (平均 Θ(n lg n), 最壞 Θ(n²))
│   │   ├── Tight code — 內層迴圈效率高
│   │   ├── In-place 排序
│   │   └── 資料局部性 (Cache locality) 佳
│   └── Heapsort (Θ(n lg n) 最壞情況)
│       ├── O(1) 額外空間
│       └── 適合安全關鍵系統
├── 搜尋演算法 (Search Algorithms)
│   └── Binary Search (Θ(lg n))
│       ├── 遞迴偽程式碼
│       └── 遞迴式: T(n) = T(n/2) + Θ(1)
└── 遞迴式分析 (Recurrence Analysis)
    ├── 代入法 (Substitution Method)
    │   ├── 猜解 → 代入 → 驗證
    │   └── 上下界都需要證明
    └── T(n) = T(n-1) + Θ(n) → Θ(n²)
```

---

## 📌 Formula Quick-Reference / 核心公式速查表

| Concept | Formula |
|---------|---------|
| Modified Merge-Sort — Sorting | $(n/k) \times \Theta(k^2) = \Theta(nk)$ |
| Modified Merge-Sort — Merging | $\Theta(n \lg(n/k))$ |
| Modified Merge-Sort — Total | $\Theta(nk + n \lg(n/k))$ |
| Modified Merge-Sort — Optimal k | $k = \Theta(\lg n)$ |
| Binary Search Recurrence | $T(n) = T(n/2) + \Theta(1) \Rightarrow T(n) = \Theta(\lg n)$ |
| Substitution Method Example | $T(n) = T(n-1) + \Theta(n) \Rightarrow T(n) = \Theta(n^2)$ |
| Quicksort — Average | $T(n) = \Theta(n \lg n)$ |
| Quicksort — Worst-case | $T(n) = \Theta(n^2)$ |
| Heapsort — All cases | $T(n) = \Theta(n \lg n)$ |
| Heapsort — Space | $O(1)$ |

---

## 📝 Example Index / 重要範例索引

| Example | Topic | Section |
|---------|-------|---------|
| Problem 1a | Insertion-Sort on n/k sublists | [1](01_modified_merge_sort.md) |
| Problem 1b | Merging n/k sublists | [1](01_modified_merge_sort.md) |
| Problem 1c | Optimal k for modified merge-sort | [1](01_modified_merge_sort.md) |
| Problem 1d | Practical k selection (Timsort, Java) | [1](01_modified_merge_sort.md) |
| Problem 2a | Binary Search pseudocode | [2](02_binary_search.md) |
| Problem 2b | Binary Search recurrence solution | [2](02_binary_search.md) |
| Problem 3 | Substitution method proof — T(n) = T(n-1) + Θ(n) | [3](03_substitution_method.md) |
| Problem 4a | Tight code & constant factors | [4](04_sorting_anatomy.md) |
| Problem 4b | Heapsort vs Quicksort for safety-critical systems | [4](04_sorting_anatomy.md) |

---

## 🖼️ Image Resources / 圖片資源

| File | Description |
|------|-------------|
| *(None)* | 本次考試為純文字題目，無圖片 |

---

## 📚 Source Material / 原始教材

- **Source**: `Midterm Exam_114 (take home).doc` (Legacy OLE2 .doc format)
- **Exam Type**: Algorithms Mid-term Exam (Take home, 40%)
- **Due Date**: 2026/05/08
- **Pages**: 1 (extracted via `antiword`)
- **Format**: Pure text (no embedded images or Equation Editor objects)
