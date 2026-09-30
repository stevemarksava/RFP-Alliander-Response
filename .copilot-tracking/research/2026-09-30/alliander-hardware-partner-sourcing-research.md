<!-- markdownlint-disable-file -->
# Task Research: Alliander Digital Schakellokalen — Hardware Partner Sourcing

Avanade is bidding on Alliander tender 226705 ("Digitale aansturing van oefenomgevingen voor
technische opleidingen"). The Hardware BRD (`4. Solution/Hardware Solution/alliander-schakellokalen-hardware-brd.md`)
defines outcome-based capability requirements for an IoT hardware partner to source, build,
enable, service, and support the instrumentation and edge-connectivity layer (layers 1-3:
physical, instrument, connect/edge) across four training environments in Haarlem and Zevenaar.
The bid team flagged sourcing this hardware partner as urgent (Marcel Westra, 29 Sep 2026:
"Er moet heel veel gedaan worden. O.a. een hardware partner. Moeten nu snel aan de bak").
This research scopes the hardware partner sourcing problem: what capability profile is needed,
what candidate partner types/companies plausibly fit, what technical alternatives (protocols,
edge platforms) a partner selection should account for, and a recommended sourcing approach.

## Task Implementation Requests

* Define the capability profile an IoT/edge hardware partner must have against the BRD.
* Identify candidate partner types/companies (NL/EU industrial IoT integrators, edge/OT
  system integrators) plausibly able to deliver layers 1-3.
* Evaluate technical alternatives for the edge/connect layer (industrial protocols, edge
  compute platform choices) relevant to partner capability assessment.
* Recommend a sourcing approach and evaluation criteria usable before the 18 Nov 2026
  submission deadline.

## Scope and Success Criteria

* Scope: hardware partner sourcing for layers 1-3 of the Digital Schakellokalen solution.
  Excludes: layers 4-6 (Avanade/Alliander scope), pricing negotiation, legal/contracting
  process, and the prior-involvement procurement conflict-of-interest question (tracked
  separately in DT coaching artifacts at `.copilot-tracking/dt/rfp-alliander/`).
* Assumptions: the BRD's outcome-based requirements are current and Vera-approved; the
  4-environment initial scope (Haarlem, Zevenaar) is stable; submission deadline 18 Nov 2026.
* Success Criteria:
  * A clear capability profile derived from the BRD and tender documents.
  * A short list of plausible candidate partner types/companies with rationale.
  * A recommended technical alternative (or alternatives) for the edge/connect layer.
  * A recommended sourcing approach with evaluation criteria and next steps.

## Outline

* Workspace context (BRD, recon, solution overview) — capability requirements extraction
* Candidate hardware partner types and companies
* Technical alternatives for edge/connect layer
* Recommended approach

## Potential Next Research

* Monitor for Alliander's answer to NvI1 Question 3 (Offline Operation, ref. Annex L
  PERF-05/SAFE-01) and, once received (NvI2 or later), confirm whether the tender's offline
  requirement is still a "temporary outage" minimum or has been clarified/tightened.
  * Reasoning: the bid team already formally asked Alliander this exact question —
    "Which functions must remain available during an internet outage, for how long and for
    which users? Must new sessions and user login work offline?" — on 23 Sep 2026; no answer
    exists in the workspace yet. This upgrades the item from "should confirm" to "already
    asked, awaiting reply."
  * Reference: onedrive/Vragen NvI 1 (23 sep 10 uur)/Alliander_NvI1_Questions_EN.md;
    .copilot-tracking/research/subagents/2026-09-30/coach-briefing-and-raw-rfp-verification.md
