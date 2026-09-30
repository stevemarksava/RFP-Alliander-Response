# Hardware Partner Capability Profile — Digital Schakellokalen (Tender 226705)

**Purpose:** Extract the complete capability profile an IoT hardware partner must meet for the Avanade/Alliander bid, from the four core workspace documents.
**Convention:** [DOC] = verbatim or close paraphrase of a document statement. [INTERP] = this researcher's interpretation/inference, not stated directly in a document. This matches the convention already used in tender-hardware-recon.md.

**Sources read in full:**
- 4. Solution/Hardware Solution/alliander-schakellokalen-hardware-brd.md (182 lines to end of Open Questions section)
- 4. Solution/Hardware Solution/recon/tender-hardware-recon.md (418 lines, includes §8 Gaps and Ambiguities)
- 4. Solution/Solution Overview/solution-overview.md (177 lines)
- README.md (95 lines)

---

## 1. Exact Scope the Hardware Partner Must Deliver (Layers 1-3)

The solution is modelled as six layers; the hardware partner's mandate is layers 1-3 only. Layers 4-6 are Avanade/Alliander's responsibility. [DOC] alliander-schakellokalen-hardware-brd.md:51-62, :47 ("Layers 1 through 3 are the hardware partner's mandate; layers 4 through 6 are how Avanade and Alliander extend value...")

### Layer 1 — Physical (pre-existing, not supplied)
- Existing training switchgear: MV/HV panels, ring main units, disconnectors, breakers, earthing switches, transformers, busbars; plus LV distribution boards, meter cabinets, street-lighting circuits. [DOC] alliander-schakellokalen-hardware-brd.md:53
- "This equipment already exists and is out of the hardware partner's supply scope; the partner instruments it." [DOC] alliander-schakellokalen-hardware-brd.md:53

### Layer 2 — Instrument (sensing and actuation added to physical assets)
- Switch position/state sensing, current/voltage signal capture, RFID/NFC identification on components or trainees, indicator and interlock monitoring, controlled fault injection at the instrumentation level. [DOC] alliander-schakellokalen-hardware-brd.md:54
- Solution Overview confirms: "sensors, relays, I/O modules, RFID/NFC, fault-injection points." [DOC] solution-overview.md (Solution Architecture diagram, Layer 2 box, lines 47-85)

### Layer 3 — Connect (edge)
- On-site IoT gateway and industrial network linking instrumentation to a training-scenario engine, including the critical on-site edge server backed by UPS. [DOC] alliander-schakellokalen-hardware-brd.md:55
- Tender requirement: keep working during *temporary* internet outage [Bijlage L PERF-05]; Avanade's design choice goes further — fully offline-capable edge operation with sync to cloud only when connectivity returns. [DOC] alliander-schakellokalen-hardware-brd.md:55, :149-151

### In-scope deliverables (explicit list)
[DOC] alliander-schakellokalen-hardware-brd.md:66-72 ("In Scope for the Hardware Partner"):
- Solution-specific hardware: relays, I/O boards, cabling, comparable control technology, smart cables, sensors, switches [Aanbestedingsleidraad §1.5.4; Bijlage L HW-01]
- Instrumentation and retrofit work on existing MV, LV, meterkast, and street-lighting (FlexOV) assets across Haarlem and Zevenaar's schakellokalen and meetvelden [Bijlage T scenario groups]
- On-site edge compute, industrial networking, power/UPS hardware for local scenario execution with resilience to temporary internet loss [Bijlage L PERF-05]
- Preventive maintenance, calibration, spares, firmware/patch management, support across the 3-year base term + up to 5 one-year extensions [Aanbestedingsleidraad §1.2, §1.4]
- A complete hardware manifest: quantities, technical specs, warranty periods, expected lifespan, maintenance/replacement requirements [Bijlage L HW-02]

