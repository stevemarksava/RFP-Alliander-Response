# Tender Hardware Reconnaissance
**Subject:** Digitale aansturing van oefenomgevingen voor technische opleidingen — Alliander N.V.
**Prepared by:** Athanasios (Superteam researcher)
**Date:** 2026-09-30 (revised same day — Bijlage L and Bijlage J incorporated)
**Purpose:** Primary input for Hardware BRD (`@brd-builder`). Accuracy over polish. Facts from documents are marked [DOC]; interpretation is marked [INTERP].

---

## 1. Sources Read / Not Read

| # | Document | Path (relative to `onedrive/`) | Status | Notes |
|---|---|---|---|---|
| 1 | Beschrijving.pdf | `1. Received from customer.../Mercell-Export-20260910/Beschrijving.pdf` | READ | 1-page tender overview |
| 2 | Planning.pdf | `1. Received from customer.../Mercell-Export-20260910/Planning.pdf` | READ | Full timeline |
| 3 | Aanbestedingsleidraad (18224691).pdf | `...3. Aanbestedingsleidraad en bijlagen/` | READ — full 14 pages | Most important document |
| 4 | Bijlage T — Kernscenario's (18224716).pdf | `...3. Aanbestedingsleidraad en bijlagen/` | READ — full 9 pages | 31 core training scenarios |
| 5 | Bijlage N — Gunningscriteria Kwaliteit (18224785).pdf | `...5. Kwaliteitscriteria/` | READ — full 7 pages | Award quality criteria |
| 6 | Bijlage Q — SLA (18224773).pdf | `...3. Aanbestedingsleidraad en bijlagen/` | READ — template only, no values filled | SLA framework |
| 7 | Bijlage V — IAM aansluitvoorwaarden (18224764).pdf | `...3. Aanbestedingsleidraad en bijlagen/` | READ — full | IAM knock-out requirements |
| 8 | Bijlage L — Programma van Eisen (18224760).xlsx | `...4. Uitsluitingsgronden, geschiktheidseisen en mi._/` | READ — extracted to text, 193 rows, 5 sheets | Sheets: Voorblad, Functionele eisen, Non-functionele eisen, Impl. + integratie + support, Eisen cloud provider. Full requirements now incorporated. |
| 9 | Bijlage J — Prijzenblad (18224795).xlsx | `...6. Prijs/` | READ — extracted to text, 62 rows, 4 sheets | Sheets: Instructie, Samenvatting, Licentie- en optionele kosten, Implementatiekosten. Pricing structure now incorporated. |
| 10 | Alliander — Schakellokaal requirements.pdf.pdf | `5. Relevant information/Previous Ava offers to Alliander/` | READ — Avanade material | 2023 requirements doc with floor plans and switchgear photos |
| 11 | Alliander — Digital Schakkellokalen — ROM Proposal v1.2 2025.pdf | `5. Relevant information/Previous Ava offers to Alliander/` | READ — full 33 pages, Avanade material | 2025 ROM proposal: architecture + hardware inventory |
| 12 | `onedrive/4. Solution/` | Solution folder | CHECKED — empty | Bid team has not yet written solution documents |
| 13 | Other bijlagen (A, B, C, D, E) | `...3. Aanbestedingsleidraad en bijlagen/` | NOT READ | Purchasing, invoicing, procedural rules — low hardware relevance |
| 14 | MVO document | `5. Relevant information/Maatschappelijk verantwoord ondernemen 5%.docx` | NOT READ | Social responsibility criteria — minimal hardware relevance |

All critical documents are now read. Bijlage L and Bijlage J were extracted from binary xlsx to text and incorporated in this revision.

---

## 2. Tender at a Glance

| Field | Value | Source |
|---|---|---|
| Client | Alliander N.V. | [DOC] Beschrijving.pdf |
| Tender title | Digitale aansturing van oefenomgevingen voor technische opleidingen | [DOC] Aanbestedingsleidraad |
| Tender number | 226705 (Mercell) | [DOC] Beschrijving.pdf |
| Procedure | European open procedure (Aanbestedingswet 2012, Boek 3, Art. 3.33) | [DOC] Aanbestedingsleidraad §1.1 |
| Contract type | Framework agreement (Raamovereenkomst), 1 contractor, no lots | [DOC] Aanbestedingsleidraad §1.2 |
| Contract duration | 3 years + 5 x 1-year extension options = max 8 years | [DOC] Aanbestedingsleidraad §1.2 |
| Contract start | 1 February 2027 | [DOC] Planning.pdf |
| Estimated contract value | EUR 3,040,000 over maximum 8 years (incl. VAT not specified) | [DOC] Aanbestedingsleidraad §1.2 |
| Award method | BPKV — Beste Prijs-Kwaliteitsverhouding (best price-quality ratio) | [DOC] Aanbestedingsleidraad §4.2 |
| Award weighting | Quality 70% / Price 30% | [DOC] Aanbestedingsleidraad §4.2 |
| MVO (social responsibility) | 5% of overall score | [DOC] Aanbestedingsleidraad §4.2 |
| NvI 1 deadline (clarification) | 23 September 2026, 10:00 | [DOC] Planning.pdf — PASSED |
| Submission deadline | 18 November 2026 | [DOC] Planning.pdf |
| Award decision | 6 January 2027 | [DOC] Planning.pdf |
| Initial scope — locations | 4 environments: 1 schakellokaal + 1 meetveld in Haarlem, 1 schakellokaal + 1 meetveld in Zevenaar | [DOC] Aanbestedingsleidraad §1.3 |
| Future scope | Additional training environments may be added under the framework during the contract term | [DOC] Aanbestedingsleidraad §1.3 |
| What the supplier delivers | Design, realise, implement, manage, maintain the digital control layer | [DOC] Aanbestedingsleidraad §1.4 |

