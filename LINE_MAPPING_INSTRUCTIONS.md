# Document Line Number Mapping Protocol (दस्तावेज-पङ्क्तिसंख्या-संरेखण-प्रोटोकॉल)

This document establishes the mandatory protocol for extracting, verifying, and mapping line numbers in the **PPSM / Dharmākūta Project**. All AI assistants, scripts, and human contributors must strictly follow these instructions.

---

## 1. Golden Rule: Rendered Document Lines vs. Raw RTF Source Lines

> [!CAUTION]
> **NEVER COUNT RAW RTF SOURCE CODE LINES!**
> Reading `DHARMAKOOTA YUDDHA KANDA for ai test.rtf.doc` as plain text in a code editor or terminal produces completely invalid line numbers.

1. **Why Raw RTF Line Counting Fails**:
   - The first 20 lines of the `.rtf` file contain raw formatting definitions, font tables, and style dictionaries (`{\rtf1\ansi... \fonttbl... \stylesheet...}`).
   - These 20 lines are completely invisible to any user viewing the document in a word processor.
   - Counting raw lines mistakenly shifts Page 1 line numbers by +20 (e.g. reporting `युद्धकाण्डः` as Line 23 instead of **Line 3**), and shifts subsequent pages by hundreds of lines.

2. **The True Standard**:
   - Scholars, editors, and proofreaders view `DHARMAKOOTA YUDDHA KANDA for ai test.rtf.doc` in **LibreOffice Writer** or **Microsoft Word** with **Line Numbering enabled** (`Tools` ➔ `Line Numbering`).
   - In this mode, line numbers are **Per-Page**, restarting from **Line 1** at the top of each page up to roughly **17–21 lines** per page.

---

## 2. Canonical Page 1 & Page 2 Benchmark

Whenever verifying document line numbers, always validate against these known benchmarks:

### Page 1 Benchmark (20 lines total)
| Line | Text | Ref ID / Description |
|---|---|---|
| **Line 1** | `॥ धर्माकूतम् ॥` | Title Header |
| **Line 2** | `श्रीत्र्यम्बकरायमखीया श्रीमद्रामायणव्याख्या` | Sub-header |
| **Line 3** | `युद्धकाण्डः` | `P01-GRAM-001` (Section Title) |
| **Line 4** | `हनुमन्मुखेन सीतासद्भावरावणबलादिविचारणानन्तरं भाविसेना-` | `P01-SPACE-001` (Compound Start) |
| **Line 5** | `नयनप्रभृतिपट्टाभिषेकान्तरामचरितवर्णनमुखेन` | Compound Continuation |
| **Line 6** | `सेनासन्नाहरणनयनव्यूहनशत्रुपरनिरोधनयुद्धप्रकारतत्कालसमागतशत्रु` | Running Prose |
| **Line 7** | `पक्षीयसङ्ग्रहणप्रकारशत्रुवध- राज्याभिषेकराज्यपरिपालनादीन्` | `P01-TYPO-001` (Hyphen Spacing) |
| **Line 8** | `राजधर्मान् प्रतिपादयितुं युद्धकाण्डमारभते भगवान् वाल्मीकिः ।` | Prose End |
| **Line 9** | `श्रुत्वा हनुमतो वाक्यं यथावदभिभाषितम् ।` | Shloka 1a-b |
| **Line 10** | `रामः प्रीतिसमायुक्तो वाक्यमुत्तरमब्रवीत् ॥` | Shloka 1c-d |
| **Line 11** | `कृतं हनुमता कार्यं सुमहद्भुवि दुर्लभम् ।` | Shloka 2a-b |
| **Line 12** | `मनसाऽपि यदन्येन न शक्यं धरणीतले ॥` | Shloka 2c-d |
| **Line 13** | `भृत्यकार्यं हनुमता सुग्रीवस्य कृतं महत् ।` | `P01-DANDA-001` (Verse 1.6 Start) |

