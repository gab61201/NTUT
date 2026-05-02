# Problem 3 / 第 3 題

## 📖 Original Text / 原文

3. The simplest error detection scheme used in data communication is parity checking. Each character consists of a number of bits (a bit is the smallest unit of information and is either 1 or 0). In parity checking, a 1 or 0 is appended to the end of each character at the transmitter to make the total number of 1's even. The receiver checks the number of 1's in every character received, and if the result is odd it signals an error. Suppose that each bit is received correctly with probability 0.999, independently of other bits. What is the probability that a 7-bit character is received in error, but the error is not detected by the parity check?

## 🇹🇼 Chinese Translation / 中文翻譯

資料通訊中最簡單的錯誤偵測機制是同位元檢查（parity checking）。每個字元由若干位元組成（位元是資訊的最小單位，值為 1 或 0）。在同位元檢查中，發送端會在每個字元末尾附加一個 1 或 0，使得字元中 1 的總數為偶數。接收端則檢查所收到的每個字元中 1 的數量，若結果為奇數則發出錯誤訊號。假設每個位元被正確接收的機率為 0.999，且各位元之間相互獨立。請問一個 7 位元的字元在接收時發生錯誤、但該錯誤未被同位元檢查偵測到的機率是多少？

## 💡 Detailed Explanation / 詳細解釋

### (1) 涉及的機率分佈

本題雖然情境較複雜，但仍然建立在 **二項分佈（Binomial Distribution）** 的基礎上。關鍵在於：每個位元被「正確接收」或「發生錯誤」是一個伯努利試驗，且 7 個位元彼此獨立。

令 $Y$ 表示 7 個位元中發生錯誤的位元數量。因為每個位元發生錯誤的機率為 $1 - 0.999 = 0.001$，且各位元獨立，所以：

$$Y \sim \text{Binomial}(n=7, p=0.001)$$

### (2) 關鍵參數與問題拆解

- **$n = 7$**：字元中的位元數量
- **$p = 0.001$**：單一位元發生錯誤的機率（即從正確的 0 變成 1，或從正確的 1 變成 0）
- **$1-p = 0.999$**：單一位元正確接收的機率

本題要求的是：「接收錯誤（有至少一個位元出錯）且同位元檢查未偵測到」的機率。

**同位元檢查何時偵測不到錯誤？** 同位元檢查是偶同位（even parity）：發送端保證所有位元中 1 的個數為偶數。當接收端收到奇數個 1 時，就會偵測到錯誤。因此：
- **未被偵測到** ⇔ 接收到的 7 個位元中，1 的個數仍然是**偶數**

這等價於：錯誤的位元數量必須是**偶數**（0、2、4、6），因為改變偶數個位元不會改變 1 的總數的奇偶性。

### (3) 解題思路提示

**關鍵洞察**：錯誤「未被偵測到」意味著發生錯誤的位元數 $Y$ 必須是偶數。但題目還要求「字元接收錯誤」，也就是 $Y \geq 1$（至少有一個位元出錯）。

因此所求機率為：

$$P(\text{undetected error}) = P(Y \text{ is even and } Y \geq 1)$$

即：

$$P(Y = 2) + P(Y = 4) + P(Y = 6)$$

其中每一項都可以用二項分佈 PMF 計算：

$$P(Y = k) = \binom{7}{k} (0.001)^k (0.999)^{7-k}$$

**注意事項**：
- $Y = 0$ 雖然是偶數，但代表沒有錯誤，不符合「received in error」的條件，所以不納入
- 由於 $p = 0.001$ 非常小，$Y \geq 3$（三個以上位元同時出錯）的機率極低，答案主要由 $P(Y=2)$ 貢獻
- 這是實際通訊系統中同位元檢查的經典缺陷：它只能偵測奇數個位元錯誤，無法偵測偶數個位元錯誤

## 🔢 Derivation Process / 推導過程

### Step 1: Identify the Distribution and Parameters

Each bit is received correctly with probability $0.999$, independently. Thus, each bit is received **in error** (flipped) with probability:

$$p = 1 - 0.999 = 0.001$$

For a 7-bit character, let $Y$ be the number of bit errors:

$$Y \sim \text{Binomial}(n=7,\; p=0.001)$$

The PMF is:

$$P(Y = k) = \binom{7}{k} (0.001)^k (0.999)^{7-k}$$

### Step 2: Understand When Parity Check Fails to Detect an Error

Even parity: the transmitter ensures the total number of 1's is even. The receiver flags an error if it counts an **odd** number of 1's.

- If an **odd** number of bits are flipped → the parity (odd/even of the 1-count) changes → error **is detected** ✓
- If an **even** number of bits are flipped → the parity stays even → error **is NOT detected** ✗

Therefore, an undetected error occurs when $Y$ is a **positive even number**:

$$Y \in \{2, 4, 6\}$$

($Y = 0$ is excluded because the problem says "received in error" — at least one bit must be wrong.)

### Step 3: Express the Target Probability

$$P(\text{undetected error}) = P(Y = 2) + P(Y = 4) + P(Y = 6)$$

### Step 4: Compute $P(Y = 2)$

$$\binom{7}{2} = \frac{7 \times 6}{2} = 21$$

$$(0.001)^2 = 10^{-6}$$

$$(0.999)^5 = (1 - 0.001)^5$$

Using binomial expansion: $(1 - x)^5 \approx 1 - 5x + 10x^2 - \cdots$ with $x = 0.001$:

$$(0.999)^5 \approx 1 - 0.005 + 0.00001 = 0.99501$$

More precisely:

$$(0.999)^5 = 0.995009990004999$$

$$P(Y = 2) = 21 \times 10^{-6} \times 0.995009990004999 \approx 2.08952 \times 10^{-5}$$

### Step 5: Compute $P(Y = 4)$

$$\binom{7}{4} = \frac{7 \times 6 \times 5}{3 \times 2 \times 1} = 35$$

$$(0.001)^4 = 10^{-12}$$

$$(0.999)^3 = 0.997002999$$

$$P(Y = 4) = 35 \times 10^{-12} \times 0.997002999 \approx 3.4895 \times 10^{-11}$$

### Step 6: Compute $P(Y = 6)$

$$\binom{7}{6} = 7$$

$$(0.001)^6 = 10^{-18}$$

$$P(Y = 6) = 7 \times 10^{-18} \times 0.999 \approx 6.993 \times 10^{-18}$$

This term is utterly negligible compared to $P(Y=2)$.

### Step 7: Sum the Probabilities

$$P(\text{undetected error}) = 2.08952 \times 10^{-5} + 3.4895 \times 10^{-11} + 6.993 \times 10^{-18}$$

The contributions from $Y=4$ and $Y=6$ are many orders of magnitude smaller, so:

$$P(\text{undetected error}) \approx 2.09 \times 10^{-5}$$

### Step 8: Final Answer

$$\boxed{P(\text{undetected error}) \approx 2.09 \times 10^{-5} = 0.0000209}$$

This extremely small probability is dominated by the chance of exactly 2 bits being flipped simultaneously — a rare but not impossible event. The parity check catches all single-bit errors (the most common case) but has this tiny blind spot for even numbers of errors.
