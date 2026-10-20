# Clinical Specialty Knowledge Base

A reusable AI-agent skill for systematically building a verifiable, source-tagged Chinese knowledge base for any clinical specialty: textbooks, Chinese and international guidelines, board exam topics, imaging atlases, and a weekly scan of top specialty and general medical journals.

The skill text itself is in Chinese: [`skills/clinical-specialty-knowledge-base/SKILL.md`](skills/clinical-specialty-knowledge-base/SKILL.md). It is written for Chinese clinicians. The agent studies and files notes; it does not quiz the user unless asked.

## What the skill does

Point the agent at one specialty (ophthalmology, cardiology, pediatrics, and so on). It builds a layered Chinese knowledge base in eight steps:

1. **Textbook skeleton.** Confirm the current editions by web search (title, editors, publisher, year, ISBN, public table of contents): the latest five-year and eight-year national planning textbooks, residency or specialty texts, plus one to three international references. Split the main textbook into chapters.
2. **Textbook notes.** Work in rounds of a few chapters. For each disease, write definition, presentation, workup, diagnosis and differential, treatment principles, and red flags, in the agent's own words.
3. **Guidelines.** For each disease group, list Chinese Medical Association and National Health Commission guidance alongside major international society guidelines. Record name, organization, year or version, journal citation, and link; note key recommendations, follow-up, and places where Chinese and international advice differ; fold the points back into the chapter notes.
4. **Board and promotion exams.** Cover residency completion, attending, and senior (associate and full) levels: subjects, question types, counts, time limits, and pass marks, with provincial differences taken from official notices. From public pages that need no login, extract topics and outline only. Original practice cases are labeled as self-written.
5. **Tests and imaging.** List the specialty's main investigations and standard atlases. For each, cover normal findings, principle and indications, a reading sequence, a sign table (disease, typical signs, differentials, easy misreads), and artifacts. Draw on public image libraries, open-access reviews, and imaging consensus statements.
6. **Verification pass.** Look up every unchecked claim and compare it with the source when one exists. Apply the source tags below.
7. **Self-check.** List files and line counts. Topic files should run about 80–100 lines or more. Refresh the knowledge-base README status and changelog.
8. **Weekly literature scan.** After the base exists, keep a standing weekly pass. Search every journal on the required list (top specialty journals, plus general and high-impact journals for papers in that specialty), then Chinese core journals, society news, new guidelines, and NMPA, FDA, and EMA approvals. Prefer trials, meta-analyses, guidelines, large cohorts, and regulatory decisions. File 5–10 papers with title, journal, date, DOI or PMID, design, a paraphrase of the conclusion, and whether practice should change. Record “nothing relevant this week” when a required journal has no hit.

Textbook, guideline, exam, imaging, and literature tracks live in separate directories and can proceed in parallel. Each track finishes a round, then works its own unchecked list.

## Directory layout

The agent writes the knowledge base at `<specialty>-knowledge/` in the workspace:

```
<specialty>-knowledge/
├── README.md                  # textbook list, index with ✅/⏳, changelog
├── 00-curriculum.md           # chapter route, priorities, must-know emergencies
├── 01-…NN-*.md                # chapter notes
├── NN-drug-quickref.md        # drug quick reference, including China approval
├── guidelines/
│   ├── INDEX.md               # disease × Chinese guideline × international guideline
│   └── <disease-group>.md
├── exams/
│   ├── INDEX.md
│   ├── residency-completion.md
│   ├── attending.md
│   ├── senior.md
│   └── case-bank.md
├── imaging/                   # or diagnostics/
│   ├── INDEX.md
│   └── <modality>.md
└── literature/
    ├── INDEX.md               # weekly index
    ├── journals.md            # required journals
    └── YYYY-Www.md            # one file per ISO week
```

## Source tags

Every claim carries one of these marks:

| Tag | Meaning |
| --- | --- |
| ✓ | Checked against the original source |
| ✓（名称） | Only the name, or the fact that the item exists, was checked |
| 〔知〕 | Written from the agent's existing knowledge, not yet checked against a source |
| 「待核」 | Looked for and not found, or still unchecked |

Before answering a clinical question, the agent searches the knowledge base and prefers ✓ material. If it cites 〔知〕 or 「待核」 content, it says so.

## Copyright and no fabrication

- Book titles, guideline names, years, recommendation grades, numbers, and exam figures are recorded only when found. Anything uncertain stays 「待核」.
- Papers, DOIs, and results are recorded only when found. A note read from the abstract alone is marked as abstract-only.
- The agent does not sign in, bypass paywalls, or bulk-copy copyrighted textbooks, atlases, or question banks. A PDF or screenshot the user supplies may be read, then paraphrased.
- Exam material from public pages is limited to topics and structure. Original items, real papers, and recalled papers are not copied. Practice cases the agent writes are labeled 「自编练习题」.
- Drug names are generic names, with China approval status noted.

## How to use

Give the skill to any agent that loads skills from a `SKILL.md` file. Copy `skills/clinical-specialty-knowledge-base/` into that agent's skills directory (for Cursor, a project `.cursor/skills/` folder or the user skills folder), or point the agent at `skills/clinical-specialty-knowledge-base/SKILL.md` directly. Then ask it to build the knowledge base for a named specialty.

## Disclaimer

This skill is an educational aid for organizing study notes. It is not medical advice, not a clinical decision tool, and not a substitute for current guidelines, local protocols, or a licensed clinician.
