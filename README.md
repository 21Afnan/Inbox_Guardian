# 📬 InboxGuardian  

InboxGuardian is a **local AI-powered email cleaner** built with [n8n](https://n8n.io/).  
It automatically scans your inbox on a schedule, classifies emails with AI, and then:  

- ✅ Sends **important emails** as notifications via Discord  
- 🗑️ Automatically deletes **unimportant emails** from Gmail  

Runs fully on your machine → **your data stays private**.  

---

## 🚀 How It Works  

1. **Scheduler Trigger** → runs the workflow at intervals you define  
2. **Gmail Get Message Node** → fetches unread emails  
3. **AI Classifier (Gemini 2.5 Flash Lite)** → analyzes & labels emails as `KEEP` or `DELETE`  
4. **Code Node** → parses AI output into JSON  
5. **IF Node** → routes based on classification:  
   - **KEEP** → sends you a notification in **Discord** via webhook  
   - **DELETE** → removes the message using **Gmail Delete Message Node**  

---

## 📂 Repository Structure  

```
├─ inboxguardian-workflow.json # exported n8n workflow
├─ screenshots/ # workflow visuals
│ └─ inboxguardian-flow.png # screenshot of workflow
  └─ demo.mp4 # short demo video (download & open locally)
├─ README.md # project description & instructions
└─ .gitignore # ignores sensitive files
```


---
```
## 🛠️ Run Locally with Docker  

### 1. Install Docker Desktop  
- Download & install [Docker Desktop](https://www.docker.com/products/docker-desktop/)  
- Start Docker Desktop  

### 2. Verify Installation  
Run this command in terminal/PowerShell:  

docker --version

### 3.Create a folder on your machine to persist workflow data (Windows example):
mkdir D:\N8N\inboxguardian

### 4. Run InboxGuardian
Start n8n with the following command:
docker run -it -p 5678:5678 ^
  -v D:\N8N\inboxguardian:/home/node/.n8n ^
  n8nio/n8n
   ### 💡 Replace D:\N8N\inboxguardian with your local folder path if different.

### 5. Open n8n
Once the container is running, open:
👉 http://localhost:5678

```


## 🔑 Setup Credentials

### Gmail

- In n8n, create new Gmail credentials (OAuth2 or service account)

- Allow read + delete access

- Discord Webhook

- Go to your Discord server → Integrations → Webhooks

- Copy webhook URL and paste into the Discord node in n8n

- AI Classifier

- Replace with your own Gemini API Key (from Google AI Studio
) in the workflow

### Import Workflow

- In n8n, click Import from File

- Upload inboxguardian-workflow.json

- Update credentials with yours

- Save & activate


## 🖼️ Workflow Preview
📸 Screenshot: See screenshots/inboxguardian-flow.png

🎥 Video Demo: Watch inboxguardian.mp4


## 🔔 Features 
- 🕒 Runs on schedule – no IMAP connection needed
- 📨 Connect Gmail node (Get Message)
- 🤖 Smart AI classification using Gemini 2.5 Flash Lite
- 📨 Important emails → instant Discord alerts
- 🗑️ Junk emails → auto-deleted from Gmail 
- 🔒 Local setup → you control your data



```
### ✅ Quick Start:
Clone the repo, run Docker, import the workflow, add your credentials → InboxGuardian is ready 🚀

git clone https://github.com/YOUR-USERNAME/inboxguardian.git
cd inboxguardian
docker run -it -p 5678:5678 -v %cd%:/home/node/.n8n n8nio/n8n
```

 📩 **Connect with me:** 
- Email: [afnanshoukat35@gmail.com](mailto:afnanshoukat35@gmail.com)
- LinkedIn: [www.linkedin.com/in/afnan-shoukat-030306267](https://www.linkedin.com/in/afnan-shoukat-030306267)
