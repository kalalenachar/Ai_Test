# PPSM / Dharmākūta Project: Master Editorial, Typography & Proofreading Instructions

All tasks in this workspace involving Sanskrit text processing, transcription, proofreading, grammatical audits, or formatting must strictly follow these comprehensive guidelines. The goal is zero-defect, publication-grade, scholar-ready Sanskrit philology and typography that decisively outperforms any web-based AI interface.

---

## 1. Daṇḍa & Punctuation Rules (दण्ड-प्रयोग-नियमाः)

1. **Ardha-Śloka (Half-Verse) Boundary**:
   - Use a single daṇḍa `।` (`U+0964`) exclusively at the end of the first half-verse (ardha-śloka / hemistich), preceded by a single space.
2. **Pūrṇa-Śloka (Full-Verse End) & Colophons**:
   - Use the dedicated authentic Unicode Double Daṇḍa `॥` (`U+0965`) exclusively at the end of a full verse, sūtra, or section/canto colophon (e.g., `... पदम् ॥ १ ॥`, `... समाप्तम् ॥`, `द्वितीये ॥`).
   - When a verse ends with citation markers, format cleanly as `... पदम् ॥ इति ।` or `... पदम् ॥ इति च ।`.
   - Never leave the second half of a verse ending with a single daṇḍa `।`.
3. **Single vs. Double Daṇḍa in Prose Commentary (*Gadya-Daṇḍa-Viveka*)**:
   - **Running Prose Within Paragraphs**: Sentences continuing *within* running prose commentary (e.g. before introductory/connecting clauses such as `तथा च...`, `अत एव...`, or mid-paragraph explanations) must ALWAYS end with a single daṇḍa `।` (`U+0964`), NEVER with a double daṇḍa `॥`.
     - Patterns such as `... सूचितम् ॥ तथा च...` or `... इत्युक्तम् ॥ तथा च...` are typesetting errors and must strictly be normalized to `... सूचितम् । तथा च...` and `... इत्युक्तम् । तथा च...`.
   - **Paragraph, Topic & Section Endings (*Prakaraṇa- / Viṣaya-Samāpti*)**: There is **NO rule** stating that prose commentary must universally end with a single daṇḍa (`गद्यवाक्ये सर्वत्र एकदण्ड एव प्रयोक्तव्यः इति नियमो नास्ति`). When a paragraph, topic, exposition, or anuvāda ends in prose (*prakaraṇa-samāpti*, e.g., `एतच्च प्राक् प्रपञ्चितम् ॥` preceding a new section like `तृतीये ॥`), an authentic Double Daṇḍa `॥` (`U+0965`) is completely legitimate, standard, and canonical in Sanskrit textual traditions. NEVER demote a legitimate double daṇḍa at the end of a paragraph or topic to a single daṇḍa.
4. **Single Daṇḍa Twice & ASCII Normalization**:
   - NEVER use two consecutive single daṇḍas (`।।` or `। ।`) or ASCII pipe symbols (`||` or `| |`).
   - Deterministically normalize all `।।`, `। ।`, `||`, and `| |` to the authentic Unicode character `॥` (`U+0965`).
5. **Standalone Ardha-Śloka Quotations**:
   - When a single pāda or half-verse is quoted as a standalone authority ending with `इति`, format uniformly as `... पदम् ॥ इति ।` (or `... पदम् । इति ।` if explicitly a single hemistich pratīka).

---

## 2. Uniform Whitespace & Formatting Standard (रिक्तान्तर-संरेखण-नियमाः)

1. **Strict Uniform Single Spacing**:
   - All text must maintain uniform single-space word boundaries (` `).
   - Collapse all consecutive multi-space sequences `[ \t]{2,}` into a single space ` `.
2. **Zero Leading & Trailing Whitespace**:
   - Every line in verse and prose must have ZERO leading whitespace. Never allow spaces or tabs at the beginning of a line (e.g. after `\line` or `\par`).
   - Never allow trailing whitespace before line breaks (`\line`) or paragraph breaks (`\par`).
3. **Daṇḍa Spacing Standard**:
   - Exactly one space before every daṇḍa: ` पदम् ।`, ` पदम् ॥`.
   - Exactly one space after every daṇḍa when followed by text on the same line: ` पदम् । तथा च...`, ` पदम् ॥ इति ।`.
4. **Elimination of Fake Layout Alignment**:
   - NEVER simulate center alignment, indentation, or stanza margins using raw space padding or tab characters.
   - Alignment must be handled purely through styling engines (CSS `text-align: center`, RTF paragraph styles, Typst, LaTeX).
