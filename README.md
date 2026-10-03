# n8n AI Assistants Portfolio 🤖

利用 n8n (Workflow Automation) 結合大型語言模型 (Groq API, HuggingFace) 與第三方服務開發的自動化 AI 助理專案集合。

## 📂 專案列表

### 1. [LINE × Google Calendar 智慧行事曆助理](./line_calendar_agent/)
整合 LINE Messaging API 與 Google Calendar API，能理解自然語言並自動執行建立、查詢、修改與刪除行程的 AI 代理人。

### 2. [自動化 AI 客服知識庫系統 (RAG)](./line_RAG_agent/)
結合 Qdrant 向量資料庫與 n8n，能夠自動切片 PDF 技術文件並進行語意檢索，提供精準問答並具備防幻覺機制的 LINE 客服機器人。

## 🛠️ 技術堆疊
* **自動化平台**: n8n (Docker)
* **LLM / Embedding**: Groq (Llama-3, Qwen), HuggingFace
* **Database**: Qdrant Vector Store
* **APIs**: LINE Messaging API, Google Calendar API, Cloudflare Tunnels
