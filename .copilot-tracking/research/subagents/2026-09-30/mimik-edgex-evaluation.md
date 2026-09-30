<!-- markdownlint-disable-file -->
# mimik and EdgeX Foundry — Evaluation as Edge-Compute Candidates/Complements

Research scope: bid-team-requested evaluation of two additional named technologies — **mimik**
(mimik Technology Inc.) and **EdgeX** (assumed EdgeX Foundry pending confirmation) — as potential
candidates or complements to the existing Connect/Edge Layer recommendation in
`.copilot-tracking/research/2026-09-30/alliander-hardware-partner-sourcing-research.md`. That
existing recommendation is: **classic Azure IoT Edge** as the primary on-site edge-compute
runtime (chosen for its documented indefinite offline-operation guarantee versus Azure IoT
Operations' 72-hour offline ceiling), fronted by a vendor-neutral protocol gateway (e.g., HiveMQ
Edge-class) for Modbus/legacy sensor translation, with OPC UA as the primary southbound protocol
and MQTT/Sparkplug B for the edge event bus/cloud sync.

## Task Implementation Requests

* Confirm what mimik (mimik Technology Inc.) actually offers, its architecture, target use case,
  offline capability, industrial/OT protocol support, Azure integration status, and fit/lack of
  fit for this project.
* Confirm "EdgeX" = EdgeX Foundry (Linux Foundation/LF Edge); document its architecture, device
  services, offline/local-operation model, Azure integration path, governance/vendor-neutrality,
  and current project health.
* Produce a comparison against the existing recommended approach using the same evaluation
  dimensions: real-time telemetry/protocol fit, Azure integration path, offline operation
  capability, vendor-neutrality/no-fixed-SKU alignment.
* Recommend whether the primary document's existing recommendation should change, stay the same
  (with mimik/EdgeX noted as considered alternatives), or be supplemented.

## Scope and Success Criteria

* Scope: this is a subagent research pass answering a specific bid-team follow-up question; it
  does not re-litigate protocol choice (OPC UA/MQTT/Modbus), only edge-compute-platform fit for
  the two named technologies.
* Success Criteria:
  * mimik's actual product/architecture is confirmed from primary sources (not assumed). **Met.**
  * "EdgeX" is confirmed as EdgeX Foundry (or corrected if research surfaces a different product).
    **Met — confirmed, no correction needed.**
  * Both technologies are assessed against the same four evaluation dimensions used in the prior
    edge-protocol-alternatives.md research. **Met.**
  * A clear, evidence-based recommendation is produced — including honestly stating non-fit
    where evidence does not support a fit. **Met.**

## Outline

* mimik (mimik Technology Inc.) — what it is, architecture, offline/OT support, Azure integration, fit
* EdgeX Foundry — confirmation, architecture, offline/local pattern, Azure integration, governance/health, fit
* Comparison table against existing recommendation
* Recommendation

## Research Executed

### External Research

