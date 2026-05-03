# Problem 10 / 第 10 題

## 📖 Original Text / 原文

To estimate the number of trout in a lake, we caught 50 trout, tagged and returned them. Later we caught 50 trout and found that four of them were tagged. From this experiment result, please estimate $n$, the total number of trout in the lake.

Hint: Let $P_n$ be the probability of four tagged trout among the 50 trout caught, if the total number of trout in the lake is $n$. Then, find the value of $n$ that maximizes $P_n$. (Note: In statistics, this approach to estimate value of $n$ is called the maximum likelihood estimate for the number of trout in lake. For this question, you may first find $P_n$, using the hypergeometric random variable. Then use the relation $\frac{P_n}{P_{n+1}} \geq 1$ and $\frac{P_n}{P_{n-1}} \geq 1$ to find the value of $n$ that maximizes $P_n$.)

## 🇹🇼 Chinese Translation / 中文翻譯

為了估計湖中鱒魚的總數，我們捕撈了 50 條鱒魚，做上標記後放回湖中。之後我們再次捕撈 50 條鱒魚，發現其中有四條帶有標記。根據此實驗結果，請估計 $n$，即湖中鱒魚的總數。

提示：令 $P_n$ 為「若湖中總共有 $n$ 條鱒魚，第二次捕撈的 50 條中有四條帶標記」的機率。然後找出使 $P_n$ 最大化之 $n$ 值。（註：在統計學中，這種估計方法稱為「最大概似估計法」(maximum likelihood estimate)，用於估計湖中鱒魚的數量。在本題中，你可以先使用超幾何隨機變數求出 $P_n$，再利用關係式 $\frac{P_n}{P_{n+1}} \geq 1$ 和 $\frac{P_n}{P_{n-1}} \geq 1$ 找出使 $P_n$ 最大化的 $n$ 值。）

## 💡 Detailed Explanation / 詳細解釋

### (1) 涉及的機率分佈與概念

此問題結合了**超幾何分佈 (Hypergeometric Distribution)** 與**最大概似估計法 (Maximum Likelihood Estimation, MLE)**。這是一個經典的「標記－重捕法」(mark-recapture method) 問題，在生態學中用於估計野生動物族群的數量，又稱為 Lincoln-Petersen 估計法。

**超幾何分佈的場景**：從有限母體中進行不放回抽樣。此處：
- 母體大小：$n$（未知，待估計）
- 母體中「成功」的數量：$K = 50$（最初標記的鱒魚）
- 樣本大小：$m = 50$（第二次捕撈的鱒魚數量）
- 樣本中的成功數：$k = 4$（第二次捕獲中的標記魚數量）

### (2) 關鍵參數分析

| 符號 | 意義 | 數值 |
|------|------|------|
| $n$ | 湖中鱒魚總數 | **未知，待估計** |
| $K$ | 標記魚總數 | $50$ |
| $m$ | 第二次捕撈數量 | $50$ |
| $k$ | 第二次捕獲中的標記魚數 | $4$ |
| $n-K$ | 未標記魚總數 | $n - 50$ |
| $m-k$ | 第二次捕獲中的未標記魚數 | $46$ |

### (3) 解題思路提示

**步驟一：寫出 $P_n$**

使用超幾何分佈，在總共 $n$ 條魚中有 $K=50$ 條標記魚的條件下，從 $n$ 條中抽取 $m=50$ 條，恰好捕獲 $k=4$ 條標記魚的機率為：
$$P_n = \frac{\binom{K}{k} \binom{n-K}{m-k}}{\binom{n}{m}} = \frac{\binom{50}{4} \binom{n-50}{46}}{\binom{n}{50}}$$

**步驟二：找出使 $P_n$ 最大化的 $n$**

$P_n$ 是 $n$ 的函數。由於 $n$ 為整數且 $n \geq 50$（至少要能容納 50 條標記魚和 46 條未標記魚，故 $n \geq 96$），我們需要找到使 $P_n$ 最大的整數 $n$。

考慮相鄰項的比值。要使 $P_n$ 在 $n = \hat{n}$ 處達到最大，必須滿足：
$$\frac{P_{\hat{n}}}{P_{\hat{n}+1}} \geq 1 \quad \text{且} \quad \frac{P_{\hat{n}}}{P_{\hat{n}-1}} \geq 1$$

**步驟三：化簡比值**