5. **Elimination of OCR Internal Word-Splitting**:
   - Detect and mend broken conjuncts or internal word splits caused by OCR (e.g. `कु र्यात्` ➔ `कुर्यात्`, `सङ् काशः` ➔ `सङ्काशः`, `लङ् का` ➔ `लङ्का`, `कृ त्यं` ➔ `कृत्यं`, `निकु म्भेन` ➔ `निकुम्भेन`, `सङ् ग्रहण` ➔ `सङ्ग्रहण`).

---

## 3. Within-a-Shloka Line Breaks (श्लोकपाद-विभाजन-नियमाः)

1. **Line Break Standard (`\line` / `\n`)**:
   - Lines within a single metrical verse must be separated by a **single line break** (`\line` in RTF, `\n` in text), NEVER a paragraph break (`\par` / `\n\n`).
   - A verse is an indivisible unit: the first half (*pūrvārdha*) and second half (*uttarārdha*) must remain together in the same verse block.
2. **Anuṣṭubh Formatting**:
   - Anuṣṭubh verses must be formatted in exactly 2 distinct, balanced lines:
     - Line 1: Pādas a & b, ending with a single space and single daṇḍa ` ।`.
     - Line 2: Pādas c & d, ending with a single space and double daṇḍa ` ॥` (or ` ॥ इति ।`).
3. **Classical Long Meters**:
   - Meters such as *Śārdūlavikrīḍita*, *Mandākrāntā*, *Sragdharā*, *Vasantatilakā*, *Rathoddhatā*, *Upajāti* must be cleanly formatted into their metric lines/hemistichs with `\line`.

---

## 4. Shloka vs. Prose Distinction & Stanza Separation (पद्य-गद्य-विवेक-नियमाः)

1. **No Shloka Kept as Running Prose (*Gadya*)**:
   - NEVER wrap or collapse a metrical verse (*padya*) into continuous running prose. Verses must always have line breaks between pādas.
2. **Paragraph Breaks Between Distinct Shlokas**:
   - Distinct verses must ALWAYS be separated from each other by a paragraph break (`\par` / `\n\n`).
   - NEVER join two consecutive verses together with a line break (`\line`).
3. **Different Meters in Separate Paragraphs**:
   - When verses of different classical meters appear successively (e.g. Śārdūlavikrīḍita followed by Rathoddhatā), each verse MUST have its own independent paragraph break (`\par`).
4. **Verse-Prose Boundary Enforcement**:
   - Paragraph breaks (`\par` / `\n\n`) are strictly required to separate:
     - A shloka block from preceding or succeeding prose commentary (*gadya* / *ṭīkā*).
     - An introductory clause (e.g. `तथा च राजधर्मे-`, `अत एव धृतराष्ट्रः कार्यकाले विचारितवान् इति प्रतिपादितमुद्योगे-`) from the quoted verse that follows.
     - Never connect prose introductory sentences to a verse line using `\line`.
5. **No Orphan Citation Markers**:
   - Citation markers like `इति ।` must be cleanly attached to the end of the verse (`... साधुः ॥ इति ।`), never isolated in an empty orphan paragraph.

---

## 5. Pāṇinian Grammar & Sandhi Audit Rules (पाणिनीय-व्याकरण-सन्धि-नियमाः)

1. **Anusvāra Before Vowels Prohibited (`मोऽनुस्वारः` ८.३.२३)**:
   - Before any vowel (`अ, आ, इ, ई, उ, ऊ, ऋ, ए, ऐ, ओ, औ`), final `म्` MUST remain a halanta makāra (`म्`), NEVER an anusvāra (`ं`).
   - Example: `कार्यम् आरभते` (correct) vs. `कार्यं आरभते` (strictly prohibited).
2. **Halanta Makāra Before Consonants Prohibited**:
   - Before a consonant (hal), final `म्` MUST be converted to anusvāra (`ं`), e.g., `कृतं कार्यम्` (not `कृतम् कार्यम्`).
3. **Repha Sandhi Before Vowels**:
   - Words and duals ending in `रुँ` preceded by vowels other than `अ/आ` before a vowel MUST combine with repha (`र्`) by *'ससजुषो रुः'* (८.२.६६).
   - Example: `द्वितीयादशम्योः + उत्तरस्याम्` ➔ **`द्वितीयादशम्योरुत्तरस्याम्`** (analogous to `राग्नेय्यां`, `र्दक्षिणस्यां`, `र्नैर्ऋत्यां`, `र्वायव्याम्`, `रैशान्याम्`).
