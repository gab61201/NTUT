# 4.5 離散隨機變數的方差與矩 (Variances and Moments of Discrete Random Variables)

---

## 📖 原文

### Def: **Variance** of $X$

$$\sigma_X^2 = \operatorname{Var}(X) = E\bigl[(X - E(X))^2\bigr] = E\bigl[(X - \mu)^2\bigr] = \sum_x (x - \mu)^2 \cdot p(x)$$

### Def: **Standard deviation** of $X$

$$\sigma_X = \sqrt{\operatorname{Var}(X)}$$

---

## 🇹🇼 中文翻譯

### 定義：**方差 (Variance)**

$$\sigma_X^2 = \operatorname{Var}(X) = E\bigl[(X - E(X))^2\bigr] = E\bigl[(X - \mu)^2\bigr] = \sum_x (x - \mu)^2 \cdot p(x)$$

### 定義：**標準差 (Standard Deviation)**

$$\sigma_X = \sqrt{\operatorname{Var}(X)}$$

---

## 💡 中文詳細解釋

**方差**衡量隨機變數的「分散程度」或「波動性」：
- $\operatorname{Var}(X)$ 越大 $\rightarrow$ $X$ 的值越分散，離平均值越遠
- $\operatorname{Var}(X)$ 越小 $\rightarrow$ $X$ 的值越集中在平均值附近

**為什麼用平方？**
1. 消除正負號（否則正負偏差會互相抵消）
2. 對大偏差給予更大權重（凸函數性質）

> 💡 **標準差** $\sigma_X$ 的單位與 $X$ 相同，而方差 $\sigma_X^2$ 的單位是 $X$ 的平方。實務上更常用標準差來描述「典型偏離程度」。

---

## 📖 Theorem 4.3 — 方差的簡化公式

### 📖 原文

**$\operatorname{Var}(X) = E(X^2) - (E(X))^2$**

Pf: $\operatorname{Var}(X) = E\bigl[(X - E(X))^2\bigr]$
$$= E\bigl[X^2 - 2XE(X) + (E(X))^2\bigr]$$
$$= E(X^2) - 2E(X)E(X) + (E(X))^2$$
$$= \mathbf{E(X^2) - (E(X))^2}$$

Application: **$(E(X))^2 \le E(X^2)$**

---

### 🇹🇼 中文翻譯

**$\operatorname{Var}(X) = E(X^2) - (E(X))^2$**

證明：$\operatorname{Var}(X) = E\bigl[(X - E(X))^2\bigr]$
$$= E\bigl[X^2 - 2XE(X) + (E(X))^2\bigr]$$
$$= E(X^2) - 2E(X)\cdot E(X) + (E(X))^2$$
$$= \mathbf{E(X^2) - (E(X))^2}$$

應用：**$(E(X))^2 \le E(X^2)$**

---

### 💡 中文詳細解釋與推導過程

這是計算方差最常用的公式！

**證明步驟：**

$$\operatorname{Var}(X) = E\bigl[(X - \mu)^2\bigr]$$
$$= E\bigl[X^2 - 2\mu X + \mu^2\bigr] \quad (\text{其中 } \mu = E(X))$$
$$= E(X^2) - 2\mu \cdot E(X) + \mu^2 \quad (\text{期望的線性性質})$$
$$= E(X^2) - 2\mu^2 + \mu^2$$
$$= \mathbf{E(X^2) - \mu^2}$$

> ⚠️ **常見錯誤**：$E(X^2) \neq (E(X))^2$！
> - $E(X^2) = \sum x^2 \cdot p(x)$（先平方再取期望）
> - $(E(X))^2 = \left(\sum x \cdot p(x)\right)^2$（先取期望再平方）

**應用推論：** $\operatorname{Var}(X) \ge 0 \Rightarrow E(X^2) \ge (E(X))^2$，這就是 **Jensen 不等式**的特例。

---

## 📝 Ex 4.27 — 擲骰子的方差

### 📖 原文

What is the variance of the random variable $X$, the outcome of rolling a fair die?

