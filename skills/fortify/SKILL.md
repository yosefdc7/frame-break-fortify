---
name: fortify
description: Strengthen a plan using reliable, user-validated source grounding, margin of safety, and adaptive controls. Use after Break, or directly with clearly labeled provisional weaknesses.
license: MIT
metadata:
  version: "0.2.0"
---

# Fortify Skill

**Mission**: Strengthen the artifact using controls and design choices that fit the actual weakness and are grounded in reliable, context-fit evidence when material external guidance is needed.

Fortify has two modes:

1. **Break-backed mode** — preferred. Use the Break Report as the weakness model and preserve `BF-###` traceability.
2. **Direct mode** — allowed when no Break Report exists. Identify provisional weaknesses directly from the document and do not pretend a formal Break analysis occurred.

**Triggers**:
* `/fortify <document>`
* `/fortify <document> BREAK-REVIEW.md`
* `/fortify <existing Fortify artifact>` to resume source validation or unfinished work

---

## Evidence Rules

Follow `references/evidence-contract.md`.

Important Fortify rules:
* Prefer governing requirements, approved internal references, official standards, primary institutional frameworks, peer-reviewed research, systematic reviews, and authoritative first-party documentation.
* Source quality and user approval are different. User approval does not make a weak source reliable.
* AI-found material design-basis sources remain candidates until the user approves their use.
* Do not fabricate searched sources when search or retrieval tools are unavailable.
* A reasoning-only recommendation must be labeled as reasoning-based and cannot be presented as an established industry standard or best practice.

---

## Core Concepts

### Margin of Safety

Break priority should influence the **strength** of treatment, but not mechanically dictate the control type.

Common patterns:

| Pattern | Best fit |
|---|---|
| **Redundancy** | A single point of failure needs an independent backup |
| **Contingency Trigger** | A known exposure can be managed through a trigger and pre-agreed response |
| **Graceful Degradation** | Partial service or reduced scope can preserve value during failure |
| **Redesign / removal** | The current design is prohibited, unsafe, or structurally wrong |
| **Validation** | The main weakness is insufficient evidence or verification |
| **Sequencing / scope change** | Exposure can be reduced by changing order or scope |
| **Governance change** | The weakness is ownership, authority, escalation, or decision rights |

Choose the treatment that addresses the failure mechanism.

### Adaptive Design

Use optionality and learning loops when they materially improve resilience. Do not add them as ceremony.

---

## Process

### Step 0 — Select Mode and Check Readiness

#### Break-backed mode

When a Break Report is supplied:
* **Ready for Fortify** — proceed normally.
* **Ready for Fortify with Conditions** — proceed while preserving the listed `BF-###` conditions.
* **Awaiting External Input** — strengthen unaffected areas only. Keep treatment paths that depend on blocking `BF-###` decisions as **Decision Required / Awaiting External Input**.

Never silently resolve or override a deferred Break decision.

#### Direct mode

When no Break Report is supplied:
1. State that no formal Break analysis was supplied or performed.
2. Identify only weaknesses that can be responsibly inferred from the document.
3. Label them **provisional weaknesses**.
4. Do not create `BF-###` IDs or imply that premortem, inversion, or full adversarial testing occurred.
5. Preserve material ambiguity as **Decision Required / External Input Needed** rather than silently deciding it.

---

### Step 1 — Choose the Source Path

Before material externally grounded recommendations are finalized, ask:

* **A. Provide sources** — the user uploads files or shares links to approved PPMs/playbooks, policies, frameworks, standards, methodologies, scientific studies, or other trusted references.
* **B. Search for candidates** — Fortify finds strong candidate sources and presents them for user validation.
* **C. Hybrid** — use supplied sources first, then search for gaps.

The user may request a **reasoning-only** pass. Reasoning-only material recommendations are **provisional** until adequately grounded; they cannot support a fully `Ready` final verdict when external grounding is materially needed.

If reliable search/retrieval tools are unavailable, do not invent sources. Ask the user to upload or share references instead.

---

### Step 2 — Maintain a Lean Source Register

Every material source receives a stable `FS-###` ID. Preserve IDs when Fortify resumes.

For each source record:
* **FS ID**
* **Source**
* **Supports** — relevant `BF-###`, theme, or Direct-mode weakness
* **Quality** — `Governing`, `Reliable`, `Supporting`, or `Weak`
* **Use** — `Approved`, `Candidate`, or `Rejected`
* **Applicability / limitation** — one concise note when material

Use these meanings:
* **Governing** — binding law, regulation, contract, or mandatory policy that applies.
* **Reliable** — strong, context-fit primary or high-quality evidence suitable as a material design basis.
* **Supporting** — useful corroboration but not strong enough to be the sole basis for a material design choice.
* **Weak** — poor authority, poor fit, or insufficient evidence; do not use as a material design basis.

`Approved` means the user accepts using the source. It does **not** upgrade its Quality.

Material externally grounded recommendations should rely on:
* applicable **Governing** sources; or
* **Reliable + Approved** sources.

Supporting sources may corroborate them.

#### When the user provides sources
1. Read the relevant material.
2. Assess Quality and applicability.
3. Mark Use as `Approved` when the user clearly supplied it as an approved basis; otherwise `Candidate`.
4. Flag material conflicts rather than silently choosing one.

