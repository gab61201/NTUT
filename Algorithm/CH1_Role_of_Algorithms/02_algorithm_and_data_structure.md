# 02. Algorithm and Data Structure

> **Slide 3**

---

## 📖 Original Text / 原文

Algorithm and Data Structure

- Donald Knuth founded the field of data structures and analysis of algorithms.
- Niklaus Wirth edited the book: Algorithms + Data Structures = Programs.
- Data Structure: a way to store and organize data, in order to facilitate access and modifications,
- One of the basic techniques for improving algorithms is to structure the data.
- Usually, the choice of data structure involves a time-space trade off.

---

## 🇹🇼 Chinese Translation / 中文翻譯

**演算法與資料結構**

- Donald Knuth 創立了資料結構與演算法分析的領域。
- Niklaus Wirth 編輯了書籍：演算法 + 資料結構 = 程式。
- 資料結構：一種儲存與組織資料的方式，以方便存取與修改。
- 改進演算法的基本技術之一就是將資料結構化。
- 通常，資料結構的選擇涉及時間與空間的權衡（time-space trade off）。

---

## 💡 Detailed Explanation / 詳細解釋

### 1. Donald Knuth 的貢獻

Donald Knuth 被譽為「演算法之父」，其代表作《The Art of Computer Programming》系統性地建立了演算法分析與資料結構的理論基礎。他引入了漸近分析（asymptotic analysis）的概念，用 $O(\cdot)$ 符號來描述演算法的效率。

### 2. Niklaus Wirth 的公式

$$\text{Algorithms} + \text{Data Structures} = \text{Programs}$$

這個公式強調：好的程式 = 好的演算法 + 好的資料結構。兩者缺一不可。

### 3. 資料結構的本質

資料結構的核心目標是讓資料的存取與修改更有效率。常見例子：

| 資料結構 | 特點 | 適用場景 |
|:---|:---|:---|
| 陣列（Array） | 隨機存取 $O(1)$，插入/刪除 $O(n)$ | 固定大小、頻繁查詢 |
| 連結串列（Linked List） | 插入/刪除 $O(1)$，隨機存取 $O(n)$ | 頻繁插入/刪除 |
| 樹（Tree） | 搜尋 $O(\log n)$ | 有序資料、層次結構 |
| 雜湊表（Hash Table） | 平均 $O(1)$ 查詢 | 快速鍵值對查詢 |

### 4. 時間－空間權衡（Time-Space Trade-off）

選擇資料結構時，通常需要在執行時間與記憶體使用之間做出取捨：

- **雜湊表**：查詢速度快 $O(1)$，但需要額外記憶體空間。
- **排序陣列 + 二分搜尋**：不需要額外空間，但查詢速度為 $O(\log n)$。
- **動態規劃**：用記憶體（表格）儲存子問題結果，以節省重複計算的時間。
