---
name: break
description: Stress-test plans and business documents, expose failure paths, and turn unresolved weaknesses into explicit findings that can be resolved now, accepted, or routed to the right person later.
disable-model-invocation: true
license: MIT
metadata:
  version: "0.2.0"
---

# Break Skill

**Mission**: Attempt to make the proposed system fail before reality does, while turning unresolved blockers and decisions into explicit findings that can be resolved now, accepted as risk, or routed to the right person later.

Use Break after there is sufficient shared understanding of the artifact, ideally after `/frame`. Break is adversarial analysis without becoming contrarian for its own sake.

Use Break when:
* A plan appears coherent but has not been stress-tested
* Dependencies, handoffs, capacity, governance, or adoption may fail under pressure
* The user wants a premortem or adversarial review
* Important weaknesses require decisions from people other than the current user
* A prior Break Report needs to be resumed after new stakeholder input arrives

**Triggers**:
* `/break <document>`
* `/break FRAME-REVIEW.md`
* `/break <existing Break Report>` to resume prior work

---

## Core Principle

Break must distinguish between:

1. **Discovering a material failure mode**, and
2. **Obtaining the decision or input required to treat that failure mode**.

Discovering a blocker, explaining how it propagates, recommending a response, and identifying the decision or input still required is a successful Break outcome even when the current user cannot personally resolve it immediately.

A Blocker or Major concern may have one of these states/dispositions:
* **Open** — transient; currently unresolved and not yet dispositioned
* **Accepted recommendation** — the recommended response is chosen
* **Alternative selected** — a different response is chosen
* **Accepted risk** — the weakness is consciously left untreated with the trade-off recorded
* **Deferred** — the decision or input is saved for another person or team

`Open` is not a terminal disposition. A material Blocker or Major concern must become **Accepted recommendation, Alternative selected, Accepted risk, or Deferred** before Break Status can become Complete.

A deferred finding is not merely an Unknown. It is a known failure exposure with an explicit decision or information need and a disposition.

---

## The Evidence Contract (Summary)

* **Evidence Hierarchy**: Prefer laws, regulations, official standards, primary documentation, and authoritative internal sources.
* **Claim Classification**: Distinguish between Verified, Supported, Inferred, Assumed, and Unknown claims.
* **Source Fit**: Only apply external frameworks if they meaningfully apply to the artifact and context.
* **Citation Rule**: Identify sources for recommendations grounded in external standards or frameworks.

*(For full details, see `references/evidence-contract.md`)*

---

## Process

### Step 0 — Check Frame Readiness

When a Frame Brief is supplied, inspect **Frame Status** and **Readiness for Break** before beginning full adversarial analysis.

* **Ready for Break** — proceed normally.
* **Ready for Break with Conditions** — proceed while preserving the listed conditions and blocking/non-blocking `FQ-###` context. Do not stress-test from assumptions that contradict those conditions.
* **Awaiting External Input** — identify the blocking `FQ-###` questions first. Break may stress-test unaffected areas, but it must not treat a failure path as fully analyzed when its logic materially depends on missing upstream information.
* **Frame Status: In Progress** — treat the Frame Brief as not fully reconstructed. Break may perform clearly labeled partial analysis on stable areas, but must not claim full Break completion while material upstream ambiguity prevents required objectives from being stress-tested.

When upstream `FQ-###` questions block analysis:
1. Preserve those IDs in the Break Report under **Upstream Frame Dependencies**.
2. Do not invent answers to them.
3. Do not create a `BF-###` finding merely to disguise an unresolved Frame question.
4. Analyze unaffected failure paths when useful.
5. Keep Break Status **In Progress** if the missing Frame input prevents any material objective from being fully stress-tested.

If no Frame Brief is supplied, Break may proceed when the artifact has sufficient shared understanding, but must not pretend that a formal Frame readiness assessment occurred.

### Step 1 — Establish the Target
Identify what constitutes meaningful failure for this artifact, such as:
* Adoption target missed
* Project delayed
* Budget overrun
* Dependency failure
* Control failure
* Unsafe or non-compliant execution
* Decision bottleneck
* Operating model breakdown

Do not invent arbitrary thresholds when the source artifact does not provide them.

### Step 2 — Run a Premortem
Assume: **"It is six months later and this initiative failed badly."**

Work backward to generate plausible causal chains explaining the failure. Generate highly specific, contextual failure chains rather than generic risks.

### Step 3 — Apply Inversion
Ask: **"What conditions would almost guarantee failure?"**

Use the inverse to expose design requirements, controls, ownership, or contingencies that may be absent.

### Step 4 — Attack the Dependencies
Stress relevant dimensions:
* People
* Process
* Technology
* Governance
* Sequencing
* Capacity
* Data
* Suppliers
* Handoffs
* Communications
* Adoption
* Controls
* Timeline
* Decision rights

