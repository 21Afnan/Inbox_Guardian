<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:4A0D2E,50:C2185B,100:FF8FC7&height=200&section=header&text=Inbox%20Guardian&fontSize=52&fontColor=FFFFFF&fontAlignY=36&desc=A%20self-hosted%20AI%20agent%20that%20keeps%20your%20Gmail%20clean&descSize=16&descAlignY=58" width="100%" alt="Inbox Guardian"/>

<p>
  <img src="https://img.shields.io/badge/n8n-EA4B71?style=for-the-badge&logo=n8n&logoColor=white" alt="n8n"/>
  <img src="https://img.shields.io/badge/Gemini-8E75B2?style=for-the-badge&logo=googlegemini&logoColor=white" alt="Gemini"/>
  <img src="https://img.shields.io/badge/Gmail%20API-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Gmail API"/>
  <img src="https://img.shields.io/badge/Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white" alt="Discord"/>
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" alt="Docker"/>
  <img src="https://img.shields.io/badge/License-MIT-FF4FA3?style=for-the-badge" alt="MIT License"/>
</p>

</div>

---

## The problem

Important emails get buried under newsletters, promotions and automated notices, and sorting them by hand every day is tiring. Most "smart inbox" tools solve this by reading your mail on their own servers.

**Inbox Guardian** is an AI agent you run yourself. On a schedule it reads new Gmail messages, asks an AI model whether each one matters, sends the important ones to you on Discord, and clears out the rest. The workflow runs in your own n8n instance, so you stay in control of your mail.

<p align="center"><img src="screenshot%26Video/Inbox_Guardian-workflow.png" width="760" alt="Inbox Guardian n8n workflow"/></p>

## How it works

```
Schedule Trigger ──> Gmail: get new messages ──> Gemini: KEEP or DELETE? ──> Code: parse to JSON ──> If
                                                                                                │
                                              KEEP ──> HTTP Request to a Discord webhook (alert)│
                                              DELETE ──> Gmail: delete message  ◄───────────────┘
```

| Step | n8n node | What it does |
|---|---|---|
| 1 | Schedule Trigger | Runs the check at the interval you choose |
| 2 | Gmail, get many messages | Fetches the latest messages |
| 3 | Google Gemini, message a model | Reads each email and labels it `KEEP` or `DELETE` |
| 4 | Code | Turns the model's answer into clean JSON the workflow can route on |
| 5 | If | Sends each email down the right branch |
| 6a | HTTP Request | Posts important emails to your Discord channel |
| 6b | Gmail, delete a message | Removes unimportant emails from the inbox |

A short demo video is in [`screenshot&Video/inbox_guardian.mp4`](screenshot%26Video/inbox_guardian.mp4) (download to watch).

## Run it

**1. Start n8n with Docker** (Windows example; change the folder to any path you like):

```bash
docker run -it -p 5678:5678 -v D:\N8N\inboxguardian:/home/node/.n8n n8nio/n8n
```

Open `http://localhost:5678`.

**2. Import the workflow:** in n8n choose *Import from File* and select `inboxguardian-workflow.json`.

**3. Add your credentials:**

| Service | What to set |
|---|---|
| Gmail | OAuth2 credentials with read and delete access |
| Gemini | Your API key from Google AI Studio |
| Discord | A webhook URL from *Server Settings, Integrations, Webhooks*, pasted into the HTTP Request node |

**4. Save and activate.** The guardian now runs on its schedule.

> Tip: test on a secondary Gmail account first, and check the prompt in the Gemini node matches what *you* consider important before letting it delete anything.

## Repository contents

```
Inbox_Guardian/
├── inboxguardian-workflow.json      # exported n8n workflow
└── screenshot&Video/
    ├── Inbox_Guardian-workflow.png  # workflow canvas
    └── inbox_guardian.mp4           # demo video
```

---

<div align="center">

**Afnan Shoukat**

<a href="mailto:afnanshoukat35@gmail.com"><img src="https://img.shields.io/badge/Email-afnanshoukat35%40gmail.com-FF4FA3?style=for-the-badge&logo=gmail&logoColor=white&labelColor=4A0D2E" alt="Email"/></a>
<a href="https://www.linkedin.com/in/afnanshoukat"><img src="https://img.shields.io/badge/LinkedIn-Afnan%20Shoukat-FF4FA3?style=for-the-badge&logo=linkedin&logoColor=white&labelColor=4A0D2E" alt="LinkedIn"/></a>
<a href="https://github.com/21Afnan"><img src="https://img.shields.io/badge/GitHub-21Afnan-FF4FA3?style=for-the-badge&logo=github&logoColor=white&labelColor=4A0D2E" alt="GitHub"/></a>

Released under the [MIT License](LICENSE).

</div>