### Page 2 Benchmark (18 lines total)
| Line | Text | Ref ID / Description |
|---|---|---|
| **Line 1** | `वैदेह्या दर्शनेनाद्य धर्मतः परिरक्षिताः ।` | Page Top Hemistich |
| **Line 2** | `अत्र सीतादर्शनकार्ये नियुक्तेन हनूमता तत्कार्याविरोधेन` | Prose Commentary |
| **Line 3** | `लङ्कापुरी-दहनराक्षसनिग्रहादिकमपि कृतं, परावमानेन आत्माऽपि` | `P02-GRAM-002` (सवर्णदीर्घः) |
| **Line 4** | `लघुतां न नीतः, अहं च रघुवंशश्च रक्षित इत्युक्त्या उत्तमो दूतः उत्तमे` | `P02-GRAM-001` (विसर्गलोपः) |
| **Line 5** | `कार्ये नियोक्तव्य इति सूचितम् । तथा चोद्योगे विदुरः-` | `P02-GRAM-003` (ASCII कोलन-दोषः) |
| **Line 6** | `त्रिविधाः पुरुषा राजन्नुत्तमाधममध्यमाः ।` | Quoted Verse 1 |
| **Line 7** | `नियोजयेद्यथावत्तांस्त्रिविधेष्वेव कर्मसु ॥ इति ।` | Quoted Verse 2 |
| **Line 8** | `ततः, सभापर्वणि युधिष्ठिरं प्रति नारदप्रश्नोऽपि-` | `P02-SPACE-001` (अनावश्यक-रिक्तता) |
| **Line 9** | `उत्तमानुत्तमेष्वेव मध्यमेषु च मध्यमाम् ।` | `P02-DANDA-001` (दण्डविपर्ययः) |
| **Line 15** | `अनेन कृतकार्यस्य स्तुतिर्बहुमतिश्च कर्तव्येति सूचितम् । तथाच` | `P02-VERSE-001` & `P02-GRAM-004` |

---

## 3. Automated Line Extraction via Headless LibreOffice

To extract and verify rendered document line numbers programmatically without opening the GUI:

### Step 1: Render RTF to PDF with Isolated Profile
Avoid GUI lock conflicts and snap AppArmor confinement by using the snap-accessible profile directory:
```bash
/snap/bin/libreoffice -env:UserInstallation=file:///home/samsho/snap/libreoffice/common/export_profile \
  --headless --convert-to pdf --outdir /home/samsho/Downloads \
  "/home/samsho/Downloads/PPSM/DHARMAKOOTA YUDDHA KANDA for ai test.rtf.doc"
```

### Step 2: Extract Layout Lines via `pdftotext`
Use `pdftotext -layout` to preserve exact lines and page breaks:
```bash
pdftotext -layout -f 1 -l 30 "/tmp/DHARMAKOOTA YUDDHA KANDA for ai test.rtf.pdf" extracted_pages.txt
```

### Step 3: Match Against changes_data.json
1. Read each page's non-empty lines (lines are 1-indexed per page).
2. For each audit item, locate its `search_phrase` and `before` diff text on the corresponding page (`P1` ➔ Page 1, `P2` ➔ Page 2, etc.).
3. Record the exact line index `1..N` in both `line_number` and `line`.

---

## 4. Ledger & Dashboard Synchronization Standard

Whenever line numbers are updated:

1. **`changes_data.json`**:
   - `page`: Must remain canonical (`P1`, `P2`, ..., `P30`).
   - `line_number` and `line`: Must be the identical integer matching the rendered page line.
   - **Sorting**: Items must be sorted strictly by `(int(page[1:]), line_number)`.
   - **Sequential IDs**: `id` must be renumbered consecutively `1..N` (1 to 269).

2. **`index.html`**:
   - The embedded offline dataset in `<script id="fallback-data" type="application/json">...</script>` must match `changes_data.json` byte-for-byte.
   - The card line tag dynamically renders:
     ```html
     <span class="line-tag" title="${it.page}, Line ${it.line || it.line_number}">Line ${it.line || it.line_number}</span>
     ```

3. **Monotonicity Verification**:
   - Ensure `0` page or line inversions:
     $$\text{Page}_{i} < \text{Page}_{i+1} \quad \text{or} \quad (\text{Page}_{i} = \text{Page}_{i+1} \land \text{Line}_{i} \le \text{Line}_{i+1})$$
