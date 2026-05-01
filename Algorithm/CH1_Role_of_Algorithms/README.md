# Chapter 1: The Role of Algorithms in Computing / 第一章：演算法在運算中的角色

---

## 📋 Course Overview / 課程總覽

本章為《Introduction to Algorithms》（CLRS）的第一章，介紹演算法的基本概念、資料結構的重要性、演算法效率的衡量方式，以及計算複雜度理論（P、NP、NP-Complete）的基礎。

| Section | Topic | Link |
|---------|-------|------|
| **1.1** | Introduction & Definition of Algorithm | [→ 01_introduction_definition.md](01_introduction_definition.md) |
| **1.2** | Algorithm and Data Structure | [→ 02_algorithm_and_data_structure.md](02_algorithm_and_data_structure.md) |
| **1.3** | Efficiency of an Algorithm | [→ 03_efficiency_of_algorithms.md](03_efficiency_of_algorithms.md) |
| **1.4** | Computers and Intractability | [→ 04_computers_and_intractability.md](04_computers_and_intractability.md) |
| **1.5** | P, NP, and NP-complete Problems | [→ 05_p_np_and_np_complete.md](05_p_np_and_np_complete.md) |
| **1.6** | NP-completeness | [→ 06_np_completeness.md](06_np_completeness.md) |
| **1.7** | Proof of NP-completeness | [→ 07_proof_of_np_completeness.md](07_proof_of_np_completeness.md) |

---

## 🗺️ Knowledge Structure / 知識結構圖

```
Chapter 1: The Role of Algorithms in Computing
│
├── 1. What is an Algorithm?
│   ├── Well-defined computation procedure
│   ├── Input → Output mapping
│   └── Correctness: halts with correct output
│
├── 2. Algorithm & Data Structure
│   ├── Knuth: founder of field
│   ├── Wirth: Algorithms + Data Structures = Programs
│   └── Time-space trade-off
│
├── 3. Efficiency
│   ├── Time (speed)
│   ├── Space (memory)
│   └── Hard problems (no efficient solution yet)
│
├── 4. Intractability
│   └── Garey & Johnson (1979): NP-Completeness theory
│
├── 5. Complexity Classes
│   ├── P: solvable in polynomial time (tractable)
│   ├── NP: verifiable in polynomial time
│   └── NP-complete: hardest problems in NP
│       └── P ⊆ NP ⊆ NP-complete (conjectured P ≠ NP)
│
└── 6. NP-Completeness & Reduction
    ├── NP-complete = NP ∩ NP-hard
    ├── Polynomial-time reduction: B ≤ₚ A
    └── If B is NP-complete and B ≤ₚ A, then A is NP-complete
```

---

## 📌 Formula Quick-Reference / 核心公式速查表

| Concept | Formula | Description |
|---------|---------|-------------|
| Complexity Class P | $O(n^k)$ | Polynomial time — tractable |
| P vs NP relationship | $P \subseteq NP$ | Every P problem is also in NP |
| NP-Complete definition | $\text{NP-complete} = \{A \mid A \in NP \land A \text{ is NP-hard}\}$ | In NP and at least as hard as all NP problems |
| Polynomial-time reduction | $B \leq_p A$ | B can be transformed to A in polynomial time |
| NP-Completeness proof | $B$ is NP-complete $\land$ $B \leq_p A$ $\implies$ $A$ is NP-complete | Reduction-based proof technique |
| Wirth's formula | $\text{Algorithms} + \text{Data Structures} = \text{Programs}$ | Programs are composed of algorithms and data structures |

---

## 📝 Example Index / 重要範例索引

| Example | Topic | Section |
|---------|-------|------|
| Algorithm correctness definition | Strict correctness (halts + correct output) | [1.1](01_introduction_definition.md) |
| Wirth's formula | Algorithms + Data Structures = Programs | [1.2](02_algorithm_and_data_structure.md) |
| Time-space trade-off | Choosing data structures involves trade-offs | [1.2](02_algorithm_and_data_structure.md) |
| Garey & Johnson cartoon | Famous NP-Completeness cartoon | [1.4](04_computers_and_intractability.md) |
| P vs NP Venn diagram | Relationship between complexity classes | [1.5](05_p_np_and_np_complete.md) |
| Reduction proof technique | How to prove a problem is NP-complete | [1.7](07_proof_of_np_completeness.md) |

---

## 📚 Source Material / 原始教材

- **Source**: `Lec1_Chapter01_v1.ppt` (Legacy PPT / OLE2 format)
- **Converted**: `Lec1_Chapter01_v1.pdf` (8 slides, via LibreOffice headless)
- **Topic**: Introduction to Algorithms — Chapter 1
- **Reference**: Cormen, Leiserson, Rivest, Stein. *Introduction to Algorithms* (CLRS)
