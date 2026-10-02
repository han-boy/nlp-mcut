# NLP 自然語言處理 (115 S1) - 課程專案

本專案為 NLP 課程開發環境與實作練習區。

---

## 開發者資訊 (Developer Info)
* **學號**：[U12627026]
* **姓名**：[han-boy]

## 硬體與環境狀態 (Environment Setup)
* **PyTorch 執行環境**：Windows CPU

---

## 課程任務清單 (Task Checklist)

### Week 2：開發環境與專案架構初始化
請在完成下列任務後，將 `[ ]` 改為 `[x]`：
- [x] 成功建立 GitHub 帳號並 Clone 本專案至本機端。
- [x] 成功建立 `.venv` 虛擬環境，並透過 `.gitignore` 隱藏底層檔案。
- [x] 成功於虛擬環境內安裝通用套件清單 (`requirements.txt`) 與專屬硬體版本的 PyTorch。
- [x] 更新本 README 文件，填寫學號、姓名與 PyTorch 環境狀態。
- [x] 成功使用 Git 完成 `commit` 並 `push` 同步至 GitHub 雲端。

### Week 4: Data Ingestion & Topology-Aware Chunking
- [x] **環境建置與套件**：更新 `.gitignore` 忽略原始 PDF 與批次 JSON，並保留 `.keep` 目錄結構。
- [x] **斷言與修復**：撰寫 Regex，將斷裂雙語標題與對照條文無縫重組。
- [x] **機械健全度 (Mechanical Sanity)**：
  - [x] 拓撲錨定率 (TAR)
  - [x] 運用「中位數 (Median)」計算文本長度。
- [x] **語意品質 (Semantic Quality)**：
  - [x] 計算 Shannon Information Entropy (香農資訊熵)，確認 Cleaned 資料之資訊熵高於 Raw 資料。
- [x] **儀表板與匯出**：
  - [x] 繪製 4 格儀表板 (4-Panel Dashboard)。
  - [x] 將核心數據匯出至根目錄下的 `metrics.json`。

