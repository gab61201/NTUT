# 第 4 章：分佈函數與離散隨機變數 (Distribution Functions and Discrete Random Variables)

---

## 📋 課程總覽

本章涵蓋機率論中**隨機變數**的核心概念，從基本定義到期望值、方差和標準化。內容分為六個小節：

| 章節 | 主題 | 講義連結 |
|------|------|----------|
| **4.1** | 隨機變數 (Random Variables) | [→ 01_random_variables.md](01_random_variables.md) |
| **4.2** | 分佈函數 (Distribution Functions / CDF) | [→ 02_distribution_functions.md](02_distribution_functions.md) |
| **4.3** | 離散隨機變數 (Discrete Random Variables / PMF) | [→ 03_discrete_random_variables.md](03_discrete_random_variables.md) |
| **4.4** | 期望值 (Expectations) | [→ 04_expectations.md](04_expectations.md) |
| **4.5** | 方差與矩 (Variances and Moments) | [→ 05_variances_and_moments.md](05_variances_and_moments.md) |
| **4.6** | 標準化隨機變數 (Standardized Random Variables) | [→ 06_standardized_random_variables.md](06_standardized_random_variables.md) |

---

## 🗺️ 知識結構圖

```
隨機變數 X: S → R
│
├── 離散型 (Discrete) ── PMF: p(x) = P(X=x), Σp(x)=1
│   │
│   ├── 期望值 E(X) = Σ x·p(x)
│   │   ├── 線性性質: E(aX+b) = aE(X)+b
│   │   └── Jensen 不等式: [E(X)]² ≤ E(X²)
│   │
│   ├── 方差 Var(X) = E(X²) - [E(X)]²
│   │   ├── Var(aX+b) = a²·Var(X)
│   │   └── Var(X)=0 ⟺ X 為常數 (a.s.)
│   │
│   └── 標準化 X* = (X-μ)/σ → E(X*)=0, Var(X*)=1
│
└── CDF: F(x) = P(X≤x)
    ├── 非遞減、右連續
    ├── lim_{x→∞}F(x)=1, lim_{x→-∞}F(x)=0
    └── P(a<X≤b) = F(b)-F(a), P(X=a) = F(a)-F(a-)
```

---

## 📌 核心公式速查表

### 隨機變數與分佈函數

| 概念 | 公式 |
|------|------|
| CDF 定義 | $F(x) = P(X \le x)$ |
| $P(a < X \le b)$ | $F(b) - F(a)$ |
| $P(X = a)$ | $F(a) - F(a-)$ |
| PMF 性質 | $p(x_i) \ge 0,\;\; \sum p(x_i) = 1$ |

### 期望值與方差

| 概念 | 公式 |
|------|------|
| $E(X)$ | $\displaystyle\sum_x x \cdot p(x)$ |
| $E(aX + b)$ | $a \cdot E(X) + b$ |
| $\operatorname{Var}(X)$ | $E(X^2) - [E(X)]^2$ |
| $\operatorname{Var}(aX + b)$ | $a^2 \cdot \operatorname{Var}(X)$ |
| $X^*$ (標準化) | $\dfrac{X - \mu}{\sigma}$，均值 $0$、方差 $1$ |

---

## 📝 重要範例索引

| 範例 | 主題 | 所在章節 |
|------|------|----------|
| Ex 4.1 | 抽牌（有放回 vs 不放回） | [4.1](01_random_variables.md) |
| Ex 4.3 | 雙胞胎出生（幾何分佈） | [4.1](01_random_variables.md) |
| Ex 4.8 | 抽球最大值問題 | [4.1](01_random_variables.md) |
| Ex 4.7 | CDF 計算練習（混合型分佈） | [4.2](02_distribution_functions.md) |
| Ex 4.9 | 公車到站時間（均勻分佈） | [4.2](02_distribution_functions.md) |
| Ex 4.11 | 擲骰子最大值（PMF + CDF） | [4.3](03_discrete_random_variables.md) |
| Ex 4.12 | 幾何級數 PMF 的歸一化 | [4.3](03_discrete_random_variables.md) |
| Ex 4.14 | 拋硬幣期望值 | [4.4](04_expectations.md) |
| Ex (樂透) | 期望收益計算 | [4.4](04_expectations.md) |
| Ex 4.18 | 聖彼得堡悖論（無限期望） | [4.4](04_expectations.md) |
| Ex 4.19 | 德國坦克問題（統計估計） | [4.4](04_expectations.md) |
| Ex 4.27 | 擲骰子方差計算 | [4.5](05_variances_and_moments.md) |
| Ex 4.25 | 已知 $E(X)$、$E[X(X-4)]$ 求 $\operatorname{Var}(-4X+12)$ | [4.5](05_variances_and_moments.md) |

---

## 🖼️ 圖片資源

所有圖解圖片存放於 `images/` 目錄：

| 檔案 | 內容 |
|------|------|
| `fig_ex4_7_cdf.png` | Ex 4.7 — CDF 階梯圖 |
| `fig_ex4_9_bus_cdf.png` | Ex 4.9 — 公車到站時間 CDF |
| `fig_ex4_11_pmf.png` | Ex 4.11 — PMF 表格 |
| `fig_ex4_11_cdf.png` | Ex 4.11 — CDF 階梯圖 |

---

## 📚 原始教材

- **來源**：CHAP4 Distribution Function.pdf（2020/5/5，共 21 頁）
- **課程日期**：2020 年 5 月 5 日
