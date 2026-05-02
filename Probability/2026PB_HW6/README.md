# Probability Homework #6 / 機率作業 #6

**Coverage: Chapter 5 — Special Discrete Distributions**

---

## 📋 Course Overview / 課程總覽

| # | Topic | Distribution | Link |
|---|-------|-------------|------|
| **1** | Birthday Probability (April/October) | Binomial | [→ 01_birthday_probability.md](01_birthday_probability.md) |
| **2** | Basketball Foul Shot — Max Probability | Binomial (Mode) | [→ 02_basketball_foul_shot.md](02_basketball_foul_shot.md) |
| **3** | Parity Checking — Undetected Error | Binomial | [→ 03_parity_checking.md](03_parity_checking.md) |
| **4** | Illegal Immigrants — Poisson Approximation | Poisson (Approx) | [→ 04_poisson_approximation.md](04_poisson_approximation.md) |
| **5** | Misprints in Book Chapters | Poisson | [→ 05_poisson_misprints.md](05_poisson_misprints.md) |
| **6** | Poisson Parameter from $P(X=1)=P(X=3)$ | Poisson | [→ 06_poisson_parameter.md](06_poisson_parameter.md) |
| **7** | Hazel Eyes — 3rd Success on 8th Trial | Negative Binomial | [→ 07_hazel_eyes_negative_binomial.md](07_hazel_eyes_negative_binomial.md) |
| **8** | Light Bulb — At Least $n$ Trials | Geometric | [→ 08_light_bulb_geometric.md](08_light_bulb_geometric.md) |
| **9** | Senior Citizens — PMF of Non-Seniors Before 10th Senior | Negative Binomial | [→ 09_senior_citizens_negative_binomial.md](09_senior_citizens_negative_binomial.md) |
| **10** | Trout Population — Capture-Recapture MLE | Hypergeometric + MLE | [→ 10_trout_hypergeometric_mle.md](10_trout_hypergeometric_mle.md) |

---

## 🗺️ Knowledge Structure / 知識結構圖

```
Chapter 5: Special Discrete Distributions
│
├── Binomial Distribution
│   ├── [1] Birthday probability → Bin(n=6, p=1/6), P(X=3)
│   ├── [2] Mode of Binomial → find k maximizing Bin(n=10, p=0.45)
│   └── [3] Parity check → Bin(n=7, p=0.001), P(undetected error)
│
├── Poisson Distribution
│   ├── [4] Poisson approximation to Binomial → λ = np, P(X ≥ 2)
│   ├── [5] Poisson model for misprints → λ = 10.5, P(X₁=10, X₅=10)
│   └── [6] Reverse-engineer λ from P(X=1)=P(X=3) → P(X=5)
│
├── Negative Binomial Distribution
│   ├── [7] Hazel eyes → NB(r=3, p=0.20), P(8th trial is 3rd success)
│   └── [9] Senior citizens → NB(r=10, p=0.15), PMF of failures before r-th success
│
├── Geometric Distribution
│   └── [8] Light bulbs → Geometric(p=1−p_defect), P(X ≥ n)
│
└── Hypergeometric Distribution
    └── [10] Trout MLE → Hypergeometric(N=n, K=50, n_s=50), maximize P(X=4)
```

---

## 📌 Formula Quick-Reference / 核心公式速查表

| Distribution | PMF | Parameters |
|-------------|-----|------------|
| **Binomial** | $P(X=k) = \binom{n}{k} p^k (1-p)^{n-k}$ | $n$ trials, $p$ success prob |
| **Binomial Mode** | $k = \lfloor (n+1)p \rfloor$ or $\lceil (n+1)p \rceil - 1$ | — |
| **Poisson** | $P(X=k) = \frac{e^{-\lambda} \lambda^k}{k!}$ | $\lambda$ = rate parameter |
| **Poisson Approx** | $\text{Bin}(n,p) \approx \text{Pois}(\lambda = np)$ | when $n$ large, $p$ small |
| **Negative Binomial** (trials) | $P(X=k) = \binom{k-1}{r-1} p^r (1-p)^{k-r}$ | $r$ successes, $p$ success prob, $k$ = trial # of $r$-th success |
| **Negative Binomial** (failures) | $P(X=k) = \binom{k+r-1}{r-1} p^r (1-p)^k$ | $r$ successes, $p$ success prob, $k$ = # failures before $r$-th success |
| **Geometric** | $P(X=k) = (1-p)^{k-1} p$ | $p$ success prob, $k$ = trial # of 1st success |
| **Geometric (tail)** | $P(X \geq n) = (1-p)^{n-1}$ | At least $n$ trials needed |
| **Hypergeometric** | $P(X=k) = \frac{\binom{K}{k} \binom{N-K}{n_s-k}}{\binom{N}{n_s}}$ | $N$ pop, $K$ successes in pop, $n_s$ sample size |
| **MLE** | $\hat{\theta} = \arg\max_\theta P(\text{data} \mid \theta)$ | Ratio method: $\frac{P_n}{P_{n+1}} \geq 1$, $\frac{P_n}{P_{n-1}} \geq 1$ |

---

## 📝 Example Index / 重要範例索引

| Example | Topic | Distribution | Section |
|---------|-------|-------------|---------|
| Prob 1 | Birthday in April/October | Binomial | [1](01_birthday_probability.md) |
| Prob 2 | Foul shot mode | Binomial Mode | [2](02_basketball_foul_shot.md) |
| Prob 3 | Parity check undetected error | Binomial + Conditional | [3](03_parity_checking.md) |
| Prob 4 | Poisson approx to binomial | Poisson Approximation | [4](04_poisson_approximation.md) |
| Prob 5 | Independent Poisson chapters | Poisson | [5](05_poisson_misprints.md) |
| Prob 6 | Solve λ from P(X=1)=P(X=3) | Poisson Parameter | [6](06_poisson_parameter.md) |
| Prob 7 | 3rd hazel-eyed as 8th passenger | Negative Binomial | [7](07_hazel_eyes_negative_binomial.md) |
| Prob 8 | Light bulb until good | Geometric | [8](08_light_bulb_geometric.md) |
| Prob 9 | Failures before 10th senior | Negative Binomial | [9](09_senior_citizens_negative_binomial.md) |
| Prob 10 | Trout capture-recapture MLE | Hypergeometric + MLE | [10](10_trout_hypergeometric_mle.md) |

---

## 🖼️ Image Resources / 圖片資源

本作業為純文字 PDF，無圖片資源。

---

## 📚 Source Material / 原始教材

| Property | Value |
|----------|-------|
| **Source File** | `2026PB_HW6.pdf` |
| **Pages** | 2 |
| **Problems** | 10 |
| **Coverage** | Chapter 5 — Special Discrete Distributions |
| **Format** | Text-only PDF (no images) |
| **Converted** | 2026-05-02 |