**What is IN scope for the supplier** [DOC] Aanbestedingsleidraad §1.5.4:
- Solution-specific hardware required for the solution to function: relays, I/O boards, cabling, comparable control technology; smart cables, sensors, switches
- Software platform and applications
- Integration with physical training assets
- Cloud and/or on-premise infrastructure for the platform
- System management and maintenance

**What is OUT OF scope** [DOC] Aanbestedingsleidraad §1.5.5:
- Design and physical construction of training environments (schakellokalen, meetvelden)
- Delivery and setup of measurement equipment (meetapparatuur)
- Generic physical infrastructure: switchrooms, meetvelden, standard cabling and power supplies
- Development of training content or didactic learning lines
- Archipel system replacement (separate tender)

**Clarification from Bijlage L Voorblad [DOC]:** Alliander explicitly states it is not looking for a generic enterprise simulation platform. It wants a pragmatic, manageable digital control layer supporting physical training environments. Trainers must be able to manage scenarios independently without structural dependency on supplier development capacity.

### Bijlage J — Pricing Structure Implications for Hardware Scope

[DOC] Bijlage J — Implementatiekosten sheet. The pricing sheet has two main cost sections:

**One-time implementation costs** (separate line items, each bidder must price individually):
- "Levering van Hardware" — hardware delivery (one-time)
- "Aansluiten van hardwarecomponenten" — connecting/installing hardware components (one-time)
- Software development: Back-end, Front-end, UX Design, Visual Design, Technical Design, Functional Design, Information Analysis, Data Analysis, Software Testing
- Project management: integration tests, project management

**Annual recurring costs** (Licentie- en optionele kosten sheet):
- "Basislicentie oplossing" — base solution licence (annual)
- "Functioneel beheer en support" — functional management and support (annual)
- "Technisch beheer en support" — technical management and support (annual)
- "Updates en nieuwe releases" — updates and new releases (annual)
- "Overige licentiekosten" — other licence costs (annual)
- Optional: hourly advisory rate (budgeted at 160 hours)

**Pricing rules [DOC] Bijlage J §Instructie:**
- All prices are all-in; no additional costs for extras, travel, or accommodation accepted
- All costs the bidder intends to charge must be on the pricing sheet
- Conditional discounts not accepted; net prices only
- If the pricing sheet lacks a necessary line item, bidder must raise it before the questions deadline

**Hardware partner implications [INTERP]:** Hardware supply and installation are distinct, separately priced line items. Ongoing hardware maintenance/replacement falls under "Technisch beheer en support" (annual). There is no separate annual hardware maintenance line item — it is embedded in managed service. The hardware partner's commercial model must map to: (1) one-time delivery cost, (2) one-time installation cost, (3) an element of the annual technical support fee. The all-in pricing rule means the bid must include hardware costs for all 4 environments with no ability to add costs later.

---

## 3. Training Environment Facts

All facts below are from documents. Where the source is the 2023 Avanade document or 2025 ROM, that is marked as [AVANADE].

### Locations [DOC] Aanbestedingsleidraad §1.3
- **Haarlem** — 1 schakellokaal (switching room) + 1 meetveld (measurement field)
- **Zevenaar** — 1 schakellokaal + 1 meetveld
- Total initial scope: 4 environments across 2 sites
- Contract allows additional environments to be added during term (scalability is a live requirement, not hypothetical)

### Physical layout — Haarlem schakellokaal [AVANADE] 2023 requirements document
Floor plan and photographs show:
- Hoofdverdeelkast (main distribution cabinet) room
- Schakeelruimte center (central switching room)
- 1000 VA transformer room
- Traforuimte (transformer room)
- Cable selection wall
- Multiple exam/training booths (approximately 7.5–13.5 m² each)
- Rooms can be interconnected

[INTERP] The Zevenaar layout is not documented in available sources. Site survey required.

### Switchgear types identified [AVANADE] 2023 requirements document and ROM v1.2
Medium voltage (MV/MS) hardware photographed or named:
- ABB SafeRing / SafePlus MV ring main units (cabinets)
- WEGA 1.2C units (voltage detection/indication system)
- Sigma voltage indicators
- SVS switches (schakelaar-veiligheidssysteem or similar — exact model not confirmed in tender documents)
- SF-6 gas-insulated switchgear components

Low voltage (LV/LS) hardware photographed or named:
- LV blade fuse boards (mespatroon/smeltveiligheid boards)
- CAM connectors
- MSR fuses (moedergroepzekering/hoofdzekering rail)
- kWh meters (metering cabinets — meterkast)
- Phase rotation indicators

