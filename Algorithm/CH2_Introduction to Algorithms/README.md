# Lec2 — Chapter 2: Getting Started (演算法入門)

---

## 📋 Course Overview / 課程總覽

| Slide | Topic | Link |
|-------|-------|------|
| **01** | Title — Introduction to Algorithms, Chapter 2 | [→ 01_slide01_title.md](01_slide01_title.md) |
| **02** | Sorting Problem (排序問題) | [→ 02_slide02_sorting_problem.md](02_slide02_sorting_problem.md) |
| **03** | Insertion Sort Example (插入排序範例) | [→ 03_slide03_insertion_sort_example.md](03_slide03_insertion_sort_example.md) |
| **04** | INSERTION-SORT Pseudocode (插入排序擬似碼) | [→ 04_slide04_insertion_sort_pseudocode.md](04_slide04_insertion_sort_pseudocode.md) |
| **05** | Cost Analysis (成本分析) | [→ 05_slide05_cost_analysis.md](05_slide05_cost_analysis.md) |
| **06** | Analysis of Insertion Sort (cont'd) | [→ 06_slide06_analysis_continued.md](06_slide06_analysis_continued.md) |
| **07** | Best and Worst Case (最佳與最壞情況) | [→ 07_slide07_best_worst_case.md](07_slide07_best_worst_case.md) |
| **08** | Sorted in Place (就地排序) | [→ 08_slide08_sorted_in_place.md](08_slide08_sorted_in_place.md) |
| **09** | Stable Property (穩定性) | [→ 09_slide09_stable_property.md](09_slide09_stable_property.md) |
| **10** | Divide-and-Conquer Approach (分治策略) | [→ 10_slide10_divide_and_conquer.md](10_slide10_divide_and_conquer.md) |
| **11** | MERGE Pseudocode (合併擬似碼) | [→ 11_slide11_merge_pseudocode.md](11_slide11_merge_pseudocode.md) |
| **12** | MERGE Example (合併範例) | [→ 12_slide12_merge_example.md](12_slide12_merge_example.md) |
| **13** | MERGE-SORT Pseudocode (歸併排序擬似碼) | [→ 13_slide13_merge_sort_pseudocode.md](13_slide13_merge_sort_pseudocode.md) |
| **14** | MERGE-SORT Example (歸併排序範例) | [→ 14_slide14_merge_sort_example.md](14_slide14_merge_sort_example.md) |
| **15** | Analyzing Divide-and-Conquer (分析分治演算法) | [→ 15_slide15_analyzing_divide_conquer.md](15_slide15_analyzing_divide_conquer.md) |
| **16** | Recursion Tree (遞迴樹) | [→ 16_slide16_recursion_tree.md](16_slide16_recursion_tree.md) |
| **17** | BUBBLE-SORT (氣泡排序) | [→ 17_slide17_bubble_sort.md](17_slide17_bubble_sort.md) |

---

## 🗺️ Knowledge Structure / 知識結構圖

```
Chapter 2: Getting Started
│
├── Part 1: Insertion Sort (插入排序)
│   ├── Sorting Problem (排序問題)
│   │   └── Card sorting analogy (撲克牌比喻)
│   ├── INSERTION-SORT Algorithm
│   │   ├── Pseudocode (擬似碼)
│   │   ├── Loop Invariant (迴圈不變式)
│   │   └── Correctness Proof (正確性證明)
│   ├── Analysis (分析)
│   │   ├── Cost Analysis (成本分析)
│   │   ├── Best Case: Θ(n) (最佳情況)
│   │   ├── Worst Case: Θ(n²) (最壞情況)
│   │   └── Summation Formulas (求和公式)
│   ├── Properties (性質)
│   │   ├── Sorted in Place (就地排序) — O(1) space
│   │   └── Stable (穩定性)
│   │
├── Part 2: Divide-and-Conquer (分治策略)
│   ├── Three Steps (三個步驟)
│   │   ├── Divide (分解)
│   │   ├── Conquer (解決)
│   │   └── Combine (合併)
│   │
│   └── Merge Sort (歸併排序)
│       ├── MERGE(A, p, q, r)
│       │   ├── Sentinel (哨兵)
│       │   └── Θ(n) time
│       ├── MERGE-SORT(A, p, r)
│       │   ├── Recursive structure (遞迴結構)
│       │   └── Recurrence: T(n) = 2T(n/2) + Θ(n)
│       └── Analysis
│           ├── Recursion Tree (遞迴樹)
│           ├── Master Theorem (主定理)
│           └── Θ(n lg n)
│
└── Part 3: Bubble Sort (氣泡排序)
    ├── Pseudocode
    └── Θ(n²) time complexity
```

---

## 📌 Formula Quick-Reference / 核心公式速查表

| Concept | Formula |
|---------|---------|
| **Insertion Sort — Best Case** | $T(n) = an + b = \Theta(n)$ |
| **Insertion Sort — Worst Case** | $T(n) = an^2 + bn + c = \Theta(n^2)$ |
| **Summation** | $\sum_{j=2}^{n} j = \frac{n(n+1)}{2} - 1$ |
| **Summation** | $\sum_{j=2}^{n} (j-1) = \frac{n(n-1)}{2}$ |
| **Merge Sort — Recurrence** | $T(n) = 2T(n/2) + \Theta(n)$ |
| **Merge Sort — Time** | $T(n) = \Theta(n \lg n)$ |
| **Divide-and-Conquer — General** | $T(n) = aT(n/b) + D(n) + C(n)$ |
| **Recursion Tree — Total Cost** | $cn(\lg n + 1) = \Theta(n \lg n)$ |
| **Bubble Sort — Time** | $T(n) = \frac{n(n-1)}{2} = \Theta(n^2)$ |

---

## 📝 Example Index / 重要範例索引

| Example | Topic | Slide |
|---------|-------|-------|
| Figure 2.1 | Card sorting analogy | [Slide 02](02_slide02_sorting_problem.md) |
| Figure 2.2 | INSERTION-SORT on $A = (5, 2, 4, 6, 1, 3)$ | [Slide 03](03_slide03_insertion_sort_example.md) |
| Figure 2.3 | MERGE(A, 9, 12, 16) step-by-step | [Slide 12](12_slide12_merge_example.md) |
| Figure 2.4 | MERGE-SORT on $A = (5, 2, 4, 7, 1, 3, 2, 6)$ | [Slide 14](14_slide14_merge_sort_example.md) |
| Figure 2.5 | Recursion tree for $T(n) = 2T(n/2) + cn$ | [Slide 16](16_slide16_recursion_tree.md) |

---

## 🖼️ Image Resources / 圖片資源

### Original PPT Slides / 原始投影片

| Slide | Description | Image |
|-------|-------------|-------|
| 01 | Title — Chapter 2 | [slide_01.png](images/slide_01.png) |
| 02 | Figure 2.1 — Card sorting | [slide_02.png](images/slide_02.png) |
| 03 | Figure 2.2 — Insertion Sort trace | [slide_03.png](images/slide_03.png) |
| 04 | INSERTION-SORT pseudocode | [slide_04.png](images/slide_04.png) |
| 05 | Cost analysis table | [slide_05.png](images/slide_05.png) |
| 06 | Summation formulas | [slide_06.png](images/slide_06.png) |
| 07 | Best/worst case analysis | [slide_07.png](images/slide_07.png) |
| 08 | Sorted in Place | [slide_08.png](images/slide_08.png) |
| 09 | Stable Property | [slide_09.png](images/slide_09.png) |
| 10 | Divide-and-Conquer Approach | [slide_10.png](images/slide_10.png) |
| 11 | MERGE pseudocode | [slide_11.png](images/slide_11.png) |
| 12 | Figure 2.3 — MERGE trace | [slide_12.png](images/slide_12.png) |
| 13 | MERGE-SORT pseudocode | [slide_13.png](images/slide_13.png) |
| 14 | Figure 2.4 — Merge Sort trace | [slide_14.png](images/slide_14.png) |
| 15 | Divide-and-Conquer analysis | [slide_15.png](images/slide_15.png) |
| 16 | Figure 2.5 — Recursion tree | [slide_16.png](images/slide_16.png) |
| 17 | BUBBLE-SORT pseudocode | [slide_17.png](images/slide_17.png) |

---

## 📚 Source Material / 原始教材

- **Source**: `Lec2_chapter02.ppt` (Legacy PPT / OLE2 format, 17 slides)
- **Textbook**: Introduction to Algorithms, Second Edition by Cormen, Leiserson, Rivest & Stein (CLRS)
- **Chapter**: Chapter 2 — Getting Started
- **Converted PDF**: `output/Lec2_chapter02.pdf` (17 pages)
- **Rendered Slides**: `output/pages/slide_01.png` — `slide_17.png` (150 DPI)
