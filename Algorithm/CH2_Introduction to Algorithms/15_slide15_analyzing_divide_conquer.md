# Slide 15 — Analyzing Divide-and-Conquer Algorithms (分析分治演算法)

## 📖 Original Text / 原文

---

**Analyzing divide-and-conquer Algorithms**

- Advantage: running time are often easily determined
- $T(n) = aT(n/b) + D(n) + C(n)$
  $T(n) = \Theta(1)$, if $n \leq c$,
- For the merge sort: $D(n) = \Theta(1)$, $C(n) = \Theta(n)$
  $T(n) = 2T(n/2) + \Theta(n)$, if $n > 1$
  $T(n) = \Theta(1)$, if $n = 1$

## 🇹🇼 Chinese Translation / 中文翻譯

**分析分治演算法**

- 優點：執行時間通常容易確定
- $T(n) = aT(n/b) + D(n) + C(n)$
  $T(n) = \Theta(1)$，若 $n \leq c$，
- 對於歸併排序：$D(n) = \Theta(1)$，$C(n) = \Theta(n)$
  $T(n) = 2T(n/2) + \Theta(n)$，若 $n > 1$
  $T(n) = \Theta(1)$，若 $n = 1$

## 💡 Detailed Explanation / 詳細解釋

**分治演算法的通式遞迴式**：

$$T(n) = \begin{cases} \Theta(1), & \text{if } n \leq c \\ aT(n/b) + D(n) + C(n), & \text{if } n > c \end{cases}$$

| 參數 | 意義 |
|------|------|
| $a$ | 子問題的數量（$a \geq 1$） |
| $n/b$ | 每個子問題的大小 |
| $D(n)$ | 分解問題的時間 |
| $C(n)$ | 合併解的時間 |

**歸併排序的參數**：
- $a = 2$（兩個子問題）
- $b = 2$（每個子問題大小為 $n/2$）
- $D(n) = \Theta(1)$（只計算中點）
- $C(n) = \Theta(n)$（MERGE 操作）

## 🔢 Derivation Process / 推導過程

歸併排序的遞迴式：$T(n) = 2T(n/2) + \Theta(n)$

代入通式：$T(n) = 2T(n/2) + \Theta(1) + \Theta(n) = 2T(n/2) + \Theta(n)$

使用**主定理（Master Theorem）**：
- $a = 2, b = 2, f(n) = \Theta(n)$
- $\log_b a = \log_2 2 = 1$
- $f(n) = \Theta(n^{\log_b a})$ → 第二種情況
- **結論**：$T(n) = \Theta(n \lg n)$