The recon document independently confirms the same in-scope list, sourced directly from the tender guide: "Solution-specific hardware required for the solution to function: relays, I/O boards, cabling, comparable control technology; smart cables, sensors, switches" plus "Integration with physical training assets," "System management and maintenance." [DOC] tender-hardware-recon.md:47-51 (§2, citing Aanbestedingsleidraad §1.5.4)

### Out-of-scope deliverables (explicit list)
[DOC] alliander-schakellokalen-hardware-brd.md:74-80 ("Out of Scope for the Hardware Partner"):
- Design and physical construction of the training environments (buildings/rooms) [Aanbestedingsleidraad §1.5.5]
- Delivery and setup of general measurement equipment (meetapparatuur) used by trainees; "the solution observes and controls the scenario, it does not read the measuring equipment itself" [Bijlage L MV-04]
- Generic physical infrastructure: standard cabling, power supplies, switchrooms as physical spaces [Aanbestedingsleidraad §1.5.5]
- Development of training content or didactic learning lines [Aanbestedingsleidraad §1.5.5]
- Replacement of the Archipel system (separate tender) [Aanbestedingsleidraad §1.5.5]

Recon confirms the identical out-of-scope list at tender-hardware-recon.md:53-58 (§2), and restates it as SCOPE-04/MV-04 knock-out-adjacent requirements at tender-hardware-recon.md:197-199 ("Clear boundary between digital layer (supplier) and physical installations (Alliander)").

### Scope boundary table (Solution Overview)
[DOC] solution-overview.md:163-168 ("Scope Boundary"):
| Layers | Scope owner | Operates |
|---|---|---|
| 1-3 (Physical, Instrument, Connect) | Hardware partner | Fully offline-capable, on-site |
| 4-6 (Digital Twin, AI & Agentic, Experience) | Avanade/Alliander | Cloud, EEA-hosted, async sync from edge |

---

## 2. Hard Constraints / Knock-Out (KO) Requirements Relevant to Hardware

All of the following are "Eis" (mandatory) in Bijlage L terminology; failure disqualifies the bid. IDs below are Bijlage L's own requirement IDs as extracted in the recon document.

