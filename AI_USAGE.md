# AI 工具使用紀錄與反思 (AI Usage & Reflection Report)

本專案於 Week 04 資料輸入與前處理流程開發過程中，善用 AI 輔助工具（包括 Gemini 1.5 Pro / ChatGPT-4o / Claude 3.5 Sonnet）協助研擬正則表示式 (Regex) 與除噪邊界邏輯。以下紀錄具體合作與審核細節：

---

### 1. 使用的 AI 工具 (Tools Used)
* **LLM 模型**：Gemini 1.5 Pro / ChatGPT-4o / Claude 3.5 Sonnet
* **開發環境與工具**：VSCode Integrated Copilot / Antigravity AI Pair Programmer

---

### 2. 主要用途 (Use Cases)
1. **動態邊界除噪 (Dynamic Header Bleed Removal)**：引導 AI 設計基於檔案名稱環境變數 `doc_title` 的動態正則表示式，清除跨頁頁首/頁尾溢出雜訊。
2. **雙語標題合併 (Bilingual Headings Merging)**：要求 AI 運用 Capture Groups 鎖定連續 `##` 標題，進行跨行斜線橋接 (Consolidation)。
3. **交錯雙語條文對齊 (Bilingual Clauses Alignment)**：請 AI 定義防禦性特徵 (如第二條清單開頭必須為英文 `[A-Za-z]`)，避免誤併連續兩條中文法規。
4. **實證評估儀表板 (Empirical Evaluation 4-Panel Dashboard)**：協助撰寫 matplotlib grouped bar chart 及 boxplot 圖表程式碼。

---

### 3. 關鍵提示詞 (Key Prompts)

#### 範例 Prompt 1：雙語條文防禦性合併
> **Prompt:**  
> "我正在處理中英對照的校園規章法規文本，解析器將中文條文與英文條文拆分為連續的 `- ` 清單項目。請幫我寫一段 Python 字典與 re.sub 正則表示式，要求：  
> 1. 第一行是以 `- ` 開頭的中文條文段落；  
> 2. 第二行是以 `- ` 開頭且緊接著英文單字 (如 `Article 15`) 的條文；  
> 3. 將兩者合併為單一行，中間以 ` / ` 分隔；  
> 4. 請特別注意防禦邏輯，絕不能把連續兩條中文條文 (如 `- 第十五條` 與 `- 第十六條`) 誤併！"

#### 範例 Prompt 2：動態檔名標題除噪
> **Prompt:**  
> "在批次處理 PDF 時，輸入檔名如 `A232020018_大學部學則.pdf`。請設計一段 Python `re.search` 正則表示式，能夠從檔名中精準萃取底線與 `.pdf` 之間的中文法規名稱 (`大學部學則`)，並組成動態除噪模組刪除內文中孤立出現的頁首標題。"

---

### 4. 人工審查與修正 (Human Oversight & Corrections)

* **發現問題**：AI 初期生成的雙語條文合併正則表示式為 `r"(- [^\n]+)\n+ - ([^\n]+)"`，未加入對第二行字元語言屬性 (`[A-Za-z]`) 的防禦限制，導致測試時把「- 第十五條 ...」與「- 第十六條 ...」連續兩條中文法規錯誤合併。
* **人工修正**：人工將正則表示式修訂為 `r"(\S[^\n]*)\n\s*-\s*([A-Za-z][^\n]*)"`，明確指定第二個清單項目必須以英文字母開頭，成功通過 TDD 斷言測試 (Assertion 1-C)。
* **路徑與編碼防禦**：Windows 環境下 HuggingFace/Docling 的符號連結權限與 non-ASCII 路徑問題，人工補上 `HF_HUB_DISABLE_SYMLINKS` 環境變數與 PyPdfiumBackend 設定。

---

### 5. 反思與總結 (Reflection)

透過本週實驗，深刻體會到 **「AI + TDD (測試驅動開發)」** 的強大綜效。AI 在處理複雜正則表示式與語法轉換上極具效率，但若無工程師建立健全的 Assertion 斷言防線與領域知識審查，容易發生過度貪婪 (Greedy Matching) 或邊界失效。

結合 AI 快速產生初步原型，再由人工進行防禦性驗證與品質測試，是確保 NLP 前處理管線 (Data Ingestion Pipeline) 兼具高效性與高可靠度的最佳模式。
