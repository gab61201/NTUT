# 04. Computers and Intractability

> **Slide 5**

---

## 📖 Original Text / 原文

---

Computers and Intractability

- The 1979 textbook by Michael Garey and David S. Johnson "Computers and Intractability: A Guide to the Theory of NP-Completeness" has been very influential and is one of the most cited books in computer science.
- The book famously features a cartoon which depicts a researcher who reports to his boss and justifies why he didn't succeed in carrying out a given task.
  - https://www.ac.tuwien.ac.at/people/szeider/cartoon/

---

## 🇹🇼 Chinese Translation / 中文翻譯

**電腦與不可處理性**

- Michael Garey 與 David S. Johnson 於 1979 年出版的教科書「Computers and Intractability: A Guide to the Theory of NP-Completeness」（電腦與不可處理性：NP-Completeness 理論指南）影響深遠，是電腦科學領域中被引用最多的書籍之一。
- 這本書最著名的特色是一幅漫畫，描繪一位研究人員向老闆報告，並解釋自己為何無法完成某項任務。
  - https://www.ac.tuwien.ac.at/people/szeider/cartoon/

---

## 💡 Detailed Explanation / 詳細解釋

### 這本書的重要性

- **出版年份**：1979 年，由 Michael Garey 和 David S. Johnson 合著。
- **地位**：被視為 NP-Completeness 理論的「聖經級」參考書，在學術界極具影響力。
- **核心主題**：系統性地整理與分類 NP-Complete 問題，提供判別問題是否為 NP-Complete 的方法論（主要透過歸約，reduction）。

### 經典漫畫的幽默

書中附有一幅經典漫畫，以幽默的方式呈現「NP-Complete 問題」的難解性：

- 一位研究員向主管匯報任務進度。
- 主管問：「你找到解法了嗎？」
- 研究員回答：「我證明了這個問題是 NP-Complete 的！」
- 主管：「那你有解了嗎？」
- 研究員：「沒有，但我證明了它不可能有多項式時間的解法」（開玩笑的，因為 P vs NP 仍是未解之謎）。

這幅漫畫生動地傳達了：NP-Complete 問題的本質難題——我們目前既找不到高效解法，也無法證明不存在高效解法。這正是計算複雜度理論中最核心、最迷人的開放問題之一。

### 學習重點

| 概念 | 說明 |
|------|------|
| **Intractability**（不可處理性） | 指問題在計算上「太難」，無法在合理時間內求解。 |
| **NP-Completeness** | 一類被認為是最難的決策問題集合；若其中任一問題有多項式時間解法，則所有 NP 問題都有。 |
| **實務意義** | 若發現問題是 NP-Complete，應轉向近似演算法、啟發式方法或限制問題規模。 |