| ID | Requirement (paraphrased) | Source location |
|---|---|---|
| **SAFE-01** | Fail-safe design: on malfunction, power failure, or communication loss, solution automatically reverts to a predefined safe state — active scenarios terminated, outputs placed safe, physical safety provisions remain functional. Marked "HARDWARE KNOCK-OUT" by the recon author. | [DOC] tender-hardware-recon.md:204, verbatim Dutch+English at :331-333; also alliander-schakellokalen-hardware-brd.md:93 (BR-004), :122 (BR-027), :149-151 |
| **SAFE-02** | Physical safety systems function independently of the digital solution; digital layer must NOT override/disable/bypass existing safety provisions, e-stops, disconnections, interlocks; failure of digital layer must not cause physical safety measures to fail. Marked "HARDWARE KNOCK-OUT." | [DOC] tender-hardware-recon.md:205, verbatim Dutch+English at :335-337; also alliander-schakellokalen-hardware-brd.md:103 (BR-010), :107 (BR-014), :150 |
| SAFE-03 | Solution presents no physical safety risk to trainers/participants; demonstrable via risk assessment | [DOC] tender-hardware-recon.md:206 |
| SAFE-04 | Solution must visually/physically distinguish training mode from safe rest state | [DOC] tender-hardware-recon.md:207 |
| PERF-05 | Solution functions when internet connection is temporarily unavailable (e.g. via local scenario execution) — note recon's own correction: this is resilience to *temporary* outage, not a permanent offline-only mandate; Avanade's fully-offline design exceeds it | [DOC] tender-hardware-recon.md:212, :159-160 (HW-04 row with correction note) |
| PERF-03 | Minimum 99% availability during training hours, defined in SLA | [DOC] tender-hardware-recon.md:210 |
| PERF-04 | Proven fallback scenarios maintain training continuity on failure; tested at acceptance | [DOC] tender-hardware-recon.md:211 |
| IT-03 | Data stored exclusively within the EEA; storage outside EEA not permitted | [DOC] tender-hardware-recon.md:208 |
| IT-04 | Data traffic encrypted to minimum TLS 1.2, preferred TLS 1.3 | [DOC] tender-hardware-recon.md:209 |
| LCD11 | Full inventory of all datacentres/cloud regions/storage services required, incl. physical country and role (prod/test/backup); EEA-only | [DOC] tender-hardware-recon.md:218, verbatim Dutch+English at :383-394 |
| LCD19 | Supplier must hold valid ISO 27001 (2022/2023) certification within scope of services delivered, or SOC 2 Type II equivalent | [DOC] tender-hardware-recon.md:219 |
| LCD08 | Only actively vendor-supported hardware/software may be used; contract must state explicit end-of-support dates for every component | [DOC] tender-hardware-recon.md:217 |
| ITAR-03 | Hardware control architecturally isolated from business logic via standardised interfaces; hardware-specific protocols/drivers confined to integration layer, ensuring hardware replaceability | [DOC] tender-hardware-recon.md:213 |
| ITAR-06 | Architecture must support a central digital network model (Digital Twin) as authoritative representation | [DOC] tender-hardware-recon.md:214 |
| SL-04 | Solution supports up to 4 simultaneous participants within one configuration | [DOC] tender-hardware-recon.md:202 |
| MV-04 | Participants use existing measuring equipment; solution does NOT read that equipment itself | [DOC] tender-hardware-recon.md:203 |
| IF-06 | Interfacing designed so coupling new/modified physical assets is possible without redesigning the solution | [DOC] tender-hardware-recon.md:198 |
| IMP-03 | Implementation starts with a pilot/PoC on a representative training environment before broad rollout | [DOC] tender-hardware-recon.md:215 |
| ACC-03 | Formal acceptance requires successful demonstration of all Bijlage T core scenarios | [DOC] tender-hardware-recon.md:216 |
| IAM knock-out | "If a minimum security level A for both IGA and AM cannot be met, knock-out follows." | [DOC] tender-hardware-recon.md:355-356, verbatim Dutch quoted |
| — AM (level A) | OIDC/OAuth 2.0 + Authorization Code + PKCE S256 preferred; SAML 2.0 fallback acceptable. Implicit Flow, ROPC, Basic Auth, NTLM, and any local password database explicitly prohibited. | [DOC] tender-hardware-recon.md:358-363 (§7.2); alliander-schakellokalen-hardware-brd.md:121 (BR-026), :153 |
| — IGA (level A) | SailPoint connector preferred; SCIM 2.0 acceptable; manual provisioning not acceptable above level A; authentication events exportable to Alliander SIEM | [DOC] tender-hardware-recon.md:365-370 |
| ISO 9001 | Supplier must demonstrably hold ISO 9001 or equivalent certified QMS | [DOC] tender-hardware-recon.md:375-377 (verbatim Dutch quoted), Aanbestedingsleidraad §4.1 |
| ISO 27001 | Supplier must demonstrably hold ISO 27001 or equivalent certified ISMS | [DOC] tender-hardware-recon.md:379-381 (verbatim Dutch quoted), Aanbestedingsleidraad §4.1 |
| NEN 3140 / NEN-EN 50110 | Training environment must comply with these electrical-safety standards wherever live or simulated-live components are involved | [DOC] tender-hardware-recon.md:327-329 (verbatim Dutch quoted); alliander-schakellokalen-hardware-brd.md:109 (BR-016) |
| GC1/GC2/GC3 = 0 | Scoring 0 on any quality criterion results in outright disqualification from award | [DOC] tender-hardware-recon.md, HW-32 row (§4 table) |

**Applies to hardware specifically:** SAFE-01 and SAFE-02 are described by the recon author as "the highest-consequence hardware requirements in the document" [INTERP-flagged in source itself] — tender-hardware-recon.md:339. Every relay board, I/O module, edge controller, and power supply must default to a safe state on power/communication loss, and no edge device or reader with a login interface may hold a local credential store (this directly implicates RFID/NFC readers and instructor control panels). [DOC/INTERP mix] tender-hardware-recon.md:371-372.