#### When Fortify searches
1. Prefer primary and authoritative sources.
2. Present a concise candidate set with `FS-###`, Quality, applicability, and limitation.
3. Ask the user to approve selected sources, approve all suitable sources, reject sources, or request alternatives.
4. Keep unapproved sources as `Candidate`.

Do not require approval for every incidental factual citation; approval is for sources that materially drive the strengthening design.

---

### Step 3 — Preserve Intent and Build Themes

Restate the agreed objective and preserve the author's intent.

In Break-backed mode:
* group related Break findings into strengthening themes;
* preserve all relevant `BF-###` IDs.

In Direct mode:
* group provisional weaknesses into themes;
* trace them to the source document rather than inventing Break IDs.

---

### Step 4 — Generate Targeted Recommendations

For each theme:
1. Name the weakness and relevant `BF-###` IDs when available.
2. State the recommendation.
3. State the source basis using relevant `FS-###` IDs, or label it **Reasoning-only / Provisional**.
4. Explain why the source fits the context when that is not obvious.
5. Choose the control by failure mechanism.
6. Make the strength of treatment proportional to the exposure.
7. Preserve useful options and learning loops where they add value.
8. Flag unresolved human decisions as **Decision Required**.

Do not present Supporting or Weak evidence as sufficient authority for a material recommendation.

### New Evidence Can Reopen Break

If a Governing source or Reliable evidence materially invalidates a Break treatment already marked **Accepted recommendation, Alternative selected, or Accepted risk**:
1. Do not implement the conflicting treatment.
2. Flag the same `BF-###` as **Reopen in Break — Source Conflict**.
3. State the conflicting `FS-###` source and why it changes the treatment.
4. Preserve the prior Break decision as history; do not silently overwrite it.
5. Continue strengthening unaffected themes.

Do not create a new `BF-###` merely because new evidence invalidates an existing treatment. Break should selectively re-evaluate that finding.

---

### Step 5 — Strengthen the Artifact

Incorporate recommendations that are approved and safe to implement.

For blocked recommendations:
* preserve **Decision Required / Awaiting External Input**;
* name the blocking `BF-###` or source-document weakness;
* preserve viable options rather than selecting one silently.

For reasoning-only material recommendations that still need evidence:
* keep the language provisional;
* do not present the control as final or externally validated.

Replace vague completion language with observable criteria. Do not invent arbitrary metrics.

---

### Step 6 — Resume Fortify

When Fortify receives an existing Fortify artifact:
1. Preserve existing `FS-###` and `BF-###` references.
2. Inspect Candidate sources, unresolved decisions, and reopened Break findings first.
3. Incorporate new source approvals, rejections, links, files, or updated Break decisions.
4. Re-run only the recommendations materially affected by the new input.
5. Do not restart completed strengthening work unless the underlying artifact materially changed.

Example:

`FS-003: Approved. FS-004: Reject; find an alternative.`

---

### Step 7 — Re-validate

Before finishing, verify:
* original intent remains intact;
* Break conditions remain visible;
* no deferred `BF-###` decision was silently resolved;
* no Source Conflict was silently ignored;
* AI-found material source candidates were not silently treated as approved;
* source Quality was not upgraded merely because the user approved it;
* reasoning-only material recommendations remain provisional when grounding is materially required;
* selected controls address the actual failure mechanism;
* no unsupported claims or new contradictions were introduced.

---

## Output

Produce three concise layers.

### Layer 0 — Source Register

| FS ID | Source | Supports | Quality | Use | Applicability / limitation |
|---|---|---|---|---|---|

Only include material design-basis or governing sources.

### Layer 1 — Targeted Recommendations

For each theme include:
* **Theme / weakness**
* **Recommendation**
* **Source Basis** — `FS-###` IDs or `Reasoning-only / Provisional`
* **Control / margin of safety**
* **Trade-off**
* **Decision Required** — when applicable

### Layer 2 — Strengthened Artifact

Include:
* **Strengthened Artifact**
* **Change Ledger** — material changes only
* **Residual Risks**
* **Outstanding Decisions / Source Conflicts**
* **Final Verdict** — Ready, Ready with conditions, or Not ready

In Direct mode, state that no formal Break analysis was performed.

---

## Fortify Status

Use:
* **Complete** — strengthening work is complete and no material source validation or upstream treatment recheck remains.
* **Awaiting Source Validation** — material `FS-###` candidates still require user approval before recommendations can be finalized.
* **In Progress** — strengthening analysis, required source grounding, or a required Break recheck is incomplete.

A reasoning-only pass may produce useful provisional recommendations, but Fortify should not be marked Complete with a fully `Ready` verdict when material recommendations still require external grounding.

---

## Completion Criterion

Fortify is complete when:
* the source path is explicit;
* material sources have stable `FS-###` IDs with Quality and Use recorded;
* material externally grounded recommendations use applicable Governing or Reliable + Approved sources;
* reasoning-only material recommendations are either grounded or remain explicitly provisional;
* source conflicts that invalidate Break decisions are routed back to the same `BF-###` for selective re-evaluation;
* all safely implementable recommendations are incorporated; and
* unresolved decisions, source validation, and residual risks remain explicit.

The goal is not to collect many citations. The goal is to make the strengthening basis reliable, visible, and resumable without adding unnecessary process.