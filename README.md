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

### Week 04 / 08: Data Ingestion & Topology-Aware Chunking
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

### Week 09：期中資料評估與報告
- [x] 完成期中 Chunks 評估與文字清洗指標分析。
- [x] 繪製長度分佈、字元差異、熵值比較圖表與總結儀表板。
- [x] 完成 `DATA_REPORT.md` 期中資料報告與 `AI_USAGE.md` 紀錄。

### Week 10：從計數到向量（關鍵字檢索 vs 語意檢索）
- [x] **環境與模型設定**：完成 `notebooks/10_setup.ipynb`，載入 `bge-small-zh-v1.5` 模型並產生 384 個 chunks 之稠密向量嵌入 (`data/embeddings/week10_chunk_emb.npy`)。
- [x] **套件與版本控管**：自動更新 `requirements.txt`（新增 jieba、rank_bm25、scikit-learn、sentence-transformers）與 `.gitignore`（忽略 `models/` 與 `data/embeddings/`）。
- [x] **關鍵字檢索實作**：使用 jieba 斷詞，完成 TF-IDF 檢索與 BM25 檢索實作 (`search_tfidf`, `search_bm25`)。
- [x] **語意檢索實作**：手刻餘弦相似度函式 (`cosine`)，並以預訓練句向量模型完成語意檢索 (`search_dense`)。
- [x] **檢索評估與人工判讀**：測試 10 組校規問答（包含專有名詞與口語換句話說），完成三種檢索方法之前三名命中判斷 (`hit@3`)。
- [x] **自訂測試題目與反思**：設計關鍵字與語意檢索專屬問題，分析比較兩種檢索架構之優缺點與混合檢索 (Hybrid Search) 的必要性。
- [x] **成果匯出**：產生檢索比較報表 `week10_retrieval_comparison.json` 並完整保留 notebook 執行結果。