Sol:
- $E(X) = \frac{1+2+3+4+5+6}{6} =$ **$\frac{7}{2}$**
- $E(X^2) = \frac{1+4+9+16+25+36}{6} =$ **$\frac{91}{6}$**
- $\operatorname{Var}(X) = \frac{91}{6} - \left(\frac{7}{2}\right)^2 =$ **$\frac{35}{12}$**

---

### 🇹🇼 中文翻譯

擲一枚公平骰子的結果 $X$，其方差是多少？

解：
- $E(X) = \frac{1+2+3+4+5+6}{6} =$ **$\frac{7}{2} = 3.5$**
- $E(X^2) = \frac{1+4+9+16+25+36}{6} =$ **$\frac{91}{6} \approx 15.17$**
- $\operatorname{Var}(X) = \frac{91}{6} - \left(\frac{7}{2}\right)^2 =$ **$\frac{35}{12} \approx 2.92$**

---

### 💡 中文詳細解釋與推導過程

**逐步計算：**

$$E(X) = \frac{1+2+3+4+5+6}{6} = \frac{21}{6} = \frac{7}{2} = 3.5$$

$$E(X^2) = \frac{1^2+2^2+3^2+4^2+5^2+6^2}{6} = \frac{1+4+9+16+25+36}{6} = \frac{91}{6}$$

$$\operatorname{Var}(X) = E(X^2) - [E(X)]^2 = \frac{91}{6} - \frac{49}{4} = \frac{182-147}{12} = \mathbf{\frac{35}{12}}$$

$$\sigma_X = \sqrt{\frac{35}{12}} \approx \mathbf{1.70}$$

> 💡 這表示骰子結果通常偏離平均值 $3.5$ 約 $\pm 1.7$。

---

## 📖 Theorem 4.4 & 4.5

### Theorem 4.4
$\operatorname{Var}(X) = 0$ if and only if $X$ is constant with probability $1$.

**翻譯**：$\operatorname{Var}(X) = 0$ 當且僅當 $X$ 以機率 $1$ 為常數。

> 💡 **直觀理解**：如果方差為零，表示沒有任何波動——$X$ 永遠等於某個固定值。

### Theorem 4.5
**$\operatorname{Var}(aX + b) = a^2 \cdot \operatorname{Var}(X)$**

**翻譯**：對任意常數 $a$ 和 $b$，$\operatorname{Var}(aX+b) = a^2 \cdot \operatorname{Var}(X)$。

> 💡 **注意**：加 $b$ 不影響方差（平移不變），乘 $a$ 使方差變為 $a^2$ 倍。

---

## 📝 Ex 4.25 — 方差計算練習

### 📖 原文

$E(X) = 2$ and $E[X(X-4)] = 5$. $\operatorname{Var}(-4X+12) = ?$

Sol:
$$E[X^2 - 4X] = E(X^2) - 4E(X) = 5$$
so $E(X^2) = 5 + 4 \times 2 =$ **$13$**

Hence $\operatorname{Var}(X) = E(X^2) - (E(X))^2 = 13 - 2^2 =$ **$9$**

By Theorem 4.5: $\operatorname{Var}(-4X+12) = (-4)^2 \times 9 =$ **$16 \times 9 = 144$**

---

### 🇹🇼 中文翻譯

已知 $E(X) = 2$ 且 $E[X(X-4)] = 5$。求 $\operatorname{Var}(-4X+12)$。

解：
$$E[X^2 - 4X] = E(X^2) - 4E(X) = 5$$
所以 $E(X^2) = 5 + 4 \times 2 =$ **$13$**

因此 $\operatorname{Var}(X) = E(X^2) - (E(X))^2 = 13 - 2^2 =$ **$9$**

由定理 4.5：$\operatorname{Var}(-4X+12) = (-4)^2 \times 9 =$ **$16 \times 9 = 144$**

---

### 💡 中文詳細解釋與推導過程

**關鍵步驟：**

1. $E[X(X-4)] = E[X^2 - 4X] = E(X^2) - 4E(X)$（線性性質）
2. 代入已知：$E(X^2) - 4(2) = 5 \Rightarrow E(X^2) = 13$
3. $\operatorname{Var}(X) = E(X^2) - [E(X)]^2 = 13 - 4 = 9$
4. $\operatorname{Var}(-4X+12) = (-4)^2 \times \operatorname{Var}(X) = 16 \times 9 =$ **$144$**

