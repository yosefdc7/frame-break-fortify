---
name: fortify
description: Strengthen a plan by building margin of safety and antifragility into it, grounded in external knowledge. Use after Break identifies weaknesses and the Break Report is sufficiently ready for treatment, or directly on a document with clearly labeled provisional weaknesses.
license: MIT
metadata:
  version: "0.2.0"
---

# Fortify Skill

**Mission**: Actively strengthen the plan by building **margin of safety** and **antifragility** into it, grounded in external knowledge. Fortify is an engineer, not a compiler — it adds controls, contingencies, and design principles that the original plan and Break findings do not already contain.

Fortify has two supported modes:

1. **Break-backed mode** — preferred. Use a Break Report as the weakness model and preserve its `BF-###` traceability and readiness conditions.
2. **Direct mode** — allowed when no Break Report exists. Fortify identifies provisional weaknesses directly from the document, clearly states that no formal Break analysis was performed, and does not invent `BF-###` IDs.

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
Design beyond the minimum requirement so the plan can absorb unexpected stress.

Break priority should influence the **strength** of the treatment, but it does not mechanically determine one mandatory control type.

Use these as default heuristics, not fixed mappings:

| Break Priority | Common starting pattern | Use when it fits the failure mechanism |
|---|---|---|
| **Blocker** | Strong structural protection, often **Redundancy** | The failure requires an independent backup path or elimination of a single point of failure |
| **Major Concern** | Often a **Contingency Trigger** | The risk can be managed through an explicit trigger and pre-agreed response |
| **Watch Item** | Often **Graceful Degradation** | Partial service or reduced scope can preserve value while the issue is contained |

Other treatments may be more appropriate, including removing a prohibited design, changing sequencing, clarifying ownership, adding validation, reducing scope, changing architecture, or redesigning the process. Choose the treatment that directly addresses the actual failure mechanism.

Never use redundancy, contingency triggers, or graceful degradation merely because the severity label suggests one.

### Antifragility
The plan gets stronger from stress, not just survives it. Two useful mechanisms:

| Mechanism | What It Means |
|---|---|
| **Optionality** | Preserve future options rather than locking in irreversible decisions. Frame decisions as "at [milestone], choose between X and Y based on [observable criteria]" when that genuinely improves the design. |
| **Learning Loops** | Post-launch activity produces documented improvement: reviews, incidents, evidence, or metrics feed concrete changes into the next cycle. |

Use these mechanisms when they fit the artifact. Do not force them into recommendations where they add ceremony without improving resilience.

---

## Process

### Step 0 — Select Mode and Check Readiness

#### Break-backed mode

When a Break Report is provided, inspect **Fortify readiness** before strengthening the artifact.

* **Ready for Fortify** — proceed normally.
* **Ready for Fortify with Conditions** — proceed while explicitly preserving the listed conditions. Do not strengthen the artifact in a way that assumes those conditions have already been resolved.
* **Awaiting External Input** — identify the blocking `BF-###` findings first. Do not invent or silently choose the missing stakeholder decision. Fortify may still strengthen unaffected themes, but any recommendation or artifact section whose direction materially depends on a blocking finding must remain **Decision Required / Awaiting External Input** rather than being presented as final.

#### Direct mode

When no Break Report is provided:
1. State that **no formal Break analysis was supplied or performed**.
2. Read the document for weaknesses that Fortify can responsibly strengthen directly, such as missing controls, unclear ownership, weak acceptance criteria, absent contingencies, fragile dependencies, or vague implementation language.
3. Label these as **provisional weaknesses**, not Break findings.
4. Group provisional weaknesses into strengthening themes.
5. Do **not** create `BF-###` IDs or imply that premortem, inversion, scenario testing, or full adversarial analysis occurred.
6. If the document is too ambiguous to strengthen responsibly, preserve the ambiguity as **Decision Required / External Input Needed** instead of silently deciding it.

Direct mode should not recreate the entire Break skill inside Fortify. Its purpose is to allow useful strengthening when the user intentionally skips Break while keeping the missing adversarial step explicit.

### Step 1 — Preserve Intent
Restate the agreed objective. Improvements must support that objective. Maintain the author's intent.

### Step 2 — Build Strengthening Themes

#### In Break-backed mode
Group Break findings (Blockers, Major Concerns, Watch Items) into themes. A theme is a shared root cause or domain. Multiple findings that share a root cause may collapse into one theme. Preserve `BF-###` identifiers in the theme mapping.

#### In Direct mode
Group provisional weaknesses from the source document into themes. Keep them labeled as provisional and trace them back to the relevant source sections or requirements rather than assigning Break IDs.

