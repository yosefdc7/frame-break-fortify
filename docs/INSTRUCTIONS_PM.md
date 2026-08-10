# Project Management Guide: Frame → Break → Fortify

As a Project Manager or Change Manager, you are frequently handed drafts — playbooks, processes, project plans, change impact assessments, governance models — and asked to manage work whose underlying assumptions you did not create.

The purpose of **Frame → Break → Fortify** is to help you interrogate those artifacts without pretending you are the subject-matter expert for every answer.

A core operating rule is:

> **The PM does not need to personally know or decide everything.**

Frame and Break separate analytical completion from downstream readiness. They can identify the exact missing question, weakness, treatment decision, or risk while routing unresolved items to the stakeholder who actually owns the answer.

Fortify adds another control: the PM should be able to see and validate the **reliable sources used as the basis for strengthening** rather than accepting an AI-selected framework invisibly.

---

## 1. Validate the Plan Before Challenging It — `/frame`

Frame reconstructs what the artifact actually says before anyone tries to improve or attack it.

It should establish:

* intended outcomes;
* scope and exclusions;
* operating logic;
* assumptions;
* dependencies;
* evidence quality;
* decision rights; and
* unresolved material questions.

### Question Register

Every material Frame interview question receives a stable `FQ-###` ID and remains in the **Question Register**, including questions answered immediately.

Question states are:

* **Open** — temporary; the question has not yet been dispositioned;
* **Answered** — resolved; or
* **Deferred** — routed to another person or team.

A material Open question means Frame is still **In Progress**. To finish the Frame review, answer it or choose **Ask someone else / save this question**.

Deferred questions also appear in **Questions for Others**, which acts as the handoff list for Legal, Engineering, a Sponsor, Vendor Management, Operations, or another stakeholder.

Example:

```text
FQ-003 — Who has final production approval authority?
Suggested respondent: Sponsor / Governance Lead
Blocking: Yes
Status: Deferred
```

When the answer arrives later:

```text
FQ-003: Steering Committee is the final approver.
```

Run `/frame` on the existing Frame Brief. Frame should update the existing question rather than restarting the review.

### What Frame should not do

Frame clarifies the system; it does **not** try to break it.

Premortems, inversion, kill conditions, worst-case failure chains, and failure propagation belong to Break. Keeping this boundary makes the sequence useful:

```text
FRAME = understand accurately
BREAK = challenge aggressively
FORTIFY = improve deliberately
```

---

## 2. Check Whether Break Can Reliably Start

When `/break` receives a Frame Brief, it must respect Frame's readiness result.

### Ready for Break
Proceed normally.

### Ready for Break with Conditions
Proceed, but preserve the listed `FQ-###` conditions. Do not silently assume those questions are already resolved.

### Awaiting External Input
Break may analyze unaffected areas, but must not claim that a failure path is fully tested when its logic still depends on missing upstream information.

Example:

```text
FQ-008 — Vendor peak capacity is unknown.
```

Break can still challenge governance, adoption, or decision rights if those areas are independent. It should not pretend the capacity failure path is complete until `FQ-008` is resolved.

If an unresolved Frame question prevents a material part of the plan from being stress-tested, Break remains **In Progress**.

---

## 3. Stress-Test the Plan — `/break`

Break assumes the plan can fail and tries to discover how.

It uses:

* premortem;
* inversion;
* dependency attacks;
* expected/adverse/extreme-but-plausible scenarios;
* edge cases;
* human-behavior failure; and
* contradiction analysis.

Material findings receive stable `BF-###` IDs.

### Break priorities

* **Blocker** — likely to invalidate the plan, prevent safe execution, or materially block treatment direction.
* **Major concern** — material weakness requiring treatment or conscious risk acceptance.
* **Watch item** — plausible but manageable uncertainty.
* **Observation** — useful improvement without material execution risk.

### Decisions after a finding

For every Blocker or Major concern, Break recommends a response before asking you to decide.

You can:

* accept the recommendation;
* choose an alternative;
* explicitly accept a legitimate risk; or
* choose **Ask someone else / save this decision**.

`Open` is temporary. A Blocker or Major concern cannot remain Open if Break is to become Complete.

Example:

```text
BF-007 — Production approval depends on one executive with no delegated authority.

Recommended response:
Establish delegated approval authority.

Disposition:
Deferred to Sponsor
```

