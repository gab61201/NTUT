# Chapter 3: Growth of Functions / 函數增長率

---

## 📋 Course Overview / 課程總覽

| Section | Topic | Link |
|---------|-------|------|
| **3.1–3.5** | Introduction, Overview, Asymptotic Analysis, Notation, Growth Rates | [→ 01_introduction_and_growth_rates.md](01_introduction_and_growth_rates.md) |
| **3.6–3.15** | O, Ω, Θ, o, ω Notations, Simplification, Exercises, Summary | [→ 02_asymptotic_notations.md](02_asymptotic_notations.md) |

---

## 🗺️ Knowledge Structure / 知識結構圖

```
Chapter 3: Growth of Functions
├── 3.1 Introduction
├── 3.2 Overview
│   ├── Order of growth → simple characterization of efficiency
│   ├── Asymptotic efficiency → comparison of algorithms
│   └── Best asymptotic ≠ best for small inputs
├── 3.3 Asymptotic Analysis
│   └── Study behavior as n → ∞
├── 3.4 Asymptotic Notation
│   └── Formal framework for growth comparison
├── 3.5 Growth Rates
│   ├── log n < √n < n < n log n < n² < n³ < 2ⁿ
│   └── Constant factors don't matter asymptotically
├── 3.6–3.8 Core Notations
│   ├── O(g(n))    : upper bound (≤)
│   ├── Ω(g(n))    : lower bound (≥)
│   └── Θ(g(n))    : tight bound (=) = O ∩ Ω
├── 3.9 Set Relationships
│   └── Venn diagram of O(n²), Ω(n²), Θ(n²)
├── 3.10 Copyright Notice
│   └── McGraw-Hill copyright page
├── 3.11 Simplifying Analysis
│   └── Drop low-order terms, ignore leading coefficient
├── 3.12 Exercises
│   └── Practice proving asymptotic relationships
├── 3.13–3.14 Strict Notations
│   ├── o(g(n)) : strictly less than (lim = 0)
│   └── ω(g(n)) : strictly greater than (lim = ∞)
└── 3.15 Summary
    └── Five notations comparison table
```

---

## 📌 Formula Quick-Reference / 核心公式速查表

| Concept | Formula |
|---------|---------|
| $O(g(n))$ | $\{ f(n) \mid \exists c, n_0 \text{ s.t. } 0 \le f(n) \le c \cdot g(n), \forall n \ge n_0 \}$ |
| $\Omega(g(n))$ | $\{ f(n) \mid \exists c, n_0 \text{ s.t. } 0 \le c \cdot g(n) \le f(n), \forall n \ge n_0 \}$ |
| $\Theta(g(n))$ | $\{ f(n) \mid \exists c_1, c_2, n_0 \text{ s.t. } 0 \le c_1 g(n) \le f(n) \le c_2 g(n), \forall n \ge n_0 \}$ |
| $o(g(n))$ | $\{ f(n) \mid \forall c > 0, \exists n_0 > 0 \text{ s.t. } 0 \le f(n) < c \cdot g(n), \forall n \ge n_0 \}$ |
| $\omega(g(n))$ | $\{ f(n) \mid \forall c > 0, \exists n_0 > 0 \text{ s.t. } 0 \le c \cdot g(n) < f(n), \forall n \ge n_0 \}$ |
| $f(n) \in \Theta(g(n))$ | $\iff f(n) \in O(g(n)) \land f(n) \in \Omega(g(n))$ |
| $f(n) \in o(g(n))$ | $\iff \lim_{n \to \infty} \frac{f(n)}{g(n)} = 0$ |
| $f(n) \in \omega(g(n))$ | $\iff \lim_{n \to \infty} \frac{f(n)}{g(n)} = \infty$ |
| Growth rate order | $\log n \ll \sqrt{n} \ll n \ll n \log n \ll n^2 \ll n^3 \ll 2^n$ |
| Stirling's approximation | $n! \approx \sqrt{2\pi n} \left(\frac{n}{e}\right)^n$ |

---

## 📝 Example Index / 重要範例索引

| Example | Topic | Section |
|---------|-------|------|
| Growth rates chart | log n, √n, n, n log n, n², n³, 2ⁿ comparison | [3.5](01_introduction_and_growth_rates.md) |
| $O(n^2)$, $\Omega(n^2)$, $\Theta(n^2)$ | Set membership examples | [3.9](02_asymptotic_notations.md) |
| $2n^2 + 4n = \Theta(n^2)$ | Exercise: tight bound proof | [3.12](02_asymptotic_notations.md) |
| $2^{n+1} = O(2^n)$ | Exercise: exponential upper bound | [3.12](02_asymptotic_notations.md) |
| $2^{2n} \neq O(2^n)$ | Exercise: exponential not bounded | [3.12](02_asymptotic_notations.md) |
| $\lg(n!) = \Theta(n \lg n)$ | Exercise: Stirling's approximation | [3.12](02_asymptotic_notations.md) |

---

## 🖼️ Image Resources / 圖片資源

| Image | Description | Section |
|-------|-------------|---------|
| `fig_growth_rates_1.png` | Growth rates chart (log n, √n, n, n log n, 100n, n², n³) | [3.5](01_introduction_and_growth_rates.md) |
| `fig_growth_rates_2.png` | Extended growth rates chart (including 2ⁿ exponential) | [3.5](01_introduction_and_growth_rates.md) |
| `fig_o_notation.png` | O Notation definition (asymptotic upper bound) | [3.6](02_asymptotic_notations.md) |
| `fig_omega_notation.png` | Ω Notation definition (asymptotic lower bound) | [3.7](02_asymptotic_notations.md) |
| `fig_theta_notation.png` | Θ Notation definition (asymptotically tight bound) | [3.8](02_asymptotic_notations.md) |
| `fig_set_diagram.png` | Venn diagram of O(n²), Ω(n²), Θ(n²) sets | [3.9](02_asymptotic_notations.md) |
| `slide_10_copyright.png` | Slide 10: Copyright notice (McGraw-Hill) | [3.10](02_asymptotic_notations.md) |

---

## 📚 Source Material / 原始教材

- **Source**: `Lec3_chapter03_2023.pdf` (16 slides, CLRS Chapter 3)
- **Textbook**: Introduction to Algorithms, Second Edition, Cormen, Leiserson, Rivest & Stein
- **Chapter**: 3 — Growth of Functions
- **Output**: 2 section files + README.md in `/workspace/CH3_Asychnotic_Analysis/`
