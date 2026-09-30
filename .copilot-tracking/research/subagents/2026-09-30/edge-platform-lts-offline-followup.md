# Follow-up: Classic Azure IoT Edge LTS/Roadmap Status, Azure IoT Operations Offline Ceiling, and Azure Local Disconnected-Operations Limits

Research scope: resolve two explicit follow-on gaps flagged in `.copilot-tracking/research/subagents/2026-09-30/edge-protocol-alternatives.md` (section "Follow-on research not completed"), to confirm or revise the recommendation in `.copilot-tracking/research/2026-09-30/alliander-hardware-partner-sourcing-research.md` to use classic Azure IoT Edge as the primary on-site edge-compute runtime for the Alliander schakellokalen training-room instrumentation project. All findings below are from official Microsoft Learn pages, fetched live in late September 2026.

## Question 1: Classic Azure IoT Edge LTS/roadmap status vs Azure IoT Operations

### Classic Azure IoT Edge — actively supported, not deprecated, with a new LTS shipped mid-2026

- **Azure IoT Edge 1.6 LTS shipped July 2026** and is supported through **November 14, 2028**, aligned to the .NET 10 support lifecycle. It is now the current/default documented version. ([Microsoft Learn — IoT Edge version history and release notes](https://learn.microsoft.com/en-us/azure/iot-edge/version-history)) ([Microsoft Learn — IoT Edge supported platforms](https://learn.microsoft.com/en-us/azure/iot-edge/support))
- **Azure IoT Edge 1.5 LTS** (previous version) remains supported until **November 10, 2026** (a few weeks after this research date), aligned to .NET 8. ([Microsoft Learn — IoT Edge version history and release notes](https://learn.microsoft.com/en-us/azure/iot-edge/version-history))
- Microsoft's own documented LTS cadence commits to **continuity beyond 1.6**: "Each new LTS release is planned to ship about six months before the prior LTS reaches end of support, giving customers time to upgrade." This is forward-looking roadmap language, not an end-of-life notice. ([Microsoft Learn — IoT Edge version history and release notes](https://learn.microsoft.com/en-us/azure/iot-edge/version-history))
- The Microsoft Lifecycle page for the product as a whole (not per-LTS-version) shows: "Azure IoT Edge | Start Date 6/28/2018 | Retirement Date: **In Support**" — i.e., no retirement/deprecation date has been set for the product. It is governed by Microsoft's **Modern Lifecycle Policy**. ([Microsoft Learn — Azure IoT Edge lifecycle](https://learn.microsoft.com/en-us/lifecycle/products/azure-iot-edge))
- The classic IoT Edge documentation itself (both the "About," "Support," and "Offline capabilities" pages, all updated within the H1/H2 2026 window) contains **no** messaging redirecting readers to Azure IoT Operations. The "recommended platform" framing for new solutions appears only in the separate Azure Architecture Center page (see below), not in the IoT Edge product documentation. ([Microsoft Learn — What is Azure IoT Edge?](https://learn.microsoft.com/en-us/azure/iot-edge/about-iot-edge)) ([Microsoft Learn — IoT Edge supported platforms](https://learn.microsoft.com/en-us/azure/iot-edge/support))
- The **indefinite offline-operation claim is unchanged and still current** in the default (1.6) version of the offline-capabilities page (dated 2026-03-02, i.e., after the flagged "post-2026" cutoff): "While disconnected from IoT Hub, the IoT Edge device, its deployed modules, and any downstream devices can keep operating **indefinitely**... IoT Edge devices and their assigned downstream devices can function offline indefinitely after the initial, one-time sync. However, message storage depends on the time to live (TTL) setting and available disk space." ([Microsoft Learn — Operate Azure IoT Edge devices offline](https://learn.microsoft.com/en-us/azure/iot-edge/offline-capabilities))

**Conclusion for Q1a: Classic Azure IoT Edge is actively supported, NOT deprecated, and has an even longer confirmed runway than before this research pass** (LTS 1.6 through November 2028, with a stated intent to keep shipping new LTS releases on a rolling cadence before the prior one expires). No deprecation or retirement date exists.

### Azure IoT Operations — still positioned as "Microsoft's recommended platform for new edge-connected solutions," more explicitly than before

- The Azure Architecture Center's **"Introduction to Azure IoT"** page (updated 2026-04-15, squarely inside the "post-2026" window) now frames the Azure IoT portfolio as having only **two primary platforms**: Azure IoT Hub (cloud-connected) and **Azure IoT Operations** (edge-connected) — classic Azure IoT Edge is **not named anywhere** in this canonical architecture-comparison document any longer. Direct quotes: "Build edge-connected solutions with Azure IoT Operations. Azure IoT Operations is Microsoft's recommended platform for new edge-connected solutions and is the foundation of the digital operations strategy for industrial and OT environments," and later, "Azure IoT Operations: Microsoft's platform for connected operations, enabling edge-connected solutions for industrial and OT environments. Azure IoT Operations is Microsoft's **primary recommendation** for new edge-connected solutions." ([Microsoft Learn — Introduction to Azure IoT](https://learn.microsoft.com/en-us/azure/architecture/guide/iiot-guidance/iiot-architecture))
- This is a **strengthening**, not a softening, of the positioning found in the original research pass — the newest version of this flagship guidance page has gone from mentioning IoT Edge alongside IoT Operations to omitting classic IoT Edge from the portfolio narrative entirely, while IoT Operations' "primary recommendation" language is repeated twice on the page.
- Important nuance: this is **positioning/roadmap messaging in architecture guidance**, not a technical or lifecycle deprecation — classic IoT Edge's own product documentation (support, version history, lifecycle pages) shows no equivalent language and continues to actively ship and support new LTS releases, as detailed above.

## Question 1 (continued): Has Azure IoT Operations' documented offline ceiling changed from 72 hours?

**No change found. The 72-hour ceiling is confirmed current and unchanged.**

- **Microsoft Learn — What is Azure IoT Operations?** (`overview-iot-operations`), fetched directly (page `updated_at`: 2026-06-04, well within the "post-2026" window), still states verbatim: "Azure IoT Operations: ... Can operate offline for a maximum of **72 hours**. Degradation might occur during this period. However, the service resumes full functionality when it reconnects." ([Microsoft Learn — What is Azure IoT Operations?](https://learn.microsoft.com/en-us/azure/iot-operations/overview-iot-operations))
- No separate "offline/disconnected-operations" sub-page specific to Azure IoT Operations was found (unlike classic IoT Edge, which has a dedicated `offline-capabilities` article); the 72-hour figure lives only in this single bullet on the product overview page in both the current and previously-fetched versions. No FAQ page exists at the guessed URL (`overview-iot-operations-faq` returned HTTP 404), and no dedicated compare/migration article was found at guessed URLs (`overview-iot-operations-compare` and `iot-edge/quickstart-migrate` both 404).

## Official guidance comparing classic IoT Edge vs Azure IoT Operations for long-duration offline scenarios

**No dedicated "when to choose IoT Edge vs IoT Operations for offline/disconnected scenarios" comparison page was found.** What exists instead:

- The Architecture Center's "Introduction to Azure IoT" page frames the choice purely as **cloud-connected (IoT Hub) vs edge-connected (IoT Operations)**, with IoT Operations as the unqualified recommendation for all edge-connected/OT scenarios — it does not mention offline-duration tradeoffs, and does not mention classic IoT Edge as an alternative at all. ([Microsoft Learn — Introduction to Azure IoT](https://learn.microsoft.com/en-us/azure/architecture/guide/iiot-guidance/iiot-architecture))
- Classic IoT Edge's own documentation does not reference Azure IoT Operations or offer comparative guidance either — it is written as a self-contained product with no "vs IoT Operations" framing.
- **No official Microsoft page was found that explicitly discusses the 72-hour offline ceiling as a decision factor, or that advises using classic IoT Edge instead of IoT Operations for long-duration disconnected/offline industrial scenarios.** This specific comparison — offline-duration tradeoff between the two platforms — appears to be an analytical gap in Microsoft's own public documentation, not merely a gap in this research pass. Direct confirmation with a Microsoft account/partner channel (as originally flagged) is still the only way to get an explicit, authoritative answer to "which one does Microsoft recommend for a site that may be disconnected far longer than 72 hours," since the two product documentation sets don't cross-reference each other on this dimension.

## Question 2: Azure Local (Stack HCI) disconnected-operations documentation

The previously-404'd page now resolves at a corrected path: **`https://learn.microsoft.com/en-us/azure/azure-local/manage/disconnected-operations-overview`** ([Microsoft Learn — Disconnected operations for Azure Local overview](https://learn.microsoft.com/en-us/azure/azure-local/manage/disconnected-operations-overview)).

Key findings from this page:

- **"Disconnected operations" is a formal, gated Azure Local deployment mode**, not simply "Azure Local also tolerates being offline." It stands up a **local control plane** (an on-premises replica of Azure Arc/Resource Manager control-plane functions) so that Azure Local can be deployed and managed **entirely without any connection to the Azure public cloud**, using a "familiar Azure portal and Azure CLI experience" served locally.
- **Eligibility is restrictive and procurement-gated**, not a default capability of any Azure Local cluster: it requires (a) an "eligible agreement" with Microsoft (Microsoft Online Subscription Agreement/MOSA is explicitly *not* eligible), (b) an active Standard-or-higher support plan (directly or via a partner), (c) a documented valid business need (sovereignty/compliance, remote/isolated locations such as "oil rigs and manufacturing sites," or heightened security posture), and (d) a **dedicated management cluster** (extra hardware) to host the local control plane. Applicants submit a form and wait up to 10 business days for approval (approved/rejected/queued/needs-more-info).
- **No documented maximum disconnection window or time-based degradation is stated for the "Disconnected operations" feature itself** — by design, it is meant to run without any Azure connectivity indefinitely (the scenarios listed — sovereign government/healthcare/finance workloads, remote oil rigs — are inherently long-duration or permanent disconnection use cases). This is the closest Azure Local analogue to classic IoT Edge's "indefinite" claim, but it is **not a lightweight or default posture** — it is a heavyweight, specially-provisioned deployment topology requiring its own dedicated cluster and a formal Microsoft approval/eligibility process.
- Separately, **standard (non-disconnected-operations) Azure Local deployments have an explicit periodic Azure connectivity requirement**: "Azure Local needs to periodically connect to Azure for [managing] Well-known Azure IPs... Outbound direction... Ports 80 (HTTP) and 443 (HTTPS)," covering "Azure Stack HCI OS management, including licensing and billing." ([Microsoft Learn — Firewall requirements for Azure Local](https://learn.microsoft.com/en-us/azure/azure-local/concepts/firewall-requirements)) This page does not state an exact maximum allowable gap (e.g., a specific day count) between check-ins; historically Azure Stack HCI/Azure Local have required periodic (commonly cited elsewhere as ~30-day) check-ins for licensing/billing compliance in the *non*-disconnected-operations mode, but no specific number could be confirmed from an official Learn page in this research pass (guessed URLs for a dedicated "cloud connection" or "compare Azure Local/Azure Stack HCI" page both returned HTTP 404). This should still be treated as an open item if Azure Local is evaluated further.

**Conclusion for Q2:** Azure Local does have a documented "disconnected operations" capability with no stated maximum offline duration, similar in spirit to classic IoT Edge's indefinite claim — but it is a **formal, procurement-gated, dedicated-hardware product tier** (extra management cluster, Microsoft eligibility approval, Standard-or-higher support plan, documented sovereign/compliance business justification), not a casual "also works if the internet drops" capability. For a training-room deployment without a sovereign/compliance mandate, this eligibility bar is a material adoption barrier that doesn't apply to classic IoT Edge's offline capability, which requires no special approval, agreement type, or dedicated hardware beyond the edge device itself.

## Sources consulted (all fetched directly in this research pass)

- https://learn.microsoft.com/en-us/azure/iot-edge/version-history (also fetched with `?view=iotedge-1.5`)
- https://learn.microsoft.com/en-us/lifecycle/products/azure-iot-edge
- https://learn.microsoft.com/en-us/azure/iot-edge/support (also fetched with `?view=iotedge-1.5`)
- https://learn.microsoft.com/en-us/azure/iot-edge/about-iot-edge (also fetched with `?view=iotedge-1.5`)
- https://learn.microsoft.com/en-us/azure/iot-edge/offline-capabilities (also fetched with `?view=iotedge-1.5`)
- https://learn.microsoft.com/en-us/azure/iot-edge/iot-edge-as-gateway (also fetched with `?view=iotedge-1.5`)
- https://learn.microsoft.com/en-us/azure/iot-operations/overview-iot-operations (fetched twice, including with `?tabs=portal`)
- https://learn.microsoft.com/en-us/azure/iot-operations/get-started-end-to-end-sample/quickstart-deploy
- https://learn.microsoft.com/en-us/azure/architecture/guide/iiot-guidance/iiot-architecture
- https://learn.microsoft.com/en-us/azure/azure-local/ (TOC/landing page)
- https://learn.microsoft.com/en-us/azure/azure-local/manage/disconnected-operations-overview
- https://learn.microsoft.com/en-us/azure/azure-local/concepts/firewall-requirements
- https://learn.microsoft.com/en-us/azure/azure-local/manage/azure-arc-vm-management-overview

Attempted but failed (HTTP 404 or content extraction failure — confirms these specific guessed URLs do not exist, not that the topic is undocumented):

- https://learn.microsoft.com/en-us/azure-stack/hci/manage/disconnected-operations (old path; superseded by azure-local path above)
- https://learn.microsoft.com/en-us/azure/azure-local/manage/disconnected-operations (missing `-overview` suffix)
- https://learn.microsoft.com/en-us/azure/iot-operations/discover-manage-assets/overview-what-is-iot-operations
- https://learn.microsoft.com/en-us/azure/iot-operations/overview-iot-operations-compare
- https://learn.microsoft.com/en-us/azure/iot-operations/overview-iot-operations-faq
- https://learn.microsoft.com/en-us/azure/iot-edge/quickstart-migrate
- https://learn.microsoft.com/en-us/azure-stack/hci/manage/review-cloud-connection
- https://learn.microsoft.com/en-us/azure/azure-local/concepts/compare-azure-local-azure-stack-hci
- https://learn.microsoft.com/en-us/azure/architecture/guide/iiot-guidance/iiot-solution-architecture
- Bing searches for `"Azure Local" disconnected operations site:learn.microsoft.com` and `"Azure IoT Edge" vs "Azure IoT Operations" site:learn.microsoft.com` (returned only Bing chrome/navigation, no usable indexed result snippets)

## Follow-on research not completed (recommended next steps)

- [ ] Confirm the exact periodic check-in/connectivity interval required for *standard* (non-disconnected-operations) Azure Local deployments for licensing/billing compliance (e.g., whether a ~30-day figure is still current) — no official Learn page with this specific number was found or fetched successfully in this pass.
- [ ] Directly ask a Microsoft account/partner contact whether any written guidance exists (even internal/partner-facing, not public Learn content) explicitly comparing classic IoT Edge vs Azure IoT Operations for long-duration (multi-day+) offline industrial scenarios, since no public page cross-references the two products on this dimension.
- [ ] If Azure Local's "Disconnected operations" feature is considered as an alternative to classic IoT Edge, obtain the eligibility-form outcome and dedicated-management-cluster hardware/cost estimate directly, since this research pass could only confirm the eligibility criteria, not concrete cost/lead-time figures.

No clarifying questions require user input at this time; both original follow-on gaps were resolved with current, cited Microsoft Learn sources.
