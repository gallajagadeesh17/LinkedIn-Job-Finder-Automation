# 🔎 LinkedIn Job Finder Automation

> **An n8n-powered job discovery workflow that turns your search criteria into structured LinkedIn job leads and saves them directly to Google Sheets.**

[![n8n](https://img.shields.io/badge/Automation-n8n-ff6d5a?style=for-the-badge&logo=n8n&logoColor=white)](https://n8n.io/)
[![Bright Data](https://img.shields.io/badge/Data-Bright%20Data-111827?style=for-the-badge)](https://brightdata.com/)
[![Google Sheets](https://img.shields.io/badge/Output-Google%20Sheets-34a853?style=for-the-badge&logo=googlesheets&logoColor=white)](https://www.google.com/sheets/about/)

---

## ✨ What is this?

**LinkedIn Job Finder Automation** is an n8n workflow designed to reduce the manual work involved in searching for jobs.

Instead of repeatedly searching LinkedIn, copying job details, and maintaining a spreadsheet manually, you provide your search criteria once. The workflow sends the request to Bright Data's LinkedIn dataset, waits for the scraping job to complete, retrieves the results, filters them, and stores useful job information in Google Sheets.

### 🎯 The goal

**Search → Collect → Filter → Organize → Apply**

---

## 🧠 How it works

```text
Search Form
   ↓
Bright Data LinkedIn Search
   ↓
Snapshot Tracking
   ↓
Ready? ── No ──→ Wait 1 minute ──→ Check again
   │
  Yes
   ↓
Fetch Jobs
   ↓
Filter Results
   ↓
Google Sheets
```

---

## 🚀 Features

- 🔍 **Custom job search** — city, job title, country, and job type.
- 🏢 **LinkedIn job discovery** — Bright Data LinkedIn dataset API.
- ⏳ **Automatic status polling** — waits until the snapshot is ready.
- 🧹 **Result filtering** — filters collected results before storage.
- 📊 **Google Sheets output** — creates a structured job tracker.
- 🔗 **Application links** — keeps available apply links with each result.
- 📅 **Recent opportunities** — configured to search the past week.
- 🔐 **Credential-safe workflow** — shared export uses placeholders instead of secrets.

---

## 📝 Search inputs

| Input | Purpose |
|---|---|
| 📍 City | Target job location |
| 💼 Job Title | Role or keyword |
| 🌎 Country | Target country |
| 🏷️ Job Type | Full-Time, Part-Time, Remote, WFH, Contract, Internship, or Freelance |

Job type is optional.

---

## 📦 Job information

The workflow requests a broad set of job fields and stores the most useful ones in Google Sheets:

- **Job Title**
- **Company Name**
- **Location**
- **Job Details / Summary**
- **Apply Link**
- **Company URL**

The Bright Data request also asks for fields such as posting date, employment type, seniority, industry, salary information, applicant count, job URL, and formatted description.

---

## 🛠️ Tech Stack

| Technology | Role |
|---|---|
| **n8n** | Workflow automation |
| **Bright Data** | LinkedIn job data collection |
| **Google Sheets** | Job storage and tracking |
| **HTTP Request nodes** | API communication |
| **n8n Form Trigger** | Search input |
| **IF / Filter / Wait nodes** | Workflow control |

---

## 📁 Repository structure

```text
Linkedin-Automation-AI/
├── workflows/
│   └── linkedin-job-finder.json   # Importable n8n workflow
├── screenshots/                   # Optional workflow screenshots
└── README.md
```

---

## ⚙️ Setup

### 1. Import the workflow

Import this file into your n8n instance:

```text
workflows/linkedin-job-finder.json
```

### 2. Configure Bright Data

Replace:

```text
Bearer YOUR_BRIGHT_DATA_API_TOKEN
```

with your own Bright Data credential in the HTTP Request nodes.

### 3. Configure Google Sheets

Connect your Google Sheets credential in n8n and replace:

```text
YOUR_GOOGLE_SHEET_ID
```

with your spreadsheet ID. Select the required worksheet.

### 4. Test a search

Example:

```text
City: Bangalore
Job Title: AI/ML Engineer
Country: India
Job Type: Full-Time
```

The workflow starts the Bright Data task, monitors the snapshot, retrieves the results, filters them, and writes the selected fields to Google Sheets.

---

## 🔐 Security

This repository intentionally uses placeholders for credentials and private connection data.

**Never commit:**

- Bright Data API tokens
- Google OAuth credentials
- Private webhook secrets
- Personal access tokens
- Service-account private keys

Use n8n's credential manager or environment variables for production secrets.

> ⚠️ If a secret has already been exposed publicly, revoke or rotate it immediately.

---

## 🎬 Workflow at a glance

**01 — Search** → Enter job requirements through the n8n form.

**02 — Discover** → Bright Data starts the LinkedIn data collection task.

**03 — Track** → n8n checks the snapshot status and waits when necessary.

**04 — Collect** → The completed snapshot is downloaded.

**05 — Organize** → Results are filtered and appended to Google Sheets.

**06 — Apply** → Use the stored job and application links to continue your search.

---

## 💡 Why this automation is useful

Manual job hunting often means:

> Search → Open jobs → Copy details → Paste into spreadsheet → Repeat

This workflow converts that repetitive process into an automated pipeline and gives you a structured job list that can be reviewed, sorted, and tracked in Google Sheets.

---

## 🔮 Future improvements

- 🤖 AI-based job matching and relevance scoring
- 📄 Resume-to-job compatibility analysis
- 📨 Email or Telegram job alerts
- 🚫 Duplicate job detection
- 📈 Application tracking dashboard
- 🧠 Skill-gap analysis from job descriptions
- ⭐ Personalized job ranking
- ⏰ Scheduled daily job searches
- 📊 Job-market analytics

---

## 👨‍💻 Author

**Galla Jagadeesh**

Built with **n8n + Bright Data + Google Sheets** to automate repetitive job-search workflows.

---

## ⭐ Support

If this project helps automate your job search, consider giving the repository a ⭐ and sharing improvements.