When the Sponsor responds:

```text
BF-007: Sponsor approved delegated authority.
```

Run `/break` on the existing Break Report. Break should update `BF-007` and selectively re-test the affected approval-bottleneck path rather than rerunning the whole review.

Watch items and observations do not require treatment decisions unless they are escalated.

---

## 4. Understand Break Completion vs Fortify Readiness

A completed Break Report does not mean every stakeholder has already made every treatment decision.

### Break Status: Complete
Means the required material objectives were stress-tested, the material weaknesses were recorded, and every Blocker/Major concern has both a recommendation and a terminal disposition.

### Ready for Fortify
Enough treatment direction exists to strengthen the plan.

### Ready for Fortify with Conditions
Fortify can proceed, but the listed `BF-###` conditions must remain visible.

### Awaiting External Input
An unresolved stakeholder decision materially changes which treatment should be implemented.

This lets the PM say:

> "The adversarial analysis is complete. We are waiting on the Sponsor for BF-007 before the governance treatment can be finalized."

That is a useful project-control outcome, not a failed review.

---

## 5. Strengthen the Plan — `/fortify`

Fortify takes the understood weaknesses and engineers stronger controls into the artifact.

### Preferred: Break-backed mode

When a Break Report exists, Fortify uses its `BF-###` findings and readiness state.

If a finding is **Awaiting External Input**, Fortify may strengthen unaffected areas but must not silently choose the missing decision.

### Optional: Direct mode

You can run Fortify without a Break Report when you intentionally want direct strengthening.

In that mode Fortify:

* explicitly states that no formal Break analysis was supplied or performed;
* identifies **provisional weaknesses** directly from the source document;
* does not create `BF-###` IDs; and
* does not imply that premortem or adversarial testing occurred.

Direct mode is useful for a fast improvement pass, but it is not equivalent to the full pipeline.

---

## 6. Choose the Source Basis Before Fortifying

Fortify should not silently decide which framework or methodology becomes the foundation of the strengthened plan.

Before material externally grounded recommendations are generated, Fortify asks how you want to establish the source basis.

### Option A — Provide approved sources

Upload files or share links to references you already trust, such as:

* approved internal PPMs or playbooks;
* internal policies or standards;
* industry standards;
* recognized methodologies or frameworks;
* peer-reviewed scientific studies or systematic reviews;
* official guidance from professional or regulatory bodies; or
* first-party reference documentation.

Fortify reads these sources, records their applicability and limitations, and treats explicitly approved references as **User Approved**.

### Option B — Ask Fortify to search

Fortify searches for strong candidate sources, prioritizing:

1. governing requirements and official standards;
2. primary institutional frameworks and methodologies;
3. peer-reviewed studies and systematic reviews;
4. authoritative first-party documentation; and
5. credible secondary sources only when stronger primary material is unavailable.

Fortify then shows a concise candidate set before relying on it.

Example:

```text
Candidate Source 1
PMI Standard for Project Management
Type: Professional standard
Supports: Governance and decision-rights theme
Why applicable: Provides formal governance and accountability concepts
Limitation: Must be adapted to the organization's operating model
Status: Candidate — Awaiting User Validation
```

You can approve all, approve selected sources, reject a source, or ask Fortify to search for alternatives.

### Option C — Hybrid

Use your approved documents first, then let Fortify search only where the supplied references do not adequately cover a Break theme.

### Source statuses

Fortify keeps a **Source Register** with statuses such as:

* **Governing** — binding law, regulation, contract, or mandatory policy;
* **User Approved** — accepted as part of the design basis;
* **Candidate — Awaiting User Validation** — found by Fortify but not yet approved for use as the material basis; or
* **Rejected** — considered but intentionally not used.

The user-validation requirement applies to material frameworks, methodologies, standards, studies, or references used as the basis of a recommendation. Fortify does not need approval for every incidental factual citation.

Binding requirements are different: a law, regulation, contract, or mandatory policy is not made optional merely because it is not the PM's preferred methodology. Fortify should surface it as a **Governing** constraint and allow the user to validate applicability or interpretation.

---

## 7. Choose Controls by Failure Mechanism, Not by Label

Break severity tells Fortify **how much protection is justified**. It does not automatically dictate the type of control.

Useful patterns include:

