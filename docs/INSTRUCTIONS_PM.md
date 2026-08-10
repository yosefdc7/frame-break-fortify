# Project Management Guide: Frame → Break → Fortify

As a Project Manager or Change Manager, you are frequently handed drafts (playbooks, processes, project plans, change impact assessments) from technical or business leads and told to "manage it."

The hardest part of your job isn't tracking the schedule—it's **interrogating these drafts for hidden risks and validating their assumptions** without having to be a subject matter expert in the underlying domains.

The **Frame → Break → Fortify** skill triplet transforms you from a "schedule tracker" into a strategic **Risk Analyst and Architect**. It provides a rigorous, objective, and non-confrontational framework to tear down a stakeholder's messy draft, validate every assumption, and rebuild it into an airtight, executable artifact.

A key operating principle is that the PM does **not** need to personally know or decide everything. Frame and Break separate analytical completion from downstream readiness: they can finish identifying the exact missing question, weakness, decision, or risk while routing unresolved items to the stakeholder who actually owns the answer.

---

## 1. Validating Assumptions (The Core Goal)

PMs constantly battle "optimism bias," where stakeholders present their assumptions as guaranteed facts.

* **The Problem**: A stakeholder claims "The engineering team will finish the API by Tuesday."
* **The Solution**: The `/frame` skill explicitly demands an **Evidence Ledger**. It forces the agent to classify every material claim in the draft as *Verified, Supported, Inferred, Assumed,* or *Unknown*.
* **The Result**: It immediately isolates risky assumptions (like the API delivery date) so they can be tested, preventing the project from being built on a house of cards.

When the PM cannot answer a material Frame question, choose **Ask someone else / save this question**. Frame records it using a stable `FQ-###` ID, explains why it matters, suggests the likely respondent role when possible, and lets the review continue. When the answer arrives later, run `/frame` on the existing Frame Brief and answer using the ID instead of restarting the interview.

## 2. Validating Project Plans & Frameworks

Project plans fail mostly due to unmapped dependencies and unrealistic sequencing.

* **The Problem**: A schedule looks good on paper but ignores external vendor bottlenecks.
* **The Solution**: The `/break` skill specifically instructs the agent to **Attack the Dependencies** (sequencing, capacity, suppliers, handoffs).
* **The Result**: By forcing a **Premortem** (assuming the project failed catastrophically six months from now and working backward), you can validate if the schedule is realistic and if the framework actually holds up when an edge case occurs.

Break assigns stable `BF-###` IDs to material findings. For each Blocker or Major concern, Break recommends a treatment before asking the PM to decide. The PM can:

* accept the recommended response;
* choose an alternative;
* explicitly accept a legitimate risk and preserve the rationale/residual exposure; or
* choose **Ask someone else / save this decision** when the decision belongs to another stakeholder.

Deferred Break findings are captured under **Decisions / Inputs Needed From Others** with the finding, required decision/input, recommended response, suggested respondent, and whether the item blocks Fortify. Break can still finish its analysis while reporting Fortify readiness separately.

When stakeholder input arrives later, run `/break` on the existing Break Report and respond using the `BF-###` ID. Break should update only the affected finding and selectively re-test impacted scenarios or dependencies rather than restarting the entire premortem.

### Practical PM Example

A Break review finds:

`BF-007 — Production approval depends on one executive with no delegated authority.`

Break recommends delegated approval authority, but the PM cannot approve that governance change. Instead of guessing, the PM defers `BF-007` to the Sponsor. The Break Report remains analytically complete but may show **Awaiting External Input** for Fortify. When the Sponsor approves delegation, the PM can resume with:

`BF-007: Sponsor approved delegated authority.`

Break incorporates the decision, re-tests the approval bottleneck failure path, and recalculates Fortify readiness.

## 3. Validating Change Impact & Change Management Plans

Change management artifacts are notorious for containing "fluff" and untestable goals.

* **The Problem**: A change management plan has a goal to "Ensure stakeholders are aligned" or "Users understand the new tool."
* **The Solution**: The `/fortify` skill directly targets this weakness. It clusters `/break` findings into themes and produces **targeted recommendations grounded in external knowledge** — each with a cited source and a margin of safety control (**Redundancy** for Blockers, **Contingency Triggers** for Major Concerns, **Graceful Degradation** for Watch Items). It also mandates replacing vague completion language with **observable criteria**.
* **The Result**: It forces you to upgrade *"users understand the change"* to *"affected users demonstrate the required process during readiness validation."* Furthermore, `/break` explicitly tests for "human-behavior failures," which is the root cause of many failed change management plans.

## 4. Validating Playbooks & Processes

A playbook is only useful if it survives contact with reality and actual users.

* **The Problem**: A process workflow looks perfect on a flowchart but fails in practice due to poor handoffs.
* **The Solution**: The `/frame` skill reconstructs the logic as `Inputs → activities → handoffs → outputs`. This visually exposes broken handoffs.
* **The Result**: Then, `/break` applies **Inversion** (*What conditions would guarantee this process fails?*) to find the missing controls in the playbook before it is ever published.

---

## Statuses to Pay Attention To

Do not confuse completion of a review with readiness for the next skill.

### Frame

* **Frame Status: Complete** means the artifact has been reconstructed and every material question has a disposition.
* **Ready for Break** means stress-testing can proceed without a material blocking information gap.
* **Ready for Break with Conditions** means Break can proceed if the listed conditions are respected.
* **Awaiting External Input** means an external answer materially affects reliable stress-testing.

### Break

* **Break Status: Complete** means the major objectives have been stress-tested, material weaknesses recorded, Blockers/Major concerns have recommendations, and findings have dispositions.
* **Ready for Fortify** means Fortify has enough resolved treatment direction to strengthen the artifact.
* **Ready for Fortify with Conditions** means Fortify can proceed under explicit conditions despite unresolved items.
* **Awaiting External Input** means an unresolved stakeholder decision or evidence materially changes which treatment should be implemented.

This prevents a common PM failure mode: treating "we found the exact decision we need from the Sponsor" as if the analysis itself failed. Finding and routing the right decision is useful project-control work even before the Sponsor answers.

---

## The Mental Models Behind the System

Instead of just trying to "think harder," this triplet acts as an operating system for established critical thinking principles:

1. **FRAME (First Principles & Steel-Manning)**: You rebuild the plan from fundamental truths (Verified facts vs Assumptions), ensuring you are evaluating the strongest possible version of the plan, rather than attacking a poorly understood straw man.
2. **BREAK (Inversion & Falsifiability)**: Charlie Munger's "Invert, always invert." By looking at the problem backward, you spot missing requirements and hidden risks. You subject the plan to rigorous attempts to prove it wrong while preserving unresolved treatment decisions for the correct owners.
3. **FORTIFY (Margin of Safety & Antifragility)**: You build a margin of safety into the plan by explicitly establishing controls and contingencies. By intentionally stressing the plan (Break) and rewriting the weaknesses (Fortify), your artifacts become more resilient and adaptive.
