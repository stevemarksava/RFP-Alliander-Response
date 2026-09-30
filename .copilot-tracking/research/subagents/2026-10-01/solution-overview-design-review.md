# Subagent Research: Solution Overview Design Review

**Task type:** Design review (solution architecture), not a code review.
**Target document under review:** 4. Solution/Solution Overview/solution-overview.md
**Grounding documents (read-only):**
- 4. Solution/Hardware Solution/alliander-schakellokalen-hardware-brd.md
- 4. Solution/Hardware Solution/recon/tender-hardware-recon.md
- 4. Solution/Solution Overview/architecture-diagram.drawio

No files were modified. This session is read/analysis only, per explicit user instruction.

## Research Questions

1. Cross-layer consistency across the seven architecture-layer sections (Business, Enterprise, Solution, Hardware, Network, Data, Security). Specific named checks: Network offline/async-sync vs Data edge-to-cloud sync; Security IAM-federation claim vs Hardware/Network no-local-credential-store claim.
2. Unflagged assumptions: factual claims stated as fact in solution-overview.md that are not properly hedged, and are not [DOC]-confirmed in tender-hardware-recon.md.
3. Design trade-offs and risks: SPOFs, scalability beyond the initial 4 environments, ITAR-03 hardware-abstraction coupling risk, fail-safe gaps relative to SAFE-01/SAFE-02.
4. GC1 (35% of total score, implementation plan) / GC2 (21% of total score, technology future vision) scoring support.
5. Top 5 prioritized, concrete recommendations before red-team/adversarial review.

## Method

Read all four documents in full (solution-overview.md ~290 lines; hardware BRD full; tender recon full, which distinguishes [DOC] confirmed facts from [INTERP] interpretation; architecture-diagram.drawio full XML). Cross-referenced every factual claim and requirement ID (SAFE-01/02/03/04, ITAR-03/06, PERF-03/04/05, IT-03/04, LCD08/11/19, SL-04, HW-01 through HW-32, GC1/GC2/GC3 weightings) between the four sources. Compared the markdown ASCII-art diagram embedded in solution-overview.md against the actual .drawio XML for drift.

## Key Discoveries (evidence-backed)

### A. Layer 6 (Experience) cannot show live in-session data as currently designed — highest-confidence finding
- solution-overview.md Scope Boundary table states literally: "4-6 (Digital Twin, AI & Agentic, Experience) | Avanade / Alliander | Cloud, EEA-hosted, syncs asynchronously from the edge." No exception carved out for a local/live view.
- The .drawio XML has exactly these edges: l1→l2, l2→l3 (PS column), l4→l5, l5→l6 (AS column), l3→l4 (labeled "sync when connectivity available... async, not required for operation"), iam→l3, safe→l2. There is NO edge from l3 (edge) directly to l6 (Experience/instructor dashboard). The ASCII-art block in solution-overview.md mirrors this exactly — both diagram representations agree with each other on this point.
- Contradicts the hardware BRD's own Live Case Walkthrough step 7: "The instructor dashboard, connected to the same on-site edge server over the local industrial network, shows the trainee's live progress and the flagged error immediately... the live view itself runs on the edge." That sentence explicitly distinguishes the live/local view from the synced Layer 4 data model.
- Net effect: taken at face value, the document's own Scope Boundary table and both diagram renderings describe an Experience layer that only ever receives async, post-sync data — which cannot support the real-time instructor observation the BRD itself describes as essential, and which is the core value proposition replacing "instructor-only manual observation."

### B. "Fully offline edge" vs "every identity touchpoint routes through IAM, no local credential store" — unresolved tension, not a flat contradiction
- Architecture Summary point 4, Security Architecture, Network Architecture, and the diagram all consistently repeat "no local credential store anywhere, including edge hardware/gateways."
- Architecture Summary point 1, Network Architecture, Business Architecture, and the diagram all consistently repeat "fully offline," "no dependency on internet breakout."
- These two consistently-repeated claims are each internally consistent but operationally incompatible with each other without a bridging mechanism, which solution-overview.md never states.
- The BRD's own Live Case Walkthrough step 1 hints at the resolution without solution-overview.md carrying it forward: "The reader authenticates the trainee against a locally cached identity token issued by Alliander's IAM, since no live connection is required at this moment."
- Likely correct resolution (standard OIDC pattern): locally cached JWKS / previously-issued signed tokens validated offline within a bounded validity window — this is NOT the same as "a local password database" (which is correctly prohibited) but the document does not draw this distinction anywhere, leaving a reader to infer it.

