# LINE × Google Calendar 智慧行事曆助理 📅

透過 n8n 打造結合 LINE Messaging API 與 Google Calendar 的自動化 AI 助理，能理解自然語言並自動執行行事曆的管理任務。

## 🎥 Demo 展示
[![行事曆助理 Demo](https://img.youtube.com/vi/YOUR_VIDEO_ID/0.jpg)](https://youtube.com/shorts/uBPsTAJVkmQ?feature=share)
*(點擊左側連結觀看 Demo 影片)*

## 🏗️ 系統架構與工作流
<img width="945" height="293" alt="Calendar_workflow" src="https://github.com/user-attachments/assets/ba7e1933-1b11-45a3-9203-545bbdf82fe8" />

系統運作流程：
1. **接收訊息**：透過 LINE Webhook 接收用戶的自然語言指令。
2. **資料處理**：擷取 `message.text` 與 `replyToken`，並過濾非文字訊息。
3. **AI 推論**：利用 Groq 平台的 `llama-3.3-70b-versatile` 模型理解意圖 (如新增、查詢、刪除、修改)。
4. **呼叫工具**：觸發對應的 Google Calendar API 節點 (Create, Get, Update, Delete)。
5. **回傳結果**：將執行結果格式化後，經由 LINE API 回傳給用戶。

## 🛠️ 技術堆疊
* **自動化平台**: n8n (Docker 自託管)
* **LLM 模型**: Groq API (`llama-3.3-70b-versatile`)
* **API 串接**: LINE Messaging API, Google Calendar API (OAuth 2.0)
* **內網穿透**: Cloudflare Tunnels (`cloudflared`)

## ✨ 核心功能
系統會自動從 LINE 接收訊息，經由 AI Agent 解析語意後執行對應工具：
1. **建立行程**：支援單人行程或加入與會者的會議建立[cite: 1, 4]。
2. **查詢行程**：可查詢特定日期的時間安排[cite: 4]。
3. **修改行程**：透過擷取 Event ID 進行時間或標題變更[cite: 4]。
4. **刪除行程**：確認行程 ID 後執行刪除操作[cite: 4]。

## 🚀 快速啟動
1. 使用 `docker-compose.yml` 啟動 n8n 容器。
2. 於 GCP 申請 Google Calendar API 的 OAuth 2.0 憑證，並於 n8n 中綁定。
3. 於 LINE Developers 建立官方帳號，獲取 Channel Secret 與 Access Token。
4. 執行 `cloudflared tunnel --url http://localhost:5678` 建立 Webhook 臨時網址並填入 LINE 後台。
5. 匯入 `line_calendar_agent_safe.json`，並替換您的 API Keys 與個人信箱。

##  Author
**施孟伶 (Meng-Ling Shih)**
國立臺北科技大學 工業工程與管理研究所 (M.S. in Industrial Engineering and Management, NTUT)

專注於 RAG 架構開發、多輪對話代理人 (Conversational Agents) 與流程自動化部署。







