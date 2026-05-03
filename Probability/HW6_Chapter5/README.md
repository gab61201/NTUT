# Probability Homework #6 / 機率作業 #6

**Coverage: Chapter 5 — Special Discrete Distributions / 範圍：第 5 章 — 特殊離散分佈**

---

## 📋 Course Overview / 課程總覽

| Problem | Topic | Distribution | Link |
|---------|-------|-------------|------|
| **1** | Birthday probability (April/October) | Binomial | [→ 01_problem_1.md](01_problem_1.md) |
| **2** | Maximum-probability baskets | Binomial (mode) | [→ 02_problem_2.md](02_problem_2.md) |
| **3** | Parity check undetected error | Binomial | [→ 03_problem_3.md](03_problem_3.md) |
| **4** | Poisson approximation to Binomial | Poisson | [→ 04_problem_4.md](04_problem_4.md) |
| **5** | Independent Poisson joint probability | Poisson | [→ 05_problem_5.md](05_problem_5.md) |
| **6** | Poisson parameter from equality | Poisson | [→ 06_problem_6.md](06_problem_6.md) |
| **7** | Hazel eyes — r-th success on n-th trial | Negative Binomial | [→ 07_problem_7.md](07_problem_7.md) |
| **8** | Defective bulbs — at least n trials | Geometric | [→ 08_problem_8.md](08_problem_8.md) |
| **9** | Senior citizens — failures before r-th success | Negative Binomial | [→ 09_problem_9.md](09_problem_9.md) |
| **10** | Trout mark-recapture estimation | Hypergeometric + MLE | [→ 10_problem_10.md](10_problem_10.md) |

---

## 🗺️ Knowledge Structure / 知識結構圖

```
Chapter 5: Special Discrete Distributions
├── Bernoulli Trials / 伯努利試驗
│   ├── Binomial Distribution / 二項分佈 — Problems 1, 2, 3
│   │   ├── PMF: P(X=k) = C(n,k)·p^k·(1-p)^(n-k)
│   │   ├── Mode (maximum probability) — Problem 2
│   │   └── Application: birthday, sports, error detection
│   │
│   ├── Geometric Distribution / 幾何分佈 — Problem 8
│   │   ├── PMF: P(X=n) = (1-p)^(n-1)·p
│   │   └── P(X ≥ n) = (1-p)^(n-1) — at least n trials
│   │
│   └── Negative Binomial / 負二項分佈 — Problems 7, 9
│       ├── PMF: P(N=n) = C(n-1, r-1)·p^r·(1-p)^(n-r)
│       ├── Counting trials until r-th success — Problem 7
│       └── Counting failures before r-th success — Problem 9
│
├── Poisson Distribution / 卜瓦松分佈 — Problems 4, 5, 6
│   ├── PMF: P(X=k) = e^(-λ)·λ^k / k!
│   ├── Poisson approximation: Binomial(n,p) → Poisson(λ=np), n large, p small
│   └── Properties: E(X)=Var(X)=λ; independent Poisson
│
└── Hypergeometric Distribution / 超幾何分佈 — Problem 10
    ├── PMF: P(X=k) = C(K,k)·C(N-K, n-k) / C(N, n)
    └── MLE / 最大概似估計法: find n maximizing Pₙ
```

---

## 📌 Formula Quick-Reference / 核心公式速查表

| Distribution | PMF / Key Formula | Parameters |
|-------------|-------------------|------------|
| **Binomial** | $P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}$ | $n$: trials, $p$: success prob |
| **Binomial mode** | $k = \lfloor (n+1)p \rfloor$ or $\lceil (n+1)p - 1 \rceil$ | Find $k$ maximizing $P(X=k)$ |
| **Poisson** | $P(X = k) = \frac{e^{-\lambda} \lambda^k}{k!}$ | $\lambda$: mean rate |
| **Poisson approx.** | $\text{Binomial}(n, p) \approx \text{Poisson}(\lambda = np)$ | $n$ large, $p$ small |
| **Geometric** | $P(X = n) = (1-p)^{n-1} p$ | $p$: success prob |
| **Geometric tail** | $P(X \geq n) = (1-p)^{n-1}$ | At least $n$ trials |
| **Negative Binomial** (trials) | $P(N = n) = \binom{n-1}{r-1} p^r (1-p)^{n-r}$ | $r$: target successes, $p$: success prob |
| **Negative Binomial** (failures) | $P(Y = k) = \binom{k+r-1}{r-1} p^r (1-p)^k$ | $Y$: failures before $r$-th success |
| **Hypergeometric** | $P(X = k) = \frac{\binom{K}{k} \binom{N-K}{n-k}}{\binom{N}{n}}$ | $N$: population, $K$: successes in pop |
| **MLE ratio method** | $\frac{P_n}{P_{n+1}} \geq 1$ and $\frac{P_n}{P_{n-1}} \geq 1$ | Find $n$ maximizing $P_n$ |

---

## 📝 Example Index / 重要範例索引

| Example | Concept | Problem |
|---------|---------|---------|
| Birthday in specific months | Basic Binomial PMF | [1](01_problem_1.md) |
| Maximum probability $k$ in Binomial | Binomial mode | [2](02_problem_2.md) |
| Parity check error detection | Binomial with compound event | [3](03_problem_3.md) |
| Poisson approximation (immigration) | Binomial → Poisson | [4](04_problem_4.md) |
| Joint independent Poisson (misprints) | Independent Poisson product | [5](05_problem_5.md) |
| Solving for λ from equality | Poisson parameter recovery | [6](06_problem_6.md) |
| r-th success at n-th trial | Negative Binomial (trial-counting) | [7](07_problem_7.md) |
| At least n trials until success | Geometric tail probability | [8](08_problem_8.md) |
| Failures before r-th success | Negative Binomial (failure-counting) | [9](09_problem_9.md) |
| Mark-recapture + MLE | Hypergeometric + maximization | [10](10_problem_10.md) |

---

## 🏷️ Per-File Structure / 每題架構

| Section | Content |
|---------|---------|
| 📖 原文 | Full English problem text (LaTeX math) |
| 🇹🇼 中文翻譯 | Traditional Chinese translation |
| 💡 詳細解釋 | Concept analysis: distribution identification, parameters, approach hints |
| 🔢 推導過程 | Complete step-by-step derivation with final boxed answer |

## 🎯 Answer Quick-Reference / 答案速查

| Problem | Final Answer |
|---------|-------------|
| **1** | $\boxed{\frac{625}{11664} \approx 0.05358}$ |
| **2** | $\boxed{k^* = 4,\ P_{\max} \approx 0.23837}$ |
| **3** | $\boxed{P \approx 2.78 \times 10^{-5}}$ |
| **4** | $\boxed{P(X \geq 2) \approx 0.5940}$ |
| **5** | $\boxed{P \approx 0.01528}$ |
| **6** | $\boxed{P(X = 5) \approx 0.06341}$ |
| **7** | $\boxed{P \approx 0.05505}$ |
| **8** | $\boxed{P(\text{至少 } n \text{ 個}) = p^{\,n-1}}$ |
| **9** | $\boxed{P(X=k) = \binom{k+9}{9}(0.15)^{10}(0.85)^k}$ |
| **10** | $\boxed{\hat{n} = 625}$ |

---

## 📚 Source Material / 原始教材

- **Source**: `2026PB_HW6.pdf`
- **Pages**: 2
- **Coverage**: Chapter 5 — Special Discrete Distributions
- **Total Problems**: 10