---

## 3. Commercial/Pricing Structure Implications (Bijlage J)

Source: tender-hardware-recon.md §2, "Bijlage J — Pricing Structure Implications for Hardware Scope" (lines ~70-96).

**One-time implementation cost lines** [DOC]:
- "Levering van Hardware" — hardware delivery (one-time)
- "Aansluiten van hardwarecomponenten" — connecting/installing hardware components (one-time)
- Software development lines (back-end, front-end, UX/visual/technical/functional design, information/data analysis, software testing) — not hardware, listed for context
- Project management: integration tests, project management

**Annual recurring cost lines** (Licentie- en optionele kosten sheet) [DOC]:
- "Basislicentie oplossing" — base solution licence (annual)
- "Functioneel beheer en support" — functional management and support (annual)
- "Technisch beheer en support" — technical management and support (annual)
- "Updates en nieuwe releases" — updates and new releases (annual)
- "Overige licentiekosten" — other licence costs (annual)
- Optional: hourly advisory rate (budgeted at 160 hours)

**Pricing rules** [DOC]:
- All prices are all-in; no additional costs for extras, travel, or accommodation accepted
- All costs the bidder intends to charge must be on the pricing sheet
- Conditional discounts not accepted; net prices only
- If the pricing sheet lacks a necessary line item, the bidder must raise it before the questions deadline

**Hardware partner implications** [INTERP, stated as such in recon]: "Hardware supply and installation are distinct, separately priced line items. Ongoing hardware maintenance/replacement falls under 'Technisch beheer en support' (annual). There is no separate annual hardware maintenance line item — it is embedded in managed service. The hardware partner's commercial model must map to: (1) one-time delivery cost, (2) one-time installation cost, (3) an element of the annual technical support fee. The all-in pricing rule means the bid must include hardware costs for all 4 environments with no ability to add costs later." — tender-hardware-recon.md (§2, final paragraph)

**Contract value context** [DOC]: estimated contract value EUR 3,040,000 over maximum 8 years; award method BPKV (Beste Prijs-Kwaliteitsverhouding), Quality 70% / Price 30%, MVO 5% of overall score. tender-hardware-recon.md:32-44 (§2 table).

---

## 4. Named Technology Preferences / Protocol Hints (Indicative Only)

The BRD explicitly states: "Any device-specific detail in this BRD is indicative only. The partner's proposal, validated against a joint site survey, determines the final hardware selection." [DOC] alliander-schakellokalen-hardware-brd.md (Executive Summary, line ~13). The Solution Overview repeats this caveat for the network layer: "Protocol names below (OPC-UA, Modbus, MQTT) are an Avanade design assumption... They are **not specified or confirmed anywhere in the tender documents** and must be validated against the hardware partner's proposal and the site survey before being stated as fact in a submission." [DOC] solution-overview.md:122-124.

Despite the "indicative only" framing, the following technology signals appear in the documents and indicate architecture direction:

