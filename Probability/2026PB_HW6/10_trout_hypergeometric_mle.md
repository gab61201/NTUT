# Problem 10 / 第 10 題

## 📖 Original Text / 原文

To estimate the number of trout in a lake, we caught 50 trout, tagged and returned them. Later we caught 50 trout and found that four of them were tagged. From this experiment result, please estimate $n$, the total number of trout in the lake.

Hint: Let $P_n$ be the probability of four tagged trout among the 50 trout caught, if the total number of trout in the lake is $n$. Then, find the value of $n$ that maximizes $P_n$. (Note: In statistics, this approach to estimate value of $n$ is called the maximum likelihood estimate for the number of trout in lake. For this question, you may first find $P_n$, using the hypergeometric random variable. Then use the relation $P_n / P_{n+1} \geq 1$ and $P_n / P_{n-1} \geq 1$ to find the value of $n$ that maximizes $P_n$.)

## 🇹🇼 Chinese Translation / 中文翻譯

為了估計湖中鱒魚的數量，我們捕獲了 50 條鱒魚，做標記後放回湖中。之後我們再次捕獲 50 條鱒魚，發現其中有 4 條帶有標記。根據此實驗結果，請估計 $n$，即湖中鱒魚的總數。

提示：令 $P_n$ 為在湖中鱒魚總數為 $n$ 的條件下，第二次捕獲的 50 條魚中恰好有 4 條帶標記的機率。然後找出使 $P_n$ 最大化的 $n$ 值。（注意：在統計學中，這種估計 $n$ 的方法稱為最大概似估計。解本題時，你可以先用超幾何隨機變數求出 $P_n$，然後利用關係式 $P_n / P_{n+1} \geq 1$ 和 $P_n / P_{n-1} \geq 1$ 來找出使 $P_n$ 最大化的 $n$ 值。）

## 💡 Detailed Explanation / 詳細解釋

### 1. 這是什麼分佈？為什麼？

此題使用**超幾何分佈 (Hypergeometric Distribution)**。判斷關鍵：

- 湖中總共有 $n$ 條鱒魚（未知，待估計）
- 其中 $K = 50$ 條是「有標記的」（視為「成功」類別）
- 剩下的 $n - 50$ 條是「無標記的」（視為「失敗」類別）
- 我們從中**不放回地**抽取 $n_{\text{sample}} = 50$ 條魚（第二次捕獲）
- 關心的是樣本中「成功」的數量（有標記的魚數）$X$，觀察值為 $x = 4$

> 這是一個典型的**捕獲-再捕獲 (Capture-Recapture)** 實驗，標準做法就是用超幾何分佈建模。

### 2. 關鍵參數拆解

| 參數 | 符號 | 數值 | 意義 |
|------|------|------|------|
| 總體大小 | $n$ (或 $N$) | **未知，待估計** | 湖中鱒魚總數 |
| 總體中成功數 | $K$ | $50$ | 第一次捕獲並標記的魚數 |
| 樣本大小 | $n_{\text{sample}}$ | $50$ | 第二次捕獲的魚數 |
| 觀察到的成功數 | $x$ | $4$ | 第二次捕獲中有標記的魚數 |
| 概似函數 | $P_n$ | — | 在給定 $n$ 下觀察到 $x=4$ 的機率 |

### 3. 解題思路提示（不給完整答案）

#### Step 1：寫出概似函數 $P_n$

超幾何分佈的 PMF 為：
$$P(X = x) = \frac{\binom{K}{x} \binom{N-K}{n_{\text{sample}}-x}}{\binom{N}{n_{\text{sample}}}}$$

代入已知數值（$K=50$, $n_{\text{sample}}=50$, $x=4$）：
$$P_n = \frac{\binom{50}{4} \binom{n-50}{46}}{\binom{n}{50}}$$

其中 $n \geq 50 + 50 - 4 = 96$（因為第二次捕獲 50 條中有 4 條有標記、46 條無標記，所以總無標記魚數 $n-50$ 至少要有 46 條）。

