---
title: Digital Schakellokalen Solution Overview
description: Consolidated solution overview for the Alliander Digital Schakellokalen tender response, with a dedicated section per architecture layer (business, enterprise, solution, hardware, network, data, security)
author: Avanade Bid Team
ms.date: 2026-09-30
ms.topic: reference
---

> **Status: DRAFT.** Working draft for internal bid team review, not yet cleared for submission to Alliander. Sections marked **Placeholder** have no content yet and are tracked as open work below.

## Purpose

This is the single source of truth for the Digital Schakellokalen solution overview during the drafting phase. It replaces the earlier separate solution-overview, architecture-diagram, and draft-solution-response files, merged here to avoid duplication and drift. It also tracks completion status per architecture layer, since GC1 and GC2 scoring depends on a credible, complete architecture package, not a single diagram.

## Architecture Layers: Status

| Layer | Covers | Status |
|---|---|---|
| [Business architecture](#business-architecture) | Stakeholders, training outcomes, scope boundary, value chain across the 8-year framework | Drafted from BRD + recon facts |
| [Enterprise architecture](#enterprise-architecture) | Fit with Alliander's existing systems (Archipel, LVS), portfolio and capability mapping | Drafted from recon facts, standards/framework fit still open |
| [Solution architecture](#solution-architecture) | The six-layer component model: physical, instrument, edge, digital twin, AI/agentic, experience | Drafted (suggested, not final) |
| [Hardware architecture](#hardware-architecture) | Instrumentation and edge device design, fail-safe behaviour, field-replaceability | Drafted from recon facts |
| [Network architecture](#network-architecture) | On-site industrial network and protocol stack, edge-to-cloud connectivity, offline operation, segmentation | Drafted from recon facts, protocol choice not yet confirmed |
| [Data architecture](#data-architecture) | Digital twin data model, learning-data flows, EEA residency, retention | Drafted from recon facts, retention policy still open |
| [Security architecture](#security-architecture) | IAM/IGA integration, SIEM export, encryption, certifications, fail-safe independence | Drafted from recon facts |

## Architecture Summary

The Digital Schakellokalen solution is a layered edge-to-cloud architecture. Unlike a typical cloud-first system, the defining constraint is that the on-site edge must keep training running through a temporary loss of internet connectivity (Bijlage L PERF-05); Avanade's design goes further and treats the edge as capable of running a full site with no dependency on internet breakout, syncing to the cloud only when connectivity is available.

**Architectural decisions driven directly by tender requirements:**

1. **Edge-first compute.** The on-site edge server is the system of record during a training session. Cloud synchronization happens asynchronously whenever connectivity allows (Bijlage L PERF-05).
2. **Fail-safe independence.** Physical safety systems, interlocks, emergency stops, and lock-out/tag-out mechanisms sit outside the digital control loop entirely. A failure of the digital layer degrades to a predefined safe state and never disables physical safety (Bijlage L SAFE-01, SAFE-02).
3. **Hardware abstraction boundary.** Hardware-specific protocols and drivers are confined to the integration layer, keeping the platform modular and the instrumented panels replaceable without redesigning the core solution (Bijlage L ITAR-03).
4. **Identity federation, not local authentication.** Every identity touchpoint routes through Alliander's IAM platform; no local credential store exists anywhere in the solution, including on edge hardware (Bijlage V §3.1-3.2).
5. **EEA-only data residency.** The digital twin and learning-data store are hosted exclusively within the EEA (Bijlage L IT-03, LCD11).

## Business Architecture

Grounded in the [Hardware BRD](../Hardware%20Solution/alliander-schakellokalen-hardware-brd.md) and the [tender hardware recon](../Hardware%20Solution/recon/tender-hardware-recon.md).

**Stakeholders:**

| Stakeholder | Role |
|---|---|
| Alliander training and learning organisation | Defines training scenarios and pedagogy; primary user of the instructor dashboard and learning data |
| Alliander trainees and monteurs | End users of the physical instrumentation; perform switching operations and receive fault scenarios |
| Alliander IAM, security, and SIEM teams | Own the identity platform the solution must integrate with; consume authentication event exports |
| Alliander procurement and contract management | Own the framework agreement, SLA, and the 8-year contract term across up to 5 one-year extensions |
| Avanade bid and delivery team | Designs layers 4-6, authors the proposal, integrates the hardware partner's deliverables |
| IoT hardware partner | Sources, builds, enables, services, and supports layers 1-3 |

**Business outcomes the framework agreement is buying:**

* Digital coverage of all 31 Bijlage T core training scenarios (10 OV, 11 MK, 5 LS, 5 MS), replacing instructor-only manual observation (Bijlage L ACC-03).
* Objective, data-backed scoring of trainee sessions instead of subjective instructor judgement, feeding the GC3 learning-data ambition.
* Training availability of at least 99% during training hours, with fallback scenarios proven at acceptance (Bijlage L PERF-03, PERF-04; Bijlage Q SLA).
* Scalability: the same architecture absorbing additional training environments added under the framework, without redesign (Aanbestedingsleidraad §1.3; Bijlage N GC2).

**Value chain across the 8-year term:** a 3-year base contract plus up to 5 one-year extensions (max. 8 years total). Implementation starts with a pilot/PoC on one representative training environment before broader rollout (Bijlage L IMP-03), then scales across the initial 4 environments (1 schakellokaal + 1 meetveld each in Haarlem and Zevenaar) and any further environments added later in the term.

**Scope boundary in business/commercial terms** (Bijlage J pricing structure): hardware delivery ("Levering van Hardware") and hardware installation ("Aansluiten van hardwarecomponenten") are one-time, separately priced line items owned by the hardware partner. Ongoing hardware upkeep is folded into the annual "Technisch beheer en support" line, not billed as a separate hardware maintenance item. Avanade's software development, base licence, and functional/technical support line items cover layers 4-6. All pricing is all-in; no line items may be added after the questions deadline.

## Enterprise Architecture

Grounded in the [tender hardware recon](../Hardware%20Solution/recon/tender-hardware-recon.md) §2-3.

**Existing Alliander systems this solution must coexist with:**

* **Archipel** — an existing system being replaced under a separate tender, out of scope here. The new platform must not depend on Archipel and must be able to operate independently of whatever replaces it (Aanbestedingsleidraad §1.5, interpreted).
* **LVS (Leer Volg Systeem)** — Alliander's existing learning management system. Not an integration requirement today, but the platform must expose open APIs so future LVS integration is possible; LVS API-readiness is itself a GC3 quality-scoring dimension.
* **Alliander IAM** — the one true integration knock-out (see [Security Architecture](#security-architecture)). Every identity touchpoint in the solution, including edge hardware, routes through it.

**Operating-model constraint (Bijlage L Voorblad, explicit statement):** Alliander is explicit that it does *not* want a generic enterprise simulation platform. It wants a pragmatic, manageable digital control layer, and trainers must be able to manage scenarios independently, without structural dependency on the supplier's development capacity after go-live. This shapes the enterprise fit: the solution should minimize ongoing custom-development dependency and favor configurable scenario management over code-level changes.

**Portfolio/capability mapping against Alliander's broader IT/OT estate:** not specified anywhere in the tender documents read to date. No enterprise architecture framework (for example TOGAF, ArchiMate), reference architecture, or IT/OT segmentation standard is named by Alliander. This is a genuine open question rather than something inferable from available sources — worth raising if a further clarification round (NvI 2) opens.

## Solution Architecture

The diagram below is rendered from the editable draw.io source: [architecture-diagram.drawio](./architecture-diagram.drawio). Open it in the draw.io desktop app, diagrams.net, or the VS Code draw.io extension to edit it, then export as PNG over [architecture-diagram.png](./architecture-diagram.png) to refresh the image below.

> **Image is stale.** `architecture-diagram.png` was exported before the latest diagram fixes (the Layer 3 → Layer 6 live-view connection, and the hedged protocol/trainee-ID labels) and was exported with a dark background instead of the intended light-grey scope containers. Re-export from the current `.drawio` file before this goes into a submission.

![Digital Schakellokalen solution architecture diagram: Partner Scope (Layers 1-3, hardware, offline-capable) on the left and Avanade/Alliander Scope (Layers 4-6, digital, cloud-hosted EEA) on the right, with Alliander IAM and physical safety systems shown as cross-cutting concerns below each column.](./architecture-diagram.png)

### Legend

* Solid arrow = data flow within a boundary
* Dashed / labeled cross-link = cross-cutting or optional connection
* Blue boxes (PS) = hardware partner delivery scope, offline-capable
* Green boxes (AS) = Avanade/Alliander digital scope, cloud-hosted (EEA)
* Orange boxes = cross-cutting concerns (identity, physical safety)

### Key Relationships

* Layers 1 through 3 form the hardware partner's delivery scope; layer 3 is the only component that must keep a training session running through a temporary loss of internet connectivity.
* Layer 3 connects to Layer 6 directly over the local network for live instructor/trainee observation during a session; this connection does not depend on cloud reachability.
* The edge-to-cloud sync (Layer 3 to Layer 4) is a separate, asynchronous, best-effort path; a training session never blocks on cloud reachability.
* Alliander's IAM platform federates identity into the edge for trainee and instructor authentication, with no local credential store anywhere in the stack.
* Physical safety systems remain entirely independent of the digital layer by design, satisfying SAFE-01 and SAFE-02.
* Layers 4 through 6 are Avanade and Alliander's digital scope, hosted with EEA-only data residency.

## Hardware Architecture

Grounded in the [tender hardware recon](../Hardware%20Solution/recon/tender-hardware-recon.md) and the [Hardware BRD](../Hardware%20Solution/alliander-schakellokalen-hardware-brd.md).

**In scope for the hardware partner** (Aanbestedingsleidraad §1.5.4; Bijlage L HW-01, HW-02): relays, I/O boards, cabling, comparable control technology, smart cables, sensors, switches, plus all interface components needed to couple the digital solution to the existing physical training assets.

**Out of scope**: the physical switchgear itself (already exists), generic physical infrastructure (standard cabling, power supplies, switchrooms), and measurement equipment (Aanbestedingsleidraad §1.5.5; Bijlage L SCOPE-04, MV-04).

**Design constraints that shape the hardware:**

* **Fail-safe by default (SAFE-01).** Every relay board, I/O module, and edge controller must default to a predefined safe state on power loss or communication loss: active scenarios terminated, outputs placed safe, physical safety provisions unaffected.
* **Hardware abstraction (ITAR-03).** Hardware-specific protocols, drivers, and implementation detail live only in the integration/hardware layer, so panels are field-replaceable without redesigning the platform.
* **Reproducible, deterministic fault injection (Bijlage T general principles).** Faults must be resettable by the instructor without interrupting other trainees, and reproducible identically across sessions; some scenarios (MK-07, MK-08) additionally require random per-phase/per-dwelling assignment.
* **Operating voltage for simulation hardware is 20-50V DC** — an Avanade design intent carried from the 2023/2025 concept work, not yet confirmed in the tender documents themselves.
* **Intensive repeated use.** Hardware must tolerate continuous training-environment duty cycles (Bijlage T general principles).
* **Lifecycle management (LCD08).** Only actively vendor-supported hardware may be used; the contract must state explicit end-of-support dates for every component.

**Per-domain instrumentation needs** (from the 31 Bijlage T core scenarios): individually addressable relay/modem control per street-lighting circuit (OV), per-meter and per-dwelling fault injection in the meter cabinet (MK), per-junction multi-fault simulation and phase-rotation signalling (LS), and signal-level fault injection on real MV switchgear (SVS, WEGA, SF-6 gauge) without exposing real MV voltage to trainees (MS). See the recon document's §5 for the full scenario-by-scenario breakdown.

## Network Architecture

> Protocol names below (OPC-UA, Modbus, MQTT) are an Avanade design assumption for an industrial edge gateway of this kind. They are **not specified or confirmed anywhere in the tender documents** and must be validated against the hardware partner's proposal and the site survey before being stated as fact in a submission.

**On-site network, per training environment (Haarlem and Zevenaar, 4 environments total):**

* An on-site edge gateway/server aggregates instrumentation signals (relays, I/O, sensors) over an industrial fieldbus/protocol stack — assumed OPC-UA and/or Modbus for switchgear I/O, MQTT for event/telemetry publishing — and exposes a single integration point to the digital layer above it (ITAR-03 hardware abstraction boundary).
* The edge server is backed by UPS and is designed to keep a training session running through a temporary loss of the site's internet connection (PERF-05); it does not depend on reaching the cloud to execute or score a scenario.
* Cloud synchronization is asynchronous and best-effort: session state, scenario results, and learning data upload to the digital twin when connectivity is available, and queue locally otherwise.
* Multi-site isolation: Haarlem and Zevenaar are treated as independent network segments; a fault or outage at one site has no effect on the other.

**Edge-to-cloud connectivity:**

* All data traffic is encrypted in transit at TLS 1.2 minimum, TLS 1.3 preferred (Bijlage L IT-04).
* No local password database or legacy/weak auth flow (Implicit Flow, ROPC, Basic Auth, NTLM) is permitted on any network-connected component, including edge gateways (Bijlage V §3.1).
* Open APIs and open standards are required end to end to avoid vendor lock-in and to keep the architecture modular and scalable to additional training environments added under the framework (Bijlage N GC2, Bijlage L HW-24, HW-25).

**Open items**: confirm the actual fieldbus/protocol choice with the hardware partner during the site survey; define VLAN/segmentation design and firewall rules between the OT instrumentation network, the edge server, and the IT network once a partner and physical topology are selected; this section should not be treated as final until that happens.

## Data Architecture

Grounded in Bijlage L (ITAR-06, IT-03, IT-04, LCD11) and Bijlage N GC3.

**Digital twin data model:** a central, authoritative digital network model representing both the physical and logical network — topology, live component state, active scenario/fault state, and session history (Bijlage L ITAR-06). This model is the basis for scenario analysis, simulation, validation, and learning-data extraction, and it is the same Layer 4 store referenced in the [Solution Architecture](#solution-architecture).

**Learning-data model (GC3):** trainee actions and outcomes captured per session — which scenario ran, what faults were injected, how the trainee responded, and the resulting score — structured as a session dossier. This is the dataset GC3 scores the solution against, and it is also the dataset that would eventually flow into LVS if that integration is built.

**Edge-to-cloud data flow:** consistent with the [Network Architecture](#network-architecture) design, session and scenario data is captured locally at the edge first (so a session never depends on cloud reachability), then synced asynchronously to the cloud-hosted digital twin and learning-data store when connectivity is available. Conflict handling and exact sync cadence are not yet designed.

**EEA-only residency (knock-out):** all data is stored exclusively within the EEA — stated twice independently in Bijlage L (IT-03, and again under cloud-provider requirements as LCD11). The supplier must supply a complete, current inventory of every datacentre, cloud region, and storage service used, including physical country and role (production, test, backup, archival, failover); any change to storage locations must be reported to Alliander in advance for re-assessment.

**Encryption:** data traffic is encrypted in transit at TLS 1.2 minimum, TLS 1.3 preferred (Bijlage L IT-04). Encryption at rest is not explicitly mandated in the tender documents read to date; treat industry-standard at-rest encryption (for example AES-256) as an Avanade design default pending confirmation, not a quoted tender requirement.

**Open items:** retention period (how long session/learning data is kept, and any Alliander-driven deletion requirement) is not specified anywhere in the tender documents and needs a decision before this section can be called complete.

## Security Architecture

Grounded in Bijlage V (IAM) and the relevant Bijlage L non-functional and cloud-provider requirements.

**Identity and access management — knock-out requirement.** The solution must meet minimum security level A for both Access Management (AM) and Identity Governance and Administration (IGA), or the bid is disqualified outright (Bijlage V).

* **AM (level A):** OIDC/OAuth 2.0 with Authorization Code flow + PKCE S256 preferred; SAML 2.0 acceptable as fallback. Implicit Flow, ROPC, Basic Auth, NTLM, and local password databases are all explicitly prohibited (Bijlage V §3.1).
* **IGA (level A):** SailPoint connector preferred; SCIM 2.0 provisioning acceptable; manual provisioning is not acceptable above level A. Authentication events must be exportable to Alliander's SIEM (Bijlage V §3.2).
* This applies to every network-connected component, including edge gateways and any device with a login interface (for example RFID/NFC trainee identification readers) — no local credential stores anywhere.

**Certifications (organisational, knock-out):** ISO 27001 (or equivalent, or SOC 2 Type II covering the relevant services) and ISO 9001 (or equivalent) are both mandatory for the supplier (Aanbestedingsleidraad §4.1; Bijlage L LCD19).

**Encryption:** TLS 1.2 minimum, TLS 1.3 preferred, for all data traffic (Bijlage L IT-04).

**Fail-safe / safety independence** (also foundational to hardware and network design): the digital solution must never override, disable, or bypass physical safety provisions, and must fail to a safe state on malfunction, power loss, or communication loss (Bijlage L SAFE-01, SAFE-02).

**Open items:** a full STRIDE-style threat model per component/boundary, and a formal risk analysis for working with live/energised components in training scenarios (required deliverable per Bijlage T), are not yet produced.

## Scope Boundary

| Layers | Scope owner | Operates |
|---|---|---|
| 1-3 (Physical, Instrument, Connect) | Hardware partner | Fully offline-capable, on-site |
| 4-6 (Digital Twin, AI & Agentic, Experience) | Avanade / Alliander | Cloud, EEA-hosted, syncs asynchronously from the edge |

## Next Steps

* **Blocked on external input — confirm the Network architecture's protocol assumptions (OPC-UA/Modbus/MQTT)** with the hardware partner and the Zevenaar/Haarlem site survey before stating them as fact in a submission. This cannot be resolved from the tender documents alone; it needs a conversation with the partner.
* Decide the data retention policy (how long session/learning data is kept) — not specified in the tender documents; needs an Alliander- or Avanade-side decision.
* Confirm whether Alliander has an enterprise architecture framework or IT/OT segmentation standard the solution should align to; not stated anywhere in the tender documents — a good candidate for an NvI 2 clarification question if another round opens.
* Confirm with the bid lead whether device-specific references (ABB SafeRing, WEGA, SVS) should remain indicative-only in the submitted version, consistent with the hardware BRD's guardrails.
* Cross-check against the final RFP text once NvI 2 (if issued) closes any open questions.
* Get a solution-architecture review of this document before it goes to Kryptonite-style red-team review.

## Related Documents

* [Hardware BRD](../Hardware%20Solution/alliander-schakellokalen-hardware-brd.md) — outcome-based hardware capability requirements for the IoT partner
* [Tender hardware recon](../Hardware%20Solution/recon/tender-hardware-recon.md) — source reconnaissance from the RFP documents
* [architecture-diagram.drawio](./architecture-diagram.drawio) — editable source for the solution architecture diagram