* Clarify how much of the 2023 broader concept (Teams integration, Leerling Volg Systeem)
  survives in the 2026 MVP tender scope.
  * Reasoning: affects whether hardware partner scope needs to account for additional
    integration surface. Confirmed so far: LVS appears in the 2026 tender only as a
    Should-priority, open-API future-integration criterion (GC3), not a delivered
    capability; Teams integration appears nowhere in any 2026 tender/BRD/solution-overview
    document. Both remain otherwise unconfirmed either way.
  * Reference: .copilot-tracking/dt/rfp-alliander/method-01-scope/scope-boundaries.md
    (corrects the earlier "Coach Briefing, Section 7" citation, which does not resolve to a
    real artifact — no file or heading named "Coach Briefing" exists in this workspace).
* Run a targeted RFI/market-sounding exercise with Axians NL, ATS Global, and 2-3
  Automation-List.com directory firms to confirm utility-sector and Azure IoT Edge
  experience, since public web research could not verify any candidate to high confidence.
  * Reasoning: no company was found with direct, publicly verifiable evidence of prior work
    on grid-training-room instrumentation retrofit; this is a genuinely narrow niche.
  * Reference: .copilot-tracking/research/subagents/2026-09-30/hardware-partner-candidates.md
* Schedule and conduct the Zevenaar joint site survey.
  * Reasoning: the BRD explicitly defers final hardware selection to a site survey; Zevenaar
    has no documented floor plan/equipment inventory (only Haarlem does, from 2023).
  * Reference: 4. Solution/Hardware Solution/alliander-schakellokalen-hardware-brd.md;
    README.md.
* Directly confirm with a Microsoft account/partner contact whether any written guidance
  (even internal/partner-facing) compares classic Azure IoT Edge vs Azure IoT Operations for
  long-duration (multi-day+) offline industrial scenarios.
  * Reasoning: research confirms classic IoT Edge remains actively supported (LTS 1.6
    through Nov 2028, no retirement date) with its indefinite-offline claim unchanged, and
    Azure IoT Operations' 72-hour offline ceiling is also unchanged — but no public
    Microsoft page cross-references the two products on this specific tradeoff, so this is
    a genuine documentation gap rather than a research gap.
  * Reference: .copilot-tracking/research/subagents/2026-09-30/edge-platform-lts-offline-followup.md
* Confirm the exact periodic connectivity/check-in interval required for standard
  (non-disconnected-operations) Azure Local licensing/billing compliance, only if Azure
  Local is pursued further as an infrastructure option.
  * Reasoning: no official Microsoft Learn page with this specific figure was found; low
    priority since Azure Local remains a deprioritized alternative (see Considered
    Alternatives).
  * Reference: .copilot-tracking/research/subagents/2026-09-30/edge-platform-lts-offline-followup.md

## Research Executed

### File Analysis

* 4. Solution/Hardware Solution/alliander-schakellokalen-hardware-brd.md
  * Full capability profile for the hardware partner: layers 1-3 scope, in/out-of-scope
    deliverables (lines 66-80), maintenance/lifecycle requirements (BR-040 to BR-054),
    indicative-only technology hints (OPC-UA/Modbus/MQTT, RFID/NFC, 20-50V DC), and an
    explicit "Open Questions and Assumptions" section enumerating 11 unresolved gaps.
* 4. Solution/Hardware Solution/recon/tender-hardware-recon.md
  * Source-of-truth extraction from the tender guide and its appendices (Bijlage L, J, N, Q,
    V). Contains the full requirement-ID table (SAFE-01/02, PERF-03/04/05, IT-03/04, LCD08/
    11/19, ITAR-03/06, IAM knock-out conditions) and an explicit gap/ambiguity log (§8, G-01
    through G-14).
* 4. Solution/Solution Overview/solution-overview.md
  * Confirms the six-layer architecture, the layers 1-3 vs 4-6 scope boundary table (lines
    163-168), and flags that protocol names (OPC-UA/Modbus/MQTT) are an Avanade design
    assumption, not a tender-confirmed requirement.
* README.md
  * Confirms project status: hardware BRD is Vera-approved; Bob and Kryptonite reviews are
    still pending; the Zevenaar site survey is an open item the BRD's assumptions depend on.