### C. Diagram (.drawio) states unconfirmed facts that the parallel text explicitly hedges
- Network Architecture section opens with an explicit blockquote: "Protocol names below (OPC-UA, Modbus, MQTT) are an Avanade design assumption... not specified or confirmed anywhere in the tender documents and must be validated..."
- The ASCII-art diagram block in solution-overview.md was written generically: "industrial protocol stack" (no specific protocol names) — correctly hedged.
- The actual .drawio XML, however, bakes the names directly into the Layer 3 box with zero hedge: `"Layer 3 - Connect (Edge)\nOn-site gateway + edge server\nOPC-UA / Modbus / MQTT, UPS\nruns FULLY OFFLINE"`. This is drift between the two diagram representations, and the .drawio is the one explicitly called out in the document as "also available as an editable draw.io file" (i.e., the presumed source of any exported image used in an actual submission).

### D. RFID/NFC trainee identification stated as fact in both diagram renderings, with zero hedge anywhere in solution-overview.md prose
- Both the ASCII-art diagram and the .drawio XML state Layer 2 includes "RFID/NFC" flatly.
- tender-hardware-recon.md gap G-05 (HIGH priority): "Trainee identification method undefined... does not specify the physical identification mechanism."
- Hardware BRD BR-006 (Should priority, not Must): "trainee and instructor identification hardware, such as an RFID or NFC reader... to be confirmed via site survey," and lists it again explicitly under Open Questions and Assumptions as unconfirmed.
- solution-overview.md's Hardware Architecture prose section (the "per-domain instrumentation needs" list) never mentions RFID/NFC at all — it only appears, unhedged, in the diagram.
- Contrast/control example done correctly: the 20-50V DC operating-voltage claim IS properly hedged in solution-overview.md's Hardware Architecture prose ("an Avanade design intent... not yet confirmed in the tender documents themselves"). This shows the hedging pattern the document is capable of, making its absence for RFID/NFC and diagram protocol names more clearly an inconsistency of execution rather than a policy gap.

### E. "4 environments" / meetveld scope treated as settled when recon flags it as a HIGH-priority open gap
- solution-overview.md (Business Architecture, Network Architecture, Scope Boundary) repeatedly states "4 environments total (1 schakellokaal + 1 meetveld each in Haarlem and Zevenaar)" as flat, settled scope.
- tender-hardware-recon.md gap G-04 (HIGH priority): "Meetveld (measurement field) scope unclear... Bijlage T's 31 core scenarios all appear to address schakellokaal-type switchgear... whether the meetveld requires its own digital control hardware, and what equipment it contains, is not stated."
- solution-overview.md's own Next Steps / Open items sections do not surface this ambiguity anywhere, despite surfacing other, arguably lower-priority open items (protocol choice, retention period, EA framework alignment).
- Related, lower-severity: recon gap G-03 (HIGH, Zevenaar layout/switchgear inventory entirely undocumented) is also never surfaced in solution-overview.md's open items, even though Haarlem and Zevenaar are repeatedly treated as symmetric.

### F. Named, mandatory (Eis) requirements silently absent from solution-overview.md
- **SL-04** ("solution supports up to 4 simultaneous participants within one configuration," Eis in Bijlage L per recon §4 and BRD BR-023) — never mentioned anywhere in solution-overview.md, including Hardware Architecture, despite the document otherwise citing Bijlage L IDs extensively. Closest proxy text ("without interrupting other trainees") omits the concrete number and the ID.
- **SAFE-03** (no physical safety risk to trainers/participants, demonstrable via risk assessment) and **SAFE-04** (solution must visually/physically distinguish training-mode from safe-rest-state) — both present in recon §4/§7.1 as Eis requirements, both entirely absent from solution-overview.md, which only ever cites SAFE-01/SAFE-02.
- **BR-027 / SAFE-01 time-bound**: the BRD frames the fail-safe transition as needing "a time bound the partner proposes" — solution-overview.md's restatement of SAFE-01 omits any mention that a response-time parameter needs to be defined at all (contrast with how the document DOES flag retention period as an explicit open parameter in Data Architecture).
- **HW-03** (automatic digital update of direction indicators/station designations on network-configuration change, Eis) — not mentioned anywhere in solution-overview.md.

### G. Segmentation (OT/IT network isolation) appears only in Network Architecture's Open Items, not in Security Architecture
- BRD BR-003 / recon HW-hardware-layer classification require industrial protocols "isolated from Alliander's corporate IT network."
- Network Architecture honestly flags VLAN/segmentation design as not yet done.
- Security Architecture section is entirely silent on network segmentation — a plausible completeness gap for the one section whose explicit job is security boundary design, even though the gap is honestly disclosed once, elsewhere in the document.

### H. Confirmed-consistent (no issue) — the two examples the user explicitly asked about
- Network's async/offline-first sync design and Data Architecture's edge-to-cloud sync description use matching language ("asynchronous," "when connectivity available," capture/queue locally otherwise) and do not contradict each other. Data Architecture additionally and honestly flags "conflict handling and exact sync cadence are not yet designed" — a legitimate, already-self-disclosed risk, not a new finding, but worth carrying into the risk section.
- Security's "no local credential store" claim and Network's identical claim are worded consistently with each other (see Discovery B for the deeper, cross-cutting tension with the offline-edge design, which is the real issue — not a literal contradiction between these two sections taken in isolation).

