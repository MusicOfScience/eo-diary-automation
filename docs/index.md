# 🗂️ EO Diary Automation — Documentation Index

*A complete guide to setup, operate, and maintain the diary automation system for the office of Dr Monique Ryan MP.*

---

## 📖 Overview

The EO Diary Automation system streamlines diary requests and meeting/event management in the electorate office by automatically:

- Reading labelled Gmail messages (`DIARY_MEETING`, `DIARY_EVENT`)
- Extracting key information and attachments
- Generating briefing notes and calendar files
- Logging and filing outputs with unique Case IDs

All operations run **entirely inside Google Workspace**, with **no external APIs** and full transparency through version control on GitHub.

---

## 🧱 Documentation Map

| Document | Purpose |
|:--|:--|
| [**README.md**](../README.md) | High-level system overview, folder structure, setup and usage instructions |
| [**CHANGELOG.md**](../CHANGELOG.md) | Version-by-version record of changes and feature additions |
| [**VERSIONING.md**](../VERSIONING.md) | Guide to incrementing version numbers, tagging, and GitHub release procedure |
| **Technical Manual** | Detailed explanation of Apps Script architecture, logic, OAuth scopes, and file-handling routines |
| **ELI5 Maintenance Guide** | Step-by-step instructions for admins to re-authorise, rotate diary managers, or refresh templates |
| **ELI5 User Guide** | Everyday usage manual for diary managers or assistants (labeling, checking logs, retrieving outputs) |
| **Run Book** | Contact list, folder links, trigger checklists, and ownership transfer process |
| **Data Flow Diagram** | Visual of the full pipeline from Outlook → Gmail → Apps Script → Drive/Sheets |
| **Testing Results Tab** | Located inside `Diary_Processing_Log`; shows validation runs and outcomes |

*(Workspace-native Docs for the manuals above are stored under `/documentation/` in the Shared Drive.)*

---

## 🧭 Quick Start

1. **Create Workspace Folder Tree**
```

EO Admin / Diary Automation 2025/
├── templates/
├── scripts/
├── logs/
├── outputs/
├── attachments/
└── documentation/

```

2. **Copy the Google Sheet log**  
→ `Diary_Processing_Log` (includes macros + bound Apps Script).

3. **Install Apps Script**
- Open **Extensions › Apps Script** in the Sheet.  
- Paste code from `/scripts/` folder.  
- Authorise Gmail, Drive, and Sheets scopes.  
- Set triggers (manual + hourly).

4. **Load Templates**
- Place `briefing_meeting.docx` and `briefing_event.docx` in `/templates/`.

5. **Configure Outlook Quick Actions**
- *Forward to Diary – Meeting* → `eleanor@moniqueryan.com.au` (`[DIARY_MEETING]`)  
- *Forward to Diary – Event* → same, `[DIARY_EVENT]`

---

## 🧩 System Highlights

- **Offline Extractive Summarisation:** ranks key sentences from attachments, no AI calls.  
- **Case ID System:** `KOY-EO-YYYYMMDD-HHMM-NNN` ensures traceable filing.  
- **Structured Output:** `/outputs/YYYY/MM/DD/<CaseID>/` holds all related artefacts.  
- **Shared Drive Logging:** single source of truth for processed entries.  
- **GitHub Sync:** non-sensitive code and docs published at  
[`github.com/MusicOfScience/eo-diary-automation`](https://github.com/MusicOfScience/eo-diary-automation).

---

## 🧰 Maintenance Shortcuts

- **Rotate Diary Manager:** run “Reassign Ownership” procedure in Maintenance Guide.  
- **Add New Label:** update label list in Apps Script constants and Sheet.  
- **Refresh Templates:** replace `.docx` files in `/templates/` and test.  
- **Backup:** zip `/logs/` and `/outputs/` into `/archive/YYYY-MM-DD/`.  
- **Audit:** use “Audit Health Check” mini-prompt to verify triggers, scopes, and Drive access.

---

## 🕒 Version History

| Version | Date | Summary |
|:--|:--|:--|
| **v0.1** | 2025-10-28 | Initial release — baseline automation and docs |
| **v0.2** | *Planned* | Add auto-archive, configurable summary length |
| **v0.3** | *Planned* | Optional AI summarisation toggle (future) |

See the full [CHANGELOG.md](../CHANGELOG.md) for detailed release notes.

---

## 🔒 Governance & Contacts

| Role | Name / Address | Responsibility |
|:--|:--|:--|
| **Diary Manager** | *Eleanor @ moniqueryan.com.au* | Owns and operates the system day-to-day |
| **Admin / Tech Lead** | *Hudson Harding @ moniqueryan.com.au* | Maintains scripts, permissions, and documentation |
| **Shared Drive** | *EO Admin / Diary Automation 2025* | Central storage for all system assets |

---

## 🧾 Licence

Internal tool — for use within the office of **Dr Monique Ryan MP (Kooyong)**.  
© 2025 Kooyong Electorate Office.  
Redistribution or external publication is not permitted.

---

### 🔗 Related Repositories
- [`MusicOfScience/eo-diary-automation`](https://github.com/MusicOfScience/eo-diary-automation)
- (future) `MusicOfScience/eo-diary-templates` – public-safe sample templates

---

*Maintained by the Kooyong Electorate Office — Office of Dr Monique Ryan MP.*  
*Internal Use Only.*