#### Step 2：最大化 $P_n$ — 使用提示中的比值法

提示建議比較相鄰的 $n$ 值：

- 條件一：$P_n \geq P_{n+1}$ 等價於 $\frac{P_n}{P_{n+1}} \geq 1$
- 條件二：$P_n \geq P_{n-1}$ 等價於 $\frac{P_n}{P_{n-1}} \geq 1$

當 $n$ 滿足這兩個不等式時，$P_n$ 達到最大值。

#### Step 3：化簡比值

超幾何機率的比值可以大幅化簡。對於 $\frac{P_n}{P_{n+1}}$：

$$\frac{P_n}{P_{n+1}} = \frac{\frac{\binom{50}{4}\binom{n-50}{46}}{\binom{n}{50}}}{\frac{\binom{50}{4}\binom{n+1-50}{46}}{\binom{n+1}{50}}} = \frac{\binom{n-50}{46}}{\binom{n}{50}} \cdot \frac{\binom{n+1}{50}}{\binom{n-49}{46}}$$

利用組合數性質 $\binom{n+1}{50} = \binom{n}{50} \cdot \frac{n+1}{n+1-50}$ 以及 $\binom{n-49}{46} = \binom{n-50}{46} \cdot \frac{n-49}{n-49-46}$，可大幅化簡。

#### Step 4：求解

- 從 $\frac{P_n}{P_{n+1}} \geq 1$ 得出一個關於 $n$ 的不等式
- 從 $\frac{P_n}{P_{n-1}} \geq 1$ 得出另一個不等式
- 兩個不等式共同界定出一個 $n$ 的範圍，通常是一個整數或極小範圍，即為 MLE 估計值

#### 💭 直觀理解

「最大概似估計」(MLE) 的核心思想是：選擇一個 $n$ 使得我們**實際觀察到的結果（50 條中有 4 條有標記）最有可能發生**。直觀上，如果湖中有非常多的魚，抓到 4 條有標記的魚就會很不尋常（因為標記魚被稀釋了）；反之如果湖中魚很少，抓到 4 條有標記的魚又顯得太少。MLE 找到的 $n$ 正好讓觀察結果的機率最大。

這道題目是經典的 **Lincoln-Petersen 估計量** 的離散版本。簡單的比例估計為 $\hat{n} \approx \frac{50 \times 50}{4} = 625$，而 MLE 方法給出的精確值可能略有不同，值得動手計算確認。

## 🔢 Derivation Process / 推導過程

### Step 1: Write the Likelihood Function $P_n$

We use the **Hypergeometric distribution** to model the second catch. In a lake with $n$ total trout, of which $K = 50$ are tagged, we catch a sample of $n_s = 50$ trout without replacement.

$$P_n = P(X = 4) = \frac{\binom{50}{4} \binom{n-50}{46}}{\binom{n}{50}}$$

The domain is $n \geq 96$ (since $n-50 \geq 46$ to have at least 46 untagged fish in the lake).

### Step 2: Set Up the Ratio Method

To find the $n$ that maximizes $P_n$, we use the condition:

$$\frac{P_n}{P_{n+1}} \geq 1 \quad \text{and} \quad \frac{P_n}{P_{n-1}} \geq 1$$

These inequalities identify where $P_n$ stops increasing and starts decreasing.

### Step 3: Simplify $\frac{P_n}{P_{n+1}}$

$$\frac{P_n}{P_{n+1}} = \frac{\frac{\binom{50}{4}\binom{n-50}{46}}{\binom{n}{50}}}{\frac{\binom{50}{4}\binom{n-49}{46}}{\binom{n+1}{50}}}
= \frac{\binom{n-50}{46}}{\binom{n-49}{46}} \cdot \frac{\binom{n+1}{50}}{\binom{n}{50}}$$

**First ratio:**

$$\frac{\binom{n-50}{46}}{\binom{n-49}{46}}
= \frac{\frac{(n-50)!}{46!\,(n-96)!}}{\frac{(n-49)!}{46!\,(n-95)!}}
= \frac{(n-50)!}{(n-49)!} \cdot \frac{(n-95)!}{(n-96)!}
= \frac{1}{n-49} \cdot (n-95)
= \frac{n-95}{n-49}$$