$$\frac{P_n}{P_{n+1}} = \frac{\frac{\binom{50}{4} \binom{n-50}{46}}{\binom{n}{50}}}{\frac{\binom{50}{4} \binom{n+1-50}{46}}{\binom{n+1}{50}}} = \frac{\binom{n-50}{46}}{\binom{n-49}{46}} \cdot \frac{\binom{n+1}{50}}{\binom{n}{50}}$$

利用組合恆等式 $\frac{\binom{a}{b}}{\binom{a-1}{b}} = \frac{a}{a-b}$ 和 $\frac{\binom{a+1}{b}}{\binom{a}{b}} = \frac{a+1}{a+1-b}$，可將比值化簡為 $n$ 的有理函數。

**步驟四：解不等式**

將化簡後的 $\frac{P_n}{P_{n+1}} \geq 1$ 和 $\frac{P_n}{P_{n-1}} \geq 1$ 分別轉化為關於 $n$ 的不等式，解出 $n$ 的範圍，即可得到使 $P_n$ 最大化的整數 $\hat{n}$。

> **直觀驗證**：根據比例法的簡單估計，若標記魚佔母體的比例 $\frac{50}{n}$ 約等於第二次捕獲中標記魚的比例 $\frac{4}{50}$，則 $\frac{50}{n} \approx \frac{4}{50}$，可得 $n \approx 625$。你的 MLE 結果應接近此值。

## 🔢 Derivation Process / 推導過程

### 步驟 1：以超幾何分佈寫出 $P_n$

此為典型的**標記−重捕法（mark-recapture method）**。已知參數：
- $K = 50$（標記魚總數）
- $m = 50$（第二次捕撈數量）
- $k = 4$（第二次捕獲中的標記魚數）
- $n$：湖中鱒魚總數（未知，待估計）

在總數 $n$ 的母體中，有 $K=50$ 條標記魚。不放回地抽取 $m=50$ 條，其中恰好有 $k=4$ 條標記魚的機率由**超幾何分佈**給出：

$$P_n = \frac{\binom{K}{k} \binom{n-K}{m-k}}{\binom{n}{m}} = \frac{\binom{50}{4} \binom{n-50}{46}}{\binom{n}{50}}$$

> 定義域：$n \geq 50 + 46 = 96$（母體必須至少能容納所有標記魚與未標記魚）

### 步驟 2：最大概似估計法（MLE）——比值法

要使 $P_n$ 在 $n = \hat{n}$ 處達到最大，必須同時滿足：
$$\frac{P_{\hat{n}}}{P_{\hat{n}+1}} \geq 1 \quad \text{且} \quad \frac{P_{\hat{n}}}{P_{\hat{n}-1}} \geq 1$$

這表示在 $\hat{n}$ 處，$P_n$ 不小於其前後鄰項。

---

### 步驟 3：化簡第一個比值 $\displaystyle \frac{P_n}{P_{n+1}}$

$$
\frac{P_n}{P_{n+1}} = \frac{\frac{\binom{50}{4} \binom{n-50}{46}}{\binom{n}{50}}}{\frac{\binom{50}{4} \binom{n-49}{46}}{\binom{n+1}{50}}}
= \frac{\binom{n-50}{46}}{\binom{n-49}{46}} \cdot \frac{\binom{n+1}{50}}{\binom{n}{50}}
$$

**化簡第一項** —— 利用 $\displaystyle \frac{\binom{N}{K}}{\binom{N+1}{K}} = \frac{N+1-K}{N+1}$

令 $N = n-50$，$K = 46$：
$$\frac{\binom{n-50}{46}}{\binom{n-49}{46}} = \frac{(n-49)-46}{n-49} = \frac{n-95}{n-49}$$

**化簡第二項** —— 利用 $\displaystyle \frac{\binom{N+1}{K}}{\binom{N}{K}} = \frac{N+1}{N+1-K}$

令 $N = n$，$K = 50$：
$$\frac{\binom{n+1}{50}}{\binom{n}{50}} = \frac{n+1}{n+1-50} = \frac{n+1}{n-49}$$

**合併**：
$$\frac{P_n}{P_{n+1}} = \frac{n-95}{n-49} \cdot \frac{n+1}{n-49} = \frac{(n-95)(n+1)}{(n-49)^2}$$

---

### 步驟 4：解第一個不等式 $\displaystyle \frac{P_n}{P_{n+1}} \geq 1$

$$\frac{(n-95)(n+1)}{(n-49)^2} \geq 1$$