Street lighting (OV — Openbare Verlichting) hardware:
- FlexOV installation (relays, modems, controls)
- Individual relay/modem control per circuit required

[DOC NOTE] The tender guide does not name specific switchgear models. The names above come from Avanade's 2023 site visit. Bijlage T scenarios name component types (WEGA, SVS, SF-6, CAM, MSR) but not brands.

### Existing digital systems [DOC] Aanbestedingsleidraad §1.5
- Archipel: an existing system being replaced by a separate tender (not in scope here). [INTERP] This system presumably handles some scheduling or trainee management. The new platform must co-exist with or be independent of it.
- LVS (Leer Volg Systeem / Learning Management System): existing Alliander LMS. The new platform must be capable of future integration. LVS API readiness is a quality criterion (GC3).
- IAM system: Alliander's existing Identity and Access Management infrastructure. The new solution must connect to it per Bijlage V knock-out requirements.

---

## 4. Hardware-Relevant Requirements

Column definitions:
- **Type**: KO = knock-out minimum requirement, QC = quality criterion, SC = scope definition, CO = constraint
- **Hardware layer**: L1 = physical switchgear, L2 = instrumentation/sensing, L3 = edge/connectivity, OT = OT/network, SEC = security, SRV = service/maintenance

| ID | Requirement (English) | Type | Source | Hardware layer |
|---|---|---|---|---|
| HW-01 | Supplier must design, supply, install, and maintain all solution-specific hardware required for the digital control layer to function | SC | Aanbestedingsleidraad §1.5.4 | L2, L3 |
| HW-02 | Hardware in scope includes: relays, I/O boards, cabling, comparable control technology, smart cables, sensors, switches | SC | Aanbestedingsleidraad §1.5.4 | L2, L3 |
| HW-03 | Generic physical infrastructure (standard cabling, power supplies, physical switchrooms) is NOT supplier's responsibility | CO | Aanbestedingsleidraad §1.5.5 | L1 |
| HW-04 | Solution must operate fully offline (on-site edge deployment). Cloud connectivity is an option, not a dependency. | KO | Aanbestedingsleidraad §1.5.3, §2; Bijlage T general principles | L3 |
| HW-05 | Each training fault/scenario must be activatable and resettable by the instructor without interrupting other trainees' sessions | KO | Bijlage T §Algemene uitgangspunten | L2, L3 |
| HW-06 | All scenarios must be reproducible identically (deterministic fault injection) | KO | Bijlage T §Algemene uitgangspunten | L2, L3 |
| HW-07 | Random fault delivery: for at least some scenarios the platform must assign faults randomly so trainees cannot predict them | KO | Bijlage T §Algemene uitgangspunten | L3 |
| HW-08 | Hardware must be suitable for intensive repeated use in a training environment | CO | Bijlage T §Algemene uitgangspunten | L2, L3 |
| HW-09 | All training activities involving live or simulated voltage must comply with NEN 3140 and NEN-EN 50110 | KO | Bijlage T §Algemene uitgangspunten | L1, L2 |
| HW-10 | Supplier must provide a safety paragraph and risk analysis covering work with live/energised components in training scenarios | KO | Bijlage T §Algemene uitgangspunten | L1, L2 |
| HW-11 | MV (MS) scenarios require simulation of SF-6 gas-pressure indication (low-pressure warning) without real SF-6 manipulation | SC | Bijlage T P2-MS-04 | L2 |
| HW-12 | MV scenarios require simulation of WEGA unit faults (voltage detection system failures) | SC | Bijlage T P2-MS-02 | L2 |
| HW-13 | MV scenarios require simulation of SVS switch defects | SC | Bijlage T P2-MS-01 | L2 |
| HW-14 | LV scenarios require per-phase voltage/fault simulation (phase sequence, phase rotation, phase-to-earth fault) | SC | Bijlage T P2-LS-04, P2-MK-09 | L2 |
| HW-15 | LV scenarios require per-dwelling simulation in meterkast (kWh meter, MSR fuse, main switch per dwelling) | SC | Bijlage T P2-MK-01 through P2-MK-11 | L2 |
| HW-16 | LV scenarios require simulation of CAM connector defects and blade cartridge (mespatroon) states | SC | Bijlage T P2-LS-05, P2-MK-08 | L2 |
| HW-17 | OV scenarios require individual relay and modem control per street lighting circuit | SC | Bijlage T P2-OV-01 through P2-OV-10 | L2 |
| HW-18 | Operating voltage for simulation hardware is 20–50 V DC (safe low-voltage for instrumentation) | CO | [AVANADE] ROM v1.2; 2023 requirements document. Confirmed as design intent; NOT confirmed in tender documents. | L2 |
| HW-19 | Platform must integrate with Alliander IAM per Bijlage V — OIDC/OAuth 2.0 (preferred) or SAML 2.0; SailPoint/SCIM 2.0 for user provisioning | KO | Bijlage V §IAM aansluitvoorwaarden | SEC |
| HW-20 | Supplier must hold ISO 27001 certification (or equivalent) | KO | Aanbestedingsleidraad §4.1 Bijzondere contractuele bepalingen | SEC |
| HW-21 | Supplier must hold ISO 9001 certification (or equivalent) | KO | Aanbestedingsleidraad §4.1 | SRV |
| HW-22 | Authentication events must be exportable to Alliander SIEM | KO | Bijlage V §3.2 | SEC |
| HW-23 | No local password database in the application; no Implicit Flow, ROPC, Basic Auth, NTLM | KO | Bijlage V §3.1 | SEC |
| HW-24 | Platform must not create vendor lock-in; open standards and APIs required | QC | Bijlage N GC2 | L3, OT |
| HW-25 | Architecture must be modular and scalable to additional training environments | QC | Bijlage N GC2 | L3 |
| HW-26 | Solution must expose open APIs for future integration with LVS (learning management system) | QC | Bijlage N GC3 | L3 |
| HW-27 | GC1 explicitly scores the integration and interfacing approach between the platform, control panel, and physical assets | QC | Bijlage N GC1 §Beoordelingscriteria | L2, L3 |
| HW-28 | Learner identification mechanism required (trainees and instructors must be identifiable per session) | SC | [AVANADE] 2023 requirements; implied by IAM requirement in Bijlage V. NFC/RFID mentioned in Avanade 2023 doc as open question. | L2, SEC |
| HW-29 | Solution must support data collection on trainee actions and learning outcomes (for GC3 learning data dossier) | QC | Bijlage N GC3 | L2, L3 |
| HW-30 | SLA KPIs must cover quality, finance, process compliance, development and optimisation, MVO (supplier proposes values) | CO | Bijlage Q §SLA structure | SRV |
| HW-31 | Contract includes managed service for the full 3–8 year term: management, maintenance, and support are in scope | SC | Aanbestedingsleidraad §1.4 | SRV |
| HW-32 | Scoring 0 on any quality criterion (GC1, GC2, GC3) results in disqualification from award | KO | Bijlage N §Beoordelingssystematiek | QC |

