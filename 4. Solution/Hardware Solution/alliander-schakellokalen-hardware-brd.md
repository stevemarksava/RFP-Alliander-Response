---
title: Alliander Digital Schakellokalen Hardware BRD
description: Outcome-based hardware requirements for the IoT partner sourcing, building, enabling, servicing, and supporting the Digital Schakellokalen training-centre hardware layer
author: Avanade Bid Team
ms.date: 2026-09-30
ms.topic: reference
---

## Executive Summary

Alliander, the Dutch regional grid operator, trains its electrical engineers and monteurs at physical training centres called schakellokalen (switching rooms), where they practise switching operations on real medium- and low-voltage switchgear. Alliander has issued an open tender, "Digitale aansturing van oefenomgevingen voor technische opleidingen" (tender 226705), for a supplier to design, build, and operate a digital control layer that connects these training environments to a managed platform so scenarios can be run, monitored, and scored digitally, and that keeps training running when the internet connection is lost.

Avanade is bidding for this framework agreement. To deliver the hardware layer that makes training assets digitally observable and controllable, Avanade needs an IoT hardware partner. This document defines what that partner must deliver: not a bill of materials, but a set of outcome-based capability requirements covering sourcing, building, enabling, servicing, and supporting the instrumentation and edge-connectivity layer across the initial four training environments in Haarlem and Zevenaar, with scalability to future sites.

The requirements in this document are drawn primarily from the tender's own documents: the tender guide (Aanbestedingsleidraad) and its appendices, in particular the requirements specification (Bijlage L) and the core scenarios (Bijlage T). Two principles shape every other requirement. Physical safety systems must remain completely independent of, and unaffected by, the digital layer [Bijlage L SAFE-01, SAFE-02]. And each site must keep training when its internet connection is lost [Bijlage L PERF-05]; Avanade's design goes further and runs each site fully offline. Any device-specific detail in this BRD is indicative only. The partner's proposal, validated against a joint site survey, determines the final hardware selection.

## Business Context and Background

Alliander's current training model relies on physical schakellokalen and meetvelden (measurement fields) where trainees operate real switchgear under instructor supervision. The 2027 framework agreement replaces manual, instructor-only observation with a digital control layer that senses device state, injects repeatable and randomized faults, and records session outcomes, while leaving all physical safety mechanisms untouched.

Avanade produced an earlier IoT and Azure concept for this training centre in 2023 and a ROM proposal in 2025. Those documents describe an architecture that begins with real switchgear (layer 1), adds sensing and actuation (layer 2), connects it through an on-site edge server that must run offline (layer 3), and then extends that foundation into a digital twin (layer 4), AI and agentic training aids (layer 5), and a trainee and instructor experience (layer 6). The current RFP formalizes and procures the underlying platform. Layers 1 through 3 are the hardware partner's mandate; layers 4 through 6 are how Avanade and Alliander extend value once the devices are digital and connected.

## Problem Statement and Business Drivers

Alliander cannot scale, standardize, or digitally assess switching-operation training using manual observation alone. Instructors need a way to inject deterministic and randomized faults consistently across 31 defined core scenarios (Bijlage T), score sessions objectively, and extend training capacity to additional locations without re-engineering the platform each time. At the same time, Alliander operates critical infrastructure and cannot accept a digital layer that depends on live connectivity, introduces a security exposure through weak identity controls, or in any way interferes with the physical safety systems already protecting trainees.

The business drivers are procurement-mandated and non-negotiable, formalized in the tender guide as knock-out (KO) minimum requirements. Failure to meet them disqualifies a bid outright. This BRD's requirements distinguish between such mandatory (Must) requirements and requirements that are scored for quality (Should) or are optional (Could), so the hardware partner can prioritize its proposal.

## Business Objectives and Success Metrics