- **Industrial protocols:** OPC-UA and/or Modbus for switchgear I/O, MQTT for event/telemetry publishing, isolated from Alliander's corporate IT network. [DOC/assumption] alliander-schakellokalen-hardware-brd.md:92 (BR-003); solution-overview.md:126-129 (Network Architecture)
- **Edge compute:** on-site IoT gateway/edge server, UPS-backed, running the full scenario engine locally/offline. [DOC] alliander-schakellokalen-hardware-brd.md:55, :91 (BR-002)
- **Identity/RFID/NFC:** trainee/instructor identification hardware "such as an RFID or NFC reader, compatible with Alliander's existing credential format, to be confirmed via site survey." [DOC] alliander-schakellokalen-hardware-brd.md:95 (BR-006); origin in 2023 Avanade requirements doc per tender-hardware-recon.md:409 (G-05)
- **Vision-based/camera validation:** "optional visual or camera hardware to support supervision or future learning-data capture, subject to confirmation this is in scope" and "visual or vision-based capture at the instrumentation layer to support future AI-based step validation" — both marked Could/open question. [DOC] alliander-schakellokalen-hardware-brd.md:96 (BR-007), :125 (BR-030)
- **Identity federation protocols (security, not OT):** OIDC/OAuth 2.0 with PKCE preferred, SAML 2.0 acceptable; SailPoint connector preferred, SCIM 2.0 acceptable. [DOC] alliander-schakellokalen-hardware-brd.md:121 (BR-026); tender-hardware-recon.md:358-370
- **Operating voltage assumption:** 20-50 V DC for instrumentation, carried from the 2023 requirements doc and 2025 ROM proposal, explicitly "not confirmed in the tender itself and must be validated against the actual switchgear." [DOC] alliander-schakellokalen-hardware-brd.md (Non-Functional Requirements section, ~line 163); solution-overview.md (Hardware Architecture, design constraints bullet)
- **Named equipment types (indicative, not a BOM):** ABB SafeRing/SafePlus MV ring main units, WEGA 1.2C voltage-detection units, SVS switches, SF-6 gas-insulated components, kWh meters, MSR fuses, CAM connectors, FlexOV street-lighting relays/modems. [DOC] alliander-schakellokalen-hardware-brd.md (final Open Questions bullet, ~line 198): "All device names in this document... are indicative references drawn from prior Avanade site visits and the tender's own scenario descriptions, not a prescribed bill of materials."

---

## 5. Maintenance / Lifecycle Expectations

- **Contract term:** 3-year base term + up to 5 x 1-year extensions = maximum 8 years. [DOC] alliander-schakellokalen-hardware-brd.md (Stakeholders table, "8-year contract term"); tender-hardware-recon.md:39 ("Contract duration | 3 years + 5 x 1-year extension options = max 8 years")
- **Contract start:** 1 February 2027. [DOC] tender-hardware-recon.md:41
- **Preventive maintenance and calibration:** required "for all instrumentation and edge hardware across the full contract term, up to 8 years." [DOC] alliander-schakellokalen-hardware-brd.md:131 (BR-040)
- **Hardware manifest:** complete documentation of quantities, technical specs, warranty periods, expected lifespan, maintenance/replacement requirements for every delivered component. [DOC] alliander-schakellokalen-hardware-brd.md:132 (BR-041); Bijlage L HW-02
- **Firmware/patch/lifecycle management:** required for all hardware and embedded software, with explicit end-of-support dates communicated. [DOC] alliander-schakellokalen-hardware-brd.md:133 (BR-042); Bijlage L LCD08 — "Only hardware and software receiving active vendor support may be used... contract must explicitly state until when support is provided for all hardware and software components." tender-hardware-recon.md:217
- **Spares/RMA:** sized to sustain required in-service availability (99% during training hours). [DOC] alliander-schakellokalen-hardware-brd.md:134 (BR-043); tender-hardware-recon.md:210 (PERF-03)
- **End-of-life/replacement planning:** should be aligned to the maximum 8-year term (Should-priority, not Must). [DOC] alliander-schakellokalen-hardware-brd.md:135 (BR-044)
- **Circular/sustainable sourcing:** offered in support of MVO (social responsibility, 5% of score) — marked Could/open question since the MVO source document was not yet reviewed. [DOC] alliander-schakellokalen-hardware-brd.md:136 (BR-045); tender-hardware-recon.md:418 (G-14)
- **Support/SLA:** minimum 99% availability during training hours, SLA KPIs to be proposed/agreed (Bijlage Q is a blank template — no values pre-defined). [DOC] alliander-schakellokalen-hardware-brd.md:142 (BR-050); tender-hardware-recon.md:416 (G-12)
- **Incident response:** hardware faults must be escalated distinctly from software/platform faults. [DOC] alliander-schakellokalen-hardware-brd.md:143 (BR-051)
- **Fallback procedure:** tested as part of formal acceptance, maintains training continuity on failure. [DOC] alliander-schakellokalen-hardware-brd.md:144 (BR-052); Bijlage L PERF-04
- **Pilot/PoC:** required on one representative training environment before broad rollout to Haarlem, Zevenaar, and future sites (Must/KO — IMP-03). [DOC] alliander-schakellokalen-hardware-brd.md:146 (BR-054)
- **Scalability to future sites:** "Additional training environments may be added under the framework during the contract term" — explicitly a live requirement. Hardware architecture and spares model must absorb additions "without redesign." [DOC] tender-hardware-recon.md:43 (Aanbestedingsleidraad §1.3); alliander-schakellokalen-hardware-brd.md (Business Objectives table, "Scale beyond the initial four environments" row, referencing Aanbestedingsleidraad §1.3 and Bijlage N GC2)
- **Initial scope:** 4 environments — 1 schakellokaal + 1 meetveld in Haarlem, 1 schakellokaal + 1 meetveld in Zevenaar. [DOC] tender-hardware-recon.md:42-45

