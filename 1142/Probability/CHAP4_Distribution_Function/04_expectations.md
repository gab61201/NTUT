# 4.4 離散隨機變數的期望值 (Expectations of Discrete Random Variables)

---

## 📖 原文

### Def: The **expected value** of a discrete random variable $X$ with the set of possible values $A$ and probability mass function $p(x)$ is defined by

$$E(X) = \sum_{x \in A} x \cdot p(x)$$

We say that $E(X)$ exists if this sum converges absolutely.

$E(X)$ is also called the **mean** or the **expectation** of $X$ and is also denoted by $E_X$, $\mu_X$, or $\mu$.

---

## 🇹🇼 中文翻譯

### 定義：離散隨機變數 $X$（可能取值集合為 $A$，機率質量函數為 $p(x)$）的**期望值**定義為

$$E(X) = \sum_{x \in A} x \cdot p(x)$$

若此級數絕對收斂，則稱 $E(X)$ 存在。

$E(X)$ 也稱為 $X$ 的**平均值 (mean)** 或**期望 (expectation)**，也可記作 $E_X$、$\mu_X$ 或 $\mu$。

---

## 💡 中文詳細解釋

### 什麼是期望值？

期望值是隨機變數的「加權平均」——每個可能值乘以其機率後再加總：

$$E(X) = x_1 \cdot p(x_1) + x_2 \cdot p(x_2) + x_3 \cdot p(x_3) + \cdots$$

**直觀理解**：如果你重複實驗無數次，$X$ 的平均值會趨近於 $E(X)$。這就是「大數法則」的核心思想。

> ⚠️ **注意**：期望值不一定等於任何一個可能取值！例如擲骰子的期望值是 $3.5$，但你永遠不可能擲出 $3.5$。

---

## 📝 Ex 4.14 — 拋硬幣期望值

### 📖 原文

Flip a fair coin twice and let $X$ be the number of heads obtained. What is the expected value of $X$?

Sol:
- $p(0) = P(X=0) = \frac{1}{4}$
- $p(1) = P(X=1) = \frac{1}{2}$
- $p(2) = P(X=2) = \frac{1}{4}$
- $E(X) = 0 \cdot p(0) + 1 \cdot p(1) + 2 \cdot p(2) =$ **$1$**

---

### 🇹🇼 中文翻譯

拋一枚公平硬幣兩次，令 $X$ 為正面朝上的次數。$X$ 的期望值是多少？

解：
- $p(0) = P(X=0) = \frac{1}{4}$（反面、反面）
- $p(1) = P(X=1) = \frac{1}{2}$（正反或反正）
- $p(2) = P(X=2) = \frac{1}{4}$（正面、正面）
- $E(X) = 0 \cdot p(0) + 1 \cdot p(1) + 2 \cdot p(2) =$ **$1$**

---

### 💡 中文詳細解釋與推導過程

$X \sim B(n=2, p=\frac{1}{2})$，二項分佈。

$$E(X) = 0 \times \frac{1}{4} + 1 \times \frac{1}{2} + 2 \times \frac{1}{4} = 0 + \frac{1}{2} + \frac{1}{2} = \mathbf{1}$$

> 💡 **驗證**：二項分佈 $B(n,p)$ 的期望值公式為 $E(X) = np = 2 \times \frac{1}{2} = 1$ ✓

---

## 📝 Ex — 樂透遊戲期望收益

### 📖 原文

In the lottery game, players pick 6 integers between 1 and 10. The cost of one bet is NT\$50. A player wins:
- NT\$10,000 for the grand prize (6 matches)
- NT\$200 for the 2nd prize (5 matches)
- NT\$100 for the 3rd prize (4 matches)

What is the expected amount of money that a player can win in a game?

Sol:
$$P(X = 9950) = \frac{\binom{6}{6}\binom{4}{0}}{\binom{10}{6}} \quad (\text{全中，淨收益 } 10000-50=9950)$$
$$P(X = 150) = \frac{\binom{6}{5}\binom{4}{1}}{\binom{10}{6}} \quad (\text{中5個，淨收益 } 200-50=150)$$
$$P(X = 50) = \frac{\binom{6}{4}\binom{4}{2}}{\binom{10}{6}} \quad (\text{中4個，淨收益 } 100-50=50)$$
$$P(X = -50) = 1 - p(9950) - p(150) - p(50) \quad (\text{未中獎，損失 } 50)$$

$$E(X) = 9950 \cdot p(9950) + 150 \cdot p(150) + 50 \cdot p(50) + (-50) \cdot p(-50)$$

---

### 🇹🇼 中文翻譯

在樂透遊戲中，玩家從 $1\sim 10$ 中選 6 個整數。一注投注金額為 NT\$50。獎項：
- 頭獎（全中 6 個）：NT\$10,000
- 二獎（中 5 個）：NT\$200
- 三獎（中 4 個）：NT\$100

