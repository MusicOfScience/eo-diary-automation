# 🗓️ EO Diary Automation — Changelog

All notable changes to this project will be documented in this file.  
The format follows the principles of [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).  
Version numbers follow **semantic versioning** (`vMAJOR.MINOR.PATCH`).

---

## [Unreleased]
### Added
- (placeholder for upcoming features)
- (e.g. add auto-cleanup for attachments older than 6 months)

### Changed
- (placeholder for UI or logic adjustments)
- (e.g. adjusted logging format for better CSV export)

### Fixed
- (placeholder for bug fixes)
- (e.g. corrected date parsing for Outlook forwards)

---

## [v0.1] — Initial Release — *2025-10-28*

### Summary
The first working version of the EO Diary Automation pipeline for the office of **Dr Monique Ryan MP**.  
Implements an entirely offline, Workspace-native process for handling diary correspondence.

### Added
- Core **Apps Script automation** bound to Google Sheet `Diary_Processing_Log`
- Automatic detection of Gmail labels `DIARY_MEETING`, `DIARY_EVENT`, and `REPROCESS`
- Extraction of key details (subject, sender, time, location, purpose)
- Offline **local extractive summariser** (no API calls)
- Automatic generation of:
  - Word briefing notes using standard templates
  - `.ics` calendar files with embedded metadata
- Case ID system: `KOY-EO-YYYYMMDD-HHMM-NNN`
- Structured Google Drive output folder system:
```

/outputs/YYYY/MM/DD/<CaseID>/
├── briefing_<CaseID>.docx
├── event_<CaseID>.ics
├── attachments/
└── log_<CaseID>.json

```
- Confirmation emails to forwarder with Drive links
- Shared Google Sheet log for audit and reporting
- Basic error handling (`TBC_FIELDS`, `TBC_ATTACHMENT`)
- **Outlook Quick Action** integration (forward from .MP inbox)
- Comprehensive documentation set:
- Technical Manual  
- Maintenance (ELI5) Guide  
- User (ELI5) Guide  
- Run Book  
- Data-flow diagram
- Public GitHub repository setup under `MusicOfScience/eo-diary-automation`
- Internal licensing statement and README

### Known limitations
- Requires manual setup of triggers during onboarding  
- Local summariser may mis-rank sentences in highly technical documents  
- No automated archival of logs or outputs yet  
- Calendar ICS output limited to single time range per event

---

## [v0.2] — *Planned*

### Planned Enhancements
- Add **auto-archive routine** for outputs/logs older than 90 days  
- Configurable summary length (short/medium/long)
- Optional “quick test mode” using `DIARY_TEST_*` labels
- Improved inline error alerts via email
- Basic usage analytics dashboard (Sheets)

---

## [v0.3] — *Planned*

### Future Ideas
- Integrate optional AI/NLP summarisation toggle (Gemini or Vertex)  
*Only if future staff have capability + approval.*
- Add Drive-to-Calendar sync for recurring events
- Include multi-recipient routing (e.g. joint meetings)

---

### 🔒 Governance Notes
- Primary Owner: **Diary Manager (currently Eleanor @ moniqueryan.com.au)**
- Admin/Technical Lead: **Hudson Harding @ moniqueryan.com.au**
- All project assets live in `@moniqueryan.com.au` Workspace Shared Drive.  
- Sensitive data and credentials are **never** committed to GitHub.

---

*Maintained by the Kooyong Electorate Office — Office of Dr Monique Ryan MP.*  
*Internal use only.*

