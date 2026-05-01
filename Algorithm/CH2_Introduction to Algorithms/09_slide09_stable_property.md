# Slide 09 — Stable Property (穩定性)

## 📖 Original Text / 原文

---

**Stable Property**

- Numbers with the same value appear in the output array in the same order as they do in the input array is called stable.
- INSERTION-SORT is stable?

## 🇹🇼 Chinese Translation / 中文翻譯

**穩定性**

- 具有相同值的元素在輸出陣列中的順序與在輸入陣列中的順序相同，稱為穩定（stable）。
- 插入排序是穩定的嗎？

## 💡 Detailed Explanation / 詳細解釋

**穩定排序（Stable Sort）**的定義：

如果兩個元素有相同的鍵值，排序後它們的相對順序保持不變。

**例**：考慮排序學生資料（按成績排序）：

| 原始順序 | 姓名 | 成績 |
|---------|------|------|
| 1 | 小明 | 85 |
| 2 | 小華 | 90 |
| 3 | 小麗 | 85 |
| 4 | 小強 | 90 |

**穩定排序結果**：小明在前於小麗（成績相同），小華在前於小強（成績相同）。

**插入排序是穩定的嗎？** → **是的！** 因為插入排序只將 $A[j]$ 與比它**嚴格更大**的元素比較（$A[i] >$ key），不會跳過相同值的元素，因此相同值的元素保持原始相對順序。

**為什麼穩定性重要？** 在多鍵排序時（先按次要鍵排序，再按主要鍵排序），穩定排序可以確保次要鍵的順序不被破壞。