Look for failure propagation, not merely isolated risks.

### Step 5 — Test Scenarios
Test realistic variations:
* Expected case
* Adverse case
* Extreme-but-plausible case
* Edge case
* Dependency failure
* Human-behavior failure

For each material scenario, ask how the failure propagates, what detects it, what contains it, and what happens if the assumed response is unavailable.

### Step 6 — Find Contradictions
Search for material contradictions such as:
* Goals inconsistent with activities
* Dependencies without owners
* Risks without treatment
* Success metrics that cannot prove success
* Decision rights that conflict with escalation paths
* Controls that depend on the same failure source they are meant to protect against
* Timelines incompatible with stated sequencing or approvals

### Step 7 — Prioritize and Assign Finding IDs
Classify findings:
* **Blocker** — likely to invalidate the plan, prevent safe execution, or make Fortify's direction unreliable until treated or explicitly accepted
* **Major concern** — material weakness requiring treatment or conscious risk acceptance
* **Watch item** — plausible but manageable uncertainty
* **Observation** — useful improvement without material execution risk

Use qualitative priority labels instead of numeric risk scores unless the source artifact already uses a meaningful scoring method.

Every material finding receives a stable ID using the format `BF-###` when it is first recorded. Do not renumber existing IDs when the Break Report is updated.

### Step 8 — Recommend Before Asking
Every **Blocker** and **Major concern** must receive:
* **Finding**
* **Why it matters**
* **Evidence / reasoning**
* **Failure scenario**
* **Recommended response**
* **Trade-off**
* **Decision owner** — role or team if known; otherwise `To be identified`
* **Disposition**
* **Fortify blocking?** — Blocking or Non-blocking

Break is an expert challenger, not a passive questionnaire. Recommend a response before asking the user to decide whenever the evidence supports a recommendation.

Do not modify the original plan. Isolate the output to the Break Report.

### Step 9 — Resolve, Accept, or Defer Material Findings
If a Blocker or Major concern requires human judgment, ask about the finding **one at a time**.

Use the finding's stable `BF-###` ID in the question.

When genuine choices exist, present structured paths. A typical pattern is:
* **A. Recommended response** — preferred treatment and why
* **B. Alternative response** — a materially different treatment and trade-off
* **C. Another viable path or explicit risk acceptance** — only when legitimate
* **D. Ask someone else / save this decision**

The user may always provide a custom response.

Do not force all questions into identical A/B/C semantics. Options must represent genuine choices for the specific finding.

When risk acceptance is a legitimate governance choice, it may be offered as an option. Do **not** present risk acceptance as a valid substitute for a mandatory law, regulation, safety requirement, contractual obligation, or other non-waivable constraint.

When the user selects a treatment:
1. Mark the finding **Accepted recommendation** or **Alternative selected**.
2. Record the selected treatment and trade-off.
3. Update Fortify readiness.

When the user chooses D, says they do not know, or asks to save the item for another person:
1. Mark the finding **Deferred**.
2. Record the unresolved decision or input under **Decisions / Inputs Needed From Others**.
3. Infer the likely respondent role only when reasonably clear.
4. Classify whether it blocks Fortify.
5. Do not ask another question merely to identify the respondent unless ownership itself is materially necessary.
6. Continue to the next material finding.

When the user explicitly accepts the risk:
1. Mark the disposition **Accepted risk**.
2. Record the rationale and known trade-off.
3. Record the accepting decision owner only if actually known.
4. Preserve the residual risk in the Break Report.
5. Do not repeatedly reopen the same accepted risk unless new evidence materially changes the exposure or invalidates the rationale.

As the user resolves, accepts, or defers findings, update the Break Report in real time.

The interview ends when every Blocker and Major concern is **Accepted recommendation, Alternative selected, Accepted risk, or Deferred**. A material Blocker or Major concern left **Open** means Break remains In Progress.

Watch items and observations do not require a treatment disposition unless they are escalated into a Blocker or Major concern.

---

## Step 10 — Resume a Break Report

When Break receives an existing Break Report, treat it as a continuation of prior work rather than automatically starting a new adversarial review.

On resume:
1. Preserve all existing `BF-###` IDs.
2. Inspect Open and Deferred Blockers / Major concerns first.
3. Re-check any unresolved upstream `FQ-###` dependencies.
4. Detect newly supplied stakeholder answers, decisions, evidence, or updated artifact content.
5. Update the affected finding's disposition and recommended response.
6. Re-run only the scenarios, dependencies, contradictions, or failure chains materially affected by the new information.
7. Create a new `BF-###` finding only when the new information reveals a genuinely new failure mode or materially distinct weakness.
8. Do not repeat questions already resolved or explicitly accepted as risk unless new evidence invalidates the prior disposition.
9. Do not restart completed Break analysis unless the underlying artifact materially changed.
10. Recalculate Fortify readiness.