### Step 3 — Generate Targeted Recommendations
For each theme, produce a recommendation that:
1. **Names the weakness**: cite the relevant `BF-###` finding(s) in Break-backed mode, or the source-document weakness in Direct mode.
2. **Retrieves external knowledge**: search training knowledge and documentation for the most relevant framework, principle, standard, or thought leadership that applies to the weakness. Apply the Evidence Contract's Source Fit check.
3. **Cites the source**: name the framework, principle, standard, or thought leader. Classify the grounding (Verified / Supported / Inferred).
4. **Chooses the treatment by failure mechanism**: use redundancy, contingency triggers, graceful degradation, redesign, validation, scope change, sequencing change, governance change, or another control only when it meaningfully addresses the weakness.
5. **Builds sufficient margin of safety**: stronger findings generally require stronger controls, but severity does not dictate a fixed control category.
6. **Preserves optionality** where useful: state what future choices remain open.
7. **Defines a learning loop** where useful: state how future evidence or stress improves the next cycle.

If a recommendation requires a decision the user hasn't made, flag it as **Decision Required** in the output. Do not invent the decision.

If the related Break finding is **Awaiting External Input** and the missing decision materially determines treatment direction, keep that recommendation provisional and do not encode one option into the Strengthened Artifact as if it were approved.

### Step 4 — Strengthen the Artifact
Incorporate all approved or safely conditionable recommendations into the plan. Where applicable, improve: objectives, scope, sequencing, ownership, responsibilities, dependencies, governance, decision rights, controls, measures, acceptance criteria, contingencies, communications, implementation steps, escalation paths.

For recommendations blocked by unresolved external input:
* Preserve the relevant place in the artifact as **Decision Required / Awaiting External Input**.
* State the `BF-###` finding that blocks finalization in Break-backed mode, or the source weakness in Direct mode.
* Preserve viable options when possible rather than choosing one silently.
* Do not treat provisional language as an approved control.

Replace vague completion language with observable criteria. Use context-appropriate metrics rather than inventing arbitrary numbers.

### Step 5 — Trace Changes
Every material change maps back to at least one of:
* Original requirement or source section
* Frame finding or `FQ-###` question
* Break finding or `BF-###` finding
* Direct-mode provisional weakness
* External evidence with citation
* Explicit user decision

### Step 6 — Re-validate
Before finishing, check:
* Original intent remains intact
* In Break-backed mode, Blockers have been addressed, explicitly accepted, or clearly preserved as unresolved external decisions
* No deferred `BF-###` decision was silently resolved by Fortify
* In Direct mode, no provisional weakness is misrepresented as a formal Break finding
* New contradictions were not introduced
* New unsupported claims were not introduced
* Critical dependencies have owners when known
* Important outcomes have observable success criteria
* Conditions from **Ready for Fortify with Conditions** remain visible in the output
* The selected control actually addresses the failure mechanism rather than merely matching a severity label

---

## Output

Produce two layers:

### Layer 1 — Targeted Recommendations

For each theme:

| Field | Content |
|---|---|
| **Theme** | The shared root cause or domain |
| **Weakness** | Break finding(s) with `BF-###` IDs, or Direct-mode provisional weakness |
| **Recommendation** | The concrete action to take |
| **Source** | The framework, principle, standard, or thought leader with citation and claim classification |
| **Margin of Safety** | The specific protection or control added and why it fits the failure mechanism |
| **Optionality Preserved** | What future options this keeps open, when applicable |
| **Learning Loop** | What this teaches the plan for the next cycle, when applicable |
| **Decision Required** | Any unresolved decision, including blocking `BF-###` IDs when applicable |

### Layer 2 — Strengthened Artifact

The revised plan incorporating all approved or safely conditionable Layer 1 recommendations. Include:

* **A. Strengthened Artifact**: The revised plan, playbook, framework, or document.
* **B. Change Ledger**: For material changes, record: Change, Reason, Source finding/weakness, Evidence, Trade-off.
* **C. Residual Risks**: Anything deliberately left unresolved or explicitly accepted.
* **D. Validation Matrix**: Table format: `Requirement | Evidence | Test | Status`.
* **E. Outstanding Decisions**: Any unresolved item that prevents finalizing a treatment, with the required decision/input and current condition.
* **F. Final Verdict**: Ready, Ready with conditions, or Not ready. Explain conditions or blockers.

In Direct mode, include a visible note that the artifact was strengthened **without a formal Break Report**.

If Break readiness was **Awaiting External Input**, Fortify's output must not claim full readiness while a blocking treatment decision remains unresolved.

---

## Completion Criterion

Fortify is complete when all applicable conditions are met:

1. **Every theme that can be responsibly treated has a targeted recommendation** with appropriate evidence and a treatment that fits the actual weakness.
2. **Margin of safety is proportional to the exposure** without mechanically mapping severity to a control type.
3. **Optionality and learning loops are included where they materially improve resilience**, not as mandatory decoration.
4. **Approved or safely conditionable recommendations are incorporated into the Strengthened Artifact**.
5. **Blocking external decisions remain explicit** — Fortify never resolves a deferred `BF-###` decision by assumption.
6. **Mode integrity is preserved** — Direct mode never implies that a formal Break analysis occurred.

If a blocking Break finding is still **Awaiting External Input**, Fortify may produce partial/provisional work for unaffected areas, but the strengthened artifact is not final for the blocked treatment path. The final verdict must reflect that dependency.