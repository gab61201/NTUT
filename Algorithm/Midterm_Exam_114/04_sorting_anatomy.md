# Problem 4 / 第四題

## 📖 Original Text / 原文

**4. The Anatomy of sorting algorithms execution:**

> **a) Tight Code & Constants:** Quicksort is often praised for having "tight code" in its inner loop. Explain what "tight code" means in this context and how it directly influences the hidden constant factor ($C$) in the runtime equation $T(n) = C \cdot n \log n$. (Hint: Compare the fundamental operations inside a Quicksort partition vs. a Mergesort merge.)
>
> **b) Algorithmic Strategy & Trade-offs:** You are designing a system for a Safety-Critical Medical Device where memory is extremely limited and you must guarantee that sorting never exceeds a certain time limit, regardless of how "messy" the input data is. Between Quicksort (with randomized pivot) and Heapsort, which would you choose? Justify your answer by discussing their Worst-case Time Complexity and Space Complexity.

---

## 🇹🇼 Chinese Translation / 中文翻譯

**4. 排序演算法執行的剖析：**

> **a) 緊湊程式碼與常數因子：** QuickSort 常因其內層迴圈具有「緊湊程式碼（tight code）」而受到讚譽。請解釋在此語境中「緊湊程式碼」的意義，以及它如何直接影響執行時間方程式 $T(n) = C \cdot n \log n$ 中的隱藏常數因子 $C$。（提示：比較 QuickSort 分割（partition）步驟與 MergeSort 合併（merge）步驟內部的基礎操作。）
>
> **b) 演算法策略與權衡：** 你正在為一台安全關鍵型醫療裝置設計系統，該系統的記憶體極度受限，且必須保證排序操作永遠不會超過某個時間上限，無論輸入資料有多「混亂」。在 QuickSort（隨機選擇樞紐點）與 HeapSort 之間，你會選擇哪一個？請透過討論它們的最壞情況時間複雜度與空間複雜度來證明你的答案。

---

## 💡 Detailed Explanation / 詳細解釋

### a) 緊湊程式碼（Tight Code）與常數因子 $C$

#### 什麼是「緊湊程式碼」？

「緊湊程式碼」指演算法的 **內層迴圈（inner loop）** 中所執行之操作的數量極少、邏輯極其簡單。在 QuickSort 的 partition 步驟中，內層迴圈的核心操作僅為：

1. **比較**（comparison）— 將陣列元素與樞紐點（pivot）比較
2. **交換**（swap）— 若需要交換兩個元素

這兩項操作的程式碼體積極小，通常只需幾行程式碼即可完成整個 partition 的掃瞄與交換。

#### 與 MergeSort 的對比

MergeSort 的 merge 步驟則需要：

1. **比較** — 來自兩個已排序子陣列的當前元素
2. **複製**（copy/move）— 將比較結果寫入暫存陣列，之後再將暫存陣列拷貝回原陣列

MergeSort 的 merge 不僅需要額外的 **$O(n)$ 輔助空間**，還涉及大量的 **資料搬運（data movement）**。每次合併時，元素必須從原陣列讀取到暫存區，比較後寫入暫存區，最後再搬回原陣列——這意味著每個元素平均經歷 **兩次以上的寫入操作**。

#### 如何影響隱藏常數 $C$？

執行時間方程式 $T(n) = C \cdot n \log n$ 中的 $C$ 代表 **每一個 $n \log n$ 單位所付出的實際操作成本**。雖然 QuickSort 與 MergeSort 的平均時間複雜度同為 $O(n \log n)$，但 QuickSort 的 $C$ 明顯更小，原因如下：

| 因素 | QuickSort (partition) | MergeSort (merge) |
|------|----------------------|-------------------|
| 內層操作 | 比較 + 交換 | 比較 + 複製 + 寫回 |
| 額外空間 | $O(1)$（就地排序） | $O(n)$ 暫存陣列 |
| 記憶體分配 | 無需額外分配 | 每次合併需準備緩衝區 |
| 快取效率 | **高** — 順序掃瞄陣列 | **較低** — 隨機存取兩子陣列 + 暫存區 |
| 分支預測 | 較易預測 | 較難預測 |

- **快取局部性（Cache Locality）**：QuickSort 的 partition 以順序方式掃瞄陣列，極佳地利用 CPU 快取的空間局部性（spatial locality）。MergeSort 的 merge 需要同時從兩個子陣列讀取並寫入暫存陣列，存取模式較為分散。
- **就地操作（In-Place）**：QuickSort 直接在原陣列上操作，無需額外記憶體配置，省去了 `malloc`/`free` 的開銷。
- **分支預測（Branch Prediction）**：QuickSort 內層的比較邏輯簡單規律，CPU 的分支預測單元更容易預測跳轉行為，減少 pipeline stall。