玩家玩一次遊戲的期望收益是多少？

解：
$$P(X = 9950) = \frac{\binom{6}{6}\binom{4}{0}}{\binom{10}{6}} \quad (\text{全中，淨收益 } 10000-50=9950)$$
$$P(X = 150) = \frac{\binom{6}{5}\binom{4}{1}}{\binom{10}{6}} \quad (\text{中5個，淨收益 } 200-50=150)$$
$$P(X = 50) = \frac{\binom{6}{4}\binom{4}{2}}{\binom{10}{6}} \quad (\text{中4個，淨收益 } 100-50=50)$$
$$P(X = -50) = 1 - p(9950) - p(150) - p(50) \quad (\text{未中獎，損失 } 50)$$

$$E(X) = 9950 \cdot p(9950) + 150 \cdot p(150) + 50 \cdot p(50) + (-50) \cdot p(-50)$$

---

### 💡 中文詳細解釋與推導過程

**計算各獎項機率：**

$\binom{10}{6} = 210$（總共 210 種組合）

- $P(\text{全中}) = \dfrac{\binom{6}{6} \cdot \binom{4}{0}}{210} = \dfrac{1}{210}$
- $P(\text{中5個}) = \dfrac{\binom{6}{5} \cdot \binom{4}{1}}{210} = \dfrac{6 \times 4}{210} = \dfrac{24}{210}$
- $P(\text{中4個}) = \dfrac{\binom{6}{4} \cdot \binom{4}{2}}{210} = \dfrac{15 \times 6}{210} = \dfrac{90}{210}$
- $P(\text{未中獎}) = 1 - \dfrac{1+24+90}{210} = \dfrac{95}{210}$

**期望收益：**

$$E(X) = 9950 \times \frac{1}{210} + 150 \times \frac{24}{210} + 50 \times \frac{90}{210} + (-50) \times \frac{95}{210}$$
$$= \frac{9950 + 3600 + 4500 - 4750}{210} = \mathbf{\frac{13,\!300}{210} \approx NT\$63.33}$$

> 💡 期望收益為正，表示這個遊戲對玩家有利（但實際樂透的機率通常遠低於此）。

---

## 📝 Ex 4.18 — 聖彼得堡悖論 (St. Petersburg Paradox)

### 📖 原文

In a game, the player flips a fair coin successively until he gets a heads. If this occurs on the $k$th flip, the player wins $2^k$ dollars.

Question: To play this game, how much should a person, who is willing to play a **fair game**, pay?

Sol: Let $X$ be the amount of money the player wins. Then $X$ is a random variable with possible values $\{2, 4, 8, \ldots\}$ and $P(X=2^k) = \frac{1}{2^k},\; k=1, 2, 3, \ldots$

Therefore,
$$E(X) = \sum_{k=1}^{\infty} 2^k \cdot \frac{1}{2^k} = \sum_{k=1}^{\infty} 1 = 1 + 1 + 1 + \cdots = \mathbf{\infty}$$

This shows that this game remains unfair even if a person pays the largest possible amount to play it.

---

### 🇹🇼 中文翻譯

在一個遊戲中，玩家連續拋公平硬幣直到出現正面。若在第 $k$ 次出現正面，玩家贏得 $2^k$ 美元。

問題：願意玩**公平遊戲**的人應該付多少錢來玩這個遊戲？

解：令 $X$ 為玩家贏得的金額。$X$ 的可能值為 $\{2, 4, 8, \ldots\}$，$P(X=2^k) = \frac{1}{2^k},\; k=1, 2, 3, \ldots$

因此，
$$E(X) = \sum_{k=1}^{\infty} 2^k \cdot \frac{1}{2^k} = \sum_{k=1}^{\infty} 1 = 1 + 1 + 1 + \cdots = \mathbf{\infty}$$

這顯示即使支付任意大的金額來玩這個遊戲，它仍然是不公平的。

---

### 💡 中文詳細解釋與推導過程

**為什麼叫「悖論」？**

- 理論上：期望值為無限大 $\Rightarrow$ 你應該願意付任何價格
- 實際上：沒人願意付超過幾十美元

**原因分析：**

| $k$（第幾次出現正面） | 獎金 $2^k$ | 機率 $\frac{1}{2^k}$ | 貢獻 = 獎金$\times$機率 |
|---|---|---|---|
| 1 | \$2 | $\frac{1}{2}$ | \$1 |
| 2 | \$4 | $\frac{1}{4}$ | \$1 |
| 3 | \$8 | $\frac{1}{8}$ | \$1 |
| ... | ... | ... | \$1 |

每次試驗的「期望貢獻」都是 \$1，無限次加總 $= \infty$。

**悖論的解釋：**
- **效用理論 (Bernoulli)**：人們對金錢的邊際效用遞減，$2^k$ 的效用遠小於 $2^k$
- **實際限制**：莊家的資金有限，不可能支付無限金額
- **風險規避**：大多數人是風險規避者，不願意為極低機率的超大獎金付出高價

