# 4.1 隨機變數 (Random Variables)

---

## 📖 原文

### Def: A real-valued function $X: S \to \mathbb{R}$ is called a **random variable** of the experiment if, for each interval $I \subseteq \mathbb{R}$, $\{s : X(s) \in I\}$ is an event.

- In probability, the set $\{s : X(s) \in I\}$ is often abbreviated as $\{X \in I\}$ or simply as **$X \in I$**.

---

## 🇹🇼 中文翻譯

### 定義：實值函數 $X: S \to \mathbb{R}$ 若對每個區間 $I \subseteq \mathbb{R}$，集合 $\{s : X(s) \in I\}$ 是一個事件，則稱 $X$ 為該實驗的**隨機變數**。

- 在機率論中，集合 $\{s : X(s) \in I\}$ 通常簡寫為 $\{X \in I\}$ 或直接寫作 **$X \in I$**。

---

## 💡 中文詳細解釋

**隨機變數 (Random Variable)** 是機率論的核心概念。它本質上是一個函數：
- **定義域**：樣本空間 $S$（所有可能的實驗結果）
- **值域**：實數集 $\mathbb{R}$

換句話說，隨機變數把每個「實驗結果」映射到一個「數字」。這樣我們就可以用數學工具來分析機率問題。

> ⚠️ 注意：雖然叫「變數」，但它其實是一個**函數**。$X(s)$ 表示當實驗結果為 $s$ 時，隨機變數 $X$ 的值。

---

## 📝 Ex 4.1 — 抽牌例子

### 📖 原文

Suppose that 3 cards are drawn from an ordinary deck of 52 cards, 1-by-1, at random and **with replacement**. Let $X$ be the number of spades drawn; then $X$ is a random variable.

If an outcome of spades is denoted by $s$, and other outcomes are represented by $t$, then $X$ is a real-valued function defined on the sample space:

$$S = \{(s,s,s), (t,s,s), (s,t,s), (s,s,t), (s,t,t), (t,s,t), (t,t,s), (t,t,t)\}$$

by $X(s,s,s)=3$, $X(s,t,s)=2$, $X(s,s,t)=2$, $X(s,t,t)=1$, and so on.

$$P(X=0) = P(\{(t,t,t)\}) = \frac{27}{64}$$
$$P(X=1) = P(\{(s,t,t), (t,s,t), (t,t,s)\}) = 3 \times \frac{9}{64} = \frac{27}{64}$$
$$P(X=2) = P(\{(s,s,t), (s,t,s), (t,s,s)\}) = \frac{9}{64}$$
$$P(X=3) = P(\{(s,s,s)\}) = \frac{1}{64}$$

If the cards are drawn **without replacement**, $P(X=i) = \dfrac{\binom{13}{i}\binom{39}{3-i}}{\binom{52}{3}}$ for $i=0,1,2,3$.

---

### 🇹🇼 中文翻譯

假設從一副標準的 52 張牌中，一張一張隨機抽取 3 張，**有放回**。令 $X$ 為抽到的黑桃 (spades) 數量；則 $X$ 是一個隨機變數。

若將抽到黑桃的結果記為 $s$，其他結果記為 $t$，則 $X$ 是定義在樣本空間上的實值函數：

$$S = \{(s,s,s), (t,s,s), (s,t,s), (s,s,t), (s,t,t), (t,s,t), (t,t,s), (t,t,t)\}$$

$X(s,s,s)=3$, $X(s,t,s)=2$, $X(s,s,t)=2$, $X(t,t,s)=1$，以此類推。

$$P(X=0) = P(\{(t,t,t)\}) = \frac{27}{64}$$
$$P(X=1) = P(\{(s,t,t), (t,s,t), (t,t,s)\}) = \frac{27}{64}$$
$$P(X=2) = P(\{(s,s,t), (s,t,s), (t,s,s)\}) = \frac{9}{64}$$
$$P(X=3) = P(\{(s,s,s)\}) = \frac{1}{64}$$

若**不放回**抽牌，則 $P(X=i) = \dfrac{\binom{13}{i}\binom{39}{3-i}}{\binom{52}{3}}$，其中 $i=0,1,2,3$。

---

### 💡 中文詳細解釋

