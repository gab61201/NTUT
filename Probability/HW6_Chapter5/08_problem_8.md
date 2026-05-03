# Problem 8 / 第 8 題

## 📖 Original Text / 原文

The probability is $p$ that a randomly chosen light bulb is defective. We screw a bulb into a lamp and switch on the current. If the bulb works, we stop; otherwise, we try another and continue until a good bulb is found. What is the probability that at least $n$ bulbs are required?

## 🇹🇼 Chinese Translation / 中文翻譯

隨機選取一個燈泡為瑕疵品的機率是 $p$。我們將一個燈泡裝入燈座並打開電源。如果燈泡正常運作，我們就停止；否則，我們換另一個燈泡繼續嘗試，直到找到一個好的燈泡為止。請問需要至少 $n$ 個燈泡的機率是多少？

## 💡 Detailed Explanation / 詳細解釋

### (1) 涉及的機率分佈

此問題涉及**幾何分佈 (Geometric Distribution)**。每一次嘗試（裝上燈泡並測試）是一次伯努利試驗 (Bernoulli trial)，其結果為「成功」（找到好燈泡，機率為 $1-p$）或「失敗」（找到瑕疵品，機率為 $p$）。我們重複試驗直到第一次成功為止，這正是幾何分佈的定義場景。

設隨機變數 $X$ 為「直到找到第一個好燈泡所需的燈泡總數」，則 $X \sim \text{Geometric}(1-p)$。

### (2) 關鍵參數分析

- **$p$**：單一燈泡為瑕疵品的機率（失敗機率）
- **$1-p$**：單一燈泡為良品的機率（成功機率）
- **$n$**：問題給定的正整數門檻值
- **「至少 $n$ 個燈泡」** 意味著前 $n-1$ 個燈泡全部都是瑕疵品（即前 $n-1$ 次試驗全部失敗）

幾何分佈的機率質量函數 (PMF) 為：
$$P(X = k) = (1-p) \cdot p^{\,k-1}, \quad k = 1, 2, 3, \ldots$$

### (3) 解題思路提示

要計算 $P(X \geq n)$，不需要對每個 $k \geq n$ 的 PMF 一一加總。關鍵觀察是：**需要至少 $n$ 個燈泡** 等價於 **前 $n-1$ 個燈泡全部都是瑕疵品**。

因此：
$$P(X \geq n) = P(\text{前 } n-1 \text{ 個燈泡皆為瑕疵品}) = p^{\,n-1}$$

這比對無窮級數求和要簡單得多。你可以進一步驗證：將 $P(X = k) = (1-p)p^{\,k-1}$ 從 $k=n$ 加到無窮大，其結果同樣收斂到 $p^{\,n-1}$，這與上述直觀推理一致。

> **提示**：注意到當 $p$ 很小時（瑕疵率低），需要至少 $n$ 個燈泡的機率會隨著 $n$ 增加而急劇下降；反之，若 $p$ 很大（瑕疵率高），此機率則較為可觀。

## 🔢 Derivation Process / 推導過程

### 步驟 1：定義隨機變數與分佈

令隨機變數 $X$ 表示「直到找到第一個良品燈泡所需的燈泡總數」。每次試驗中：
- 成功（找到良品）的機率為 $1-p$
- 失敗（找到瑕疵品）的機率為 $p$

由於我們重複進行獨立試驗直到第一次成功為止，$X$ 服從幾何分佈：
$$X \sim \text{Geometric}(1-p)$$

其機率質量函數（PMF）為：
$$P(X = k) = (1-p) \cdot p^{\,k-1}, \quad k = 1, 2, 3, \ldots$$

### 步驟 2：轉化問題 ——「至少 $n$ 個」的等價條件

「需要至少 $n$ 個燈泡」即 $X \geq n$，這意味著前 $n-1$ 個燈泡**全部都是瑕疵品**。因為只要前 $n-1$ 個中有任何一個是良品，我們早就在那時停止了。

因此：
$$P(X \geq n) = P(\text{前 } n-1 \text{ 個燈泡皆為瑕疵品})$$

### 步驟 3：計算機率

每次試驗中燈泡為瑕疵品的機率為 $p$，且各次試驗互相獨立。因此前 $n-1$ 次全部失敗的機率為：
$$P(X \geq n) = \underbrace{p \cdot p \cdot \cdots \cdot p}_{n-1 \text{ 次}} = p^{\,n-1}$$

### 步驟 4：以無窮級數驗證（選讀）

我們也可以用 PMF 求和來驗證此結果：
$$
\begin{aligned}
P(X \geq n) &= \sum_{k=n}^{\infty} P(X = k) \\[4pt]
&= \sum_{k=n}^{\infty} (1-p) \cdot p^{\,k-1} \\[4pt]
&= (1-p) \cdot p^{\,n-1} \sum_{j=0}^{\infty} p^{\,j} \quad (\text{令 } j = k-n) \\[4pt]
&= (1-p) \cdot p^{\,n-1} \cdot \frac{1}{1-p} \\[4pt]
&= p^{\,n-1}
\end{aligned}
$$

兩種方法得到一致的結果，驗證了推導的正確性。

### 步驟 5：最終答案

$$\boxed{P(\text{至少需要 } n \text{ 個燈泡}) = p^{\,n-1}}$$

其中 $p$ 為單一燈泡是瑕疵品的機率，$n$ 為任意正整數（$n \geq 1$）。

> **補充說明**：此結果亦為幾何分佈的**生存函數（survival function）**，即 $\bar{F}(n-1) = P(X \geq n) = p^{\,n-1}$。當 $n=1$ 時，$P(X \geq 1) = p^0 = 1$，即至少需要 1 個燈泡的機率為 100%，與直覺相符。