The user may respond by finding ID, for example:

`BF-003: Sponsor approved delegated approval authority.`

Break should incorporate that decision without requiring the original finding or question to be reproduced.

---

## Output

Produce a persistent Break Report containing:

1. Failure thesis
2. Top failure paths
3. Premortem results
4. Fragile assumptions
5. Missing controls
6. Dependency failures
7. Contradictions
8. Edge cases
9. Blockers
10. Major concerns
11. Watch items
12. Recommended responses
13. Upstream Frame Dependencies
14. Decisions / Inputs Needed From Others
15. Accepted risks
16. Break status
17. Fortify readiness

### Upstream Frame Dependencies

When a Frame Brief was supplied with unresolved conditions or blocking input, record:
* **FQ ID**
* **Question / missing input**
* **Why it affects Break**
* **Break areas affected**
* **Status**

Do not duplicate the full Frame Question Register; include only upstream items that materially constrain Break.

### Decisions / Inputs Needed From Others

For each Deferred Blocker or Major concern that requires external input, record:
* **BF ID**
* **Finding**
* **Decision or input needed**
* **Why it matters**
* **Recommended response**
* **Suggested respondent** — role or team when reasonably inferable; otherwise `To be identified`
* **Fortify blocking?** — Blocking or Non-blocking
* **Status** — Deferred or Resolved
* **Answer / decision** — blank until supplied

When useful, group unresolved items by likely respondent so the user can directly copy them into email, chat, meeting notes, or another stakeholder handoff.

Do not require due dates unless the source artifact or user explicitly provides them.

### Accepted Risks

For each explicitly accepted material risk, record:
* **BF ID**
* **Risk accepted**
* **Rationale**
* **Trade-off / residual exposure**
* **Decision owner** — only if known
* **Conditions that would trigger reconsideration** — when inferable from the chosen rationale; do not invent arbitrary thresholds

---

## Status Model

Break completion and Fortify readiness are separate concepts.

### Break Status

Use:
* **Complete** — every major stated objective has been stress-tested, every material weakness is recorded and prioritized, every Blocker / Major concern has a recommended response and terminal disposition, and no upstream Frame dependency prevents required material analysis
* **In Progress** — material failure analysis remains incomplete, a Blocker/Major concern remains Open, or upstream Frame ambiguity prevents required objectives from being fully stress-tested

Deferred findings do **not** prevent Break Status from becoming Complete when the analysis itself is otherwise complete.

### Fortify Readiness

Use exactly one of:

* **Ready for Fortify** — no unresolved decision or external input materially prevents strengthening the artifact; Blockers have a selected treatment or are explicitly accepted risks
* **Ready for Fortify with Conditions** — deferred items remain, but Fortify can still strengthen the artifact safely under clearly stated conditions
* **Awaiting External Input** — one or more Deferred findings materially affect which treatment Fortify should implement or whether strengthening can proceed reliably

For **Ready for Fortify with Conditions**, list the applicable `BF-###` IDs and conditions.

For **Awaiting External Input**, list the blocking `BF-###` IDs and the decision or information required.

If Break Status is **In Progress**, do not report the artifact as fully Ready for Fortify.

---

## Completion Criterion

Break is complete when:
* Every major stated objective has been tested against plausible failure conditions
* Material failure paths and propagation chains have been explored
* Every material weakness is recorded, supported with reasoning or evidence, and prioritized
* Every Blocker and Major concern has a recommended response and trade-off
* Every Blocker and Major concern has a terminal disposition: Accepted recommendation, Alternative selected, Accepted risk, or Deferred
* No Blocker or Major concern remains Open
* Deferred external items are captured under **Decisions / Inputs Needed From Others**
* Accepted risks are explicitly preserved as residual exposure
* Upstream Frame dependencies no longer prevent required material analysis
* Fortify readiness is calculated separately from Break completion

Break does **not** require the current user to personally make every decision before the Break Report can be completed.

A completed Break Report may legitimately end with **Awaiting External Input** when material treatment decisions or evidence have been identified and routed for follow-up.

When those answers or decisions become available, the user can run Break again on the existing Break Report. Break must resume from the saved `BF-###` state, incorporate the new information, selectively re-test affected failure paths, and recalculate Fortify readiness without restarting completed work.

The goal is not to eliminate every risk or uncertainty immediately. The goal is to expose material failure modes, make the treatment decision explicit, preserve accepted risk, route unresolved decisions to the right people, and leave a reliable state that can be resumed later.