## Risks / Trade-offs Beyond Consistency (research question 3)

- **SPOF — single edge server per site.** Described as sole "system of record" during a session with no redundancy/HA/failover design discussed anywhere. SAFE-01's "fail-safe" (terminate safely) is conflated with resilience/failover (resume service) in the document — these are different properties and only the former is designed.
- **SPOF — cloud digital twin/learning-data store.** No backup/DR/RTO-RPO discussion despite being called "authoritative."
- **Re-introduced SPOF via IAM.** If offline-token-caching isn't explicitly designed (see Discovery B), Alliander's central IAM becomes a hard dependency for an architecture whose core selling point is resilience to connectivity loss.
- **Scalability — digital twin data model.** No statement of whether the twin is single global model, per-site instance, or multi-tenant; this materially affects both GC2 credibility and real engineering cost of onboarding new sites.
- **Scalability — AI/vision layer (Layer 5).** Vision-based step validation likely needs per-site calibration/retraining for new camera angles/panel layouts/lighting; this per-site marginal cost is not acknowledged anywhere, weakening the "no redesign needed" scalability claim specifically for Layer 5.
- **ITAR-03 coupling risk at the Layer 3/Layer 5 boundary.** The single-sentence claim that Layer 3 "exposes a single integration point" to the digital layer is not backed by any described interface contract/schema (e.g., an abstracted fault/scenario definition every panel type maps to). Without this, real implementation risk exists that fault-selection logic in Layer 5 ends up hardware-aware, silently violating the stated hardware-abstraction boundary during actual build even though the design intent is correctly stated.

## GC1 / GC2 Assessment (research question 4)

- **GC1 (35% of total score, implementation plan):** Current support is roughly one sentence (pilot/PoC before broader rollout, citing IMP-03). No phasing, milestones against the 3-year base term, rollout sequencing logic, risk-mitigation approach, or acceptance-testing detail beyond a citation. HW-27 ("GC1 explicitly scores the integration and interfacing approach between the platform, control panel, and physical assets" per recon §6) is also thinly served — the ITAR-03 "single integration point" claim is asserted, not described. This is the single largest point-scoring gap relative to the tender's own weighting.
- **GC2 (21% of total score, technology future vision):** Ingredients are present and correctly cited (modularity/ITAR-03, open APIs/standards in Network Architecture, scalability language in Business Architecture), but never synthesized into a forward-looking narrative. The document reads as "what we are building" rather than "where this goes and why it is future-proof" (e.g., no roadmap across the 8-year term, no stated LVS-integration timeline, no multi-site onboarding runbook, no AI/agentic-layer maturity path).

## Top 5 Recommendations (delivered to user; recorded here for traceability)

1. Fix the Layer 6 live-observation data-flow gap (Discovery A) — add an explicit local/edge-to-Experience connection in both diagram and text, or explicitly scope an on-site live-view component distinct from the cloud-hosted reporting/historical component.
2. Explicitly design and document offline authentication (Discovery B) — name the bridging mechanism (e.g., cached JWKS-validated tokens, bounded offline-validity window) and use precise language distinguishing prohibited local password stores from permitted cached federated tokens.
3. Reconcile the .drawio file with its own text hedges (Discoveries C and D) — remove or qualify unconfirmed protocol names and RFID/NFC in the actual diagram file, not just the markdown ASCII art.
4. Write an actual GC1 implementation-plan narrative and flesh out the Layer 3/Layer 5 interface contract (GC1 assessment + Discovery risk on ITAR-03 coupling) — given GC1 is the single largest scoring weight.
5. Close the named, verifiable gaps against the document's own source material (Discoveries E and F): meetveld scope ambiguity (G-04, HIGH), SL-04, SAFE-03/SAFE-04.

## Status

**Complete.** All five research questions answered directly from the four provided documents; no external research was needed or performed. Full structured report delivered to the user in the same turn as this tracking document.

## Recommended Next Research (not performed this session)

- [ ] If a joint site survey report becomes available, re-validate the 20-50V DC assumption, Zevenaar layout, and WEGA/SVS interface specs (recon G-06/G-03/G-08) against solution-overview.md's Hardware Architecture section.
- [ ] If NvI 2 (second clarification round) is issued, re-check whether it resolves the meetveld scope (G-04) or enterprise-architecture-framework question, and update solution-overview.md's Open items accordingly.
- [ ] Once a hardware partner is selected, revisit the Network Architecture protocol-choice open item and the diagram simultaneously so both stay in sync going forward.

## Clarifying Questions for the User

None required — the request was fully answerable from the four provided documents without ambiguity.
