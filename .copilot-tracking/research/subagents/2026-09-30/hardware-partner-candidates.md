# Hardware Integration Partner Candidates — Digital Schakellokalen (Alliander)

Status: Complete (public web research only; no candidate has been confirmed against this specific tender scope)

## Research Questions

1. What type of company profile fits the layers 1-3 hardware scope (physical instrumentation retrofit, edge/industrial networking, on-site edge compute + UPS) for the Digital Schakellokalen project?
2. Real, named companies (NL/Benelux/EU priority) matching this profile — with sector experience and Azure/Microsoft partnership evidence where findable.
3. Sourcing channels/directories (Dutch/EU industrial IoT integrator lists, Azure IoT Edge partner listings, utility-sector SI lists).
4. Explicit confidence flags — no fabricated capabilities.

## Note on the real underlying tender

A live TED/Tenderned procurement notice from Alliander N.V. matching this project's description was found during research:

- Title: "Digitale aansturing van oefenomgevingen voor technische opleidingen"
- Buyer: Alliander N.V. (registered in Arnhem, national reg. no. 34108286)
- Published: 2026-09-09 (OJS 2026/S 175-624073); deadline 2026-11-18
- Scope description (NL): "een digitale oplossing voor het centraal aansturen van fysieke oefenomgevingen... netconfiguraties en storingsscenario's centraal te configureren, activeren, beheren en doorontwikkelen voor meerdere schakellokalen en meetvelden binnen Alliander"
- Estimated value: €3,040,000; framework agreement, single-supplier ("Maximumaantal deelnemers: 1")
- CPV codes are all software-services codes (72xxx, 48000000) — this notice appears to cover the software/digital-twin/control-layer side of the programme, not a separately-coded hardware/instrumentation lot. No separate hardware-specific tender notice was found in this research pass.
- Sources: [nl.openprocurements.com tender page](https://nl.openprocurements.com/tender/digitale-aansturing-van-oefenomgevingen-voor-technische-opleidingen/), [tenderimpulse.com listing](https://tenderimpulse.com/government-tenders/netherlands/digitale-aansturing-van-oefenomgevingen-voor-technische-opleidingen-14768082)

This confirms the project is real and active but does not identify a hardware-layer supplier — no award notice or hardware-specific lot was located. Treat the rest of this document as profile/candidate guidance, not as evidence of who Alliander has already selected.

## Section 1: Company-type profile and rationale

| Profile type | Fit rationale | Caveats |
|---|---|---|
| **Industrial OT/IoT systems integrator** (designs + installs sensors, PLC/relay I/O, industrial networking, commissions and supports on-site) | Best overall fit. The scope is fundamentally a retrofit-and-integrate job: sensors, RFID/NFC, relays, I/O, smart cabling, OPC-UA/Modbus/MQTT gateways, and an edge box — this is the daily work of an OT/IoT systems integrator, not a product vendor or a software house. | Many Dutch OT integrators are strongest in manufacturing/process (food, semiconductor, logistics) rather than utilities specifically — sector crossover needs to be checked per firm. |
| **SCADA/MES/PLC integrator with an existing "smart grid" or utilities practice** | Directly relevant: these firms already speak Modbus/OPC-UA/IEC 61850-adjacent protocols and already sell into DSO/TSO-type customers, reducing ramp-up risk on grid vocabulary (schakelvelden, storingsscenario's, meetvelden). | Fewer of these exist at the mid-size, multi-year-framework-ready scale in NL; several are large multinationals (Siemens, Schneider, ABB) whose commercial model may not suit a 3+5×1-year framework with a training-focused, budget-constrained customer segment. |
| **Azure IoT Edge-experienced integrator / Microsoft (Gold) partner with industrial focus** | Directly relevant given the explicit requirement for an edge server that runs fully offline and syncs to Azure only when connectivity allows — this is exactly the Azure IoT Edge "offline-first, cloud-when-available" design pattern. A partner who has actually shipped Azure IoT Edge deployments (container-based edge modules, offline queuing, module twin sync) removes significant integration risk versus a generalist automation firm bolting on cloud connectivity later. | Being "a Microsoft partner" in general (reseller, Dynamics, M365) is not the same as IoT Edge / industrial-edge experience — must verify the specific competency, not just partner-tier badges. |
| **Utility/industrial training-simulation specialist** (companies building practical/VR training environments for grid operators) | Directly relevant to the *training* domain and stakeholder credibility (they understand switching procedures, storingsscenario's, safety/LOTO concepts) but these firms are typically training/curriculum or VR-content providers, not hardware/OT integrators — likely to be subcontractors to, or a different lot from, the hardware partner rather than the hardware partner itself. | Found one concrete example (Omexom Institute, see below) but it is a training-delivery/VR-content organisation, not an instrumentation/edge-compute integrator. |
| **Electrical infrastructure / switchgear contractor** (builds and maintains MV/LV switchgear, e.g., Alliander's own "Qirion" or peers like Omexom/Volker/Croonwolter&dros) | Partial fit only — they know the physical switchgear and safety context deeply, but the brief explicitly excludes "building the physical switchrooms" and these firms are generally not specialist IoT/edge-compute integrators; their sensor/automation capability is usually subcontracted. | Good potential *subcontractor or advisor* on physical retrofit constraints, unlikely to be the prime hardware integrator on their own. |
| **Large industrial automation OEM with regional systems-integrator/alliance network** (Schneider Electric, Siemens, ABB, Eaton) | Fit on paper — all four sell sensors/IO/edge gateways/UPS and have Azure-integration stories (e.g., Siemens Industrial Edge + Azure, Schneider EcoStruxure). Siemens already has a *separate*, large strategic partnership with Alliander for LV-grid digital-twin software ("Gridscale X" — not the schakellokalen project). | Likely oversized/over-scoped for a €3M-class, multi-site training-room retrofit framework; more plausible as a *component/hardware supplier* behind a smaller systems-integrator prime, or as the systems integrator only via their regional "Alliance Partner" network rather than the OEM itself. |

## Section 2: Candidate companies

Confidence levels: **Medium** = company's published scope/sector focus plausibly matches, but no direct evidence they have worked on this or an equivalent Alliander project. **Low** = directional/type match only, meaningful gaps or uncertainty in evidence. No candidate reached **High** confidence (i.e., verified evidence of doing this exact kind of work for a utility training environment) in this research pass.

### Axians Nederland (part of VINCI Energies)

- What they do: Dutch ICT/OT integrator; explicit "Modernizing Smart Grids" and utilities industry practice combining ICT and OT expertise; separate IoT platform practice ("Maestro") for connecting machines/sensors/IoT to data/analytics platforms.
- Relevant fit evidence: Dedicated utilities/smart-grid industry page; dedicated OT-to-IT integration product (Maestro) explicitly aimed at industrial customers; large NL footprint under VINCI Energies (which also owns Dutch high-voltage/switchgear contractors elsewhere in the group).
- Azure/Microsoft evidence: Not independently confirmed in this pass (their IoT/data pages did not show an explicit Azure IoT Edge partner badge).
- Sources: [axians.com/industries/utilities](https://www.axians.com/industries/utilities/), [axians.nl homepage](https://www.axians.nl/), [Axians Maestro OT/IT](https://www.axians.nl/oplossing/maestro/maestro-voor-de-industrie/verbind-ot-en-it-met-maestro/), [Axians IoT platform](https://www.axians.nl/expertises/data-analytics/iot/iot-platform/)
- Confidence: Medium

### ATS Global

- What they do: Global MES/SCADA/IIoT systems integrator, headquartered in the Netherlands (Zaltbommel), with a dedicated "Smart Grid" solution offering.
- Relevant fit evidence: Explicit smart-grid page; deep MES/SCADA/OT-to-IT integration pedigree; long track record of multi-site industrial digitization rollouts (relevant to scaling from 4 sites to more).
- Azure/Microsoft evidence: Not independently confirmed in this pass; their materials referenced the Ignition SCADA/MES/IIoT platform (Inductive Automation) rather than an explicit Azure IoT Edge partnership.
- Sources: [ats-global.com/us](https://www.ats-global.com/us/), [ats-global.com/smart-grid](https://www.ats-global.com/smart-grid/)
- Confidence: Medium

### Macaw

- What they do: Dutch IT/digital-transformation integrator (AI, data, cloud, digital platforms) with an explicit "Energie & Nutsbedrijven" (Energy & Utilities) industry page.
- Relevant fit evidence: Named utilities-sector practice; broad Microsoft-centric digital transformation positioning typical of NL system integrators serving DSOs/TSOs.
- Azure/Microsoft evidence: General cloud/digital-transformation positioning; no explicit Azure IoT Edge / industrial-edge certification found in this pass — likely stronger on the software/data side than on physical instrumentation retrofit.
- Sources: [macaw.nl/energie-nutsbedrijven](https://www.macaw.nl/energie-nutsbedrijven), [macaw.nl](https://www.macaw.nl/)
- Confidence: Low (fit is plausible for the software/IoT-platform slice of layer 2-3, less evidence for physical retrofit/sensor installation work)

### Savaco (Belgium/Netherlands)

- What they do: Benelux industrial-automation and Microsoft-partner firm offering "Industrial Internet of Things met Microsoft Azure" services (IIoT platform connecting industrial assets to Azure).
- Relevant fit evidence: Explicitly markets an Azure-based IIoT integration offering; Benelux industrial base gives geographic proximity.
- Azure/Microsoft evidence: Direct — their own marketing page is built around Microsoft Azure as the IIoT backbone.
- Sources: [savaco.com/nl/industrial-internet-of-things/microsoft-azure](https://www.savaco.com/nl/industrial-internet-of-things/microsoft-azure)
- Confidence: Low-Medium (clear Azure IIoT positioning, but no utility/energy-sector or training-simulation evidence found)

### Dutch general industrial-automation/system-integrator directory listings (multiple firms, unverified against this specific scope)

Found via the Automation-List.com Netherlands system-integrator directory (11 firms listed at time of research): Foorz Automation, ATS Global (see above), EKB Groep, ICT Group, 101 Industriële Automatisering, Bilfinger Engineering & Consultancy (Tebodin), Kuijpers, 4ProcessMation, Neohance, AT-Automation.

- Relevant fit evidence: All are positioned as PLC/SCADA/MES/OT-IT integrators serving Dutch industry; Bilfinger Tebodin in particular has a broad industrial/engineering consultancy background that sometimes extends into utilities and energy infrastructure; AT-Automation explicitly offers the Ignition SCADA/MES/IIoT platform.
- Azure/Microsoft evidence: Not checked per-company in this pass — flagged as **unverified**, listed only as a sourcing pool.
- Source: [automation-list.com — System Integrators, Netherlands](https://www.automation-list.com/en/category/system-integrator/country/netherlands)
- Confidence: Low (directory-level match only; no firm-specific utility/training evidence gathered)

### Large OEM automation/UPS vendors with regional alliance-partner networks (Schneider Electric, Siemens, ABB, Eaton) — as a *sourcing route*, not necessarily as prime

- What they do: Global suppliers of sensors, I/O, industrial edge gateways, and UPS systems, each running a regional "systems integrator"/"alliance partner" accreditation programme in the Netherlands.
- Relevant fit evidence: Schneider Electric publishes a Dutch-language "Systeemintegrators in de industriële sector" alliance-partner directory; Siemens has a large, separate, already-announced strategic partnership with Alliander for LV-grid digital-twin software (Gridscale X), showing Alliander's precedent of partnering with large OT/automation vendors on grid-digitization initiatives (though that is a different project, not schakellokalen hardware).
- Azure/Microsoft evidence: Siemens explicitly promotes "Industrial Edge with Microsoft Azure" integration (Docker-container based); this is evidence of ecosystem capability, not of an Alliander schakellokalen engagement specifically.
- Sources: [Schneider Electric NL — System Integrators alliance program](https://www.se.com/nl/nl/partners/system-integrators/industry/), [Siemens partners with Alliander — Gridscale X press release](https://press.siemens.com/global/en/pressrelease/siemens-partners-alliander-accelerate-flexible-grid-management-netherlands), [Siemens Industrial Edge with Microsoft Azure](https://industrial.softing.com/expertise/industrial-iot/edge-computing/industrial-edge-with-microsoft-azure.html) (third-party overview referencing Siemens Azure integration)
- Confidence: Low as a direct hardware-partner candidate for this project (likely oversized/commercially mismatched for a framework of this size); Medium as a *sourcing channel* for a regional integrator who resells/installs their hardware.

### Omexom Institute (VINCI Energies)

- What they do: Practical, VR-supported training centre for high-voltage (hoogspanning) skills in the Dutch energy sector ("Praktijkgericht leren in hoogspanning... via theorie, praktijklessen, e-learning en virtual reality").
- Relevant fit evidence: Directly relevant to the *training-simulation and utility-sector* dimension of the brief, and notably sits inside VINCI Energies — the same group as Axians (above) — which could plausibly enable a joint VINCI Energies bid combining Axians' OT/IoT integration with Omexom's utility-training domain expertise.
- Azure/Microsoft evidence: None found; this is a training-delivery organisation, not an edge/IoT hardware integrator.
- Source: [omexom.nl/omexom-institute](https://www.omexom.nl/omexom-institute/)
- Confidence: Low as a hardware-partner candidate on its own; flagged mainly because of the potential VINCI Energies group synergy with Axians.

### Explicitly flagged as NOT verified / could not confirm fit

- No Dutch or Benelux company was found in this research pass with public evidence of having built sensor/RFID/edge-compute retrofit instrumentation specifically for an electricity-grid *training simulator* (schakellokaal/meetveld) environment. This exact niche (utility training-room instrumentation retrofit) does not appear to have an obviously dominant, easily-searchable incumbent.
- No company was found with an explicit, publicly documented "Azure IoT Edge certified partner" badge specific to the Netherlands industrial/utilities segment (several claim general Microsoft/Azure partnership or IIoT-on-Azure capability, which is weaker evidence).
- Do not treat any name above as a confirmed, ready-to-shortlist supplier — all require direct capability validation (reference calls, technical deep-dive, security/OT posture review) before being put into a real RFP shortlist.

## Section 3: Sourcing channels and directories

- [Automation-List.com — System Integrators, Netherlands](https://www.automation-list.com/en/category/system-integrator/country/netherlands) — curated directory of NL industrial-automation/SCADA/PLC/MES system integrators; useful first-pass sourcing list, not utility-sector filtered.
- [Schneider Electric Nederland — Systeemintegrators in de industriële sector (Alliance Partner programme)](https://www.se.com/nl/nl/partners/system-integrators/industry/) — vendor-run accreditation directory of regional integrators using Schneider Electric industrial automation/IIoT technology.
- [Weidmüller Solution Partner Network](https://www.weidmueller.com/int/company/our_partners/find_your_iiot_and_automation_solution_partner/index.jsp) — international IIoT/automation solution-partner directory (hardware vendor-run, includes some NL/EU partners).
- [Microsoft Partner Center — Find a Microsoft partner (NL)](https://partner.microsoft.com/nl-nl/partnership/find-a-partner) — official Microsoft partner directory; can be filtered by solution area (e.g., Azure/IoT) and country to find Dutch Azure partners, though it does not have a distinct "IoT Edge" certification filter separate from general Azure competencies.
- [Azure IoT Edge documentation / "IoT Edge as gateway" pattern](https://learn.microsoft.com/en-us/azure/iot-edge/about-iot-edge) — useful for validating a candidate's claimed Azure IoT Edge depth against Microsoft's own reference architecture (offline operation, module twins, downstream device gateway pattern) during due diligence.
- [TenderNed / TED Europa via nl.openprocurements.com](https://nl.openprocurements.com/buyer/alliander-n-v/) and [TenderImpulse Netherlands tenders](https://tenderimpulse.com/netherlands-tenders) — public procurement notice aggregators; used in this research to confirm the live Alliander tender for the digital/software layer of this programme, and could be monitored for any separate hardware/instrumentation lot Alliander may publish.
- General B2B/IoT vendor directories found but of lower precision for this use case (broad "top IoT companies" listicles, not utility- or OT-specific): [GoodFirms — Top IoT Companies in Netherlands](https://www.goodfirms.co/internet-of-things/netherlands), [ensun.io — IoT development companies, Netherlands](https://ensun.io/search/iot-development/netherlands).

## Summary of confidence and gaps

- Strongest, evidence-backed company-type match: mid-size Dutch/Benelux **OT/IoT systems integrators with an existing utilities or smart-grid practice** (Axians, ATS Global) — Medium confidence.
- Plausible but weaker-evidence candidates: Macaw and Savaco (more IT/data/cloud-IoT oriented than physical-retrofit oriented) — Low confidence.
- Large OEM automation/UPS vendors (Schneider, Siemens, ABB, Eaton) are a credible **component and ecosystem source** and Siemens has a genuine (separate) Alliander relationship, but are Low confidence as the actual framework-agreement hardware prime given likely scale/commercial mismatch.
- No company was found with direct, publicly verifiable evidence of prior work on grid-training-room instrumentation retrofit specifically — this appears to be a narrow enough niche that public web research cannot resolve it with high confidence; a targeted RFI/market-sounding exercise or direct outreach via the sourcing channels above is recommended rather than relying solely on this list.

## Innotractor — Follow-up Check

### What the company actually is

A real company was found matching this name (spelled "InnoTractor"): **InnoTractor BV**, a Dutch company headquartered in Tilburg, Netherlands.

- Legal entity: InnoTractor BV, visiting address Nwe Tivolistraat 50-52, 5017 HR Tilburg, KvK (Dutch Chamber of Commerce) number 78475139, BTW NL8614.16.235.B01.
- Core business: **supply chain data/dataspace software** — described on their own site as "Innovators in trusted supply chain data solutions." They build digital infrastructure that connects fragmented systems and shares data across supply-chain stakeholders while preserving data ownership ("dataspace" model), with a strong emphasis on traceability, digital passports, and real-time visibility rather than physical equipment or grid/electrical work.
- Named sector focus: **ports** (container/port logistics, e.g. Port of Rotterdam), **aviation** (aircraft maintenance, MRO data flows — case study "Hyperion" with KLM Engineering & Maintenance, NLR, Dutch Ministry of Defence, OneLogistics, ILIAS), and **medical/healthcare** (Connected POCT — point-of-care diagnostics logistics, reagent inventory, ambulance/remote use).
- Their "Connected POCT" case study does reference "encrypted IoT communication," sensor/reagent inventory tracking, and operating "without relying on local IT infrastructure" — the only place their marketing touches IoT/edge-adjacent language — but this is healthcare diagnostics logistics, not industrial/electrical OT instrumentation.
- No mention anywhere on their site of: electricity/utility/grid sector, MV/LV switchgear, relays, RFID/NFC sensor retrofit of physical training equipment, OPC-UA/Modbus/MQTT industrial protocols, on-site edge-compute servers with UPS, or Microsoft Azure/Azure IoT Edge specifically.
- No case studies, clients, or public statements connect InnoTractor to Alliander, the Dutch electricity-grid sector, or any training-simulation/schakellokalen-type project.
- Company appears to be a specialized SME/scale-up (values page mentions team culture, "collaboration & enjoyment," typical of a small/mid firm) rather than a large industrial systems integrator; no employee count was independently confirmed (LinkedIn company page is behind a login wall and could not be read in this pass).

### Assessment against the hardware-partner requirements

| Requirement | Fit |
|---|---|
| Instrumentation retrofit of physical MV/LV switchgear (sensors, RFID/NFC, relays, I/O, smart cables, fault injection) | **No evidence of fit.** No physical/electrical retrofit work found; their product is data-sharing software, not hardware instrumentation. |
| On-site industrial edge/networking (OPC-UA/Modbus/MQTT class) | **No evidence of fit.** No industrial-protocol or OT-networking capability mentioned anywhere in their materials. |
| On-site offline-capable edge compute server with UPS, syncing to Azure | **No evidence of fit.** Their "without relying on local IT infrastructure" language (Connected POCT) is about cloud/mobile-first data exchange for diagnostics, not an on-prem UPS-backed edge server pattern; no Azure/Azure IoT Edge partnership evidence found. |
| Multi-year maintenance/support framework, multi-site scalability | Unverifiable either way from public materials — they do describe supporting "solutions throughout their entire lifecycle," a generic claim also common to software vendors, not specific evidence of a multi-year hardware maintenance framework. |

**Overall: Innotractor/InnoTractor does not plausibly fit the hardware-partner profile for this tender.** It is a real, findable Dutch company, but it operates in an adjacent-but-distinct space — supply-chain traceability/dataspace software for ports, aviation MRO, and medical logistics — not industrial OT/IoT hardware integration for electrical-grid training equipment. The company name is not related to agriculture/tractors as the name might suggest; "Tractor" here appears to be a branding choice (possibly evoking "traction"/data-pulling), unrelated to farm equipment.

### Confidence

- **High confidence** that InnoTractor BV (Tilburg, NL) is the real company the bid team was referring to (name match is exact, spelling "InnoTractor" is their own branding).
- **High confidence** that this company is **not a credible fit** for the physical instrumentation/edge-hardware/on-site-UPS-server scope described in the tender requirements, based on their own published case studies, solution pages, and about-us material — no industrial OT, electrical, or utility-sector work was found.
- If the bid team's informal consideration was based on a different, more industrial-sounding company, no better-matching alternative with a similar name ("InnoTraxion," "Innotractor Industrial," etc.) was found in this research pass — this appears to be the one real company matching the name.

### Sources

- [innotractor.com (homepage)](https://innotractor.com/)
- [innotractor.com/solution](https://innotractor.com/solution/)
- [innotractor.com/about-us](https://innotractor.com/about-us/)
- [innotractor.com/case-studies](https://innotractor.com/case-studies/)
- [linkedin.com/company/innotractor](https://www.linkedin.com/company/innotractor/) (login-walled; not independently readable in this pass, listed for reference only)