**Additional requirements from Bijlage L — Programma van Eisen (now read)**

The following requirements are drawn from Bijlage L. Type column uses the document's own terminology: "Eis" = mandatory requirement (non-compliance means exclusion); "Wens" = desired but not mandatory.

| ID (Bijlage L) | Requirement (English) | Type | Source (Bijlage L sheet) | Hardware layer |
|---|---|---|---|---|
| SCOPE-01 | Supplier is responsible for design, realisation, implementation, and working delivery of the digital solution including hardware and cabling necessary for the digital solution | Eis | Functionele eisen | L2, L3 |
| SCOPE-04 | Clear boundary between digital layer (supplier) and physical installations (Alliander); supplier provides integration hardware/cabling needed for the digital solution | Eis | Functionele eisen | L2 |
| IF-05 | Interface specifications must be worked out and agreed with Alliander in advance of implementation | Eis | Functionele eisen | L2, L3 |
| IF-06 | Interfacing must be designed so coupling with new or modified physical assets is possible without redesigning the solution | Eis | Functionele eisen | L2, L3 |
| HW-01 | Supplier delivers all hardware necessary for the digital solution and coupling with physical training environments; includes interface components, relays, I/O modules, sensors, smart cables, additional switches | Eis | Functionele eisen | L2, L3 |
| HW-02 | Supplier delivers a complete hardware manifest: quantities, technical specifications, warranty periods, expected lifespan, maintenance/replacement requirements | Eis | Functionele eisen | SRV |
| HW-03 | When network configurations change, direction indicators and station designations must digitally update automatically with the configured situation | Eis | Functionele eisen | L2, L3 |
| SL-04 | Solution supports up to 4 simultaneous participants within one configuration | Eis | Functionele eisen | L2, L3 |
| MV-04 | Participants perform physical measurements on real assets using existing measuring equipment within the controlled scenario; the solution does NOT read the measuring equipment itself | Eis | Functionele eisen | L1, L2 |
| **SAFE-01** | **HARDWARE KNOCK-OUT: Fail-safe design required. At malfunction, power failure, or communication loss the solution automatically switches to a predefined safe state where no unwanted actuation of physical assets can occur. Active scenarios terminated, outputs placed in safe state, physical safety provisions remain functional.** | **Eis** | **Non-functionele eisen** | **L2, L3** |
| **SAFE-02** | **HARDWARE KNOCK-OUT: Physical safety systems must function independently of the digital solution. The digital solution must NOT override, disable, or bypass existing physical safety provisions, emergency stops, disconnections, interlocks, or other safety facilities.** | **Eis** | **Non-functionele eisen** | **L1, L2** |
| SAFE-03 | Solution presents no physical safety risk to trainers and participants; demonstrable via risk assessment | Eis | Non-functionele eisen | L2 |
| SAFE-04 | Solution distinguishes between training mode and safe rest state; visually and/or physically clearly identifiable | Eis | Non-functionele eisen | L2 |
| IT-03 | Data stored exclusively within the EEA (European Economic Area); storage outside EEA is not permitted | Eis | Non-functionele eisen | OT, SEC |
| IT-04 | Data traffic encrypted with current industry standard; minimum TLS 1.2, preferred TLS 1.3 | Eis | Non-functionele eisen | OT, SEC |
| PERF-03 | Minimum 99% availability during training hours, defined in SLA | Eis | Non-functionele eisen | SRV |
| PERF-04 | When solution fails, proven fallback scenarios must maintain training continuity; fallback tested as part of acceptance | Eis | Non-functionele eisen | L3, SRV |
| PERF-05 | Solution functions also when internet connection is temporarily unavailable; e.g., via local scenario execution | Eis | Non-functionele eisen | L3 |
| ITAR-03 | Hardware control must be architecturally isolated from business logic via standardised, well-defined interfaces; hardware-specific protocols, drivers, and implementation details must reside only within the integration/hardware layer — ensuring hardware replaceability | Eis | Non-functionele eisen | L2, L3 |
| ITAR-06 | Architecture must support a central digital network model (Digital Twin) as the authoritative representation of the physical and logical network; basis for scenario analysis, simulation, validation, and learning data | Eis | Non-functionele eisen | L3 |
| IMP-03 | Implementation starts with a pilot/PoC on a representative training environment before broad rollout | Eis | Impl. + integratie + support | SRV |
| ACC-03 | Formal acceptance requires a successful demonstration of all core scenarios defined in Bijlage T; operation must demonstrably match the described situation and desired behaviour | Eis | Impl. + integratie + support | L2, L3 |
| LCD08 | Only hardware and software receiving active vendor support may be used; lifecycle management is required; contract must explicitly state until when support is provided for all hardware and software components | Eis | Eisen cloud provider | SRV |
| LCD11 | Data stored exclusively in EEA countries; bidder must provide a complete, current inventory of all datacentres, cloud regions, and storage services, including physical country and role (prod/test/backup) | Eis | Eisen cloud provider | OT, SEC |
| LCD19 | Supplier must hold valid ISO 27001 (2022/2023) certification; the services delivered to Alliander must fall within the certification scope. Alternative: SOC 2 Type II statement covering relevant services | Eis | Eisen cloud provider | SEC |
| SL-07 | Switching operations and sequences can be practised and checked; system can signal an incorrect or unsafe switching sequence | Wens (not mandatory) | Functionele eisen | L2, L3 |

