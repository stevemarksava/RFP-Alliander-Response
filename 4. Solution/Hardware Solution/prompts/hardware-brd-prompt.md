@brd-builder

# Task: Author a Hardware Business Requirements Document (BRD)

You are a solution architect + business analyst. Produce a partner-facing **Hardware BRD**
for an IoT hardware partner we are sourcing. Keep it **outcome- and capability-based, NOT a
prescriptive bill of materials** — describe what we need and why, and how we see it, so a
partner can propose the "how." Anything device-specific is indicative only and "to be
confirmed via a joint site survey and against the RFP."

## Background / context
- Client: **Alliander** (Dutch DSO / semi-government energy network operator).
- Solution: **"Digital Schakellokalen"** — digitally connecting and driving Alliander's
  **physical training centre** where electrical engineers/monteurs practise **switching
  operations** on real medium-/high-voltage switchgear (schakellokalen = switching rooms).
- Origin: an Avanade IoT/Azure concept (2023) to connect the training-centre devices to the
  cloud so training scenarios can be run, monitored and scored digitally. It is now a live
  **RFP: "Alliander – Digital Schakellokalen MVP."**
- The bid team needs an IoT partner to **source, build, enable, service and support** the
  hardware layer. This BRD defines what that partner must deliver.

## The vision to convey (layered narrative)
Frame the solution as a progression — the partner's job is layers 1–3; layers 4–6 are how we
extend value once devices are digital and connected:
1. **Physical** — the real training switchgear (MV/HV panels, RMUs, disconnectors, breakers,
   earthing switches, transformers, busbars).
2. **Instrument** — sense & actuate: switch position/state, current/voltage signals,
   RFID/NFC on components, cameras/vision, indicators & interlocks.
3. **Connect (edge)** — on-site IoT gateway/PLC, industrial protocols (OPC-UA / Modbus /
   MQTT), industrial network, and a critical **on-site edge server that runs the site fully
   OFFLINE** (no breakout/internet) with UPS, syncing to cloud only when connectivity allows.
4. **Digital twin** — live virtual replica of the switchgear (real-time state, topology,
   energisation, scenario/fault state, session history).
5. **AI & agentic** — vision-based step validation, procedure copilot, fault/scenario engine,
   automated scoring & feedback. (Enabled *once devices are digital & connected*.)
6. **Experience** — instructor dashboard, trainee HMI/tablet, optional AR/MR overlay, voice.

Cross-cutting principle to state explicitly: **Safety & identity are independent of the
digital layer** — hard-wired interlocks, emergency stop, physical lock-out/tag-out and access
control must never be overridable by software. The digital layer observes and augments; it
does not control real electrical safety.

## What the BRD must specify (capability-based)
For the partner scope (layers 1–3), define requirements — not products — across:
- **Source**: what classes of hardware to procure (sensing, edge compute, networking, power/
  UPS, mounting), sourcing/lead-time and standardisation expectations.
- **Build**: assembly, retrofit/instrumentation of existing switchgear, cabinets, wiring,
  ruggedisation, labelling.
- **Enable**: connectivity, commissioning, integration to Azure IoT / digital twin, protocols,
  provisioning & device identity, edge deployment.
- **Service**: preventive maintenance, calibration, spares, firmware/patching, RMA.
- **Support**: SLAs, on-site vs remote, monitoring, incident response, training the trainers.
Also cover: environmental/electrical safety constraints, offline-first operation, data
ownership/residency, scalability across multiple training locations, and modularity so more
panels can be instrumented later.

## Required output structure
1. **Executive summary** (≈½ page) — the need, the layered vision, and the partner's mandate
   in plain business language for a hardware vendor.
2. **Solution overview** — the 6 layers, with a clear line around **partner scope (1–3)**.
3. **Hardware capability requirements** — grouped by Source / Build / Enable / Service /
   Support, each as outcome-based requirement statements (use "The partner shall be able
   to…"), with a Priority column (Must / Should / Could).
4. **Non-functional & constraints** — offline operation, safety independence, security,
   scalability, maintainability, environmental.
5. **A "Live Case" walkthrough** — a concrete end-to-end scenario of ONE trainee performing a
   switching procedure on ONE instrumented panel: trainee taps in (RFID) → operates a
   disconnector → sensors capture state → edge server updates the digital twin in real time →
   AI validates the step and flags an error → instructor sees it live → session runs and is
   scored **entirely offline**, then syncs to Azure when reconnected. Use it to make the
   hardware requirements tangible (call out which sensor/edge/network element enables each step).
6. **Open questions / assumptions** — flag what must be confirmed via site survey and RFP.

## Tone & guardrails
- Business-readable, vendor-neutral, Microsoft Azure-aligned but not locked to specific SKUs.
- Do not invent Alliander-confidential specifics; where unknown, state an assumption.
- Keep device mentions indicative ("e.g., …") and repeat that the final BOM is the partner's
  proposal against a joint survey.

Deliver as a well-structured document (headings, requirement tables with Priority, and the
Live Case as a numbered walkthrough).

## Source documents (read-only — never write to `onedrive/`)
- **Primary reference:** `4. Solution/Hardware Solution/recon/tender-hardware-recon.md` — English summary of the tender's
  hardware-relevant requirements, with source references. Where a BRD requirement comes from
  the tender, cite its reference (for example "RFP: Bijlage T, scenario 3").
- Official tender title: *Digitale aansturing van oefenomgevingen voor technische opleidingen*.
- Tender documents (Dutch):
  `onedrive/1. Received from customer (do not change)/Mercell-Export-20260910/1. Gunningsfase/1. Offerteaanvraag/`
  - `3. Aanbestedingsleidraad en bijlagen/` — tender guide and Bijlage T (core scenarios)
  - `4. Uitsluitingsgronden, geschiktheidseisen en mi._/` — minimum requirements
  - `5. Kwaliteitscriteria/` — quality award criteria (Bijlage N)
- Previous Avanade material:
  `onedrive/5. Relevant information/Previous Ava offers to Alliander/`
  (ROM Proposal v1.2 2025, Schakellokaal requirements)

If anything in this prompt conflicts with the tender, the tender wins. List the conflict under
Open questions.

## Output
Write the BRD to `4. Solution/Hardware Solution/alliander-schakellokalen-hardware-brd.md`.
