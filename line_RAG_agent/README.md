# 自動化 AI 客服知識庫系統 (RAG) 🤖

基於 Retrieval-Augmented Generation (RAG) 架構建置的 LINE 智能客服，能針對上傳的專業技術文件（如用電設備規則、台電營業規則）進行精準問答。

## 🛠️ 技術架構
* **自動化工作流**：n8n (自託管 Docker 環境)[cite: 3]
* **向量資料庫**：Qdrant (本地部署版)[cite: 3]
* **嵌入模型 (Embeddings)**：HuggingFace API (`intfloat/multilingual-e5-base`)[cite: 2, 3]
* **LLM 模型**：Groq API (`qwen/qwen3-32b`)[cite: 2, 3]
* **文件處理**：Recursive Character Text Splitter (Chunk Overlap: 100)[cite: 2]

## ✨ 核心功能
* **自動化向量存儲**：透過 n8n Form Trigger 上傳 PDF 文件，自動切片並轉換為向量儲存至 Qdrant[cite: 2, 3]。
* **精準文件檢索**：用戶透過 LINE 提問後，系統會從文件庫中檢索最相關的 3 筆資料 (Top-K=3) 進行回答[cite: 2, 3]。
* **防幻覺機制**：系統提示詞嚴格限制僅能根據檢索內容回答，若無相關資料則統一回覆「文件中未提及」或轉交真人客服[cite: 2]。
* **記憶功能**：內建 Simple Memory 緩衝區，支援上下文連貫對話[cite: 2]。

## 🚀 快速啟動
1. 透過 `docker compose -f docker-compose.with-qdrant.yml up -d` 同時啟動 n8n 與 Qdrant 容器[cite: 3]。
2. 匯入 `line_rag_customer_service.json`。
3. 設定 HuggingFace Token (用於 Embedding) 與 Groq API Key (用於生成回答)[cite: 3]。
4. 將 Qdrant 連線 URL 設定為 `http://qdrant:6333`[cite: 3]。

## Author
**施孟伶 (Meng-Ling Shih)**
國立臺北科技大學 工業工程與管理研究所 (M.S. in Industrial Engineering and Management, NTUT)
具備精實管理 (Lean Management) 與資料科學分析背景，擅長透過 Python 與 n8n 整合企業 AI 應用解決方案。