* Web fetch: mimik corporate site (`mimik.com` / `www.mimik.com`) — homepage, About, Partners/Cloud pages
  * Confirms mimik's **current (2026)** flagship product is **mimOE ("the Agentix Operating
    Engine")** — a lightweight (10-20 MB) runtime positioned entirely around **operationalizing
    agentic AI** (discovery, choreography, zero-trust security, and observability for AI agents
    running across "device, edge, and multi-cloud"). The homepage explicitly frames mimik as
    *not* "another container, orchestration tool, or cloud provider" but an "intelligent Agentix
    infrastructure." There is no mention of OPC UA, Modbus, MQTT, or any named industrial
    telemetry/fieldbus protocol anywhere on the corporate site content retrieved.
    Source: [mimik.com](https://www.mimik.com/), [mimik — About](https://www.mimik.com/about-mimik)
  * The "Cloud Providers" partner page (`/partners/cloud`) is a generic pitch about monetizing
    spare/interruptible cloud capacity via mimOE; it names no specific cloud vendor (no Azure,
    AWS, or GCP by name) and describes a capacity-brokerage value proposition, not a
    protocol/data-plane integration. No Azure-specific integration, connector, or partnership
    was found anywhere in the fetched mimik content.
    Source: [mimik — Cloud Providers](https://www.mimik.com/partners/cloud)
  * Partner/customer logos shown on the homepage: NXP, Zoara, Texas Instruments, ARM, Veea, IBM,
    AWS, Red Hat, Zamil Group, Saudi Aramco, Fathom IO, AMD, Centific, Marelli, QNX, NVIDIA,
    Carahsoft — **Microsoft/Azure does not appear** in this list. These are logo mentions only
    (no linked case-study detail was found for the industrial/Aramco-type names).
    Source: [mimik.com](https://www.mimik.com/)
  * News items confirm mimik does pursue an "industrial edge" narrative at the level of running
    AI agents at industrial sites (e.g., "mimik Ignites Abu Dhabi Edge AI Revolution... Global
    Blueprint for Industrial Edge Agentic AI"; "Advantech and mimik Join Forces to Simplify AI
    Deployment Across Edge and Cloud") — but every one of these is about AI-agent
    orchestration/compute placement on industrial-adjacent hardware (Advantech makes industrial
    PCs), not about OT protocol translation, instrumentation telemetry, or industrial
    fieldbus/SCADA integration.
    Source: [mimik.com](https://www.mimik.com/) (homepage news list)
* Web fetch: mimik GitHub organization (`github.com/mimikgit`)
  * Confirms mimik's **historical** product line: `mimik-rtos-sdk` (archived, last updated Nov
    2020) and `Awesome-edgeEngine-training` (archived, last updated Aug 2023) — "edgeEngine" was
    mimik's earlier hybrid/mobile edge-computing SDK (consistent with mimik's known historical
    positioning as a company that turned mobile/consumer devices into edge micro-servers). Both
    repos are now marked "Public archive," i.e., mimik has retired this product line in favor of
    the current mimOE/Agentix positioning.
  * The org's 20 repositories are overwhelmingly forked general-purpose infrastructure libraries
    used to build their engine (civetweb embedded web server, OpenSSL, SQLite, Duktape JS
    engine, spdlog, RxCpp, vsomeip automotive SOME/IP middleware — also archived) plus a small
    number of first-party repos for the current mimOE/agent product (`aaosa-mimoe`). **No
    repository implementing or wrapping an industrial/OT protocol (OPC UA, Modbus, BACnet,
    Sparkplug B) was found in the org.**
    Source: [github.com/mimikgit](https://github.com/mimikgit)
  * `developer.mimik.com/docs/ai-foundation` returned an HTTP 403 (access-restricted) during this
    research pass and could not be reviewed directly; this is a documented access gap rather
    than a confirmed absence of protocol documentation, and is flagged in follow-on research.
* Web fetch: EdgeX Foundry corporate site (`edgexfoundry.org`)
  * Confirms **EdgeX Foundry** is indeed "a vendor-neutral, open-source project hosted by The
    Linux Foundation" (specifically under the **LF Edge** umbrella) — this is the only "EdgeX"
    product found and matches the user's assumption exactly; no correction needed.
  * Confirms it is a "plug and play distributed microservices software architecture" that
    "bridges Operational Technology (OT) and Information Technology (IT) systems," explicitly
    marketed on real-time-despite-intermittent-connectivity grounds: "Achieve real-time results
    despite intermittent connectivity and simplify OT/IT integration."
  * Surfaced multiple named industrial/utility-adjacent case studies, most notably **Eaton**
    (global electrical/power-management leader) and **Tuxmart.io** (secure air-gapped building
    automation, 700+ devices) — see dedicated case-study fetch below.
    Source: [edgexfoundry.org](https://www.edgexfoundry.org/)
* Web fetch: EdgeX Foundry documentation (`docs.edgexfoundry.org/3.1/`) — Overview, Device
  Services chapter, Store and Forward chapter
  * Confirms the **three-tier microservices architecture** the task expected: **Core Services**
    (Core Data, Core Metadata, Core Command), a **Device Services** layer (southbound protocol
    adapters), and an **Application Services** layer (northbound export to "the cloud, database,
    enterprise application or other external system").
  * Confirms the **official/native device-service list** as of version 3.1: BACnet, CoAP, GPIO,
    **Modbus**, **MQTT**, ONVIF camera, REST, RFID LLRP, SNMP, UART, USB camera, plus
    Virtual/Random test services. **No native/first-party OPC UA device service exists in this
    list.** New protocols (including OPC UA) require building a custom device service using
    EdgeX's Go or C Device Service SDK — this is explicitly supported and documented
    ("EdgeX also provides the means to create new device services through device service
    software development kits (SDKs) when you encounter a new protocol").
    Source: [EdgeX Foundry — Device Services Overview](https://docs.edgexfoundry.org/3.1/microservices/device/Ch-DeviceServices/)
  * Confirms a **Store and Forward** capability at the Application Services (northbound/export)
    layer: failed export attempts persist data (default backing store Redis, pluggable via a
    `StoreClient` interface, e.g., NATS JetStream) and are retried at a configurable
    `RetryInterval`; setting `MaxRetryCount: 0` yields **endless retries** — i.e., Store and
    Forward *can* be configured for indefinite-style retry/buffering, though EdgeX's own
    documentation does not make an explicit marketed "indefinite offline" guarantee comparable
    to Microsoft's classic-IoT-Edge offline-operations page.
    Source: [EdgeX Foundry — App Functions SDK: Store and Forward](https://docs.edgexfoundry.org/3.1/microservices/application/sdk/details/StoreAndForward/)
  * Confirms current documentation covers versions through **3.1-Napa** (stable, cited
    extensively above) plus newer **4.0-Odesa**, **4.0.2-Palau**, and **4.1-Queensland (WIP)**
    releases already listed in the docs version sidebar — direct evidence of continued
    version progression past 3.x.
* Web fetch: Eaton EdgeX Foundry case study (`edgexfoundry.org/use-cases/eaton-use-case/`)
  * **Eaton** (global electrical leader — power distribution, circuit protection, power
    quality/backup power, control and automation) surveyed open-source IoT/edge platforms in
    early 2022 and selected EdgeX Foundry to build a common edge platform for its Brightlayer
    Edge Linux-based hardware, citing EdgeX's lightweight/efficient footprint (versus
    Python/Java-based alternatives) and its modular, event-driven microservices architecture.
  * Directly on point for this project's domain: "The initial portfolio of products required
    **Modbus, BLE, and BACnet** device protocol support – all of which EdgeX provides. Eaton
    also supports proprietary IoT connectivity and has **future needs to support additional
    Northbound protocols including BACnet, Modbus, Ethernet IP, OPC-UA**, and a host of
    electrical infrastructure protocols." This is a named, evidenced electrical-power-management
    company independently confirming the same gap this research found: **OPC-UA is not
    out-of-the-box in EdgeX and was, for Eaton, a documented future/custom-integration need**,
    not a shipped native capability.
  * Eaton has since joined EdgeX's Technical Steering Committee and contributes back to the
    project — evidence of sustained, real industrial-sector investment in the platform, and a
    close domain analog (electrical/power-management edge gateways) even though it is not a
    grid-training-room or switchgear-training use case specifically.
    Source: [EdgeX Foundry — Eaton case study](https://www.edgexfoundry.org/use-cases/eaton-use-case/)
* Web fetch: EdgeX Foundry `edgex-go` GitHub releases page
  * Confirms an active, ongoing release cadence through 2025-2026: v3.0.0 Minnesota (31 May
    2023) → v3.1.0 Napa (15 Nov 2023) → v3.1.1 (15 May 2024) → v4.0.0 (13 Mar 2025) → v4.0.1 (25
    Nov 2025) → **v4.0.2 marked "Latest" (29 May 2026)** — a consistent roughly-6-month release
    rhythm continuing into the current year, which directly answers the "is it actively
    maintained as of 2026?" question: **yes, with a recent 2026 release.**
    Source: [github.com/edgexfoundry/edgex-go/releases](https://github.com/edgexfoundry/edgex-go/releases)

## Key Discoveries

### mimik (mimik Technology Inc.) — not the same company/product profile it once was

mimik has **pivoted away from** its historically known hybrid/mobile edge-computing product
("edgeEngine" — an SDK that turned mobile/consumer devices into edge micro-servers) toward a
completely different current flagship: **mimOE ("Agentix Operating Engine")**, a lightweight
runtime whose entire value proposition is **operationalizing agentic AI** — agent discovery,
choreography, zero-trust security, and observability across a "Device-First Continuum" of
devices, edge, and multi-cloud. The historical edgeEngine/mobile-edge SDK repositories on
mimik's GitHub org are explicitly archived, confirming this is not merely a rebrand of the same
underlying product but a genuine strategic shift in what the company sells.

Assessed against the research questions:

* **What it offers today:** an "operating engine" for running and coordinating AI agents across
  heterogeneous compute (phones, gateways, industrial PCs, robots, cameras), not an
  IoT/OT-instrumentation or protocol-translation platform.
* **Industrial/OT protocol support:** **none found.** No OPC UA, Modbus, MQTT, BACnet, or any
  named fieldbus/SCADA protocol appears anywhere in mimik's current corporate site, GitHub org,
  or partner pages retrieved in this research pass. mimik's own GitHub repositories are general
  infrastructure libraries (web server, crypto, SQLite, JS engine) supporting the agent runtime,
  not protocol adapters.
  Any conclusion about protocol support inside `developer.mimik.com` documentation specifically
  is limited by an HTTP 403 access restriction hit during this pass (see Follow-on research).
* **Offline capability:** mimik markets "Local and Offline-First" and "Robust, Uninterrupted
  Local Operation" as headline traits of mimOE, but no engineering documentation equivalent to
  Microsoft's classic-IoT-Edge offline-operations page (with explicit duration guarantees,
  store-and-forward semantics, or reconnect/resync behavior) was found. This is a **marketing
  claim without the kind of verifiable technical documentation** the existing recommendation
  relies on for classic Azure IoT Edge.
* **Azure integration:** **none found.** Microsoft/Azure does not appear among mimik's listed
  partners/customers (NXP, ARM, IBM, AWS, Red Hat, Saudi Aramco, AMD, NVIDIA, etc., are shown;
  Azure is not). The dedicated "Cloud Providers" partner page is generic multi-cloud capacity
  brokerage messaging, not a documented connector or integration path into Azure IoT Hub, Azure
  IoT Edge, or Azure IoT Operations.
* **Industrial/utility/grid case study:** **none found.** News items reference an "Industrial
  Edge Agentic AI" joint venture (Abu Dhabi) and an Advantech partnership (industrial PC OEM),
  but both describe running AI agents on industrial-adjacent hardware, not instrumenting
  switchgear, ingesting OPC UA/Modbus telemetry, or any grid/utility training or production
  domain.
* **Fit for this project:** mimik solves a **different problem** than the one this project's
  Connect/Edge layer has. This project needs protocol-level instrumentation ingestion
  (switch-state, current/voltage, RFID/NFC), industrial-protocol translation, and an
  offline-capable telemetry sync pipeline into Azure — a data-plane/OT-integration problem.
  mimik's mimOE is a compute/agent-orchestration-plane product for running distributed AI
  workloads, which is conceptually adjacent to (and could theoretically sit *above*, at
  layers 4-6) an instrumentation layer, but there is no evidence it does, or is designed to do,
  the OT protocol/telemetry job this layer actually requires. Forcing a fit here would not be
  evidence-based.

### EdgeX Foundry — confirmed match to "EdgeX"; credible as a device-service/protocol layer, not as a full Azure IoT Edge replacement

**Confirmation:** "EdgeX" = **EdgeX Foundry**, the vendor-neutral, open-source edge-computing
platform hosted by The Linux Foundation under the **LF Edge** umbrella. No other, more relevant
"EdgeX" product for industrial/utility use was found — this is the correct product and matches
the bid team's assumption.

**Architecture** (confirms the expected three-tier model):

* **Core Services:** Core Data (event/reading storage), Core Metadata (device/profile registry),
  Core Command (device actuation/command dispatch).
* **Device Services** (southbound protocol adapters — one independent microservice per
  protocol): official/native support for **Modbus, MQTT, BACnet, CoAP, GPIO, ONVIF (camera),
  REST, RFID LLRP, SNMP, UART, USB camera**, plus test/demo services (Virtual, Random). **OPC UA
  is not a native device service** — it would require a custom device service built with EdgeX's
  Go or C Device Service SDK, which EdgeX explicitly supports as an intended extension path but
  does not ship out-of-the-box. This is corroborated independently by Eaton's own case study,
  which lists OPC-UA as a documented **future** Northbound protocol need, not a shipped one.
* **Application Services** (northbound/export layer): configurable pipelines that push data "to
  the cloud, database, enterprise application, or other external system," with a built-in
  **Store and Forward** capability (Redis-backed by default, pluggable) that retries failed
  exports at a configurable interval — settable to endless retries (`MaxRetryCount: 0`).

**Offline/local-operation characteristics:** EdgeX is designed to run entirely on-premises/at
the edge (core services, device services, and the message bus all run locally); the Store and
Forward pattern at the Application Services layer is EdgeX's direct analog to classic Azure IoT
Edge's store-and-forward/offline buffering, and can be configured for indefinite retry. However,
this is a **configurable mechanism**, not a documented, marketed "indefinite offline" guarantee
the way Microsoft explicitly states for classic IoT Edge — no equivalent authoritative EdgeX
Foundry documentation page makes an explicit maximum/indefinite offline-duration claim. There is
**no documented first-party EdgeX-to-Azure-IoT-Hub or EdgeX-to-Azure-IoT-Edge export/app-service
connector** in the material reviewed; achieving that bridge would mean either (a) writing a
custom EdgeX Application Service targeting Azure IoT Hub's MQTT/AMQP endpoint (a moderate,
well-trodden but custom integration effort, since EdgeX's Application Service SDK is designed
exactly for building new northbound targets), or (b) running EdgeX purely as a
protocol-translation/device-service layer that publishes onto a shared MQTT broker which Azure
IoT Edge (or a gateway like HiveMQ Edge) then also consumes/bridges — i.e., EdgeX sitting
*alongside or in front of* Azure IoT Edge rather than replacing it.

**Vendor-neutrality and governance:** confirmed open-source, Apache-2.0-style LF Edge/Linux
Foundation governance with a public Technical Steering Committee that includes real industrial
adopters (Eaton) as voting members — a strong, direct match to the BRD's "no fixed SKUs,
vendor-neutral" posture, arguably a *better* match than a commercial gateway product (e.g.,
HiveMQ Edge) because there is no vendor lock-in or licensing dependency at all.

**Project health/activity:** confirmed **actively maintained as of 2026** — the `edgex-go`
GitHub releases show a sustained ~6-month cadence continuing into the current year: v4.0.0 (Mar
2025) → v4.0.1 (Nov 2025) → **v4.0.2, tagged "Latest" (May 2026)** — with a further v4.1
"Queensland" already documented as work-in-progress.

**Industrial/utility relevance:** the **Eaton** case study is a strong, named, real-world analog
— a global electrical/power-management company built a common edge platform on EdgeX
specifically for Modbus/BLE/BACnet-instrumented power-management hardware, explicitly because of
EdgeX's lightweight footprint and OT/IT bridging design. **Tuxmart.io** (secure air-gapped
building automation, 700+ devices) is a second relevant analog for the "fully offline/air-gapped
site" requirement, though it is building-automation rather than electrical-switchgear domain.
Neither is a direct grid-training-room or MV/LV switchgear match, but both are considerably
closer domain analogs than anything found for mimik.

**Fit for this project:** EdgeX Foundry is a **credible complementary device-service/protocol-
translation layer**, functionally comparable to (and arguably a more vendor-neutral,
zero-licensing-cost alternative to) the already-recommended "HiveMQ Edge-class gateway" role for
Modbus/BACnet/legacy sensor translation — with the caveat that OPC UA support would need to be
custom-built rather than being native, which HiveMQ Edge-class commercial gateways may or may not
also require confirmation on (not verified in this pass). EdgeX is **not** a strong candidate to
*replace* classic Azure IoT Edge as the primary on-site runtime: it has no documented first-party
Azure bridge, its offline-buffering guarantee is configurable-but-unmarketed rather than
contractually documented the way classic IoT Edge's is, and adopting it as the primary runtime
would mean EdgeX's own Core Services (Data/Metadata/Command) and message bus become the
authoritative on-site system of record — an materially larger scope change than using it as a
protocol-adapter layer feeding into Azure IoT Edge.

## Comparison Against Existing Recommendation

| Dimension | Existing recommendation (classic Azure IoT Edge + OPC UA + MQTT/Sparkplug B + vendor-neutral gateway) | mimik (mimOE) | EdgeX Foundry |
| --- | --- | --- | --- |
| Real-time telemetry/protocol fit | Strong — OPC UA (client-server + PubSub) for instrumentation, MQTT/Sparkplug B for event bus/offline-state | **Not applicable** — no OT/industrial protocol support found; mimOE is an AI-agent compute/orchestration runtime, not a telemetry/protocol platform | Strong for Modbus/BACnet/MQTT/BLE/RFID (native device services); **no native OPC UA** — would require a custom device service via EdgeX's SDK |
| Azure integration path | First-party — classic IoT Edge is a native Azure product (IoT Hub store-and-forward, module twins) | **None found** — no Azure partnership, connector, or integration documented anywhere reviewed | **None first-party** — no documented EdgeX-to-Azure-IoT-Hub/IoT-Edge export connector; would require a custom Application Service (moderate, SDK-supported effort) or running EdgeX alongside Azure IoT Edge via a shared MQTT bridge |
| Offline operation capability | Strong and explicitly documented — indefinite offline operation is Microsoft's stated design point for classic IoT Edge | Marketed as "Local and Offline-First" but **no verifiable engineering documentation** (duration limits, buffering semantics) found | Configurable Store-and-Forward at the Application Services layer (Redis-backed, pluggable, settable to endless retries) — functionally comparable mechanism, but **not marketed/documented as an explicit indefinite guarantee** the way classic IoT Edge is |
| Vendor-neutrality / no-fixed-SKU alignment | Good — classic IoT Edge runs as a single device/VM; gateway choice (e.g., HiveMQ Edge) remains a commercial, swappable product | Fully proprietary, single-vendor platform (mimik Technology Inc.) — **weaker** vendor-neutrality fit than either the existing recommendation or EdgeX | Excellent — genuinely vendor-neutral, Linux Foundation/LF Edge-governed open source with no licensing cost and a real industrial adopter (Eaton) on its governance body; arguably **stronger** vendor-neutrality fit than a commercial gateway product |

## Recommendation

**Keep the primary research document's existing recommendation unchanged** (classic Azure IoT
Edge as the primary on-site runtime, OPC UA as primary southbound protocol, MQTT/Sparkplug B for
the edge event bus/cloud sync), and handle mimik and EdgeX Foundry differently:

* **mimik:** note as a **considered-and-rejected alternative**, not a credible candidate or
  complement for this Connect/Edge layer. Confidence: **High** that it does not fit — the
  evidence (current product positioning, GitHub org contents, partner list, and the complete
  absence of any OT/industrial-protocol or Azure-integration material) is unambiguous and
  consistent across every source reviewed. mimik solves a materially different problem
  (distributed AI-agent orchestration) than this layer requires (industrial-protocol
  instrumentation and offline-capable telemetry sync). It is conceivably relevant only as a
  much-later-stage, out-of-scope consideration for layers 4-6 (e.g., if Avanade ever wanted to
  run distributed AI/agentic scoring workloads across devices rather than centrally in Azure) —
  but even that would still need a documented Azure integration path that does not currently
  exist, so it should not be carried forward even as a layers 4-6 note without further direct
  vendor engagement.
* **EdgeX Foundry:** worth **adding as a named, evidence-backed alternative to the generic
  "HiveMQ Edge-class gateway"** reference in the existing recommendation's protocol-translation
  role — i.e., supplement rather than replace. Confidence: **Medium** that it is a credible
  complement in this specific role, **Low** confidence that it should replace classic Azure IoT
  Edge as the primary runtime. Rationale: EdgeX Foundry is a genuinely vendor-neutral,
  actively-maintained (confirmed 2026 releases), real-industrial-adopter-validated (Eaton)
  open-source platform with native Modbus/BACnet/MQTT/BLE/RFID device services and a
  configurable offline store-and-forward mechanism — functionally it can do the same
  "protocol-translate legacy/Modbus sensors and buffer offline" job the BRD's gateway role calls
  for, at zero licensing cost and with stronger vendor-neutrality credentials than a commercial
  gateway product. It falls short of replacing classic Azure IoT Edge because (a) it has no
  native OPC UA device service (the existing recommendation's primary protocol) — this would
  need custom development, matching Eaton's own documented experience — and (b) it has no
  first-party Azure bridge, so a custom Application Service (or a shared-MQTT-broker bridge
  pattern) would be required either way. The hardware partner (once sourced) should be asked
  directly whether they have existing EdgeX Foundry experience, since it would be a legitimate,
  evidence-backed option for them to propose in place of (or alongside) a commercial gateway —
  but this research does not have grounds to mandate it over a partner's own preferred
  protocol-gateway product.

## Follow-on research not completed (recommended next steps)

* [ ] Retry access to `developer.mimik.com/docs/ai-foundation` (returned HTTP 403 in this pass,
  likely requiring authentication/account sign-up) to fully rule out any undocumented
  OT-protocol or industrial-IoT SDK capability not visible from the public marketing site and
  GitHub org.
  * Reasoning: closes a specific, named access gap rather than relying solely on public-site
    absence-of-evidence for the "High confidence" non-fit conclusion on mimik.
* [ ] If EdgeX Foundry is carried forward as a named alternative, prototype or directly confirm
  whether a custom EdgeX Application Service targeting Azure IoT Hub's MQTT/AMQP endpoint is a
  known, published pattern in the EdgeX community (versus purely a theoretical SDK capability),
  to firm up the "moderate, SDK-supported effort" characterization in this document.
  * Reasoning: the comparison table's Azure-integration-path assessment for EdgeX currently
    relies on inferring feasibility from the Application Service SDK's general design rather
    than a confirmed, named EdgeX-to-Azure integration example.
  * Reference: [EdgeX Foundry — Application Services](https://docs.edgexfoundry.org/3.1/microservices/application/ApplicationServices/)
* [ ] Confirm with the eventual hardware partner whether any commercial OPC UA device service
  exists for EdgeX Foundry from a third party (e.g., IOTech's commercial EdgeX distribution,
  referenced in an EdgeX Foundry use-case listing but not independently verified in this pass),
  which could close the OPC UA gap without requiring the hardware partner to build one from
  scratch.
  * Reasoning: this research found an "IOTech: Open Edge Platform for Industrial Edge Systems"
    case study reference (a commercial version of EdgeX) but did not fetch or verify its content
    in this pass, since it was tangential to the immediate mimik/EdgeX comparison task.
  * Reference: [EdgeX Foundry — IOTech use case](https://www.edgexfoundry.org/use-cases/iotech-systems-use-case/)

## Citations (all URLs fetched in this research pass)

* [mimik.com](https://www.mimik.com/) / [mimik.com (root domain)](https://mimik.com/)
* [mimik — About mimik](https://www.mimik.com/about-mimik)
* [mimik — Cloud Providers partner page](https://www.mimik.com/partners/cloud)
* [github.com/mimikgit](https://github.com/mimikgit) (mimik Technology's GitHub organization)
* [developer.mimik.com/docs/ai-foundation](https://developer.mimik.com/docs/ai-foundation) — HTTP 403, could not be reviewed
* [en.wikipedia.org/wiki/Mimik_Technology](https://en.wikipedia.org/wiki/Mimik_Technology) — HTTP 404, no such page
* [edgexfoundry.org](https://www.edgexfoundry.org/)
* [en.wikipedia.org/wiki/EdgeX_Foundry](https://en.wikipedia.org/wiki/EdgeX_Foundry) — HTTP 404, no such page
* [docs.edgexfoundry.org/3.1/](https://docs.edgexfoundry.org/3.1/) (Overview)
* [docs.edgexfoundry.org/3.1/microservices/device/Ch-DeviceServices/](https://docs.edgexfoundry.org/3.1/microservices/device/Ch-DeviceServices/) (Device Services Overview)
* [docs.edgexfoundry.org/3.1/microservices/application/sdk/details/StoreAndForward/](https://docs.edgexfoundry.org/3.1/microservices/application/sdk/details/StoreAndForward/) (Store and Forward)
* [edgexfoundry.org/use-cases/eaton-use-case/](https://www.edgexfoundry.org/use-cases/eaton-use-case/) (Eaton case study)
* [github.com/edgexfoundry/edgex-go/releases](https://github.com/edgexfoundry/edgex-go/releases) (release cadence/version confirmation)
