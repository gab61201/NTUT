# Problem 4: Anatomy of Sorting Algorithms / 排序演算法剖析

---

## 📖 Original Text / 原文

**The Anatomy of sorting algorithms execution:**

**(a) Tight Code & Constants:** Quicksort is often praised for having "tight code" in its inner loop. Explain what "tight code" means in this context and how it directly influences the hidden constant factor $(C)$ in the runtime equation $T(n) = C (n \log n)$. *(Hint: Compare the fundamental operations inside a Quicksort partition vs. a Mergesort merge.)*

**(b) Algorithmic Strategy & Trade-offs:** You are designing a system for a Safety-Critical Medical Device where memory is extremely limited and you must guarantee that sorting never exceeds a certain time limit, regardless of how "messy" the input data is. Between Quicksort (with randomized pivot) and Heapsort, which would you choose? Justify your answer by discussing their Worst-case Time Complexity and Space Complexity.

---

## 🇹🇼 Chinese Translation / 中文翻譯

**排序演算法執行剖析：**

**(a) 緊湊程式碼與常數因子：** Quicksort 常因其內部迴圈具有「緊湊程式碼 (tight code)」而受到讚譽。請解釋在此情境下「緊湊程式碼」的意義，以及它如何直接影響執行時間方程式 $T(n) = C (n \log n)$ 中的隱藏常數因子 $(C)$。*(提示：比較 Quicksort 分割操作與 Mergesort 合併操作中的基本運算。)*

**(b) 演算法策略與取捨：** 你正在為一個安全關鍵的醫療設備設計系統，其記憶體極為有限，且你必須保證無論輸入資料多「混亂」，排序都不會超過特定的時間限制。在 Quicksort（隨機化樞紐）和 Heapsort 之間，你會選擇哪一個？請透過討論它們的最壞情況時間複雜度和空間複雜度來證明你的答案。

---

## 💡 Detailed Explanation / 詳細解釋

### (1) 涉及的排序演算法

本題比較三個 $O(n \log n)$ 排序演算法的實務特性：

| 演算法 | 最壞時間 | 平均時間 | 空間複雜度 | 穩定性 |
|--------|----------|----------|------------|--------|
| **Quicksort** | $O(n^2)$ | $O(n \log n)$ | $O(\log n)$（遞迴堆疊） | 否 |
| **Mergesort** | $O(n \log n)$ | $O(n \log n)$ | $O(n)$（輔助陣列） | 是 |
| **Heapsort** | $O(n \log n)$ | $O(n \log n)$ | $O(1)$（原地） | 否 |

### (2) 關鍵參數分析

#### (a) Tight Code 與常數因子 C

**"Tight Code"（緊湊程式碼）** 指的是演算法內部迴圈中的指令數量極少，且每條指令都是簡單、低成本的機器操作。

Quicksort 的內部迴圈（partition）的核心運算：
- 比較：`A[j] ≤ pivot`
- 遞增索引：`i++`
- 交換：`swap(A[i], A[j])`

這些指令在現代 CPU 上通常各只需 1 個時脈週期，且容易被**管線化 (pipelining)** 和**分支預測 (branch prediction)** 優化。

相比之下，Mergesort 的內部迴圈（merge）的核心運算：
- 比較：`L[i] ≤ R[j]`
- 複製到輔助陣列：`A[k] = L[i]`
- 額外的記憶體存取和邊界檢查

雖然兩者都是 $\Theta(n \log n)$，但 Quicksort 每次迭代做的工作**更少**，因此隱藏常數 $C_{\text{quick}} < C_{\text{merge}}$。這就是為什麼 Quicksort 在實務上通常比 Mergesort 快約 2-3 倍。

**核心要點：** 漸近分析告訴我們成長趨勢（$\Theta(n \log n)$），但常數因子 $C$ 決定了相同漸近階下的實際效能差異。

#### (b) 安全關鍵醫療設備的選擇

**情境約束：**
- ⚠️ 記憶體極度有限 → 不能使用 $O(n)$ 輔助空間
- ⏱️ 必須保證不超過時間限制 → 最壞情況必須有保證
- 🏥 安全關鍵 → 不能有 $O(n^2)$ 的退化風險

**Quicksort 的問題：**
- 即使使用隨機化樞紐，最壞情況仍是 $O(n^2)$（雖然機率極低，但在安全關鍵系統中**不可接受**）
- 隨機化只降低機率，不消除風險

**Heapsort 的優勢：**
- 最壞情況保證 $O(n \log n)$，無退化風險
- 空間複雜度 $O(1)$（原地排序），適合記憶體受限環境
- 雖然平均情況下常數因子略大於 Quicksort，但保證性遠比微小的效能差異重要

**答案：選擇 Heapsort。** 在安全關鍵系統中，**可預測性 (predictability)** 和**最壞情況保證**遠比平均效能重要。"Never exceeds a certain time limit" 這句話直接指向需要最壞情況保證。

### (3) 解題思路提示

**(a) Tight Code 答題結構：**
1. 先定義「tight code」：內部迴圈指令少、簡單、低成本
2. 具體比較 Quicksort partition 和 Mergesort merge 的操作
3. 解釋這些操作差異如何影響常數因子 $C$
4. 提出結論：Quicksort 的 $C$ 較小，因此在 $\Theta(n \log n)$ 演算法中實務最快

