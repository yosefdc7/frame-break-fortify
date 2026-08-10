---
name: fortify
description: Strengthen a plan by building margin of safety and antifragility into it, grounded in external knowledge. Use after Break identifies weaknesses and the Break Report is sufficiently ready for treatment. Produces targeted recommendations per Break theme, then a strengthened artifact.
license: MIT
metadata:
  version: "0.2.0"
---

# Fortify Skill

**Mission**: Actively strengthen the plan by building **margin of safety** and **antifragility** into it, grounded in external knowledge. Fortify is an engineer, not a compiler — it adds controls, contingencies, and design principles that the original plan and Break findings do not already contain.

Use Fortify after Break identifies weaknesses. Rely on Break's findings as the input. Use external knowledge (training knowledge + documentation lookup) to generate recommendations that tackle those weaknesses. The Evidence Contract governs source quality.

When a Break Report is supplied, respect its **Fortify readiness** status before deciding how far Fortify can proceed. Never silently override a deferred Break decision or invent the answer to a blocking `BF-###` finding.

**Triggers**: `/fortify <document>` or `/fortify <document> BREAK-REVIEW.md`

---

## The Evidence Contract (Summary)

* **Evidence Hierarchy**: Prefer laws, regulations, and official standards.
* **Claim Classification**: Distinguish between Verified, Supported, Inferred, Assumed, and Unknown claims.
* **Source Fit**: Only apply external frameworks if they meaningfully apply to the artifact and context.
* **Citation Rule**: Identify sources for recommendations grounded in external standards.

*(For full details, see `references/evidence-contract.md`)*

---

## Core Concepts

### Margin of Safety
Design beyond the minimum requirement so the plan can absorb unexpected stress. Three forms, weighted by Break priority:

| Break Priority | Margin of Safety Form | What It Means |
|---|---|---|
| **Blocker** | **Redundancy** | A structurally independent backup path. If the primary fails, the backup executes without depending on the same person, process, or system. |
| **Major Concern** | **Contingency Trigger** | An explicit trigger condition and a pre-agreed response. Not "monitor X" but "if X happens, do Y, and Z person is accountable." |
| **Watch Item** | **Graceful Degradation** | A defined partial-success path. Not binary launch/don't-launch, but a spectrum of what the plan looks like if a dependency partially fails. |

### Antifragility
The plan gets stronger from stress, not just survives it. Two mechanisms:

| Mechanism | What It Means |
|---|---|
| **Optionality** (primary) | Preserve future options rather than locking in irreversible decisions. Every recommendation should keep at least one alternative path open. Frame decisions as "at [milestone], choose between X and Y based on [observable criteria]" rather than "we will do X." |
| **Learning Loops** (secondary) | Every post-launch activity produces a documented improvement. AARs, hypercare incidents, and adoption metrics feed concrete changes to the next cycle — not just "reviews." |

---

## Process

### Step 0 — Check Break Readiness

When a Break Report is provided, inspect **Fortify readiness** before strengthening the artifact.

* **Ready for Fortify** — proceed normally.
* **Ready for Fortify with Conditions** — proceed while explicitly preserving the listed conditions. Do not strengthen the artifact in a way that assumes those conditions have already been resolved.
* **Awaiting External Input** — identify the blocking `BF-###` findings first. Do not invent or silently choose the missing stakeholder decision. Fortify may still strengthen unaffected themes, but any recommendation or artifact section whose direction materially depends on a blocking finding must remain **Decision Required / Awaiting External Input** rather than being presented as final.

If no Break Report is supplied, Fortify may proceed from the user's document and available context, but must not pretend that a formal Break readiness assessment occurred.

### Step 1 — Preserve Intent
Restate the agreed objective. Improvements must support that objective. Maintain the author's intent.

### Step 2 — Cluster Break Findings into Themes
Group Break's findings (Blockers, Major Concerns, Watch Items) into themes. A theme is a shared root cause or shared domain (e.g., "capacity risk", "data trust", "governance gaps"). Multiple findings that share a root cause collapse into one theme. Each theme gets one targeted recommendation.

Preserve `BF-###` identifiers in the theme mapping so recommendations remain traceable to the Break Report.

