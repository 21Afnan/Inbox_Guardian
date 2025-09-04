# 📬 InboxGuardian  

InboxGuardian is a **local AI-powered email cleaner** built with [n8n](https://n8n.io/).  
It automatically scans your inbox on a schedule, classifies emails with AI, and then:  

- ✅ Sends **important emails** as notifications via Discord  
- 🗑️ Automatically deletes **unimportant emails** from Gmail  

Runs fully on your machine → **your data stays private**.  

---

## 🚀 How it Works  

1. **Scheduler Trigger** → runs the workflow at intervals you define  
2. **Gmail Get Message Node** → fetches latest emails  
3. **AI Classifier (Gemini 2.5 Flash Lite)** → analyzes & labels emails as `KEEP` or `DELETE`  
4. **Code Node** → parses structured AI output into JSON  
5. **IF Node** → routes based on classification  
   - **KEEP** → sends you a notification in **Discord** via webhook  
   - **DELETE** → removes the message using **Gmail Delete Message Node**  

---

## 📂 Repo Contents  
```
├─ workflow.json # exported n8n workflow
├─ screenshots/ # workflow visuals
│ └─ flow.png # screenshot of workflow
├─ media/ # workflow demo assets
│ ├─ workflow.png # static workflow image
│ └─ demo.mp4 # short video demo (download & open locally)
├─ README.md # project description & instructions
└─ .gitignore # ignores sensitive files
``` 
```

---

## 🛠️ Run Locally with Docker  

1. **Install Docker Desktop**  
   - Download & install [Docker Desktop](https://www.docker.com/products/docker-desktop/)  
   - Start Docker Desktop  

2. **Verify Docker Installation**  
   ```sh
   docker --version

3.docker run -it -p 5678:5678 ^
  -v D:\N8N\inboxguardian:/home/node/.n8n ^
  n8nio/n8n
4.Open n8n
👉 http://localhost:5678

```
## 🖼️ Workflow Preview
Workflow Image

Workflow Video

📹 Download & open demo.mp4
## 🔔 Features  

- 🕒 Runs on schedule – no IMAP connection needed  
- 🤖 Smart AI classification using Gemini 2.5 Flash Lite  
- 📨 Important emails → instant Discord alerts  
- 🗑️ Junk emails → auto-deleted from Gmail  
- 🔒 Local setup → you control your data  