**Second ratio:**

$$\frac{\binom{n+1}{50}}{\binom{n}{50}}
= \frac{\frac{(n+1)!}{50!\,(n-49)!}}{\frac{n!}{50!\,(n-50)!}}
= \frac{(n+1)!}{n!} \cdot \frac{(n-50)!}{(n-49)!}
= (n+1) \cdot \frac{1}{n-49}
= \frac{n+1}{n-49}$$

**Combined:**

$$\frac{P_n}{P_{n+1}} = \frac{n-95}{n-49} \cdot \frac{n+1}{n-49} = \frac{(n-95)(n+1)}{(n-49)^2}$$

### Step 4: Apply the First Inequality $\frac{P_n}{P_{n+1}} \geq 1$

$$\frac{(n-95)(n+1)}{(n-49)^2} \geq 1$$

$$(n-95)(n+1) \geq (n-49)^2$$

$$n^2 - 94n - 95 \geq n^2 - 98n + 2401$$

$$-94n - 95 \geq -98n + 2401$$

$$4n \geq 2496$$

$$n \geq 624$$

### Step 5: Simplify $\frac{P_n}{P_{n-1}}$

$$\frac{P_n}{P_{n-1}} = \frac{\frac{\binom{50}{4}\binom{n-50}{46}}{\binom{n}{50}}}{\frac{\binom{50}{4}\binom{n-51}{46}}{\binom{n-1}{50}}}
= \frac{\binom{n-50}{46}}{\binom{n-51}{46}} \cdot \frac{\binom{n-1}{50}}{\binom{n}{50}}$$

**First ratio:**

$$\frac{\binom{n-50}{46}}{\binom{n-51}{46}}
= \frac{\frac{(n-50)!}{46!\,(n-96)!}}{\frac{(n-51)!}{46!\,(n-97)!}}
= \frac{n-50}{n-96}$$

**Second ratio:**

$$\frac{\binom{n-1}{50}}{\binom{n}{50}}
= \frac{\frac{(n-1)!}{50!\,(n-51)!}}{\frac{n!}{50!\,(n-50)!}}
= \frac{(n-1)!}{n!} \cdot \frac{(n-50)!}{(n-51)!}
= \frac{1}{n} \cdot (n-50)
= \frac{n-50}{n}$$

**Combined:**

$$\frac{P_n}{P_{n-1}} = \frac{n-50}{n-96} \cdot \frac{n-50}{n} = \frac{(n-50)^2}{n(n-96)}$$

### Step 6: Apply the Second Inequality $\frac{P_n}{P_{n-1}} \geq 1$

$$\frac{(n-50)^2}{n(n-96)} \geq 1$$

$$(n-50)^2 \geq n(n-96)$$

$$n^2 - 100n + 2500 \geq n^2 - 96n$$

$$-100n + 2500 \geq -96n$$

$$2500 \geq 4n$$

$$n \leq 625$$

### Step 7: Combine Both Inequalities

From Step 4: $n \geq 624$
From Step 6: $n \leq 625$

Therefore: $624 \leq n \leq 625$

Both $n = 624$ and $n = 625$ are candidates.

### Step 8: Check Tie at the Boundary

Evaluate $\frac{P_{624}}{P_{625}}$:

$$\frac{P_{624}}{P_{625}} = \frac{(624-95)(624+1)}{(624-49)^2} = \frac{529 \times 625}{575^2} = \frac{330625}{330625} = 1$$

So $P_{624} = P_{625}$. Both values of $n$ give exactly the same probability, so both are maximum likelihood estimates.

### Step 9: Final Answer

$$\boxed{\hat{n}_{\text{MLE}} = 624 \text{ or } 625}$$

**Remark:** The simple Lincoln-Petersen estimator gives $\hat{n} \approx \frac{50 \times 50}{4} = 625$, which is consistent with our MLE result.
