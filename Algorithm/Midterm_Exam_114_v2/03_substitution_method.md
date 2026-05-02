# Problem 3: Substitution Method / 代入法

---

## 📖 Original Text / 原文

Use the substitution method to prove that the recurrence $T(n) = T(n-1) + \Theta(n)$ has the solution $T(n) = \Theta(n^2)$.

---

## 🇹🇼 Chinese Translation / 中文翻譯

使用代入法證明遞迴式 $T(n) = T(n-1) + \Theta(n)$ 的解為 $T(n) = \Theta(n^2)$。

---

## 💡 Detailed Explanation / 詳細解釋

### (1) 涉及的演算法概念

**代入法 (Substitution Method)** 是解遞迴式的三大方法之一（另外兩個是遞迴樹法和主定理）。其步驟為：

1. **猜測**解的漸近形式（例如猜 $T(n) = O(n^2)$）
2. **歸納假設**：假設對於所有 $m < n$，$T(m) \leq c \cdot m^2$（上界證明）
3. **代入遞迴式**，證明 $T(n) \leq c \cdot n^2$ 對於足夠大的 $c$ 成立
4. **驗證基底情況**

本題的遞迴式 $T(n) = T(n-1) + \Theta(n)$ 是典型的**線性遞迴**，展開後得到 $T(n) = \Theta(1) + \Theta(2) + \dots + \Theta(n) = \Theta(n^2)$。代入法的目的是**形式化**這個直覺。

### (2) 關鍵參數分析

| 概念 | 說明 |
|------|------|
| 遞迴形式 | $T(n) = T(n-1) + \Theta(n)$ |
| 猜測的上界 | $T(n) = O(n^2)$，即 $T(n) \leq cn^2$ |
| 猜測的下界 | $T(n) = \Omega(n^2)$，即 $T(n) \geq c'n^2$ |
| 證明策略 | 先證上界，再證下界（各自獨立的歸納證明） |

### (3) 解題思路提示

**上界證明 $T(n) = O(n^2)$：**

- 將 $\Theta(n)$ 具體化為「存在 $d > 0$ 使得附加成本 $\leq dn$」
- 歸納假設：$T(n-1) \leq c(n-1)^2$
- 代入：$T(n) = T(n-1) + \Theta(n) \leq c(n-1)^2 + dn$
- 展開：$c(n-1)^2 + dn = c(n^2 - 2n + 1) + dn = cn^2 - 2cn + c + dn$
- 需要：$cn^2 - 2cn + c + dn \leq cn^2$
- 化簡：$-2cn + c + dn \leq 0$，即 $n(d - 2c) + c \leq 0$
- 關鍵：對於 $c > d/2$，當 $n$ 足夠大時不等式成立
- 基底情況：驗證 $T(1) \leq c \cdot 1^2$ 對於足夠大的 $c$ 成立

**下界證明 $T(n) = \Omega(n^2)$：**
- 類似但不等式方向相反，使用 $T(n) \geq c'n^2$ 的形式
- 由於 $\Theta(n)$ 也有下界（存在 $d' > 0$ 使附加成本 $\geq d'n$），$T(n) = T(n-1) + \Theta(n) \geq c'(n-1)^2 + d'n$

> **注意：** 完整的證明需要分別證明 $T(n) = O(n^2)$ 和 $T(n) = \Omega(n^2)$，兩者結合才能得出 $T(n) = \Theta(n^2)$。

---

## 🔢 Derivation Process / 推導過程

### 上界證明：$T(n) = O(n^2)$

將 $\Theta(n)$ 具體化：存在常數 $d > 0$，使得對於足夠大的 $n$，附加成本 $\leq dn$。

遞迴式變為：

$$T(n) \leq T(n-1) + dn$$

**猜測**：$T(n) \leq cn^2$（對於某個 $c > 0$）

**歸納假設**：對於 $n-1$，$T(n-1) \leq c(n-1)^2$

**代入**：

$$
\begin{aligned}
T(n) &\leq T(n-1) + dn \\
     &\leq c(n-1)^2 + dn \\
     &= c(n^2 - 2n + 1) + dn \\
     &= cn^2 - 2cn + c + dn \\
     &= cn^2 - (2c - d)n + c
\end{aligned}
$$

**需要證明**：$cn^2 - (2c - d)n + c \leq cn^2$

即 $-(2c - d)n + c \leq 0$，也就是 $(2c - d)n \geq c$。

選擇 $c \geq d$，則 $2c - d \geq d > 0$。對於所有 $n \geq \dfrac{c}{2c - d}$，不等式成立。

因此對於足夠大的 $c$（如 $c = \max(d, T(1))$），歸納成立。

$$\boxed{T(n) = O(n^2)}$$

---

### 下界證明：$T(n) = \Omega(n^2)$

將 $\Theta(n)$ 的下界具體化：存在常數 $d' > 0$，使得對於足夠大的 $n$，附加成本 $\geq d'n$。

遞迴式變為：

$$T(n) \geq T(n-1) + d'n$$

**猜測**：$T(n) \geq c'n^2$（對於某個 $c' > 0$）

**歸納假設**：對於 $n-1$，$T(n-1) \geq c'(n-1)^2$

**代入**：

$$
\begin{aligned}
T(n) &\geq T(n-1) + d'n \\
     &\geq c'(n-1)^2 + d'n \\
     &= c'(n^2 - 2n + 1) + d'n \\
     &= c'n^2 - 2c'n + c' + d'n \\
     &= c'n^2 - (2c' - d')n + c'
\end{aligned}
$$

**需要證明**：$c'n^2 - (2c' - d')n + c' \geq c'n^2$

即 $-(2c' - d')n + c' \geq 0$，也就是 $(2c' - d')n \leq c'$。

選擇 $c' \leq d'/2$，則 $2c' - d' \leq 0$，因此 $-(2c' - d')n$ 為非負項，加上 $c' > 0$ 後不等式對所有 $n$ 成立。

因此對於足夠小的 $c'$（如 $c' = \min(d'/2, T(1))$），歸納成立。

$$\boxed{T(n) = \Omega(n^2)}$$

---

### 合併結論

由上界 $T(n) = O(n^2)$ 與下界 $T(n) = \Omega(n^2)$：

$$\boxed{T(n) = \Theta(n^2)}$$

**直覺驗證**：展開 $T(n) = T(n-1) + \Theta(n) = T(1) + \sum_{i=2}^{n} \Theta(i) = \Theta\left(\sum_{i=1}^{n} i\right) = \Theta(n^2)$，與代入法結論一致。