| Objective | Success metric | Source |
|---|---|---|
| Enable resilient local training operation at every site | Training sessions run and are scored without dependency on internet connectivity; the solution functions during temporary internet outage per Bijlage L PERF-05. Avanade's design extends this to fully offline-capable edge operation as a design choice that exceeds the tender requirement. Verified during acceptance testing | Bijlage L PERF-05 |
| Demonstrate credible, integration-ready hardware scope in the bid | GC1 (implementation plan, 35% of total score) scored above the disqualifying floor of 0, driven partly by the hardware integration narrative | Bijlage N GC1 |
| Cover all defined training scenarios | All 31 Bijlage T core scenarios (10 OV, 11 MK, 5 LS, 5 MS) demonstrated as working on instrumented hardware at formal acceptance | Bijlage L ACC-03 |
| Protect trainee and asset safety | Zero incidents where the digital layer overrides, disables, or bypasses a physical safety provision, verified through the required risk analysis | Bijlage L SAFE-01, SAFE-02 |
| Maintain training availability | Minimum 99% availability of training environments during training hours, per agreed SLA KPIs | Bijlage L PERF-03; Bijlage Q |
| Scale beyond the initial four environments | Hardware architecture and spares model absorb additional training locations added under the framework without redesign | Aanbestedingsleidraad §1.3; Bijlage N GC2 |

## Stakeholders and Roles