---

## 5. Core Scenarios (Bijlage T) — Hardware Capability Implications

Bijlage T defines 31 minimum scenarios across 4 training domains. These are the floor — the supplier may add more. All scenarios share the general principles in HW-05 through HW-10 above.

### 5.1 OV — Openbare Verlichting (Street Lighting) — 10 scenarios

The training installation is a FlexOV installation: a simulated street lighting network with individual controllable circuits (relays, modems).

| Scenario ID | Summary | Hardware capability required |
|---|---|---|
| P2-OV-01 | Cable damage in street lighting circuit | Ability to simulate open-circuit / high-resistance fault on a specific OV cable segment |
| P2-OV-02 | Joint defect in cable | Ability to simulate intermittent or partial connection fault at a cable joint |
| P2-OV-03 | Fuse activation (fuse blown) | Remote fuse state control per OV circuit — fuse-open simulation |
| P2-OV-04 | Lamp defect (failure of a luminaire) | Per-lamp load simulation or open-circuit simulation on lamp leg |
| P2-OV-05 | Relay defect | Relay inhibit/fault injection on FlexOV relay per circuit |
| P2-OV-06 | Modem defect in OV controller | Modem disable / fault simulation per OV control modem |
| P2-OV-07 | Permanent energisation (circuit stays live when it should turn off) | Ability to override OV relay to remain closed regardless of control signal |
| P2-OV-08 | Phase defect (loss of one phase to OV installation) | Per-phase disable or high-impedance simulation at OV feed point |
| P2-OV-09 | Overload on OV circuit | Electrical load injection or current simulation above rated threshold |
| P2-OV-10 | Multiple simultaneous OV faults (combination scenario) | Ability to inject 2+ independent faults simultaneously across OV circuits |

[INTERP] OV scenarios require individually addressable relay/modem control per circuit. The hardware layer must be able to isolate, inject, and reset faults on a per-circuit basis without affecting adjacent circuits.

### 5.2 MK — Meterkast (Meter Cabinet / Consumer Installation) — 11 scenarios

The training installation simulates a residential/commercial metering cabinet with multiple dwellings, each with kWh meter, MSR fuse, main switch, and CAM connectors.

| Scenario ID | Summary | Hardware capability required |
|---|---|---|
| P2-MK-01 | kWh meter defect (meter failure) | Per-meter simulation of defect state (reading error, non-response, or display fault) |
| P2-MK-02 | MSR fuse activation (blown fuse on main group) | Per-fuse remote trip and reset capability |
| P2-MK-03 | Short circuit on dwelling circuit | Current surge simulation or hard short injection on specific dwelling leg |
| P2-MK-04 | Earth fault (aardlekkage) on dwelling circuit | Earth leakage simulation — residual current injection or earth-loop fault |
| P2-MK-05 | Phase-to-earth fault | Controlled phase-to-earth fault injection per dwelling |
| P2-MK-06 | Main switch defect (hoofdschakelaar niet afschakelbaar) | Inhibit/defect simulation on dwelling main switch — cannot trip on command |
| P2-MK-07 | Neutral conductor defect (nulgeleider) | Open neutral simulation — voltage imbalance effect on dwelling |
| P2-MK-08 | CAM connector defect | Resistance injection or open-circuit simulation on CAM connector point |
| P2-MK-09 | Phase sequence error (fasevolgorde) | Phase rotation error simulation — out-of-sequence phase presentation |
| P2-MK-10 | Overload on dwelling circuit | Overcurrent simulation on specific dwelling without tripping other dwellings |
| P2-MK-11 | Multiple simultaneous meterkast faults | 2+ independent faults across different dwellings simultaneously |

