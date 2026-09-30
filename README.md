# Alliander RFP – Schakellokalen: solution workspace

This folder is the **solution-shaping workspace** for the Alliander tender. Solution work (architecture, approach, answers to the quality criteria, question lists) is done here.

The tender documents themselves are **not copied here**. They stay in OneDrive and are reached through a folder link.

**Repo:** https://github.com/stevemarksava/RFP-Alliander-Response (private). The repo mirrors the OneDrive folder structure for solution work. `onedrive/` is gitignored, so no tender documents are ever committed.

## Status (2026-09-30)

| Step | Status |
|---|---|
| Tender hardware recon (Athanasios) | Done and corrected. Internal only: don't send to the partner |
| Hardware BRD (HVE `@brd-builder`) | Corrected draft, md and Word, Vera-approved; Word copy in OneDrive `4. Solution/Hardware Solution/` |
| Solution overview + architecture diagram | Draft, one consolidated md/docx/drawio set in `4. Solution/Solution Overview/`; all 7 architecture layers now have content. Network protocol choice and data retention policy still open |
| Bob review | Pending |
| Kryptonite review | Pending |

The Word version is generated from the markdown: `python tools/md_to_docx.py "4. Solution/Hardware Solution/alliander-schakellokalen-hardware-brd.md" "4. Solution/Hardware Solution/alliander-schakellokalen-hardware-brd.docx"`. Edit the markdown, not the Word file. The same script converts `4. Solution/Solution Overview/solution-overview.md`.

Open item: the Zevenaar site survey. The BRD's assumptions about that site depend on it.

## Tender

- **Client:** Alliander N.V.
- **Tender:** *Digitale aansturing van oefenomgevingen voor technische opleidingen* (digital control of training environments for technical training, the "Schakellokalen")
- **Platform:** Mercell (export dated 2026-09-10)
- **Round 1 (NvI 1, clarification questions):** deadline was 23 Sep 2026, 10:00

## Where the source documents are

| What | Path |
|---|---|
| OneDrive master folder | `C:\Users\s.marks\OneDrive - Avanade\Alliander - RFP Schakellokalen` |
| Link inside this folder | [onedrive/](onedrive/) |

`onedrive/` is a Windows **directory junction**. It points at the OneDrive folder, so:

- files always match OneDrive, and nothing is duplicated
- edits made through `onedrive/` change the real OneDrive files
- deleting *contents* through `onedrive/` deletes them from OneDrive. To remove only the link, delete the `onedrive` entry itself (`Remove-Item .\onedrive` without `-Recurse`)

Recreate the link if it is missing (no admin rights needed):

```powershell
New-Item -ItemType Junction -Path "C:\dev\Avanade\rfp-alliander\onedrive" -Target "C:\Users\s.marks\OneDrive - Avanade\Alliander - RFP Schakellokalen"
```

Some OneDrive files are online-only. If a tool can't read a file ("cloud operation is invalid"), right-click the OneDrive folder and choose **Always keep on this device**.

## OneDrive folder structure

| Folder | Contents |
|---|---|
| `1. Received from customer (do not change)` | Mercell export: tender guide (Aanbestedingsleidraad), appendices, criteria, pricing sheet. **Read-only.** |
| `2. Sent to Client (do not change)` | Everything submitted to Alliander. **Read-only.** |
| `3. Bidmanagement` | Bid planning and admin |
| `4. Solution` | Solution material, including `Hardware Solution` (hardware BRD) |
| `Vragen NvI 1 (23 sep 10 uur)` | Round 1 clarification questions (at the OneDrive root) |
| `5. Relevant information` | Background, MVO document, previous Avanade proposals to Alliander |
| `6. Orals` | Oral presentation preparation |

The OneDrive folder also contains a `.venv` and `.vscode` folder. These are tooling, not bid documents.

## Key documents

Paths are relative to `onedrive/1. Received from customer (do not change)/Mercell-Export-20260910/1. Gunningsfase/1. Offerteaanvraag/` unless stated.

| Document | Location |
|---|---|
| Tender guide | `3. Aanbestedingsleidraad en bijlagen/Aanbestedingsleidraad - Digitale aansturing van oefenomgevingen voor technische opleidingen(18224691).pdf` |
| Purchasing and invoicing terms (Bijlage A, B) | `3. Aanbestedingsleidraad en bijlagen/` |
| Procedure rules, planning, checklist (Bijlage C, D, E) | `3. Aanbestedingsleidraad en bijlagen/` |
| Core scenarios (Bijlage T) | `3. Aanbestedingsleidraad en bijlagen/Bijlage T - Kernscenario's(18224716).pdf` |
| Exclusion grounds, suitability and minimum requirements | `4. Uitsluitingsgronden, geschiktheidseisen en mi._/` |
| Quality award criteria (Bijlage N) | `5. Kwaliteitscriteria/` |
| Pricing sheet (Bijlage J) | `6. Prijs/Bijlage J - Prijzenblad(18224795).xlsx` |
| NvI 1 legal question matrix | `onedrive/Vragen NvI 1 (23 sep 10 uur)/Alliander_NvI1_Juridische_Vragenmatrix.xlsx` |
| Previous Avanade ROM proposal (2025) | `onedrive/5. Relevant information/Previous Ava offers to Alliander/Alliander - Digital Schakkellokalen - ROM Proposal v1.2 2025.pdf` |
| Previous requirements document | `onedrive/5. Relevant information/Previous Ava offers to Alliander/Alliander - Schakellokaal requirements.pdf.pdf` |
| MVO (social responsibility, 5% weighting) | `onedrive/5. Relevant information/Maatschappelijk verantwoord ondernemen 5%.docx` |

## Workspace layout

| Path | Purpose |
|---|---|
| `4. Solution/Hardware Solution/` | Hardware BRD for the IoT partner (md and Word, written by HVE `@brd-builder`) |
| `4. Solution/Hardware Solution/recon/` | Athanasios's English recon of the hardware-relevant tender requirements, with RFP references |
| `4. Solution/Hardware Solution/prompts/` | Prompts to paste into `@brd-builder` |
| `tools/md_to_docx.py` | Converts a markdown BRD to Word |
| `.squad/decisions/` | Decision log |

## Working rules

- Never edit anything in `1. Received from customer` or `2. Sent to Client`.
- Solution work goes in this folder (outside `onedrive/`), in the folder matching OneDrive (for example `4. Solution/Hardware Solution/`). Copy finished Word versions to the same folder in OneDrive when they're ready to share with the bid team.
- Don't copy tender documents into this folder. Read them through `onedrive/`.