**(b) 醫療設備選擇的答題結構：**
1. 先列出兩者的最壞時間和空間複雜度
2. 分析每個約束條件（記憶體、時間保證）對應的選擇理由
3. 討論隨機化 Quicksort 最壞情況仍然是 $O(n^2)$ 的本質
4. 權衡：可預測性 vs. 平均效能 → 安全關鍵場景選擇可預測性
5. 結論：Heapsort

---

## 🔢 Derivation Process / 推導過程

### (a) Tight Code 與常數因子 $C$ 的推導

**定義**：執行時間可表達為 $T(n) = C \cdot f(n)$，其中 $f(n)$ 是漸近成長函數（此處 $f(n) = n \log n$），$C$ 是隱藏常數，由每次基本運算的成本決定。

**Quicksort 的 Partition 內部迴圈**（每次迭代的核心操作）：

```
for j ← p to r-1
    if A[j] ≤ pivot
        i ← i + 1
        exchange A[i] ↔ A[j]
```

每次迭代的基本運算數：**1 次比較 + (條件成立時) 2 次記憶體寫入**（遞增 $i$ + 交換）。總計約 $3 \sim 4$ 條機器指令。

**Mergesort 的 Merge 內部迴圈**（每次迭代的核心操作）：

```
while i ≤ n₁ and j ≤ n₂
    if L[i] ≤ R[j]
        A[k] ← L[i]
        i ← i + 1
    else
        A[k] ← R[j]
        j ← j + 1
    k ← k + 1
```

每次迭代的基本運算數：**1 次比較 + 1 次記憶體讀取 + 1 次記憶體寫入 + 2 次索引遞增**。總計約 $5 \sim 7$ 條指令，且需要額外的輔助陣列存取。

**常數因子比較**：

$$C_{\text{quick}} \approx \frac{3 \sim 4 \text{ ops}}{\text{iteration}} \quad \text{vs.} \quad C_{\text{merge}} \approx \frac{5 \sim 7 \text{ ops}}{\text{iteration}}$$

$$\frac{C_{\text{merge}}}{C_{\text{quick}}} \approx 1.5 \sim 2.0$$

這解釋了為什麼實務上 Quicksort 比 Mergesort 快約 1.5 到 2 倍，儘管兩者都是 $\Theta(n \log n)$。

**關鍵因素**：
- **指令數量**：Quicksort 內部迴圈指令更少
- **記憶體存取模式**：Quicksort 在原地操作（cache-friendly），Mergesort 需要輔助陣列
- **分支預測**：Quicksort 的比較結果在隨機樞紐下難以預測，但指令數優勢仍壓過這個劣勢

$$\boxed{T_{\text{quick}}(n) = C_{\text{quick}} \cdot n \log n < C_{\text{merge}} \cdot n \log n = T_{\text{merge}}(n) \text{ in practice}}$$

---

### (b) 安全關鍵醫療設備：Heapsort vs. Quicksort 正式分析

**情境約束形式化**：

1. **記憶體極度有限** → $\text{Space}(n) = O(1)$ 強烈偏好
2. **必須保證時間上限** → $\forall \text{ inputs}, T(n) \leq T_{\text{max}}$，即要求 $T_{\text{worst}}(n)$ 有保證

**Quicksort（隨機化樞紐）分析**：

- 最壞情況時間複雜度：$T_{\text{worst}}(n) = O(n^2)$
- 隨機化降低機率但不消除：存在輸入（無論機率多低）使分割極度不平衡
- 空間複雜度：$O(\log n)$（遞迴堆疊深度）

$$T_{\text{quick-worst}}(n) = \Theta(n^2) \quad \text{— 無法保證時間上限}$$

**Heapsort 分析**：

- 最壞情況時間複雜度：$T_{\text{worst}}(n) = O(n \log n)$，**無例外**
- BUILD-MAX-HEAP：$\Theta(n)$
- $n-1$ 次 EXTRACT-MAX：每次 $O(\log n)$

$$T_{\text{heap}}(n) = \Theta(n) + \sum_{i=1}^{n-1} O(\log i) = \Theta(n \log n)$$

- 空間複雜度：$O(1)$（原地排序，僅用常數額外空間）

$$S_{\text{heap}}(n) = O(1)$$

**決策矩陣**：

| 條件 | Quicksort（隨機樞紐） | Heapsort | 勝出 |
|------|----------------------|----------|------|
| 最壞時間保證 | ❌ $O(n^2)$ | ✅ $O(n \log n)$ | **Heapsort** |
| 記憶體空間 | ⚠️ $O(\log n)$ | ✅ $O(1)$ | **Heapsort** |
| 平均效能 | ✅ 較快（較小 $C$） | ⚠️ 稍慢 | Quicksort |

在安全關鍵系統中，**最壞情況保證的權重**遠大於平均效能差異。Heapsort 在兩個關鍵約束（時間保證 + 空間效率）上均勝出。

$$\boxed{\text{選擇 Heapsort}}$$