因此，**QuickSort 的 $C$ 遠小於 MergeSort 的 $C$**，使得 QuickSort 在實際執行中通常比 MergeSort 快，即使兩者的漸進複雜度相同。

---

### b) 演算法策略與權衡：QuickSort vs. HeapSort

#### 結論：選擇 **HeapSort**

在安全關鍵型醫療裝置的場景下，**HeapSort 是唯一正確的選擇**。

#### 詳細理由

| 性質 | QuickSort（隨機樞紐） | HeapSort |
|------|----------------------|----------|
| 平均時間 | $O(n \log n)$ | $O(n \log n)$ |
| 最壞時間 | $O(n^2)$ | **$O(n \log n)$** ✅ |
| 空間複雜度 | $O(\log n)$ 遞迴棧 | **$O(1)$** ✅ |
| 時間可預測性 | 低（存在變異） | **高（確定性上界）** ✅ |
| 安全性保證 | 無法保證上限 | 可保證上限 ✅ |

##### 1. 最壞情況時間複雜度：$O(n^2)$ vs. $O(n \log n)$

QuickSort 即使採用 **隨機選擇樞紐點（randomized pivot）**，其最壞情況仍為 $O(n^2)$。雖然機率極低（約 $1/n!$ 的排列會觸發最壞情況），但在 **安全關鍵系統** 中，**任何非零的可能性都是不可接受的**。理由如下：

- 醫療裝置必須通過嚴格的 **功能安全認證**（如 IEC 62304、ISO 13485），這些標準要求系統行為必須具有 **可驗證的確定性上界（deterministic upper bound）**。
- 隨機化演算法本質上引入 **非確定性（non-determinism）**，無法在設計階段提供嚴格的執行時間保證（WCET — Worst-Case Execution Time）。
- 在醫療情境中，排序延遲可能直接影響病患生命（例如：即時心電圖分析、藥物劑量計算、影像重建）。

HeapSort 則 **嚴格保證** 任何輸入下的執行時間為 $O(n \log n)$，可精確計算 WCET 並通過安全認證審核。

##### 2. 空間複雜度：$O(\log n)$ vs. $O(1)$

題目明確指出 **記憶體極度受限**：

- QuickSort 的遞迴呼叫需要 $O(\log n)$ 的 **呼叫棧（call stack）** 空間。雖然可透過尾遞迴最佳化或「小陣列用插入排序」的技巧降低，但棧空間在嵌入式系統中往往是 **固定大小且極其有限** 的資源。
- HeapSort 是 **嚴格就地（strictly in-place）** 的演算法，僅使用 $O(1)$ 的額外空間（僅需幾個變數）。這在嵌入式醫療裝置的極限記憶體環境中是決定性的優勢。

##### 3. 無遞迴棧溢位風險

HeapSort 可完全以 **迭代（iterative）** 方式實作，完全不需要遞迴，因此：

- 不存在 **堆疊溢位（stack overflow）** 風險
- 記憶體使用量在編譯期即可完全確定
- 符合嵌入式系統的 **靜態記憶體分析（static memory analysis）** 要求

#### 總結

| 考量面 | 選擇 HeapSort 的原因 |
|--------|---------------------|
| 時間保證 | $O(n \log n)$ 最壞情況確定，可計算 WCET |
| 空間保證 | $O(1)$ 額外空間，適合極限記憶體環境 |
| 安全認證 | 確定性行為，可通過醫療裝置安全標準 |
| 可靠性 | 無棧溢位風險，可完全迭代實作 |

QuickSort 雖然在日常應用中因常數因子小而表現優異，但在安全關鍵系統中，**可保證的上界永遠優於平均表現**。

---

## 🔢 Derivation Process / 推導過程

此題為概念性比較題，無嚴格數學推導。以下列出關鍵複雜度關係供參考：

### QuickSort 的時間複雜度

$$T_{QS}(n) = \begin{cases} O(n^2) & \text{最壞情況（每次分割極端不均）} \\ O(n \log n) & \text{平均情況} \end{cases}$$

隨機樞紐點使最壞情況的機率降至極低，但 **機率非零**：
$$P(\text{最壞情況}) > 0 \quad \Rightarrow \quad \text{無法排除 } O(n^2)$$

### HeapSort 的時間複雜度

建堆（build-heap）：$O(n)$  
每次提取最大值並維護堆性質：$O(\log n)$，共 $n$ 次

$$T_{HS}(n) = O(n) + n \cdot O(\log n) = O(n \log n) \quad \text{（所有輸入均成立）}$$

### 空間複雜度對比

$$S_{QS}(n) = O(\log n) \quad \text{（遞迴棧深度）}$$
$$S_{HS}(n) = O(1) \quad \text{（僅需數個暫存變數）}$$

---

> **關鍵記憶點**：QuickSort 勝在「快」，HeapSort 勝在「穩」。安全關鍵系統選「穩」。
