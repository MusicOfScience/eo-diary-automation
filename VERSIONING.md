# 🧮 EO Diary Automation — Versioning Guide

This document explains **how version numbers are assigned and updated** for the EO Diary Automation project.

It ensures that everyone in the office — current and future diary managers, admins, or technical leads — can maintain a consistent and auditable release history.

---

## 🔢 Version Format

The project uses **Semantic Versioning (SemVer)** in the form:

```

vMAJOR.MINOR.PATCH

````

Each part increases based on the type of change:

| Component | Meaning | Example |
|------------|----------|----------|
| **MAJOR** | Significant changes — breaking compatibility or complete redesign | `v2.0.0` |
| **MINOR** | Feature additions or updates that don’t break previous behaviour | `v1.2.0` |
| **PATCH** | Bug fixes, documentation updates, or minor corrections | `v1.2.3` |

---

## 🪜 Incrementing Rules

### 1. **MAJOR (X.0.0)**
Increment when:
- The script or system structure changes in a way that breaks old behaviour  
- Drive or Sheet layout is redefined  
- A new platform or architecture (e.g. switching from Apps Script to API-based) is introduced  

**Example:**
> Migrating from a single shared log sheet to a full multi-tab database  
> → Move from `v1.3.2` → `v2.0.0`

---

### 2. **MINOR (1.X.0)**
Increment when:
- You add or modify features (new label types, templates, or file handling)  
- You change summarisation logic  
- You alter email or output formatting  
- You introduce new documentation or logs

**Example:**
> Added auto-archive for logs and new label `DIARY_TEST_MEETING`  
> → Move from `v1.2.0` → `v1.3.0`

---

### 3. **PATCH (1.2.X)**
Increment when:
- You fix bugs, formatting issues, or small logic errors  
- You update documentation or changelog text only  
- You adjust file paths or correct folder permissions

**Example:**
> Fixed attachment summary error for `.pdf` files  
> → Move from `v1.3.0` → `v1.3.1`

---

## 🧭 Version Tagging Steps

When you finalise an update:

1. **Edit the Script Header**
   - In the main Apps Script file (`main.gs`), update:
     ```js
     const VERSION = 'v1.3.0';
     ```

2. **Update the Google Sheet Log**
   - Add the new version number to the `About` tab in `Diary_Processing_Log`.

3. **Edit the `CHANGELOG.md`**
   - Add a new section summarising the update.

4. **Commit & Tag on GitHub**
   - Commit changes with a clear message:
     ```
     git commit -m "Release v1.3.0 – Added archive automation + new label support"
     git tag v1.3.0
     git push origin main --tags
     ```

5. **Notify the Team**
   - Post in Slack or email:
     ```
     EO Diary Automation updated to v1.3.0
     - New auto-archive feature
     - Updated template parser
     - Docs refreshed in /documentation/
     ```

---

## 🧰 Branching Convention (Optional)

For simple maintenance, use one main branch (`main`).

If multiple people ever collaborate:
````

main            ← production-ready
feature/...     ← new feature (e.g. feature/archive)
hotfix/...      ← urgent fixes (e.g. hotfix/attachments)

```

---

## 🧾 Version Reference Table

| Version | Release Date | Summary | Maintainer |
|:--|:--|:--|:--|
| v0.1 | 2025-10-28 | Initial release | Hudson Harding |
| v0.2 | TBD | Planned: Auto-archive + configurable summaries | — |
| v0.3 | TBD | Future: Optional AI summarisation toggle | — |

---

## 🧭 Governance

- **Primary Owner:** Current Diary Manager (`@moniqueryan.com.au`)  
- **Admin / Tech Lead:** Hudson Harding  
- **All releases must be logged** in both:
  - `CHANGELOG.md` (GitHub)
  - “Version” tab in `Diary_Processing_Log` Sheet

---

## ✅ Quick Recap

| Action | Type | Example |
|--------|------|----------|
| Added feature | MINOR | `v1.2.0 → v1.3.0` |
| Fixed bug | PATCH | `v1.3.0 → v1.3.1` |
| Rebuilt or changed file structure | MAJOR | `v1.3.1 → v2.0.0` |

---

**Remember:**  
Version tags are your institutional memory — they tell future staff *what changed, when, and why.*  
Keep them clean, consistent, and meaningful.

---

*Maintained by the Kooyong Electorate Office — Office of Dr Monique Ryan MP*  
*Internal use only.*