---

## 📝 Ex 4.19 — 坦克編號估計問題 (German Tank Problem)

### 📖 原文

The tanks of a country's army are numbered $1$ to $N$. In a war this country loses $n$ random tanks to the enemy, who discovers that the captured tanks are numbered. If $X_1, X_2, \ldots, X_n$ are the numbers of the captured tanks, what is $E(\max X_i)$? How can the enemy use $E(\max X_i)$ to find an estimate of $N$?

Sol: Let $Y = \max X_i$; then for $k=n, n+1, \ldots, N$:
$$P(Y=k) = \frac{\binom{k-1}{n-1}}{\binom{N}{n}}$$

$$E(Y) = \sum_{k=n}^{N} k \cdot P(Y=k) = \frac{n}{N+1} \cdot \sum_{k=n}^{N} \binom{k}{n}$$

It is noted that $\displaystyle\sum_{k=n}^{N} \binom{k}{n} = \binom{N+1}{n+1}$

$$E(Y) = \frac{n}{N+1} \times \frac{\binom{N+1}{n+1}}{\binom{N}{n}} = \frac{N(n+1)}{n+1} - \frac{n}{n+1} \cdots$$

**$N = E(Y) \cdot \dfrac{n+1}{n} - 1$**

If enemy captures $12$ tanks and the maximum number is $117$, then:
$$N \approx \frac{13}{12} \times 117 - 1 = \mathbf{126}$$

---

### 🇹🇼 中文翻譯

某國軍隊的坦克編號為 $1$ 到 $N$。戰爭中該國損失了 $n$ 輛隨機坦克給敵方，敵方發現被俘獲的坦克有編號。若 $X_1, X_2, \ldots, X_n$ 是被俘獲坦克的編號，$E(\max X_i)$ 是多少？敵方如何利用 $E(\max X_i)$ 來估計 $N$（該國坦克總數）？

解：令 $Y = \max X_i$；則對 $k=n, n+1, \ldots, N$：
$$P(Y=k) = \frac{\binom{k-1}{n-1}}{\binom{N}{n}}$$

$$E(Y) = \sum_{k=n}^{N} k \cdot P(Y=k) = \frac{n}{N+1} \cdot \sum_{k=n}^{N} \binom{k}{n}$$

注意到 $\displaystyle\sum_{k=n}^{N} \binom{k}{n} = \binom{N+1}{n+1}$

**$N = E(Y) \cdot \dfrac{n+1}{n} - 1$**

若敵方俘獲了 $12$ 輛坦克，最大編號為 $117$：
$$N \approx \frac{13}{12} \times 117 - 1 = \mathbf{126}$$

---

### 💡 中文詳細解釋與推導過程

這是二戰期間著名的**德國坦克問題**。盟軍利用被俘獲坦克的編號，準確估計了德國坦克的生產數量。

**核心思路：**
- $Y = \max(X_1, \ldots, X_n)$ 是樣本中的最大編號
- $E(Y) = \dfrac{N(n+1)}{n+1} - \dfrac{n}{n+1}$，整理後得 $N \approx Y \cdot \dfrac{n+1}{n} - 1$
- 用觀測到的最大值 $y$ 代替 $E(Y)$，得到估計值

**歷史驗證：**
- 統計方法估計：約 270 輛/月
- 間諜情報估計：約 1500 輛/月
- 戰後德國記錄：約 246 輛/月（統計方法更準確！）

> 💡 **啟示**：好的統計方法可以比間諜情報更可靠。

---

## 📖 Theorems — 期望值的性質

### Theorem 4.1
If $X$ is a constant random variable, that is, if $P(X=c)=1$ for a constant $c$, then $E(X) = c$.

**翻譯**：若 $X$ 是常數隨機變數（$P(X=c)=1$），則 $E(X) = c$。

### Theorem 4.2
Let $g$ be a real-valued function. Then $g(X)$ is a random variable with:
$$E[g(X)] = \sum_{x \in A} g(x) \cdot p(x)$$

**翻譯**：令 $g$ 為實值函數，則 $g(X)$ 是隨機變數且 $E[g(X)] = \sum g(x) \cdot p(x)$。

### Corollary (線性性質)
$$E\bigl[a_1 g_1(X) + a_2 g_2(X) + \cdots + a_n g_n(X)\bigr] = a_1 E[g_1(X)] + a_2 E[g_2(X)] + \cdots + a_n E[g_n(X)]$$

**翻譯**：期望值具有線性性質——加權和的期望等於期望的加權和。

### Theorem (線性法則)
For any constants $a$ and $b$: **$E(aX + b) = a \cdot E(X) + b$**

**翻譯**：對任意常數 $a$ 和 $b$，$E(aX+b) = aE(X)+b$。因此 $E(X)$ 服從線性法則。

---
