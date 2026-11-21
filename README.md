# धर्माकूतम् (युद्धकाण्डम्) — व्याकरणदोष-श्लोकमुद्रण-परिशोधन-वृत्तान्तः
### Dharmākūtam (Yuddhakāṇḍam) — Sanskrit Proofreading & Philological Audit Dashboard

[![Live Dashboard](https://img.shields.io/badge/Live_Dashboard-GitHub_Pages-2ea44f?style=for-the-badge)](https://kalalenachar.github.io/Ai_Test/)

Interactive scholar-ready editorial dashboard and JSON audit ledger documenting all philological emendations, Pāṇinian sandhi corrections, and typography normalizations across the **Dharmākūtam (Yuddhakāṇḍam)** critical edition text.

---

## 🌐 Live Interactive Dashboard

Access the fully interactive proofreading viewer directly in your browser:
👉 **[https://kalalenachar.github.io/Ai_Test/](https://kalalenachar.github.io/Ai_Test/)**

Features of the dashboard:
- **Real-Time Synchronized Diff View**: Side-by-side comparison of original readings (`<del>`) versus critical emendations (`<ins>`).
- **Pāṇinian Justifications**: Sūtra references (e.g., *मोऽनुस्वारः* ८.३.२३, *ससजुषो रुः* ८.२.६६, *एतत्तदोः सुलोपोऽकोरनञ्समासे हलि* ६.१.१३२).
- **Categorical Filtering**: Filter by Sandhi, Metre, Danda, Line Breaks, and Compound Word Corrections.
- **Dynamic Data Loading**: Reads directly from `changes_data.json` with an embedded fallback for offline inspection.

---

## 📁 Repository Contents

| File | Description |
| :--- | :--- |
| **[`changes_data.json`](changes_data.json)** | Master JSON audit ledger containing every emendation record, sequential IDs, contextual search keys, before/after diffs, and grammatical justifications. |
| **[`changes_done.html`](changes_done.html)** | Standalone, publication-grade interactive visual inspection dashboard. |
| **[`index.html`](index.html)** | GitHub Pages entry point (synchronized copy of `changes_done.html`). |
| **[`GEMINI.md`](GEMINI.md)** | Master Editorial, Typography & Proofreading Instruction Manual (Pāṇinian and Sanskrit typography rules). |

---

## 📜 Editorial & Typographical Standards

All editorial corrections adhere to canonical Pāṇinian grammar and classical Sanskrit typography standards:
1. **Danda Rules**: Half-verse demarcated by single danda (`।`), full verse ends and colophons by Unicode double danda (`॥`). Elimination of ASCII pipes (`||`) and double single dandas (`।।`).
2. **Whitespace Normalization**: Single uniform word-spacing, zero leading/trailing line whitespace.
3. **Verse Structure**: Distinct metrical lines separated by single line breaks, verses isolated by paragraph breaks.
4. **Sandhi Rigor**: Absolute compliance with *Mo'nusvāraḥ*, *Lopaḥ Śākalyasya*, and *Sasajuṣo ruḥ*.
