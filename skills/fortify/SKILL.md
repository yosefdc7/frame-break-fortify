---
name: fortify
description: Strengthen a plan by building margin of safety and antifragility into it, grounded in external knowledge. Use after Break identifies weaknesses. Produces targeted recommendations per Break theme, then a strengthened artifact.
---

# Fortify Skill

**Mission**: Actively strengthen the plan by building **margin of safety** and **antifragility** into it, grounded in external knowledge. Fortify is an engineer, not a compiler — it adds controls, contingencies, and design principles that the original plan and Break findings do not already contain.

Use Fortify after Break identifies weaknesses. Rely on Break's findings as the input. Use external knowledge (training knowledge + documentation lookup) to generate recommendations that tackle those weaknesses. The Evidence Contract governs source quality.

**Triggers**: `/fortify <document>` or `/fortify <document> BREAK-REVIEW.md`

---

## The Evidence Contract (Summary)

*   **Evidence Hierarchy**: Prefer laws, regulations, and official standards.
*   **Claim Classification**: Distinguish between Verified, Supported, Inferred, Assumed, and Unknown claims.
*   **Source Fit**: Only apply external frameworks if they meaningfully apply to the artifact and context.
*   **Citation Rule**: Identify sources for recommendations grounded in external standards.

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

### Step 1 — Preserve Intent
Restate the agreed objective. Improvements must support that objective. Maintain the author's intent.

### Step 2 — Cluster Break Findings into Themes
Group Break's findings (Blockers, Major Concerns, Watch Items) into themes. A theme is a shared root cause or shared domain (e.g., "capacity risk", "data trust", "governance gaps"). Multiple findings that share a root cause collapse into one theme. Each theme gets one targeted recommendation.

### Step 3 — Generate Targeted Recommendations
For each theme, produce a recommendation that:
1. **Names the weakness**: Which Break finding(s) this addresses.
2. **Retrieves external knowledge**: Search training knowledge and documentation for the most relevant framework, principle, or thought leadership that applies to this weakness. Apply the Evidence Contract's Source Fit check — only use knowledge that meaningfully applies to this artifact and context.
3. **Cites the source**: Name the framework, principle, or thought leader. Classify the grounding (Verified / Supported / Inferred).
4. **Builds margin of safety**: Apply the appropriate form based on Break priority (Redundancy / Contingency Trigger / Graceful Degradation).
5. **Preserves optionality**: State what future options this recommendation keeps open.
6. **Defines a learning loop** (where applicable): What this recommendation teaches the plan for the next cycle.

If a recommendation requires a decision the user hasn't made, flag it as **Decision Required** in the output. Do not stop to interview — proceed with the recommendation and flag the decision.

### Step 4 — Strengthen the Artifact
Incorporate all recommendations into the plan. Where applicable, improve: objectives, scope, sequencing, ownership, responsibilities, dependencies, governance, decision rights, controls, measures, acceptance criteria, contingencies, communications, implementation steps, escalation paths.

Replace vague completion language with observable criteria. Use context-appropriate metrics rather than inventing arbitrary numbers.

### Step 5 — Trace Changes
Every material change maps back to at least one of:
* Original requirement
* Frame finding
* Break finding
* External evidence (with citation)
* Explicit user decision

### Step 6 — Re-validate
Before finishing, check:
* Original intent remains intact
* Blockers have been addressed or explicitly accepted
* New contradictions were not introduced
* New unsupported claims were not introduced
* Critical dependencies have owners
* Important outcomes have observable success criteria

---

## Output

Produce two layers:

### Layer 1 — Targeted Recommendations (Primary Deliverable)

For each Break theme:

| Field | Content |
|---|---|
| **Theme** | The shared root cause or domain |
| **Weakness** | The Break finding(s) being addressed |
| **Recommendation** | The concrete action to take |
| **Source** | The framework, principle, or thought leader (with citation and claim classification) |
| **Margin of Safety** | The specific control added: Redundancy / Contingency Trigger / Graceful Degradation |
| **Optionality Preserved** | What future options this keeps open |
| **Learning Loop** | What this teaches the plan for the next cycle (if applicable) |
| **Decision Required** | Any decision the user must make (if applicable) |

### Layer 2 — Strengthened Artifact (Secondary Deliverable)

The revised plan incorporating all Layer 1 recommendations. Include:

* **A. Strengthened Artifact**: The revised plan, playbook, framework, or document.
* **B. Change Ledger**: For material changes, record: Change, Reason, Source finding, Evidence, Trade-off.
* **C. Residual Risks**: Anything deliberately left unresolved.
* **D. Validation Matrix**: Table format: `Requirement | Evidence | Test | Status`
* **E. Final Verdict**: Ready, Ready with conditions, or Not ready (explain conditions or blockers).

---

## Completion Criterion

Fortify is complete when all three conditions are met:

1. **Every Break theme has a targeted recommendation** with a cited source and an appropriate margin of safety control.
2. **Recommendations build antifragility** — they preserve optionality and define learning loops where applicable.
3. **The Strengthened Artifact incorporates all recommendations** — nothing stays in the recommendation layer without landing in the plan.
