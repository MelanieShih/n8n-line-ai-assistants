# 自動化 AI 客服知識庫系統 (RAG) 🤖

基於 Retrieval-Augmented Generation (RAG) 架構建置的 LINE 智能客服，能針對上傳的專業技術文件（如用電設備規則、台電營業規則）進行精準問答，大幅降低客服人力成本。

## 🎥 Demo 展示
[![RAG 客服 Demo](https://img.youtube.com/vi/YOUR_VIDEO_ID/0.jpg)](https://youtube.com/shorts/v3r8fZs8Yis?feature=share)
*(點擊左側連結觀看 Demo 影片)*

## 🏗️ 系統架構與工作流
<img width="777" height="275" alt="RAG_workflow" src="https://github.com/user-attachments/assets/14bbd7eb-d507-479e-b3ae-e5a23c6bbf03" />


系統運作流程包含兩個獨立環節：

**1. 知識建置 (Knowledge Ingestion)**
* 透過 n8n 表單上傳 PDF 文件。
* 使用 Text Splitter 進行切片 (Chunk Overlap: 100)。
* 經由 HuggingFace 進行向量化 (Embedding)，並存入 Qdrant 向量資料庫。

**2. 檢索問答 (Retrieval & Generation)**
* 接收 LINE 用戶提問。
* AI Agent 根據問題，從 Qdrant 檢索出 Top 3 相關內容。
* 將檢索結果與歷史對話 (Simple Memory) 送入 Groq (`qwen/qwen3-32b`) 生成最終回答。
* 具備防幻覺機制：若無相關資訊，系統會統一回覆「文件中未提及」或轉交真人客服。

## 🛠️ 技術堆疊
* **自動化平台**: n8n (Docker)
* **向量資料庫**: Qdrant (本地容器化部署)
* **Embedding 模型**: HuggingFace API (`intfloat/multilingual-e5-base`)
* **LLM 模型**: Groq API (`qwen/qwen3-32b`)
* **API 串接**: LINE Messaging API

## 🚀 快速啟動
1. 透過 `docker compose -f docker-compose.with-qdrant.yml up -d` 同時啟動 n8n 與 Qdrant 容器。
2. 匯入 `line_rag_customer_service_safe.json`。
3. 設定 HuggingFace Token (用於 Embedding) 與 Groq API Key (用於生成回答)。
4. 將 Qdrant 連線 URL 設定為 `http://qdrant:6333`。
5. 透過表單上傳技術文件 PDF 建立知識庫，即可在 LINE 上進行對話與問答測試。