### External Research

* Web search (via subagent): live tender confirmation
  * Confirmed tender 226705 is real and active (TED/TenderNed notice, deadline 2026-11-18,
    EUR 3.04M, single-supplier framework). CPV codes are software-services only; no separate
    hardware/instrumentation lot was found publicly.
    * Source: [nl.openprocurements.com](https://nl.openprocurements.com/tender/digitale-aansturing-van-oefenomgevingen-voor-technische-opleidingen/)
* Web search (via subagent): candidate hardware partners
  * See Key Discoveries below; full detail in
    .copilot-tracking/research/subagents/2026-09-30/hardware-partner-candidates.md
* Web search (via subagent): "Innotractor" follow-up (user-raised candidate)
  * Identified as InnoTractor BV (Tilburg, NL) — a supply-chain dataspace/traceability
    software company (ports, aviation MRO, healthcare logistics). No evidence of MV/LV
    switchgear instrumentation, industrial networking, or Azure edge-compute work. Assessed
    as a non-match for this hardware-partner scope.
* Web search (via subagent): industrial protocols and Azure edge compute platforms
  * See Technical Scenarios below; full detail in
    .copilot-tracking/research/subagents/2026-09-30/edge-protocol-alternatives.md

### Project Conventions

* Followed the existing [DOC]/[INTERP] citation convention already used in
  tender-hardware-recon.md when extracting workspace facts.
* Followed the workspace's existing markdown style (used in the Hardware BRD and Solution
  Overview) for structuring requirement tables and scope lists.

## Key Discoveries

### Hardware Partner Capability Profile

The hardware partner's mandate is tightly bounded to layers 1-3 (physical instrumentation,
sensing/actuation, edge/connect), with two disqualifying knock-out requirements that shape
every other design decision:

* **SAFE-01/SAFE-02** (hardware knock-outs): on any malfunction, power loss, or
  communications loss, the system must revert to a predefined safe state, and the digital
  layer must never override, disable, or bypass any existing physical safety provision
  (interlocks, e-stops, LOTO). See
  .copilot-tracking/research/subagents/2026-09-30/workspace-hardware-context.md, section 2.
* Commercial structure splits hardware into one-time delivery + one-time installation cost
  lines, with ongoing maintenance folded into an annual "Technisch beheer en support" fee —
  no separate annual hardware-maintenance line exists in the pricing sheet.
* All device-specific details (protocols, voltages, named equipment models) are explicitly
  "indicative only" pending a joint site survey — required for Zevenaar specifically, since
  only Haarlem has a documented 2023 site visit.
* 11 open gaps block a fully complete capability profile (Zevenaar layout, meetveld scope,
  trainee ID mechanism, operating voltage, SF-6 simulation method, WEGA/SVS interface specs,
  Archipel coexistence, camera scope, SLA KPI targets, scalability quantification, MVO
  requirements) — see workspace-hardware-context.md section 6 for the full table.

### Candidate Hardware Partners

Public web research could not verify any company to high confidence for this specific niche
(utility training-room instrumentation retrofit). Medium-confidence candidates, in order of
fit:

* **Axians Nederland** (VINCI Energies) — dedicated "Modernizing Smart Grids" utilities
  practice plus an OT/IT IoT integration product (Maestro).
* **ATS Global** — NL-headquartered SCADA/MES/IIoT integrator with an explicit "Smart Grid"
  offering and multi-site industrial rollout experience.
* Lower-confidence: Macaw and Savaco (more IT/data/cloud-IoT oriented than physical-retrofit
  oriented); large OEM alliance networks (Schneider Electric, Siemens, ABB) as a component/
  sourcing channel rather than a likely prime (Siemens separately has a real, unrelated
  Alliander partnership — Gridscale X digital twin).