---

## 6. Gaps / Open Questions Blocking a Complete Capability Profile

Both the BRD's own "Open Questions and Assumptions" section and the recon's "§8 Gaps and Ambiguities" table enumerate unresolved items. Cross-referenced list below; recon's gap IDs (G-xx) shown where applicable.

| Gap | Detail | Status/priority | Source |
|---|---|---|---|
| Joint site survey requirement | The BRD states repeatedly that device-specific details are "indicative only" and that "the partner's proposal, validated against a joint site survey, determines the final hardware selection" — confirming a joint site survey **is** required before final hardware selection, though not yet scheduled/dated for Zevenaar. | Open — survey not yet conducted for Zevenaar per README | [DOC] alliander-schakellokalen-hardware-brd.md (Executive Summary, ~line 13; Open Questions intro, ~line 184); README.md:15 ("Open item: the Zevenaar site survey. The BRD's assumptions about that site depend on it.") |
| Zevenaar layout/switchgear inventory unknown | Only Haarlem has documented floor plans and equipment photos (2023 visit); Zevenaar is fully undocumented — room count, dimensions, switchgear inventory. | HIGH (G-03) | [DOC] tender-hardware-recon.md:407; alliander-schakellokalen-hardware-brd.md (Open Questions, first bullet) |
| Meetveld (measurement field) scope unclear | Bijlage T's 31 core scenarios all appear to address schakellokaal-type switchgear; whether meetveld needs its own digital control hardware, and what equipment it contains, is not stated. | HIGH (G-04) | [DOC] tender-hardware-recon.md:408; alliander-schakellokalen-hardware-brd.md (Open Questions, 2nd bullet) |
| Trainee/instructor identification mechanism undefined | BRD assumes RFID/NFC compatible with an existing Alliander badge format, but this is "not confirmed in the tender documents." | HIGH (G-05) | [DOC] tender-hardware-recon.md:409; alliander-schakellokalen-hardware-brd.md (Open Questions, 3rd bullet; BR-006) |
| Instrumentation operating voltage unconfirmed | Assumed 20-50 V DC from 2023 doc/2025 ROM; "not confirmed in the tender itself and must be validated against the actual switchgear." | HIGH (G-06) | [DOC] tender-hardware-recon.md:410; alliander-schakellokalen-hardware-brd.md (Open Questions, 4th bullet) |
| SF-6 simulation method unspecified | P2-MS-05 requires simulating gas-pressure gauge state without manipulating real SF-6 equipment; the tender describes the scenario outcome, not the method; safety risk of proximity to real SF-6 equipment must be addressed in the risk analysis. | HIGH (G-07) | [DOC] tender-hardware-recon.md:411; alliander-schakellokalen-hardware-brd.md (Open Questions, 5th bullet) |
| WEGA/SVS electrical interface specs not published | Voltage levels, signal types, protocols for WEGA and SVS units must be obtained on site or from the manufacturer. | MEDIUM (G-08) | [DOC] tender-hardware-recon.md:412; alliander-schakellokalen-hardware-brd.md (Open Questions, 6th bullet) |
| Archipel coexistence/transition scope | Unclear whether the new platform must exchange data with or coexist alongside Archipel (being replaced under a separate tender) during a transition period. | MEDIUM (G-10) | [DOC] tender-hardware-recon.md:414; alliander-schakellokalen-hardware-brd.md (Open Questions, 7th bullet) |
| Camera/visual-monitoring scope unresolved | 2023 Avanade document raised cameras as desired; current tender documents do not reference cameras at all. | MEDIUM (G-11) | [DOC] tender-hardware-recon.md:415; alliander-schakellokalen-hardware-brd.md (Open Questions, 8th bullet; BR-007, BR-030) |
| SLA KPI targets undefined | Bijlage Q is a blank template; no availability/response-time/replacement SLA targets are defined — partner's actual support capability should inform what Avanade proposes. | MEDIUM (G-12) | [DOC] tender-hardware-recon.md:416; alliander-schakellokalen-hardware-brd.md (Open Questions, 9th bullet) |
| Scalability not quantified | Number and timeline of additional training environments under the framework is not stated, affecting spares sizing and bulk pricing. | LOW (G-13) | [DOC] tender-hardware-recon.md:417; alliander-schakellokalen-hardware-brd.md (Open Questions, 10th bullet) |
| MVO/circular hardware requirements unconfirmed | Whether circular sourcing, repairability, or end-of-life requirements apply under Alliander's MVO scoring criterion (5% of score) is unknown; source document not yet reviewed. | LOW (G-14) | [DOC] tender-hardware-recon.md:418; alliander-schakellokalen-hardware-brd.md (Open Questions, 11th bullet) |

