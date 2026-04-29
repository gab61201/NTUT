# 4.6 標準化隨機變數 (Standardized Random Variables)

---

## 📖 原文

### Def: Let $X$ be a random variable with mean $\mu$ and standard deviation $\sigma$. The random variable

$$X^* = \frac{X - \mu}{\sigma}$$

is called the **standardized $X$**. We have:

$$E(X^*) = E\left(\frac{X - \mu}{\sigma}\right) = \frac{1}{\sigma}(E(X) - \mu) = \mathbf{\frac{1}{\sigma}(\mu - \mu) = 0}$$

$$\operatorname{Var}(X^*) = \operatorname{Var}\left(\frac{X - \mu}{\sigma}\right) = \frac{1}{\sigma^2} \cdot \operatorname{Var}(X) = \mathbf{\frac{\sigma^2}{\sigma^2} = 1}$$

---

## 🇹🇼 中文翻譯

### 定義：令 $X$ 為平均值 $\mu$、標準差 $\sigma$ 的隨機變數。隨機變數

$$X^* = \frac{X - \mu}{\sigma}$$

稱為 **$X$ 的標準化形式**。我們有：

$$E(X^*) = E\left(\frac{X - \mu}{\sigma}\right) = \frac{1}{\sigma}(E(X) - \mu) = \mathbf{\frac{1}{\sigma}(\mu - \mu) = 0}$$

$$\operatorname{Var}(X^*) = \operatorname{Var}\left(\frac{X - \mu}{\sigma}\right) = \frac{1}{\sigma^2} \cdot \operatorname{Var}(X) = \mathbf{\frac{\sigma^2}{\sigma^2} = 1}$$

---

## 💡 中文詳細解釋與推導過程

### 什麼是標準化？

**標準化 (Standardization)** 是將隨機變數轉換為「平均值為 $0$、方差為 $1$」的過程：

$$X^* = \frac{X - \mu}{\sigma}$$

這個操作也叫 **Z-score 轉換**。

### 為什麼要標準化？

1. **消除量綱**：不同單位/尺度的數據可以比較
2. **統一基準**：所有變數都變成「以平均值為中心、標準差為單位」的尺度
3. **統計推論**：許多定理（如中心極限定理）的結果都以標準化形式表達

### 推導過程

**期望值：**

$$E(X^*) = E\left[\frac{X - \mu}{\sigma}\right]$$
$$= \frac{1}{\sigma} \cdot E[X - \mu] \quad (\text{常數提出來})$$
$$= \frac{1}{\sigma} \cdot [E(X) - \mu] \quad (\text{線性性質})$$
$$= \frac{1}{\sigma} \cdot [\mu - \mu]$$
$$= \mathbf{\frac{1}{\sigma} \cdot 0 = 0} \;\; ✓$$

**方差：**

$$\operatorname{Var}(X^*) = \operatorname{Var}\left[\frac{X - \mu}{\sigma}\right]$$
$$= \frac{\operatorname{Var}(X - \mu)}{\sigma^2} \quad (\operatorname{Var}(aX) = a^2 \cdot \operatorname{Var}(X)，這裡 } a = 1/\sigma)$$
$$= \frac{\operatorname{Var}(X)}{\sigma^2} \quad (\operatorname{Var}(X-c) = \operatorname{Var}(X)，平移不變)$$
$$= \frac{\sigma^2}{\sigma^2}$$
$$= \mathbf{1} \;\; ✓$$

---

## 💡 實際應用範例

### 考試成績比較

假設兩門考試：
- 數學：平均分 $70$，標準差 $10$
- 英文：平均分 $85$，標準差 $5$

小明數學考 $85$、英文考 $92$。他在哪一科表現更好？

**標準化後：**
- 數學 Z-score = $\dfrac{85 - 70}{10} =$ **$1.5$**（高於平均 $1.5$ 個標準差）
- 英文 Z-score = $\dfrac{92 - 85}{5} =$ **$1.4$**（高於平均 $1.4$ 個標準差）

→ 小明的**數學表現相對更好**！

### 與正態分佈的關係

若 $X \sim N(\mu, \sigma^2)$，則標準化後：
$$X^* = \frac{X - \mu}{\sigma} \sim \mathbf{N(0, 1)} \quad (\text{標準正態分佈})$$

這使得我們可以用同一張 Z-table 來計算任何正態分佈的機率。

---

## 📊 本章重點總結

| 概念 | 公式 | 意義 |
|------|------|------|
| 隨機變數 | $X: S \to \mathbb{R}$ | 實驗結果到數字的映射 |
| CDF | $F(x) = P(X \le x)$ | 累積機率，四性質：非減、右連續、極限 $0/1$ |
| PMF | $p(x) = P(X=x)$ | 離散變數的點機率，$\sum p(x)=1$ |
| 期望值 | $E(X) = \sum x \cdot p(x)$ | 加權平均，線性性質 $E(aX+b)=aE(X)+b$ |
| 方差 | $\operatorname{Var}(X) = E(X^2)-[E(X)]^2$ | 分散程度，$\operatorname{Var}(aX+b)=a^2 \cdot \operatorname{Var}(X)$ |
| 標準化 | $X^*=\dfrac{X-\mu}{\sigma}$ | Z-score，均值 $0$、方差 $1$ |

---