* **Innotractor (user-raised) is a non-match** — confirmed as InnoTractor BV, a supply-chain
  dataspace/traceability software company (ports, aviation MRO, healthcare logistics), with
  no evidence of industrial OT/IoT or electrical-switchgear work.
* No confirmed incumbent or awarded hardware supplier was found; the live tender notice's
  CPV codes are software-only.

Full candidate list, confidence levels, and sourcing channels (Automation-List.com NL
directory, Schneider Electric alliance-partner directory, Microsoft Partner Center) are in
.copilot-tracking/research/subagents/2026-09-30/hardware-partner-candidates.md.

### API and Schema Documentation

* [OPC Foundation — Unified Architecture](https://opcfoundation.org/about/opc-technologies/opc-ua/)
* [Azure/Industrial-IoT — OPC Publisher](https://github.com/Azure/Industrial-IoT/blob/main/readme.md)
* [Microsoft Learn — Operate Azure IoT Edge devices offline](https://learn.microsoft.com/en-us/azure/iot-edge/offline-capabilities?view=iotedge-1.5)
* [Microsoft Learn — What is Azure IoT Operations?](https://learn.microsoft.com/en-us/azure/iot-operations/overview-iot-operations)
* [Microsoft Learn — IoT Edge version history and release notes](https://learn.microsoft.com/en-us/azure/iot-edge/version-history)
* [Microsoft Learn — Azure IoT Edge lifecycle](https://learn.microsoft.com/en-us/lifecycle/products/azure-iot-edge)
* [Microsoft Learn — Introduction to Azure IoT](https://learn.microsoft.com/en-us/azure/architecture/guide/iiot-guidance/iiot-architecture)
* [Microsoft Learn — Disconnected operations for Azure Local overview](https://learn.microsoft.com/en-us/azure/azure-local/manage/disconnected-operations-overview)
* [HiveMQ Edge](https://www.hivemq.com/products/hivemq-edge/)
* [EdgeX Foundry — Device Services Overview](https://docs.edgexfoundry.org/3.1/microservices/device/Ch-DeviceServices/)
* [EdgeX Foundry — Eaton case study](https://www.edgexfoundry.org/use-cases/eaton-use-case/)

## Technical Scenarios

### Connect/Edge Layer: Protocol and Edge-Compute Selection

**Requirements:**

* Instrument MV/LV switchgear (switch position/state, current/voltage capture, RFID/NFC,
  fault injection) and feed an on-site edge server.
* Edge server must run the entire training site fully offline, syncing to Azure only when
  connectivity becomes available (exceeds the tender's PERF-05 "temporary outage" minimum).
* Stay Azure-aligned but vendor-neutral, with no fixed SKUs (per the BRD's own guardrails).
* Safety-critical interlocks/e-stops remain physically independent of the digital layer
  (SAFE-01/SAFE-02) — no protocol or platform choice may touch this boundary.

**Preferred Approach:**

* **Protocol:** OPC UA as the primary southbound instrumentation protocol (native
  certificate-based security, first-party Microsoft OPC Publisher bridge), paired with
  MQTT/Sparkplug B for the edge event bus and cloud sync (what Azure's edge-native broker
  speaks natively; Sparkplug B's birth/death convention solves offline-state detection).
  Modbus remains valid for simple legacy sensor I/O but should sit behind a protocol-
  translation gateway rather than serve as the primary protocol, given it has no native
  security. IEC 61850 (GOOSE/SV) is domain-authentic for real substation equipment but lacks
  a first-party Azure connector, so it is a "nice to have" companion spec, not the core
  protocol.
* **Edge compute:** classic Azure IoT Edge (not Azure IoT Operations) as the on-site
  runtime, fronted by a vendor-neutral OT protocol gateway (e.g., HiveMQ Edge-class or
  EdgeX Foundry) for Modbus/legacy translation. Rationale: classic IoT Edge is the only
  option with a documented, indefinite offline-operation guarantee; Azure IoT Operations —
  despite being Microsoft's current recommended platform for new edge-connected solutions —
  has a documented 72-hour offline ceiling with degradation, which directly conflicts with
  the fully-offline requirement. This choice is confirmed durable, not merely provisional:
  classic IoT Edge shipped a new LTS release (1.6, supported through November 2028) as
  recently as July 2026, carries no retirement date under Microsoft's Modern Lifecycle
  Policy, and its indefinite-offline claim is unchanged in current documentation — the real
  residual risk is positioning/auditability, since Microsoft's flagship architecture-
  guidance page now omits classic IoT Edge from its portfolio narrative entirely in favor of
  Azure IoT Operations (whose 72-hour ceiling is likewise confirmed unchanged). Treat this as
  a deliberate, evidence-based departure from Microsoft's current default recommendation,
  documented here for exactly that reason.

```text
Site (Haarlem / Zevenaar)
├── Layer 1: Physical switchgear (pre-existing, not partner-supplied)
├── Layer 2: Instrumentation (sensors, RFID/NFC, relays, I/O, fault injection)
│     └── Modbus/legacy sensors → protocol gateway (HiveMQ Edge-class or EdgeX Foundry;
│           disk-backed/Store-and-Forward offline buffer)
│     └── OPC UA-capable devices → direct to OPC Publisher module
└── Layer 3: Connect/Edge
      ├── Azure IoT Edge (classic) — on-site runtime, UPS-backed industrial PC/gateway
      │     ├── OPC Publisher module (OPC UA → MQTT/UADP)
      │     ├── Training scenario-engine module (local, offline-capable)
      │     └── edgeHub (local module bus, store-and-forward)
      └── Sync to Azure (IoT Hub, store-and-forward) only when connectivity available
            └── Layers 4-6 (Avanade/Alliander scope): Digital Twin, AI/agentic, Experience
```

**Considered Alternatives:**

* Azure IoT Operations as the primary edge platform — rejected as the sole platform due to
  its documented 72-hour offline ceiling (re-confirmed unchanged as of mid-2026), despite
  being Kubernetes-native (better suited to hosting a heavier scenario-engine/AI workload)
  and Microsoft's currently promoted default — a positioning gap that has since hardened:
  Microsoft's flagship "Introduction to Azure IoT" architecture guidance (updated
  2026-04-15) now omits classic IoT Edge from its portfolio narrative entirely. Worth
  revisiting if a future need for edge-hosted AI/agentic scoring at scale outweighs the
  offline-duration risk, or once Azure IoT Operations' offline guarantees mature. No
  official Microsoft guidance was found comparing the two platforms specifically on
  long-duration offline tradeoffs; this remains a genuine documentation gap best closed via
  a direct Microsoft/partner conversation rather than further public research.
* Azure Local (Stack HCI) as the infrastructure layer — rejected as unnecessarily heavy
  infrastructure for a 4-site (scaling to more) training-room deployment. Its "Disconnected
  operations" mode does offer an indefinite-offline posture comparable in spirit to classic
  IoT Edge, but confirmed research shows it is a formal, procurement-gated deployment tier
  requiring an eligible Microsoft agreement, a Standard-or-higher support plan, a documented
  sovereignty/compliance/remote-site business case, a dedicated management cluster, and
  Microsoft approval (up to 10 business days) — a materially heavier adoption bar than
  classic IoT Edge's offline capability, which needs none of this. It is also priced
  per-core and requires a prescriptive, partner-validated hardware catalog, cutting against
  the BRD's "no fixed SKUs" vendor-neutral posture. Remains a viable underlying
  infrastructure choice only if the hardware partner's proposal independently favors it and
  a genuine sovereignty/compliance driver exists.
* Modbus or IEC 61850 as the primary site-wide protocol — rejected as primary due to,
  respectively, no native security/event-push model, and no first-party Azure connector;
  both remain valid as secondary/companion protocols behind a gateway.
* mimik (mimOE / "Agentix Operating Engine") as an edge-compute candidate — rejected; mimik
  has pivoted entirely away from its historical mobile/hybrid edge-computing product
  ("edgeEngine," now archived) into an AI-agent orchestration runtime with no evidence of
  OPC UA/Modbus/MQTT/BACnet support, no documented Azure partnership, and no industrial
  OT/utility case study. It solves a compute/agent-orchestration problem, not the OT
  protocol-translation and offline-telemetry-sync problem this layer requires; forcing a fit
  here would not be evidence-based. Full detail:
  .copilot-tracking/research/subagents/2026-09-30/mimik-edgex-evaluation.md.
* EdgeX Foundry as a full replacement for classic Azure IoT Edge — rejected for that
  specific role (no first-party Azure bridge; its Store-and-Forward offline buffering is
  configurable but not marketed as an explicit indefinite guarantee the way classic IoT
  Edge's is; adopting it as the primary runtime would make its own Core Services the on-site
  system of record, a materially larger scope change). Accepted instead as a named,
  evidence-backed alternative to a commercial "HiveMQ Edge-class gateway" for the
  Modbus/BACnet/legacy protocol-translation role (see Preferred Approach above): it is
  vendor-neutral Linux Foundation/LF Edge open source (arguably a stronger fit to the BRD's
  "no fixed SKUs" posture than a commercial gateway), natively supports Modbus/BACnet/MQTT/
  RFID device services, is actively maintained (v4.0.2, May 2026), and has a direct
  industrial analog in Eaton's own Brightlayer Edge platform — though, like the primary
  recommendation, it also lacks a native OPC UA device service and would need a custom
  device service (supported via EdgeX's SDK) for that protocol. Full detail:
  .copilot-tracking/research/subagents/2026-09-30/mimik-edgex-evaluation.md.

### Hardware Partner Sourcing Approach

**Requirements:**

* Identify and engage a credible IoT/edge hardware partner before the 18 Nov 2026 submission
  deadline, given the bid team's own urgency flag (Marcel Westra, 29 Sep 2026).
* Partner must plausibly deliver layers 1-3: instrumentation retrofit, industrial networking,
  and an offline-capable edge server, across a multi-year framework with scalability to
  future sites.

**Preferred Approach:**

* Treat Axians Nederland and ATS Global as the highest-confidence starting points for direct
  outreach/RFI, given their explicit utilities/smart-grid practices and OT/IT integration
  pedigree — but validate both directly (reference calls, technical deep-dive, OT/security
  posture review) since no public evidence confirms either has done this exact kind of work.
* Treat the Automation-List.com NL system-integrator directory and Schneider
  Electric/Weidmüller alliance-partner directories as a secondary sourcing pool if Axians/ATS
  do not pan out.
* Do not rely on public web research alone to select a partner — this is a narrow enough
  niche (utility training-room hardware retrofit) that a targeted RFI/market-sounding
  exercise is necessary regardless of which candidates are shortlisted.
* Innotractor, the one candidate the bid team had informally already considered, is
  confirmed as a non-match and should be dropped from consideration.

**Considered Alternatives:**

* Large OEM automation vendors (Schneider Electric, Siemens, ABB, Eaton) as direct prime
  candidates — considered but deprioritized as likely oversized/commercially mismatched for
  a EUR 3.04M-class framework; more plausible as a component/hardware source behind a
  smaller systems-integrator prime.
* Electrical infrastructure/switchgear contractors (e.g., Alliander's own Qirion, or peers
  like Omexom/Volker/Croonwolter&dros) as direct primes — considered but deprioritized since
  the BRD explicitly excludes building physical switchrooms and these firms are generally
  not specialist IoT/edge-compute integrators; better suited as a subcontractor/advisor on
  physical retrofit constraints.