**Deferred explicitly to the partner's own proposal** [DOC]: "Any device-specific detail in this BRD is indicative only. The partner's proposal, validated against a joint site survey, determines the final hardware selection." — alliander-schakellokalen-hardware-brd.md Executive Summary. The closing Open Questions bullet reiterates this for all named device models (ABB SafeRing/SafePlus, WEGA, SVS, FlexOV, CAM, MSR): "not a prescribed bill of materials. The partner's proposal, validated against a joint site survey and the final RFP text, determines the actual hardware selection." — alliander-schakellokalen-hardware-brd.md (final line of file).

**Solution Overview's own open items** (network/architecture level, not yet finalized) [DOC] solution-overview.md:170-175 ("Next Steps"):
- Business, Enterprise, and Data architecture sections are still placeholders (no content yet) — GC1/GC2 scoring depends on a complete architecture package.
- Network architecture's protocol assumptions (OPC-UA/Modbus/MQTT) must be confirmed with the hardware partner and the Zevenaar/Haarlem site survey before being stated as fact in a submission.
- Whether device-specific references (ABB SafeRing, WEGA, SVS) should remain indicative-only in the submitted version needs bid-lead confirmation.
- Cross-check against the final RFP text once NvI 2 (if issued) closes any open questions.

**Closed gaps (for completeness, not open):** G-01 (Bijlage L unread) and G-02 (Bijlage J unread) are marked CLOSED in recon — both documents were subsequently extracted and incorporated. G-09 (EEA data residency) is marked CLOSED — confirmed via IT-03 and LCD11. [DOC] tender-hardware-recon.md:405-406, :413.

---

## Summary of Status Context (README)

- Tender hardware recon: done and corrected, internal-only (not for the partner). [DOC] README.md:11
- Hardware BRD: corrected draft, Vera-approved, Word copy exists in OneDrive. [DOC] README.md:12
- Solution overview + architecture diagram: draft; business, enterprise, and data architecture sections still placeholders. [DOC] README.md:13
- Bob review and Kryptonite review: both pending. [DOC] README.md:14
- NvI 1 (round-1 clarification questions) deadline already passed: 23 Sep 2026, 10:00. [DOC] README.md:28