[INTERP] 11 scenarios across a single cabinet type. Hardware must support per-dwelling isolation to at least 3 electrical parameters: fuse state, earth fault, phase/neutral integrity. Random assignment (which trainee gets which fault) must be software-driven but hardware-executed.

### 5.3 LS — Laagspanningsnet (Low Voltage Distribution Network) — 5 scenarios

The training installation simulates LV distribution network components: MSR fuses, cable joints, CAM connectors, and phase measurement.

| Scenario ID | Summary | Hardware capability required |
|---|---|---|
| P2-LS-01 | MSR fuse fault on LV distribution board | Per-fuse remote trip on LV busbar fuse position |
| P2-LS-02 | Overload on LV cable or feeder | Overcurrent injection or load simulation above rated on specific LV feeder |
| P2-LS-03 | Cable joint defect in LV network | Resistance/open-circuit simulation at joint point in LV cable run |
| P2-LS-04 | Phase rotation error in LV network | 3-phase rotation simulation at LV measurement point |
| P2-LS-05 | CAM connector defect in LV network | Resistance injection or open-circuit at CAM connector position in LV network |

[INTERP] LS and MK scenarios share hardware types (CAM, MSR, phase measurement). Hardware must work at LV distribution level as well as consumer installation level — these may be different physical installation positions in the schakellokaal.

### 5.4 MS — Middenspanning (Medium Voltage Switchgear) — 5 scenarios

The training installation includes real MV switchgear (de-energised physical equipment) with simulated electrical states injected at the instrumentation layer.

| Scenario ID | Summary | Hardware capability required |
|---|---|---|
| P2-MS-01 | SVS switch defect (safety isolation switch) | Remote simulation of SVS switch fault state — closed when should be open, or locked-out |
| P2-MS-02 | WEGA device defect (voltage detection unit) | Ability to inhibit or falsify WEGA voltage indication — simulate "no voltage" when voltage present, or vice versa |
| P2-MS-03 | Phase rotation fault on MV feeder | 3-phase rotation simulation at MV measurement interface |
| P2-MS-04 | SF-6 gas pressure alarm (low pressure indication) | Digital input simulation to trigger SF-6 low-pressure alarm on switchgear status panel — without real SF-6 manipulation |
| P2-MS-05 | Fault indicator direction error (richtingaanwijzer) | Ability to inject incorrect fault direction signal on MV feeder fault passage indicator |

[INTERP] MV scenarios are the most complex. The instrumentation must interface with physical MV switchgear (ABB SafeRing, WEGA units, SVS) that operates at real medium-voltage levels (6 kV, 10 kV, or 20 kV). The simulation must inject electrical signals at the instrumentation/sensing level without exposing the hardware or trainees to real MV voltages. This is the highest-risk and highest-complexity hardware domain. Bijlage T's requirement for a supplier safety paragraph and risk analysis is especially critical here.

---

## 6. Quality Criteria Affecting Hardware Partner Input

Source: Bijlage N — Gunningscriteria Kwaliteit

Award quality weighting: 70% of total score. All three criteria must score above 0 or the bidder is eliminated.

| Criterion | Weight (of quality) | Weight (of total score) | Hardware-relevant scoring dimensions |
|---|---|---|---|
| GC1 — Implementation plan | 50% | 35% | Integration and interfacing approach between the platform, control panel, and physical assets is explicitly named as a scoring element. The physical assets ARE the schakellokaal hardware. A hardware partner's input directly shapes this section. |
| GC2 — Technology future vision | 30% | 21% | Modular architecture, scalability to additional locations, vendor lock-in prevention. Open standards and open APIs. Hardware modularity and field replaceability are implied scoring factors. |
| GC3 — Learning data opportunities | 20% | 14% | Data collection from trainee sessions, integration with LVS (LMS), IAM integration for user identification. Requires sensors or instrumentation capable of event logging at the trainee action level. |

**Critical point for hardware partner [INTERP]:** GC1 is worth 35 points and accounts for 35% of total score. The bid team must describe exactly how the hardware integrates with the digital layer. A vague or generic hardware integration answer risks a 0 score on GC1 — which is disqualification.

**MVO (social responsibility) — 5% of total score [DOC] Aanbestedingsleidraad §4.2.** Source document not read in full. Likely covers circular hardware sourcing, repairability, end-of-life disposal. Hardware partner should be asked about sustainability certifications.

---

## 7. Safety and Security Constraints

### 7.1 Safety — Electrical Training Standards and Fail-Safe Hardware Requirements

