# 01. Introduction & Definition

> **Slides 1–2**

---

## 📖 Original Text / 原文

**Slide 1**

The Role of Algorithms
in Computing

Chapter 1

**Slide 2**

What is algorithm?

- Any well-defined computation procedure that takes some value, or set of values, as input and produces some value, or set of values, as output.
- Or tool for solving well-specified computational problem.
- An algorithm is said to be correct if for every input instance, it halts with the correct output.

---

## 🇹🇼 Chinese Translation / 中文翻譯

**Slide 1**

**Chapter 1**

演算法在運算中的角色

**Slide 2**

什麼是演算法？

- 任何明確定義的計算程序，接受一些值或一組值作為輸入，並產生一些值或一組值作為輸出。
- 或為解決明確規範之計算問題的工具。
- 若對每一個輸入案例，演算法皆能終止並輸出正確結果，則稱該演算法為正確的。

---

## 💡 Detailed Explanation / 詳細解釋

### 1. 「明確定義」的意義

「明確定義」（well-defined）意味著演算法的每一步都必須精確無歧義。

| 明確的指令 ✅ | 模糊的指令 ❌ |
|:---|:---|
|「將 $a$ 與 $b$ 相加，結果存入 $c$」|「把 $a$ 和 $b$ 組合起來」|
|「從 $1$ 數到 $n$」|「數一些數字」|

### 2. 輸入與輸出

演算法可視為一個數學函數：

$$A: \text{Input} \rightarrow \text{Output}$$

- **輸入**：演算法接收的資料（可能為空）
- **輸出**：演算法產生的結果

### 3. 正確性的嚴格定義

演算法的正確性包含兩個條件：

$$\forall \text{ input instance } x, \quad A(x) \text{ halts } \land A(x) = \text{correct output}$$

- **終止性（Termination）**：必須在有限步驟內結束，不會無限循環。
- **正確性（Correctness）**：終止時給出的結果必須是正確的。

若一個演算法「有時正確、有時不正確」，在定義上即為**不正確**。

---

## 🔢 Derivation Process / 推導過程

> 本節為定義性內容，無公式推導。可將正確性形式化為：

令 $\mathcal{I}$ 為所有合法輸入的集合，$\mathcal{O}$ 為所有合法輸出的集合。

- 演算法 $A$ 是一個函數：$A: \mathcal{I} \rightarrow \mathcal{O}$
- $A$ 是正確的，當且僅當：

$$\forall x \in \mathcal{I}, \quad A(x) \text{ terminates and } A(x) = f(x)$$

其中 $f: \mathcal{I} \rightarrow \mathcal{O}$ 是該計算問題的正確映射。