- **有放回 (with replacement)**：每次抽完一張後放回去，所以每次抽到黑桃的機率都是 $\frac{13}{52} = \frac{1}{4}$，非黑桃為 $\frac{39}{52} = \frac{3}{4}$。
- $P(X=0) = \left(\frac{3}{4}\right)^3 = \frac{27}{64}$（三次都非黑桃）
- $P(X=1) = \binom{3}{1} \times \left(\frac{1}{4}\right)^1 \times \left(\frac{3}{4}\right)^2 = 3 \times \frac{9}{64} = \frac{27}{64}$
- $P(X=2) = \binom{3}{2} \times \left(\frac{1}{4}\right)^2 \times \left(\frac{3}{4}\right)^1 = 3 \times \frac{3}{64} = \frac{9}{64}$
- $P(X=3) = \left(\frac{1}{4}\right)^3 = \frac{1}{64}$

這符合**二項分佈** $B(n=3, p=\frac{1}{4})$。

---

### 📝 Ex 4.3 — 雙胞胎出生例子

### 📖 原文

In the U.S., the number of twin births is approximately **1 in 90**. Let $X$ be the number of births in a certain hospital until the first twins are born. $X$ is a random variable.

Denote twin births by $T$ and single births by $N$. The sample space:
$$S = \{T, NT, NNT, NNNT, \ldots\}$$

The set of all possible values of $X$ is $\{1, 2, 3, \ldots\}$

$$P(X=i) = P(NNN\cdots NT) = \left(\frac{89}{90}\right)^{i-1} \times \frac{1}{90}, \quad i=1,2,3,\ldots$$

---

### 🇹🇼 中文翻譯

在美國，雙胞胎出生的比例約為 **90 分之 1**。令 $X$ 為某醫院直到第一次出現雙胞胎為止的出生次數。$X$ 是一個隨機變數。

用 $T$ 表示雙胞胎出生，$N$ 表示單胎出生。樣本空間：
$$S = \{T, NT, NNT, NNNT, \ldots\}$$

$X$ 所有可能的值集合為 $\{1, 2, 3, \ldots\}$

$$P(X=i) = P(NNN\cdots NT) = \left(\frac{89}{90}\right)^{i-1} \times \frac{1}{90}, \quad i=1,2,3,\ldots$$

---

### 💡 中文詳細解釋

這是一個**幾何分佈 (Geometric Distribution)** 的經典例子：
- 每次「試驗」是一次出生事件，成功（雙胞胎）機率 $p = \frac{1}{90}$
- $X =$ 「第一次成功所需的試驗次數」
- $P(X=i) = (1-p)^{i-1} \times p$

幾何分佈的特點：**記憶無效性**——無論已經等了多久，下一次成功的機率永遠是 $p$。

---

### 📝 Ex 4.8 — 抽球最大值問題

### 📖 原文

Three balls are selected randomly **without replacement** from a box containing 20 balls numbered 1 through 20. What is the probability that the largest number of the drawn balls is as large as or larger than 17?

Let $X$ denote the largest drawn number.

**Sol. (a)** $P(X=k) = \dfrac{\binom{k-1}{2}}{\binom{20}{3}},\quad k=3,\ldots,20$
$$P(X \ge 17) = \sum_{k=17}^{20} P(X=k)$$

**Sol. (b)** $P(X \ge 17) = 1 - P(X \le 16) = 1 - \dfrac{\binom{16}{3}}{\binom{20}{3}}$

---

### 🇹🇼 中文翻譯

從一個裝有編號 $1\sim 20$ 的 20 個球的盒子中，隨機**不放回**地抽取 3 個球。抽到的球中最大號碼大於或等於 17 的機率是多少？

令 $X$ 表示抽到的最大號碼。

**解法 (a)** $P(X=k) = \dfrac{\binom{k-1}{2}}{\binom{20}{3}},\quad k=3,\ldots,20$
$$P(X \ge 17) = \sum_{k=17}^{20} P(X=k)$$

**解法 (b)** $P(X \ge 17) = 1 - P(X \le 16) = 1 - \dfrac{\binom{16}{3}}{\binom{20}{3}}$

---

### 💡 中文詳細解釋

- **解法 (a)**：直接計算。若最大值為 $k$，則另外兩個球必須從 $\{1,\ldots,k-1\}$ 中選，有 $\binom{k-1}{2}$ 種方式。
- **解法 (b)**：利用互補事件。$X \le 16$ 表示三個球都來自 $\{1,\ldots,16\}$，有 $\dfrac{\binom{16}{3}}{\binom{20}{3}}$。

> 💡 **技巧**：遇到「至少」或「大於等於」的問題時，考慮用 $1 - P(\text{互補事件})$ 通常更簡單。

---
