# 📬 InboxGuardian

**InboxGuardian** is a local AI-powered agent built with [n8n](https://n8n.io/) that automatically classifies emails into **Important** and **Unimportant**, and routes the junk toward Trash to keep your inbox clean.  
Runs fully on your machine → your data stays private.

---

## 🚀 How it works
1. **IMAP Email Trigger** → fetches emails from your inbox  
2. **AI (Gemini)** → classifies emails as *IMPORTANT* or *UNIMPORTANT*  
3. **IF Node** → branches logic  
4. **Trash Node (demo)** → routes unimportant emails to deletion  

---
# 📂 Repo contents

```InboxGuardian/
├─ workflow.json         # exported n8n workflow
├─ screenshots/
│  └─ flow.png           # screenshot of workflow canvas
├─ README.md             # project description & instructions
└─ .gitignore            # ignores sensitive files
```
## 🛠️ Run Locally with Docker

### 1. Install Docker Desktop
- Download & install [Docker Desktop](https://www.docker.com/products/docker-desktop/) for your OS.  
- Start Docker Desktop.

### 2. Verify Docker installation
Open a terminal (PowerShell / Command Prompt) and check version:
```bash
docker --version
Docker version 26.0.0, build <hash>
docker run -it -p 5678:5678 ^
  -v D:\N8N\inboxguardian:/home/node/.n8n ^
  n8nio/n8n
http://localhost:5678