由於 $(n-49)^2 > 0$（因為 $n \geq 96$），兩邊同乘 $(n-49)^2$：
$$(n-95)(n+1) \geq (n-49)^2$$

展開兩邊：
$$n^2 - 95n + n - 95 \geq n^2 - 98n + 2401$$
$$n^2 - 94n - 95 \geq n^2 - 98n + 2401$$

消去 $n^2$：
$$-94n - 95 \geq -98n + 2401$$
$$4n \geq 2496$$
$$n \geq 624$$

> **結論一**：當 $n \geq 624$ 時，$P_n \geq P_{n+1}$（序列從 $n=624$ 開始不再遞增）。

---

### 步驟 5：化簡第二個比值 $\displaystyle \frac{P_n}{P_{n-1}}$

$$
\frac{P_n}{P_{n-1}} = \frac{\frac{\binom{50}{4} \binom{n-50}{46}}{\binom{n}{50}}}{\frac{\binom{50}{4} \binom{n-51}{46}}{\binom{n-1}{50}}}
= \frac{\binom{n-50}{46}}{\binom{n-51}{46}} \cdot \frac{\binom{n-1}{50}}{\binom{n}{50}}
$$

**化簡第一項** —— 利用 $\displaystyle \frac{\binom{N}{K}}{\binom{N-1}{K}} = \frac{N}{N-K}$

令 $N = n-50$，$K = 46$：
$$\frac{\binom{n-50}{46}}{\binom{n-51}{46}} = \frac{n-50}{(n-50)-46} = \frac{n-50}{n-96}$$

**化簡第二項** —— 利用 $\displaystyle \frac{\binom{N-1}{K}}{\binom{N}{K}} = \frac{N-K}{N}$

令 $N = n$，$K = 50$：
$$\frac{\binom{n-1}{50}}{\binom{n}{50}} = \frac{n-50}{n}$$

**合併**：
$$\frac{P_n}{P_{n-1}} = \frac{n-50}{n-96} \cdot \frac{n-50}{n} = \frac{(n-50)^2}{n(n-96)}$$

---

### 步驟 6：解第二個不等式 $\displaystyle \frac{P_n}{P_{n-1}} \geq 1$

$$\frac{(n-50)^2}{n(n-96)} \geq 1$$

由於 $n > 96$ 時 $n(n-96) > 0$，兩邊同乘 $n(n-96)$：
$$(n-50)^2 \geq n(n-96)$$

展開兩邊：
$$n^2 - 100n + 2500 \geq n^2 - 96n$$

消去 $n^2$：
$$-100n + 2500 \geq -96n$$
$$2500 \geq 4n$$
$$n \leq 625$$

> **結論二**：當 $n \leq 625$ 時，$P_n \geq P_{n-1}$（序列在 $n=625$ 之前一直遞增）。

---

### 步驟 7：綜合判斷 —— 找出使 $P_n$ 最大化的 $\hat{n}$

由兩個不等式結果：
- $n \geq 624$ 時，$P_n \geq P_{n+1}$（序列非遞增）
- $n \leq 625$ 時，$P_n \geq P_{n-1}$（序列非遞減）

合併得：$624 \leq \hat{n} \leq 625$

在此範圍內詳細比對：
- 當 $n = 624$：由第一個條件 $(n \geq 624)$，得 $P_{624} \geq P_{625}$
- 當 $n = 625$：由第二個條件 $(n \leq 625)$，得 $P_{625} \geq P_{624}$

因此：
$$P_{624} = P_{625}$$

兩者均為最大值。在實際應用中，MLE 通常取：
$$\hat{n} = 625$$

### 步驟 8：以 Lincoln-Petersen 估計法驗證

根據 Lincoln-Petersen 的簡單比例估計：
$$\frac{K}{\hat{n}} \approx \frac{k}{m} \quad \Rightarrow \quad \hat{n} \approx \frac{K \cdot m}{k} = \frac{50 \times 50}{4} = 625$$

與 MLE 結果完全一致 ✓

### 步驟 9：最終答案

$$\boxed{\hat{n} = 625}$$

> **補充說明**：此結果表示，根據實驗數據（50 條標記魚、第二次捕獲 50 條中有 4 條標記魚），湖中鱒魚總數的最大概似估計值為 **625 條**。在更精確的分析中，$n=624$ 與 $n=625$ 給出相等的 $P_n$ 值，兩者皆為 MLE 的解，實務上通常取 $625$。
