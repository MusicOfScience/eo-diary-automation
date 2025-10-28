# 🗓️ EO Diary Automation  
*A lightweight, maintainable automation system for managing meeting and event briefs in the office of Dr Monique Ryan MP.*

---

## 📖 Overview

The EO Diary Automation system streamlines the handling of meeting and event requests received by email.  
It automatically:

1. Reads Gmail messages labelled **DIARY_MEETING** or **DIARY_EVENT**  
2. Extracts structured information and attachments  
3. Generates standardised **Word briefing notes** and **ICS calendar files**  
4. Stores all artefacts in a consistent **filing structure with unique Case IDs**  
5. Logs every action in a **Google Sheet**, including timestamps and summary status  
6. Sends a confirmation email to the forwarder with links to all outputs  

Everything runs **entirely within Google Workspace** — no external APIs, servers, or paid dependencies.

---

## 🧭 System Architecture

```

Outlook (.mp inbox)
│
├── Quick Action → Forward to Diary Manager
│       ↳ [DIARY_MEETING] or [DIARY_EVENT]
│
Gmail (moniqueryan.com.au)
│
├── Label detection & parsing (Apps Script)
│       ├── Extract structured info
│       ├── Summarise attachments (offline NLP)
│       ├── Populate Word briefing note
│       ├── Create .ics calendar file
│       ├── Log to Google Sheet
│       └── Email confirmation
│
Google Drive
├── /templates/
├── /logs/
├── /outputs/YYYY/MM/DD/<CaseID>/
├── /attachments/
└── /documentation/

```

---

## 🧱 Folder Structure

| Folder | Purpose |
|:--|:--|
| `/templates/` | Word templates for meeting and event briefs |
| `/scripts/` | Apps Script project files (`.gs`, `.js`) |
| `/logs/` | Google Sheet logs and backups |
| `/outputs/` | Generated briefs, ICS files, and per-case folders |
| `/attachments/` | Extracted attachments by Case ID |
| `/documentation/` | Manuals, diagrams, run-book, ELI5 guides |

---

## 🧩 Key Concepts

### Case ID  
Every record uses a unique ID in the form:  
```

KOY-EO-YYYYMMDD-HHMM-NNN

```
This ID appears in all filenames, folder names, log entries, and confirmation emails.

### Local Extractive Summarisation  
Attachments (`.docx`, `.pdf`, `.txt`, `.rtf`) are summarised locally without APIs:
1. Text is tokenised into sentences  
2. Sentences scored by keyword frequency  
3. Top 2–3 sentences inserted into the briefing’s “Background” section  

This produces readable summaries with **no AI or external dependencies**.

---

## ⚙️ Installation & Setup

### 1. Workspace Environment
1. In Google Drive, create a shared folder:
```

EO Admin / Diary Automation 2025

```
2. Add subfolders as above (`templates/`, `scripts/`, etc.).
3. Share with:
- **Diary Manager** (owner)
- **Hudson Harding** (admin)

### 2. Google Apps Script
1. Open the `Diary_Processing_Log` Google Sheet.  
2. Go to **Extensions › Apps Script**.  
3. Paste in the automation scripts from `/scripts/`.  
4. Authorise Gmail, Drive, and Sheets scopes.  
5. Create triggers:
- **Manual run** on demand  
- **Time-based** (hourly recommended)

### 3. Templates
Place briefing templates in `/templates/`:
- `briefing_meeting.docx`
- `briefing_event.docx`

### 4. Outlook Quick Actions (.MP inbox)
1. Create two **Quick Steps**:
- **Forward to Diary – Meeting** → `eleanor@moniqueryan.com.au`  
  (Subject prefix `[DIARY_MEETING]`, Category Teal, Keep Unread)  
- **Forward to Diary – Event** → `eleanor@moniqueryan.com.au`  
  (Subject prefix `[DIARY_EVENT]`)  
2. Optionally add a rule to move sent items into “Forwarded to Diary”.

---

## 📊 Logging

Each processed item appends a row to the log Sheet:

| Timestamp | Case ID | Label | Sender | Subject | Status | Attachments | Summary Method | Notes |
|:--|:--|:--|:--|:--|:--|:--|:--|:--|

- Status values: `Processed`, `TBC_FIELDS`, `TBC_ATTACHMENT`, `Error`.  
- Summary Method: `local_extractive` (default).

---

## 🧰 Maintenance

### Common Tasks
| Task | How to Run |
|:--|:--|
| **Rotate Diary Manager** | Reassign Drive ownership + re-authorise triggers |
| **Add New Label** | Edit label list in `main.gs` + update docs |
| **Refresh Templates** | Replace files in `/templates/` + test |
| **Backup Logs** | Zip `/logs/` + `/outputs/` → `/archive/YYYY-MM-DD/` |
| **Health Check** | Run `diagnostics.gs` or the “Audit” menu item |

### Quarterly Review
1. Verify Gmail labels exist and match script constants.  
2. Check triggers are active (Edit › Triggers).  
3. Confirm Drive storage under quota.  
4. Review log for errors > 5 %.  
5. Update version tag in GitHub (`v0.x` → `v0.y`).

---

## 💻 GitHub Repository

Repository: **[MusicOfScience/eo-diary-automation](https://github.com/MusicOfScience/eo-diary-automation)**  

Contains:
- Apps Script source code  
- Markdown documentation and ELI5 guides  
- Example template and sample log  
- Changelog and version tags  

Sensitive folders (`/auth/`, `/private/`) are excluded via `.gitignore`.

---

## 🧭 Roles

| Role | Responsibility |
|:--|:--|
| **Diary Manager** (currently Eleanor) | Operates workflow, labels emails, reviews outputs |
| **Admin / Tech Lead** (Hudson) | Maintains scripts, permissions, documentation |
| **Future 2IC / Delegate** | May assume Diary Manager role if structure changes |

Ownership and triggers can be reassigned in minutes using the Maintenance Guide.

---

## 🧠 Why No External AI

- Keeps the workflow **completely internal** to Google Workspace  
- No API costs, tokens, or dependency management  
- Easier onboarding for future staff  
- Predictable, reproducible summaries  

---

## 📜 Licence & Attribution

Internal tool for the office of **Dr Monique Ryan MP**, created and maintained by the Kooyong EO Team.  
Code and documentation © 2025 – present, released under a permissive internal use licence (not for redistribution).

---

### 🏁 Version
Current Release: **v0.1**  
Next Planned: **v0.2** – Add configurable summary length + auto-archive toggle.



Would you like me to create a matching `CHANGELOG.md` template next (so you can track versions when you start tagging them on GitHub)?