4. **Visarga Lopa of `सः / एषः` Before Consonants (`एतत्तदोः सुलोपोऽकोरनञ्समासे हलि` ६.१.१३२)**:
   - Before any consonant, `सः` and `एषः` must drop visarga: `स गच्छति`, `एष पश्यति` (never `सः गच्छति`, `एषः पश्यति`).
5. **Visarga Lopa Before Vowels (`भोभगोअघो...` ८.३.१७ & `लोपः शाकल्यस्य` ८.३.१९)**:
   - After `अ/आ`, visarga before vowels drops: `दूत उत्तमे` (not `दूतः उत्तमे`).
6. **Avagraha Standard (`एङः पदान्तादति` ६.१.१०९)**:
   - Short `अ` preceded by `ए` or `ओ` merges and takes an avagraha: `सोऽब्रवीत्`, `तेऽपि` (never `सो अब्रवीत्` or `ते अपि`).
7. **Verbal & Nominal Form Validity**:
   - Verify correct Ātmanepada / Parasmaipada: `प्रयतेत` (not `प्रयतेत्`), `वर्तते` (not `वर्तति`), `करोमि` (not `कुर्मि`), `शोचन्ति` (not `शोचन्ते`), `त्यक्ष्यन्ति` (not `त्यक्षन्ति`).
   - Verify gender and case concord (e.g. `युद्धकाण्डम्` neuter in grantha colophons, `आधेयवस्तूनि च वीर्यवन्ति` neuter plural).

---

## 6. Textual Criticism, Apparatus & Print Artifact Handling (मुद्रणदोष-शोधन-नियमाः)

1. **Elimination of Broken Compounds Across Lines**:
   - Remove physical print-line hyphens breaking compound words (e.g. `भाविसेना-\line नयन...` ➔ `भाविसेनानयन...`).
   - Remove spurious spaces after hyphens in samāsa (e.g. `शत्रुवध- राज्याभिषेक...` ➔ `शत्रुवध-राज्याभिषेक...`).
2. **CP1252 & Encoding Corruption Sanitization**:
   - Detect and eliminate raw CP1252 byte artifacts (`\'96` en-dash, `\'97` em-dash) in document text bodies, replacing them with standard ASCII hyphens `-`.
3. **Apparatus & Bracket Cleaning in Metrical Verse**:
   - Critical editorial brackets or manuscript variants (like `((घोषान्) [योधान्]`, `(को) [सो]ऽयं`, `वीर्यवन्ती[ति]`) must not remain inside the metrical verse body where they disrupt syllable counts.
   - Restore the metrically pure reading in the verse body (e.g. `योधान् न्यसेत`, `सोऽयं`, `वीर्यवन्ति`) and record the apparatus note in the explanation ledger.
4. **Dittography & Duplicate Verse Detection**:
   - Detect and remove accidental duplications of lines or stanzas caused by typesetting repeats.

---

## 7. Mandatory Verification Scorecard & Ledger Workflow (परीक्षण-प्रमाणीकरण-कार्यप्रणाली)

Before any audit batch is finalized, the following automated scorecard must be programmatically verified with zero deviations:

```
================ MANDATORY SCORECARD ================
1. Double Daṇḍa Variants (।।, । ।, ||, | |) : 0
2. Consecutive Multi-Spaces ([ \t]{2,})       : 0
3. Lines with Leading Whitespace             : 0
4. Lines with Trailing Whitespace            : 0
5. Double Daṇḍas in Running Prose Sentences  : 0
6. Paragraphs Mixing Verse & Prose (>2 lines): 0
7. Corrupted CP1252 Raw Bytes (\x96, \x97)   : 0
8. Anusvāra Before Vowels (ं [अ-औ])          : 0
9. Unjoined Visarga Before Vowels            : 0 (Except exact cited pāda pratīkas)
=====================================================
```

### Safety & Logging Protocol:
1. **Timestamped Safety Backup**: Always create a clean backup of the master file before applying any modification batch.
2. **JSON Audit Ledger (`changes_data.json`)**: Every single emendation must be recorded with unique sequential IDs, group labels, exact search phrases, before/after diffs (`<del>` / `<ins>`), and Pāṇinian grammatical justifications.
3. **Interactive Visual Dashboard (`changes_done.html`)**: Must remain synchronized with `changes_data.json` with both dynamic fetch and embedded fallback data for offline and local review.