**Requirement [DOC] Bijlage T §Algemene uitgangspunten:**
> "De oefenomgeving dient te voldoen aan de NEN 3140 en NEN-EN 50110 normen."
> ("The training environment must comply with NEN 3140 and NEN-EN 50110 standards.")

**Requirement — Fail-safe [DOC] Bijlage L SAFE-01:**
> "De oplossing is fail-safe ingericht. Bij storing, spanningsuitval of verlies van communicatie schakelt de oplossing automatisch naar een vooraf gedefinieerde veilige toestand waarin geen ongewenste aansturing van fysieke assets kan plaatsvinden. Onder een veilige toestand wordt verstaan dat actieve scenario's worden beëindigd, uitgangen naar een veilige stand worden gebracht en de fysieke veiligheidsvoorzieningen onverminderd blijven functioneren."
> ("The solution has a fail-safe design. At malfunction, power failure, or communication loss, the solution automatically switches to a predefined safe state where no unwanted actuation of physical assets can occur. A safe state means active scenarios are terminated, outputs are placed in a safe position, and physical safety provisions continue to function without impairment.")

**Requirement — Physical safety system independence [DOC] Bijlage L SAFE-02:**
> "Fysieke veiligheidssystemen functioneren onafhankelijk van de digitale oplossing. De digitale oplossing mag bestaande fysieke beveiligingen, noodstops, afschakelingen, vergrendelingen of andere veiligheidsvoorzieningen niet overrulen, uitschakelen of omzeilen. Het uitvallen of onjuist functioneren van de digitale oplossing mag niet leiden tot het uitvallen van fysieke veiligheidsmaatregelen."
> ("Physical safety systems function independently of the digital solution. The digital solution must not override, disable, or bypass existing physical safety provisions, emergency stops, disconnections, interlocks, or other safety facilities. Failure or incorrect functioning of the digital solution must not cause physical safety measures to fail.")

[INTERP] SAFE-01 and SAFE-02 are the highest-consequence hardware requirements in the document. Every relay board, I/O module, edge controller, and power supply in the instrumentation layer must default to a safe state on loss of power or communication. The hardware design must not create any condition where a loss of digital control also disables physical interlocks or emergency stops on the switchgear.

**Requirement [DOC] Bijlage T §Algemene uitgangspunten:**
> "De aanbieder dient een veiligheidsparagraaf en risico-analyse aan te leveren voor het werken met onder spanning staande componenten binnen de trainingsscenario's."
> ("The supplier must provide a safety paragraph and risk analysis for working with live/energised components within the training scenarios.")

**Requirement [DOC] Bijlage T §Algemene uitgangspunten:**
> "De hardware dient geschikt te zijn voor intensief herhaald gebruik in een trainingsomgeving."
> ("The hardware must be suitable for intensive repeated use in a training environment.")

NEN 3140 governs the operation and maintenance of electrical installations; NEN-EN 50110 governs safe working on electrical installations. Both are mandatory compliance standards for electrical training in the Netherlands. [INTERP] The hardware partner must ensure all instrumentation, cabling, and control hardware installed on or near real switchgear complies with these norms.

### 7.2 Security — IAM Knock-Out (Bijlage V)

**KNOCK-OUT — exact Dutch wording [DOC] Bijlage V:**
> "Als er niet minimaal aan beveiligingsniveau A voor zowel IGA als AM kan worden voldaan dan volgt knock out."
> ("If a minimum security level A for both IGA [Identity Governance and Administration] and AM [Access Management] cannot be met, knock-out follows.")

This is an absolute disqualification condition. The solution must support:

**Access Management (AM) — minimum level A [DOC] Bijlage V §3.1:**
- OIDC/OAuth 2.0 with Authorization Code flow + PKCE S256 (preferred)
- SAML 2.0 (fallback — acceptable for level A)
- NOT permitted: Implicit Flow, Resource Owner Password Credentials (ROPC), Basic Auth, NTLM, local password database in the application

**Identity Governance and Administration (IGA) — minimum level A [DOC] Bijlage V §3.2:**
- SailPoint connector (preferred)
- SCIM 2.0 provisioning (acceptable for level A)
- API connector (lower preference)
- Manual provisioning (not acceptable above level A)
- Authentication events must be exportable to Alliander SIEM

**Implication for hardware [INTERP]:** Any edge device, gateway, or on-site server that manages user sessions or trainee identification must route authentication through Alliander IAM. Local user databases on hardware or embedded systems are prohibited. This affects RFID/NFC reader systems, instructor control panels, and any device with a login interface.

### 7.3 Security — Contractual Requirements [DOC] Aanbestedingsleidraad §4.1

> "De opdrachtnemer dient aantoonbaar te beschikken over een ISO 9001 of gelijkwaardig gecertificeerd kwaliteitsmanagementsysteem."
> ("The contractor must demonstrably hold ISO 9001 or equivalent certified quality management system.")

> "De opdrachtnemer dient aantoonbaar te beschikken over een ISO 27001 of gelijkwaardig gecertificeerd informatiebeveiligingsmanagementsysteem."
> ("The contractor must demonstrably hold ISO 27001 or equivalent certified information security management system.")

