# Problem 6 / 第 6 題

## 📖 Original Text / 原文

Suppose that $X$ is a Poisson random variable with $P(X = 1) = P(X = 3)$. Find $P(X = 5)$.

## 🇹🇼 Chinese Translation / 中文翻譯

假設 $X$ 是一個卜瓦松隨機變數，且滿足 $P(X = 1) = P(X = 3)$。求 $P(X = 5)$。

## 💡 Detailed Explanation / 詳細解釋

### (1) 涉及的機率分佈

本題直接處理 **卜瓦松分佈（Poisson Distribution）** 的參數求解問題。已知 $X \sim \text{Poisson}(\lambda)$，但 $\lambda$ 未知——必須先從給定的等式 $P(X = 1) = P(X = 3)$ 中解出 $\lambda$，再代入計算 $P(X = 5)$。

這是一道典型的「從條件反推參數，再計算目標機率」的題型，考驗對卜瓦松 PMF 的代數操作能力。

### (2) 關鍵參數分析

| 參數 | 符號 | 說明 |
|------|------|------|
| 卜瓦松參數 | $\lambda$ | 未知，需由條件等式求解 |
| 已知條件 | $P(X = 1) = P(X = 3)$ | 用於建立 $\lambda$ 的方程式 |
| 目標 | $P(X = 5)$ | 代入求得的 $\lambda$ 計算 |

卜瓦松 PMF：

$$P(X = k) = \frac{e^{-\lambda} \lambda^k}{k!}$$

### (3) 解題思路提示

- **第一步**：寫出 $P(X = 1)$ 和 $P(X = 3)$ 的 PMF 表達式：

$$P(X = 1) = \frac{e^{-\lambda} \lambda^1}{1!} = e^{-\lambda} \lambda$$

$$P(X = 3) = \frac{e^{-\lambda} \lambda^3}{3!} = \frac{e^{-\lambda} \lambda^3}{6}$$

- **第二步**：令兩式相等並解 $\lambda$：

$$e^{-\lambda} \lambda = \frac{e^{-\lambda} \lambda^3}{6}$$

兩邊同時消去 $e^{-\lambda}$（因為 $e^{-\lambda} > 0$ 恆成立）：

$$\lambda = \frac{\lambda^3}{6}$$

移項得：

$$\lambda^3 - 6\lambda = 0 \quad \Rightarrow \quad \lambda(\lambda^2 - 6) = 0$$

- **第三步**：$\lambda = 0$ 對卜瓦松分佈無意義（期望值為 0 意味著永遠為 0，此時 $P(X=1)=P(X=3)=0$，雖滿足等式但為退化解），因此取 $\lambda = \sqrt{6}$。

- **第四步**：代入 $\lambda = \sqrt{6}$ 計算 $P(X = 5)$：

$$P(X = 5) = \frac{e^{-\sqrt{6}} \cdot (\sqrt{6})^5}{5!}$$

> 💡 **提示**：$(\sqrt{6})^5 = 6^{5/2} = 6^2 \cdot \sqrt{6} = 36\sqrt{6}$，且 $5! = 120$。因此 $P(X=5) = \dfrac{e^{-\sqrt{6}} \cdot 36\sqrt{6}}{120} = \dfrac{3\sqrt{6}}{10} e^{-\sqrt{6}}$。$e^{-\sqrt{6}}$ 可留作符號形式或近似計算數值（$\sqrt{6} \approx 2.449$）。

## 🔢 Derivation Process / 推導過程

### 步驟 1：寫出卜瓦松 PMF

已知 $X \sim \text{Poisson}(\lambda)$，其中 $\lambda$ 未知。卜瓦松 PMF 為：

$$P(X = k) = \frac{e^{-\lambda} \lambda^k}{k!}$$

### 步驟 2：利用條件 $P(X = 1) = P(X = 3)$ 建立方程式

分別寫出 $k = 1$ 與 $k = 3$ 的機率：

$$
\begin{aligned}
P(X = 1) &= \frac{e^{-\lambda} \lambda^1}{1!} = \lambda e^{-\lambda} \\[6pt]
P(X = 3) &= \frac{e^{-\lambda} \lambda^3}{3!} = \frac{\lambda^3 e^{-\lambda}}{6}
\end{aligned}
$$

令兩式相等：

$$\lambda e^{-\lambda} = \frac{\lambda^3 e^{-\lambda}}{6}$$

### 步驟 3：解出 $\lambda$

兩邊同時除以 $\lambda e^{-\lambda}$（因為 $\lambda > 0$ 且 $e^{-\lambda} > 0$）：

$$1 = \frac{\lambda^2}{6}$$

$$\lambda^2 = 6$$

$$\lambda = \sqrt{6} \quad (\text{取正根，} \lambda > 0)$$

> 註：$\lambda = 0$ 亦滿足等式，但對卜瓦松分佈而言 $\lambda = 0$ 為退化解（$X \equiv 0$ 恆成立），故取 $\lambda = \sqrt{6}$。

### 步驟 4：計算 $P(X = 5)$

代入 $\lambda = \sqrt{6}$ 與 $k = 5$：

$$P(X = 5) = \frac{e^{-\sqrt{6}} \cdot (\sqrt{6})^5}{5!}$$

化簡分子：

- $(\sqrt{6})^5 = (\sqrt{6})^2 \cdot (\sqrt{6})^3 = 6 \cdot 6\sqrt{6} = 36\sqrt{6}$

或者 $(\sqrt{6})^5 = 6^{5/2} = 6^2 \cdot 6^{1/2} = 36\sqrt{6}$

分母：$5! = 120$

因此：

$$P(X = 5) = \frac{e^{-\sqrt{6}} \cdot 36\sqrt{6}}{120} = \frac{3\sqrt{6}}{10} \, e^{-\sqrt{6}}$$

### 步驟 5：數值代入

$$
\begin{aligned}
\sqrt{6} &\approx 2.44949 \\
e^{-\sqrt{6}} &\approx e^{-2.44949} \approx 0.086294 \\
(\sqrt{6})^5 &\approx (2.44949)^5 \approx 88.1816
\end{aligned}
$$

代入計算：

$$
\begin{aligned}
P(X = 5) &= \frac{0.086294 \times 88.1816}{120} \\[6pt]
&= \frac{7.6097}{120} \\[6pt]
&= 0.063414
\end{aligned}
$$

### 📦 最終答案

$$
\boxed{P(X = 5) \approx 0.06341}
$$

> 亦可保留精確形式：$\displaystyle P(X = 5) = \frac{3\sqrt{6}}{10}\, e^{-\sqrt{6}}$。