### Step 3 — Generate Targeted Recommendations
For each theme, produce a recommendation that:
1. **Names the weakness**: Which Break finding(s) this addresses, including `BF-###` IDs when available.
2. **Retrieves external knowledge**: Search training knowledge and documentation for the most relevant framework, principle, or thought leadership that applies to this weakness. Apply the Evidence Contract's Source Fit check — only use knowledge that meaningfully applies to this artifact and context.
3. **Cites the source**: Name the framework, principle, or thought leader. Classify the grounding (Verified / Supported / Inferred).
4. **Builds margin of safety**: Apply the appropriate form based on Break priority (Redundancy / Contingency Trigger / Graceful Degradation).
5. **Preserves optionality**: State what future options this recommendation keeps open.
6. **Defines a learning loop** (where applicable): What this recommendation teaches the plan for the next cycle.

If a recommendation requires a decision the user hasn't made, flag it as **Decision Required** in the output. Do not invent the decision.

If the related Break finding is marked **Awaiting External Input** and the missing decision materially determines the treatment direction, keep that recommendation provisional and do not encode one option into the Strengthened Artifact as if it were approved.

### Step 4 — Strengthen the Artifact
Incorporate all approved or safely conditionable recommendations into the plan. Where applicable, improve: objectives, scope, sequencing, ownership, responsibilities, dependencies, governance, decision rights, controls, measures, acceptance criteria, contingencies, communications, implementation steps, escalation paths.

For recommendations blocked by unresolved external input:
* Preserve the relevant place in the artifact as **Decision Required / Awaiting External Input**.
* State the `BF-###` finding that blocks finalization.
* Preserve viable options when possible rather than choosing one silently.
* Do not treat provisional language as an approved control.

Replace vague completion language with observable criteria. Use context-appropriate metrics rather than inventing arbitrary numbers.

### Step 5 — Trace Changes
Every material change maps back to at least one of:
* Original requirement
* Frame finding or `FQ-###` question
* Break finding or `BF-###` finding
* External evidence (with citation)
* Explicit user decision

### Step 6 — Re-validate
Before finishing, check:
* Original intent remains intact
* Blockers have been addressed, explicitly accepted, or clearly preserved as unresolved external decisions
* No deferred `BF-###` decision was silently resolved by Fortify
* New contradictions were not introduced
* New unsupported claims were not introduced
* Critical dependencies have owners when known
* Important outcomes have observable success criteria
* Conditions from **Ready for Fortify with Conditions** remain visible in the output

---

## Output

Produce two layers:

### Layer 1 — Targeted Recommendations (Primary Deliverable)

For each Break theme:

| Field | Content |
|---|---|
| **Theme** | The shared root cause or domain |
| **Weakness** | The Break finding(s) being addressed, with `BF-###` IDs when available |
| **Recommendation** | The concrete action to take |
| **Source** | The framework, principle, or thought leader (with citation and claim classification) |
| **Margin of Safety** | The specific control added: Redundancy / Contingency Trigger / Graceful Degradation |
| **Optionality Preserved** | What future options this keeps open |
| **Learning Loop** | What this teaches the plan for the next cycle (if applicable) |
| **Decision Required** | Any unresolved decision, including blocking `BF-###` IDs when applicable |

### Layer 2 — Strengthened Artifact (Secondary Deliverable)

The revised plan incorporating all approved or safely conditionable Layer 1 recommendations. Include:

* **A. Strengthened Artifact**: The revised plan, playbook, framework, or document.
* **B. Change Ledger**: For material changes, record: Change, Reason, Source finding, Evidence, Trade-off.
* **C. Residual Risks**: Anything deliberately left unresolved or explicitly accepted.
* **D. Validation Matrix**: Table format: `Requirement | Evidence | Test | Status`.
* **E. Outstanding Decisions**: Any unresolved `BF-###` items that prevent finalizing a treatment, with the required decision/input and current condition.
* **F. Final Verdict**: Ready, Ready with conditions, or Not ready. Explain conditions or blockers.

If Break readiness was **Awaiting External Input**, Fortify's output must not claim full readiness while a blocking treatment decision remains unresolved.

---

## Completion Criterion

Fortify is complete when all applicable conditions are met:

1. **Every Break theme that can be responsibly treated has a targeted recommendation** with a cited source and an appropriate margin of safety control.
2. **Recommendations build antifragility** — they preserve optionality and define learning loops where applicable.
3. **Approved or safely conditionable recommendations are incorporated into the Strengthened Artifact** — nothing that can be implemented safely stays only in the recommendation layer.
4. **Blocking external decisions remain explicit** — Fortify never resolves a deferred `BF-###` decision by assumption.

If a blocking Break finding is still **Awaiting External Input**, Fortify may produce partial/provisional work for unaffected areas, but the strengthened artifact is not final for the blocked treatment path. The final verdict must reflect that dependency.
