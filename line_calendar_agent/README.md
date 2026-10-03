# LINE × Google Calendar 智慧行事曆助理 📅

透過 n8n 打造結合 LINE Messaging API 與 Google Calendar 的自動化 AI 助理，能理解自然語言並自動執行行事曆的管理任務。

## 🎥 Demo 展示
[![行事曆助理 Demo](https://img.youtube.com/vi/YOUR_VIDEO_ID/0.jpg)]([https://www.youtube.com/watch?v=YOUR_VIDEO_ID](https://youtube.com/shorts/uBPsTAJVkmQ?feature=share))
*(點擊上方圖片觀看 Demo 影片)*

## 🏗️ 系統架構與工作流
<img width="945" height="293" alt="Calendar_workflow" src="https://github.com/user-attachments/assets/ba7e1933-1b11-45a3-9203-545bbdf82fe8" />


## 🛠️ 技術架構
* **自動化工作流**：n8n (自託管 Docker 環境)
* **LLM 模型**：Groq API (`llama-3.3-70b-versatile`)[cite: 1]
* **第三方串接**：LINE Messaging API, Google Calendar API (OAuth 2.0)[cite: 4]
* **內網穿透**：Cloudflare Tunnels (`cloudflared`) 建立對外 Webhook[cite: 4]

## ✨ 核心功能
系統會自動從 LINE 接收訊息，經由 AI Agent 解析語意後執行對應工具：
1. **建立行程**：支援單人行程或加入與會者的會議建立[cite: 1, 4]。
2. **查詢行程**：可查詢特定日期的時間安排[cite: 4]。
3. **修改行程**：透過擷取 Event ID 進行時間或標題變更[cite: 4]。
4. **刪除行程**：確認行程 ID 後執行刪除操作[cite: 4]。

## 🚀 快速啟動
1. 建立 `docker-compose.yml` 啟動 n8n 容器。
2. 於 GCP 申請 Google Calendar API 的 OAuth 2.0 憑證，並於 n8n 中綁定[cite: 4]。
3. 於 LINE Developers 建立官方帳號，獲取 Channel Secret 與 Access Token[cite: 4]。
4. 匯入 `line_calendar_agent.json`，並將佔位符替換為您的 API Keys。

##  Author
**施孟伶 (Meng-Ling Shih)**
國立臺北科技大學 工業工程與管理研究所 (M.S. in Industrial Engineering and Management, NTUT)
專注於 RAG 架構開發、多輪對話代理人 (Conversational Agents) 與流程自動化部署。