[INTERP] ISO 27001 applies to the supplier's organisation, not the hardware itself. However, hardware partners that process or have access to Alliander system data may need to demonstrate equivalent information security controls, or operate under Avanade's ISO 27001 scope.

### 7.4 Data Residency [DOC / INTERP]

The tender guide does not explicitly state data residency requirements. [INTERP] Given Alliander is a Dutch critical infrastructure operator and the IAM requirements reference Dutch/EU standards, data residency in the EU (likely NL) is probable. This was not confirmed in the readable documents. Bijlage L (unread xlsx) may contain an explicit requirement.

---

## 8. Gaps and Ambiguities

These are open questions for site survey, clarification round (NvI 2 if applicable), or the hardware partner's assessment. [INTERP] throughout this section.

| # | Gap / Question | Source of gap | Priority |
|---|---|---|---|
| G-01 | ~~Bijlage L not read~~ | **CLOSED** — Bijlage L extracted and fully incorporated in this revision. All 193 rows across 5 sheets reviewed. New hardware requirements and knock-outs added to Sections 4 and 7. | CLOSED |
| G-02 | ~~Bijlage J not read~~ | **CLOSED** — Bijlage J extracted and incorporated. Hardware delivery and installation are separate one-time line items. Annual hardware maintenance is embedded in "Technisch beheer en support". See Section 2 for full pricing structure analysis. | CLOSED |
| G-03 | **Zevenaar layout and switchgear inventory unknown.** Only Haarlem has documented floor plans and equipment photos (from 2023 Avanade visit). Zevenaar's schakellokaal and meetveld configuration, switchgear types, room count, and physical dimensions are undocumented. Site survey required. | Source documents | HIGH |
| G-04 | **Meetveld (measurement field) scope unclear.** The tender names "schakellokaal" and "meetveld" as distinct environments. The scenarios in Bijlage T appear to address schakellokaal-type equipment (MS, LS, OV, MK). No meetveld-specific scenarios are described. Does the meetveld require digital control hardware? What equipment does it contain? | Bijlage T only covers switchgear scenarios | HIGH |
| G-05 | **Trainee identification method undefined.** The tender requires IAM integration (Bijlage V) and learning data collection (GC3). The 2023 Avanade requirements document raised NFC/RFID/access card identification as an open question. The tender does not specify the physical identification mechanism. Does Alliander use a badge/card already? What hardware standard? | 2023 Avanade doc; no tender confirmation | HIGH |
| G-06 | **Operating voltage confirmation.** The ROM v1.2 2025 specifies 20–50 V DC for instrumentation. The 2023 requirements document mentions 25/50 V. Neither is confirmed in the tender documents. If the actual switchgear uses different voltages or AC, the hardware design changes. | Tender silent on voltage specs | HIGH |
| G-07 | **SF-6 simulation method.** P2-MS-04 requires SF-6 low-pressure alarm simulation. On real SF-6 switchgear the pressure indicator is a mechanical/electrical sensor. Exactly how this signal is to be intercepted and falsified — whether via relay injection on the indicator circuit, or a bypass sensor — is unspecified. The safety risk of manipulating real SF-6 equipment during training must be addressed in the risk analysis. | Bijlage T describes the scenario outcome, not the method | HIGH |
| G-08 | **WEGA and SVS interface specifications.** The tender names WEGA and SVS as equipment types but does not provide electrical interface specifications (voltage levels, signal types, protocols). The hardware partner needs these to design instrumentation. | Source documents name types only | MEDIUM |
| G-09 | ~~Data residency unconfirmed~~ | **CLOSED** — Bijlage L IT-03 (Non-functionele eisen) and LCD11 (Eisen cloud provider) both explicitly require EEA-only data storage. Storage outside EEA is not permitted. No further ambiguity. | CLOSED |
| G-10 | **Archipel integration scope.** The tender states Archipel replacement is a separate tender, but does not clarify whether the new digital control platform must import data from or coexist with Archipel during a transition period. | Aanbestedingsleidraad §1.5.5 | MEDIUM |
| G-11 | **Camera and visual monitoring requirements.** The 2023 Avanade requirements document mentions smart cameras as desired. The tender documents do not reference cameras. Are they in scope? If so, are they part of the safety/supervision system (NEN 3140) or the learning data system (GC3)? | Avanade 2023 vs tender silence | MEDIUM |
| G-12 | **SLA KPI targets.** Bijlage Q is a blank template. The supplier proposes KPI values. No availability, response time, or hardware replacement SLA targets are defined in the tender. The hardware partner's support capability must be established before the bid team can propose credible KPIs. | Bijlage Q blank | MEDIUM |
| G-13 | **Scalability quantification.** The tender requires scalability to additional environments but does not define how many additional sites are expected, or on what timeline. The hardware partner needs this to size spares, support contracts, and bulk pricing. | Aanbestedingsleidraad §1.3 — "additional environments may be added" | LOW |
| G-14 | **MVO / circular hardware requirements.** The MVO scoring document was not read. Whether the hardware must be circular, repairable, or meet specific sustainability standards is unknown. | Source document not read | LOW |

---

*End of tender hardware reconnaissance. Athanasios — 2026-09-30 (revised: Bijlage L and Bijlage J incorporated).*