| Pattern | Best fit |
|---|---|
| **Redundancy** | A single point of failure needs an independent backup path |
| **Contingency Trigger** | A known exposure can be managed through a defined trigger and pre-agreed response |
| **Graceful Degradation** | Partial service or reduced scope can preserve value during failure |
| **Redesign / removal** | The current design is fundamentally unsafe, prohibited, or structurally wrong |
| **Validation** | The main weakness is insufficient evidence or verification |
| **Sequencing / scope change** | Exposure can be reduced by changing what happens first or how much is attempted |
| **Governance change** | The weakness is ownership, authority, escalation, or decision rights |

A Blocker often needs strong structural protection, but not every Blocker needs redundancy.

Example:

```text
Blocker:
The process violates a mandatory contractual requirement.
```

The appropriate treatment is likely to redesign the process to comply — not to create a redundant version of the non-compliant process.

Fortify should select the treatment that directly addresses the actual failure mechanism.

Optionality and learning loops should also be used where they materially improve resilience, not added as ceremony to every recommendation.

---

## 8. Practical End-to-End Example

A project plan assumes an external team will approve production deployment.

### Frame

```text
FQ-004 — Who has final production approval authority?
Status: Deferred
Suggested respondent: Sponsor / Governance Lead
Blocking: Yes
```

Frame can finish its reconstruction, but reports **Awaiting External Input** for Break.

The Sponsor answers:

```text
FQ-004: CTOO Steering Committee owns final approval.
```

Frame resumes and becomes **Ready for Break**.

### Break

Break discovers:

```text
BF-006 — Steering Committee meets too infrequently for the stated release model.
Priority: Blocker
Recommended response: Establish delegated approval for predefined low-risk releases.
```

The PM cannot authorize the governance change, so `BF-006` is Deferred to the Sponsor.

Break can complete its analysis but reports **Awaiting External Input** for Fortify.

The Sponsor later replies:

```text
BF-006: Delegated approval approved for predefined low-risk releases.
```

Break selectively re-tests the approval failure path and becomes **Ready for Fortify**.

### Fortify — select the evidence basis

Fortify asks:

```text
How should I ground the strengthening recommendations?

A. I will upload/share approved sources
B. Search for reliable candidate sources and let me validate them
C. Hybrid — use my sources first, then search for gaps
```

The PM chooses **B**.

Fortify searches and proposes suitable governance/decision-rights references. The PM validates the sources that are appropriate for the organization.

Fortify then incorporates:

* delegated authority rules;
* eligibility criteria for delegated approval;
* an escalation path for exceptions;
* evidence/validation for the new control; and
* any useful contingency or learning mechanism.

The final change remains traceable back to `BF-006`, the upstream `FQ-004` context, and the **User Approved** source basis.

---

## Statuses to Pay Attention To

### Frame

* **Frame Status: Complete** — reconstruction complete; no material question remains Open.
* **Ready for Break** — reliable stress-testing can proceed.
* **Ready for Break with Conditions** — proceed while respecting listed `FQ-###` conditions.
* **Awaiting External Input** — external input materially blocks reliable stress-testing.

### Break

* **Break Status: Complete** — required stress-testing complete; Blockers/Major concerns have recommendations and terminal dispositions.
* **Ready for Fortify** — treatment direction is sufficient.
* **Ready for Fortify with Conditions** — Fortify can proceed under explicit `BF-###` conditions.
* **Awaiting External Input** — external input materially determines treatment direction.

### Fortify source grounding

* **Governing** — mandatory source or constraint.
* **User Approved** — accepted design-basis source.
* **Candidate — Awaiting User Validation** — AI-found source not yet approved as the material basis.
* **Rejected** — considered but not used.

---

## Mental Models

1. **FRAME — First principles and steel-manning**: reconstruct the strongest accurate version of the plan from evidence, assumptions, and explicit decisions.
2. **BREAK — Inversion and falsifiability**: attempt to prove the plan wrong before reality does.
3. **FORTIFY — Evidence-grounded margin of safety and adaptive design**: select a reliable, validated source basis; build controls proportional to the actual failure mechanism; and preserve useful options and learning where they improve resilience.

The result is not a PM who knows every answer. It is a PM who can reliably distinguish **what is known, what can fail, who must decide, which evidence is trusted, and what must change next**.