> 💡 **技巧**：遇到 $E[X \cdot g(X)]$ 時，展開後利用期望的線性性質拆分。

---

## 📖 Theorem 4.6 — 集中度與方差

### 📖 原文

Def: Let $w$ be a given point. $X$ is **more concentrated about $w$ than** $Y$ if for all $t > 0$:
$$P(|Y - w| \le t) \le P(|X - w| \le t)$$

Theorem 4.6: Suppose that $E(X) = E(Y) = a$. If $X$ is more concentrated about $a$ than is $Y$, then **$\operatorname{Var}(X) \le \operatorname{Var}(Y)$**.

---

### 🇹🇼 中文翻譯

定義：令 $w$ 為給定點。若對所有 $t > 0$，$P(|Y-w|\le t) \le P(|X-w|\le t)$，則稱 $X$ **比 $Y$ 更集中在 $w$ 附近**。

定理 4.6：假設 $E(X) = E(Y) = a$。若 $X$ 比 $Y$ 更集中在 $a$ 附近，則 **$\operatorname{Var}(X) \le \operatorname{Var}(Y)$**。

---

### 💡 中文詳細解釋

**直觀理解：**
- 「更集中」意味著 $X$ 的值更接近平均值 $a$
- 方差衡量的是「離平均值的平均距離（平方）」
- 所以更集中的隨機變數有較小的方差

> 💡 **應用場景**：比較兩個投資組合的風險。若兩者預期收益相同，但一個波動更小（更集中），則其方差更低、風險更小。

---

## 📖 Moments — 矩的定義

### 📖 原文

Let $c$ be a constant, $n \ge 0$ be an integer, and $r > 0$ be any real number.

| $E[g(X)]$ | Definition |
|---------|-----------|
| $E(X^n)$ | The **$n$th moment** of $X$（$X$ 的 $n$ 階矩） |
| $E(\|X\|^r)$ | The **$r$th absolute moment** of $X$（$X$ 的 $r$ 階絕對矩） |
| $E(X-c)$ | The **1st moment of $X$ about $c$**（$X$ 關於 $c$ 的一階矩） |
| $E[(X-c)^n]$ | The **$n$th moment of $X$ about $c$**（$X$ 關於 $c$ 的 $n$ 階矩） |
| $E[(X-E(X))^n]$ | The **$n$th central moment** of $X$（$X$ 的 $n$ 階中心矩） |

---

### 🇹🇼 中文翻譯

令 $c$ 為常數，$n \ge 0$ 為整數，$r > 0$ 為任意實數。

| $E[g(X)]$ | 定義 |
|---------|------|
| $E(X^n)$ | $X$ 的 **$n$ 階矩** |
| $E(\|X\|^r)$ | $X$ 的 **$r$ 階絕對矩** |
| $E(X-c)$ | $X$ 關於 $c$ 的 **一階矩** |
| $E[(X-c)^n]$ | $X$ 關於 $c$ 的 **$n$ 階矩** |
| $E[(X-E(X))^n]$ | $X$ 的 **$n$ 階中心矩** |

---

### 💡 中文詳細解釋

**「矩」(Moment)** 是描述分佈形狀的一系列統計量：

| 矩 | 公式 | 意義 |
|----|------|------|
| 一階矩 (mean) | $E(X) = \mu$ | **位置**——平均值 |
| 二階中心矩 (variance) | $E[(X-\mu)^2] = \sigma^2$ | **分散度**——方差 |
| 三階標準化中心矩 | $E\left[\left(\dfrac{X-\mu}{\sigma}\right)^3\right]$ | **偏態 (Skewness)**——對稱性 |
| 四階標準化中心矩 | $E\left[\left(\dfrac{X-\mu}{\sigma}\right)^4\right]$ | **峰態 (Kurtosis)**——尾部厚度 |

> 💡 **記憶技巧**：「矩」就像物理中的力矩——一階矩是重心，二階矩是慣性矩（分散程度），高階矩描述更細微的形狀特徵。

---