| Stakeholder | Role |
|---|---|
| Alliander training and learning organisation | Defines training scenarios and pedagogy; primary user of the instructor dashboard and learning data |
| Alliander trainees and monteurs | End users of the physical instrumentation; perform switching operations and receive fault scenarios |
| Alliander IAM, security, and SIEM teams | Own the identity and access management platform the hardware and edge software must integrate with; consume authentication event exports |
| Alliander procurement and contract management | Own the framework agreement, SLA, and the 8-year contract term across up to 5 one-year extensions |
| Avanade bid and delivery team | Designs the digital control layer (layers 4 through 6), authors the winning proposal, and integrates the hardware partner's deliverables into the overall solution |
| IoT hardware partner (this BRD's audience) | Sources, builds, enables, services, and supports the physical instrumentation and edge-connectivity layer (layers 1 through 3, with layer 1 largely pre-existing) |

## Solution Overview

The solution is best understood as a six-layer progression, from the physical switchgear that already exists at Alliander's training centres through to the trainee and instructor experience. The hardware partner's mandate covers layers 1 through 3. Layers 4 through 6 build on a digitally connected foundation and are Avanade's and Alliander's responsibility to design and deliver.

1. Physical: the existing training switchgear. Medium- and high-voltage panels, ring main units, disconnectors, breakers, earthing switches, transformers, and busbars, plus low-voltage distribution boards, meter cabinets, and street-lighting circuits. This equipment already exists and is out of the hardware partner's supply scope; the partner instruments it.
2. Instrument: sensing and actuation added to the physical assets. Switch position and state sensing, current and voltage signal capture, RFID or NFC identification on components or trainees, indicator and interlock monitoring, and controlled fault injection at the instrumentation level.
3. Connect (edge): the on-site IoT gateway and industrial network that links instrumentation to a training-scenario engine. This layer includes the critical on-site edge server, backed by UPS. The tender requires the solution to keep working during a temporary internet outage [Bijlage L PERF-05]; in Avanade's design the edge server runs the entire site fully offline, with no dependency on internet breakout, and syncs to the cloud only when connectivity becomes available.
4. Digital twin: a live virtual replica of the switchgear, reflecting real-time state, topology, energisation, scenario and fault state, and session history. Built on top of the connected foundation the hardware partner enables.
5. AI and agentic capability: vision-based step validation, a procedure copilot, a fault and scenario engine, and automated scoring and feedback. Enabled once devices are digital and connected, not a hardware partner deliverable.
6. Experience: the instructor dashboard, trainee HMI or tablet interface, optional AR or MR overlay, and voice interaction. The user-facing layer built on everything below it.

A cross-cutting principle applies to every layer the hardware partner touches. Safety and identity are independent of the digital layer. Hard-wired interlocks, emergency stop circuits, physical lock-out and tag-out procedures, and access control must never be overridable by software. The digital layer observes and augments training; it does not control real electrical safety.

## Scope

### In Scope for the Hardware Partner

* Solution-specific hardware required for the digital control layer to function: relays, I/O boards, cabling, comparable control technology, smart cables, sensors, and switches [Aanbestedingsleidraad §1.5.4; Bijlage L HW-01].
* Instrumentation and retrofit work on the existing MV, LV, meterkast, and street-lighting (FlexOV) assets across Haarlem and Zevenaar's schakellokalen and meetvelden [Bijlage T scenario groups].
* On-site edge compute, industrial networking, and power/UPS hardware needed to run training scenarios locally, with resilience to temporary internet connectivity loss [Bijlage L PERF-05]. Avanade's design choice is fully offline-capable edge operation.
* Preventive maintenance, calibration, spares, firmware and patch management, and support across the 3-year base term plus up to 5 one-year extensions [Aanbestedingsleidraad §1.2, §1.4].
* A complete hardware manifest: quantities, technical specifications, warranty periods, expected lifespan, and maintenance and replacement requirements [Bijlage L HW-02].

### Out of Scope for the Hardware Partner

* Design and physical construction of the training environments themselves (the schakellokalen and meetvelden as buildings and rooms) [Aanbestedingsleidraad §1.5.5].
* Delivery and setup of general measurement equipment (meetapparatuur) used by trainees to take readings; the solution observes and controls the scenario, it does not read the measuring equipment itself [Bijlage L MV-04].
* Generic physical infrastructure: standard cabling, power supplies, and the switchrooms as physical spaces [Aanbestedingsleidraad §1.5.5].
* Development of training content or didactic learning lines [Aanbestedingsleidraad §1.5.5].
* Replacement of the Archipel system, which is being procured under a separate tender [Aanbestedingsleidraad §1.5.5].

## Hardware Capability Requirements

Each requirement is expressed as an outcome the partner must be able to deliver, not a prescribed product. Priority follows the tender's own classification: Must reflects a knock-out (KO) or mandatory (Eis) requirement whose failure disqualifies the bid; Should reflects a scored quality criterion; Could reflects a desired-but-optional (Wens) item or an item still pending confirmation.

### Source

| ID | Requirement | Priority | Source |
|---|---|---|---|
| BR-001 | The partner shall be able to source instrumentation-grade sensing hardware, such as relays, I/O modules, smart cables, and position or state sensors, suitable for retrofitting onto existing MV and LV switchgear without altering its original electrical function. | Must | Bijlage L HW-01; Aanbestedingsleidraad §1.5.4 |
| BR-002 | The partner shall be able to source edge compute or gateway hardware capable of running the full training and scenario engine locally, remaining operational during temporary internet connectivity loss. Avanade's design intent is fully offline-capable edge operation, which goes beyond the tender's minimum of resilience to temporary outage. | Must | Bijlage L PERF-05 |
| BR-003 | The partner shall be able to source industrial networking hardware, such as managed switches and protocol gateways, supporting industrial protocols (for example OPC-UA, Modbus, or MQTT) isolated from Alliander's corporate IT network. | Must | Bijlage T Algemene uitgangspunten; Bijlage L ITAR-03 |
| BR-004 | The partner shall be able to source power and UPS hardware that keeps the instrumentation and edge layer able to reach a defined safe state through a power interruption. | Must | Bijlage L SAFE-01 |
| BR-005 | The partner shall be able to source standardized, ruggedized mounting and enclosure hardware suitable for repeated, intensive use in a training environment. | Should | Bijlage T Algemene uitgangspunten |
| BR-006 | The partner shall be able to source trainee and instructor identification hardware, such as an RFID or NFC reader, compatible with Alliander's existing credential format, to be confirmed via site survey. | Should | 2023 Avanade requirements document; Bijlage V |
| BR-007 | The partner shall be able to source optional visual or camera hardware to support supervision or future learning-data capture, subject to confirmation this is in scope. | Could | Open question: camera scope (see Open Questions and Assumptions) |
| BR-008 | The partner shall be able to standardize hardware classes across Haarlem, Zevenaar, and future training sites to minimize spares inventory and support cost. | Should | Bijlage N GC2 |

### Build

| ID | Requirement | Priority | Source |
|---|---|---|---|
| BR-010 | The partner shall be able to instrument existing MV switchgear, indicatively including ring main units, WEGA voltage-detection units, and SVS switches, without modifying the switchgear's primary electrical safety function. | Must | Bijlage T P2-MS-01 through P2-MS-05; Bijlage L SAFE-02 |
| BR-011 | The partner shall be able to instrument LV distribution and meterkast assets, indicatively including kWh meters, MSR fuses, CAM connectors, and main switches, to enable per-circuit or per-dwelling fault simulation. | Must | Bijlage T P2-LS and P2-MK scenarios |
| BR-012 | The partner shall be able to instrument street-lighting (FlexOV) circuits with individually addressable relay and modem control per circuit. | Must | Bijlage T P2-OV scenarios |
| BR-013 | The partner shall be able to perform all cabling, wiring, and cabinet retrofit work needed to connect instrumentation to the edge layer, using labelling conventions that support long-term maintainability. | Must | Bijlage L HW-02 |
| BR-014 | The partner shall be able to complete retrofit and build work without removing, bypassing, or degrading any existing physical safety provision, including interlocks, emergency stops, or lock-out and tag-out mechanisms. | Must | Bijlage L SAFE-02 |
| BR-015 | The partner shall be able to design instrumentation so that adding new panels or circuits at existing or future sites does not require re-engineering the core hardware architecture. | Should | Bijlage L IF-06; Bijlage N GC2 |
| BR-016 | The partner shall be able to perform all build work in compliance with NEN 3140 and NEN-EN 50110 wherever live or simulated-live components are involved. | Must | Bijlage T Algemene uitgangspunten |

### Enable

| ID | Requirement | Priority | Source |
|---|---|---|---|
| BR-020 | The partner shall be able to enable local edge operation of every training scenario, with the edge server remaining operational during temporary internet connectivity loss (Bijlage L PERF-05, Eis). Avanade's design intent is fully offline-capable operation, exceeding this minimum, so that no session is ever dependent on cloud connectivity. | Must | Bijlage L PERF-05 |
| BR-021 | The partner shall be able to enable deterministic, repeatable fault injection so an identical scenario can be reproduced across sessions. | Must | Bijlage T Algemene uitgangspunten |
| BR-022 | The partner shall be able to enable randomized fault assignment, software-driven and hardware-executed, so trainees cannot predict which fault they will receive. | Must | Bijlage T Algemene uitgangspunten |
| BR-023 | The partner shall be able to enable independent, instructor-controlled activation and reset of one trainee's scenario without interrupting other concurrent sessions, supporting a minimum of four simultaneous participants. | Must | Bijlage T Algemene uitgangspunten; Bijlage L SL-04 |
| BR-024 | The partner shall be able to enable commissioning and provisioning of a device identity for every instrumentation and edge component, supporting secure onboarding and replacement. | Must | Bijlage L ITAR-03 |
| BR-025 | The partner shall be able to enable synchronization of session, scenario, and state data from the on-site edge server to the cloud digital twin whenever connectivity becomes available, without requiring connectivity during the session itself. | Must | Bijlage L PERF-05; Bijlage N GC3 |
| BR-026 | The partner shall be able to enable integration of trainee and instructor authentication with Alliander's IAM platform (OIDC and OAuth 2.0 with PKCE preferred, SAML 2.0 acceptable), with authentication events exportable to Alliander's SIEM, and with no local password database on any hardware or edge component. | Must | Bijlage V §3.1 to §3.2 |
| BR-027 | The partner shall be able to enable a fail-safe response so that on malfunction, power loss, or communications loss, all instrumentation and edge hardware autonomously revert to a predefined safe state, terminating the active scenario, placing outputs in a safe position, and leaving physical safety systems unaffected, within a time bound the partner proposes. | Must | Bijlage L SAFE-01 |
| BR-028 | The partner shall be able to enable open, documented APIs and industry-standard protocols at the hardware and edge integration layer to avoid vendor lock-in and support future integration with Alliander's LVS. | Should | Bijlage N GC2, GC3 |
| BR-029 | The partner shall be able to enable automatic digital updates to direction indicators and station designations whenever the represented network configuration changes. | Should | Bijlage L HW-03 |
| BR-030 | The partner shall be able to enable visual or vision-based capture at the instrumentation layer to support future AI-based step validation, subject to confirmation of scope. | Could | Open question: camera scope (see Open Questions and Assumptions) |

### Service

| ID | Requirement | Priority | Source |
|---|---|---|---|
| BR-040 | The partner shall be able to provide preventive maintenance and calibration for all instrumentation and edge hardware across the full contract term, up to 8 years. | Must | Aanbestedingsleidraad §1.2, §1.4 |
| BR-041 | The partner shall be able to provide a complete hardware manifest documenting quantities, technical specifications, warranty periods, expected lifespan, and maintenance or replacement requirements for every component delivered. | Must | Bijlage L HW-02 |
| BR-042 | The partner shall be able to provide firmware and software patching and lifecycle management for all hardware and embedded software components, communicating explicit end-of-support dates. | Must | Bijlage L LCD08 |
| BR-043 | The partner shall be able to provide spares and an RMA process sized to sustain the required in-service availability of the training environments. | Must | Bijlage Q; Bijlage L PERF-03 |
| BR-044 | The partner shall be able to propose end-of-life and replacement lifecycle planning aligned with the maximum 8-year contract term. | Should | Bijlage L LCD08 |
| BR-045 | The partner shall be able to offer circular or sustainable hardware sourcing and disposal options in support of Alliander's social responsibility (MVO) scoring criterion. | Could | Open question: MVO hardware requirements (see Open Questions and Assumptions) |

### Support

| ID | Requirement | Priority | Source |
|---|---|---|---|
| BR-050 | The partner shall be able to provide on-site and remote support that meets a minimum 99% availability target for training environments during training hours, with SLA KPIs proposed and agreed with Alliander. | Must | Bijlage L PERF-03; Bijlage Q |
| BR-051 | The partner shall be able to provide incident response and monitoring for instrumentation and edge hardware, escalating hardware faults distinctly from software or platform faults. | Must | Bijlage Q |
| BR-052 | The partner shall be able to provide a tested fallback procedure that maintains training continuity if hardware or edge software fails, validated as part of formal acceptance testing. | Must | Bijlage L PERF-04, ACC-03 |
| BR-053 | The partner shall be able to support training-the-trainer activities so Alliander instructors can manage scenarios independently, without structural dependency on the partner's development capacity. | Should | Bijlage L Voorblad |
| BR-054 | The partner shall be able to participate in a pilot or proof-of-concept on one representative training environment before broad rollout to Haarlem, Zevenaar, and future sites. | Must | Bijlage L IMP-03 |
| BR-055 | The partner shall be able to demonstrate all 31 Bijlage T core scenarios operating correctly on instrumented hardware as part of formal acceptance. | Must | Bijlage L ACC-03 |

## Non-Functional Requirements and Constraints

Local edge operation resilience is a mandatory requirement (Eis): the solution must keep functioning during a temporary loss of internet connectivity, for example by running scenarios locally [Bijlage L PERF-05]. Avanade's design goes further: the on-site edge server runs every scenario fully offline, and the cloud is used only for synchronisation, never for operation. This exceeds PERF-05 and is the right architecture for a training environment.

Safety independence is absolute. The digital layer must never override, disable, or bypass an existing physical safety provision, emergency stop, disconnection, interlock, or lock-out and tag-out mechanism, and a failure of the digital layer must never cause a physical safety measure to fail [Bijlage L SAFE-01, SAFE-02]. All work involving live or simulated-live components must comply with NEN 3140 and NEN-EN 50110, and the partner must contribute to a safety paragraph and risk analysis covering this work [Bijlage T Algemene uitgangspunten].

Security requirements are also knock-out conditions. The solution must meet a minimum security level A for both access management and identity governance; acceptable access management mechanisms are OIDC/OAuth 2.0 with PKCE (preferred) or SAML 2.0, with the Implicit Flow, ROPC, Basic Auth, NTLM, and any local password database explicitly prohibited. Identity governance must use a SailPoint connector or SCIM 2.0 provisioning, and authentication events must be exportable to Alliander's SIEM [Bijlage V §3.1 to §3.2]. Data traffic must be encrypted to at least TLS 1.2, with TLS 1.3 preferred [Bijlage L IT-04]. The winning supplier must hold ISO 27001 and ISO 9001 certification, or an accepted equivalent such as SOC 2 Type II [Aanbestedingsleidraad §4.1; Bijlage L LCD19].

Data residency is fixed. All data must be stored exclusively within the EEA; storage outside the EEA is not permitted, and the bidder must provide a complete inventory of every datacentre, cloud region, and storage service involved, including physical country and role [Bijlage L IT-03, LCD11].

Scalability and modularity are scored quality criteria. The architecture must be modular enough to absorb additional training environments added to the framework during its term without redesign, and it must expose open APIs and avoid vendor lock-in [Bijlage N GC2]. Hardware control must be architecturally isolated from business logic through standardized interfaces, so hardware-specific protocols and drivers stay confined to the integration layer and hardware remains replaceable [Bijlage L ITAR-03].

Maintainability follows directly from the lifecycle and manifest requirements. Only hardware and software under active vendor support may be used, with explicit end-of-support commitments stated in the contract [Bijlage L LCD08], and every component must appear in a manifest with its specifications, warranty, expected lifespan, and maintenance needs [Bijlage L HW-02].

Environmental durability reflects the training use case. Hardware must be suitable for intensive, repeated use in a training environment [Bijlage T Algemene uitgangspunten], and where instrumentation approaches real MV equipment, it must not expose trainees or trainers to real medium-voltage levels; the previous Avanade concept assumed a 20 to 50 V DC instrumentation layer, but this is not confirmed in the tender and must be validated on site.

Availability is measured against a minimum 99% target during training hours, defined through SLA KPIs the partner helps Avanade propose [Bijlage L PERF-03; Bijlage Q].

## Live Case Walkthrough

The following walkthrough traces one trainee performing a medium-voltage switching procedure on one instrumented ring main unit panel, entirely offline, to make the hardware requirements concrete. Bracketed references point to the requirement IDs each step depends on.

1. The trainee arrives at the schakellokaal and taps an RFID or NFC credential at the panel's reader to start the session. The reader authenticates the trainee against a locally cached identity token issued by Alliander's IAM, since no live connection is required at this moment [BR-006, BR-026].
2. The instructor, from the instructor console, activates a specific core scenario for this trainee's session only, for example a WEGA voltage-detection fault (P2-MS-02), while three other trainees continue unrelated scenarios on other panels without interruption [BR-023].
3. The trainee begins the switching sequence on the ring main unit. Position and state sensors instrumented onto the panel capture each physical action, such as opening a disconnector or checking a voltage indicator, in real time [BR-010, BR-021].
4. The on-site edge server, running entirely offline with its own instrumentation and industrial network, receives these sensor events and updates its local digital twin state to reflect the panel's live topology and energisation status [BR-002, BR-003, BR-020].
5. Because the scenario requires a WEGA fault, the instrumentation layer injects a falsified voltage-indication signal at the moment the trainee checks the WEGA unit, without touching any real high-voltage circuit [BR-010, BR-022].
6. The edge server detects that the trainee proceeded as if voltage were absent when the fault scenario says it should still be flagged as present, and marks this step as an error in the local session record [BR-021].
7. The instructor dashboard, connected to the same on-site edge server over the local industrial network, shows the trainee's live progress and the flagged error immediately, letting the instructor intervene or let the trainee self-correct [BR-025 supports the same data model once synced; the live view itself runs on the edge].
8. If, mid-session, the site loses its internet connection or experiences a momentary power dip, the UPS-backed edge and instrumentation hardware hold their last safe state and the active scenario terminates safely rather than leaving any output in an undefined condition; the physical panel's own interlocks and emergency stop remain fully functional throughout, independent of this fail-safe behaviour [BR-004, BR-027, SAFE-02].
9. The trainee completes the sequence, and the session is scored entirely offline based on the sensor-captured timeline and the flagged error [BR-020].
10. Later, when the site's edge server regains connectivity, it synchronizes the completed session, its score, and its state history to the cloud digital twin and learning-data platform, without having required that connection for the session to run [BR-025].

## Open Questions and Assumptions

The following items must be confirmed through a joint site survey or the RFP clarification process before the partner finalizes its hardware proposal. Where the RFP conflicts with any assumption in this document, the RFP governs.

* Zevenaar's schakellokaal and meetveld layout, room count, dimensions, and switchgear inventory are undocumented; only Haarlem has a documented floor plan and equipment photos from the 2023 site visit.
* The scope of the meetveld (measurement field) environments is unclear. Bijlage T's 31 core scenarios all appear to address schakellokaal-type switchgear; whether the meetveld requires its own digital control hardware, and what equipment it contains, is not stated.
* The physical trainee and instructor identification mechanism is undefined. This BRD assumes an RFID or NFC credential compatible with an existing Alliander badge format, but this is not confirmed in the tender documents.
* The instrumentation operating voltage is assumed to be 20 to 50 V DC, based on the 2023 Avanade requirements document and the 2025 ROM proposal, but this is not confirmed in the tender itself and must be validated against the actual switchgear.
* The method for simulating an SF-6 gas-pressure gauge state (P2-MS-05) without manipulating real SF-6 equipment is not specified in the tender and needs a specific engineering approach validated in the risk analysis.
* Exact electrical interface specifications for WEGA and SVS units, such as voltage levels, signal types, and protocols, are not published in the tender and must be obtained on site or from the equipment manufacturer.
* Whether the Archipel system, being replaced under a separate tender, must exchange data with or coexist alongside this platform during a transition period is not addressed.
* Whether camera or visual-monitoring hardware is in scope at all is unclear; the 2023 Avanade document raised it as a desired capability, but the current tender documents do not reference cameras.
* SLA KPI target values are not defined in Bijlage Q, which is a blank template; the partner's actual support capability should inform what Avanade proposes.
* The number and timeline of additional training environments that may be added under the framework agreement is not quantified, which affects spares sizing and bulk pricing assumptions.
* Whether circular sourcing, repairability, or specific end-of-life requirements apply to hardware under Alliander's MVO (social responsibility) scoring criterion has not been confirmed, since that source document has not yet been reviewed.
* All device names in this document (ABB SafeRing/SafePlus, WEGA, SVS, FlexOV, CAM, MSR) are indicative references drawn from prior Avanade site visits and the tender's own scenario descriptions, not a prescribed bill of materials. The partner's proposal, validated against a joint site survey and the final RFP text, determines the actual hardware selection.
