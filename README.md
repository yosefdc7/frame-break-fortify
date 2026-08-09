# Frame → Break → Fortify

Agent Skills for reviewing and strengthening plans, playbooks, frameworks, strategies, change-management plans, operating models, procedures, specifications, governance documents, and similar business artifacts.

**Frame like a reviewer. Break like an adversary. Fortify like an architect. Evidence governs all three.**

---

## The Philosophy

The system optimizes for **process predictability rather than identical answers** — the agent takes the same rigorous process every run, whatever the artifact.

| Stage | Role | Question it answers |
|---|---|---|
| **Frame** | Reviewer | *What is this plan actually saying, and what is true about it?* |
| **Break** | Adversary | *How would this plan fail in the hands of reality?* |
| **Fortify** | Engineer | *How do we make it survive — and get stronger from — the failures we found?* |

Frame and Break interview you with structured decision menus until the artifact is ready. Fortify is an **engineer, not a compiler** — it adds controls, contingencies, and design principles the original plan never contained, grounded in external knowledge.

---

## The Pipeline

```
                    ┌──────────────────────────────┐
  your document ──▶ │  /frame                      │
                    │  reconstruct intent, logic,  │
                    │  evidence                    │
                    │  → Grill to Readiness        │
                    │    (A/B/C decision menus)    │
                    └──────────────┬───────────────┘
                                   ▼  Frame Brief
                    ┌──────────────────────────────┐
                    │  /break                      │
                    │  premortem, inversion,       │
                    │  dependency attacks          │
                    │  → Grill to Readiness        │
                    │    (A/B/C decision menus)    │
                    └──────────────┬───────────────┘
                                   ▼  Break Report
                    ┌──────────────────────────────┐
                    │  /fortify                    │
                    │  margin of safety +          │
                    │  antifragility, grounded in  │
                    │  external knowledge          │
                    └──────────────┬───────────────┘
                                   ▼
                    Targeted Recommendations
                    + Strengthened Artifact
```

Each skill can be used independently, but the sequence is where the system earns its name.

---

## The Skills

### `/frame` — Establish the truth

Reconstructs the document into a clear, evidence-aware mental model before judging or changing it. Withholds all critique.

* **Frame Brief**: executive interpretation, intended outcomes, logic/operating model, key assumptions, dependencies, evidence ledger, unknowns, decisions requiring confirmation, potential contradictions, readiness verdict.
* **Grill to Readiness**: if the brief is not ready, a structured interview resolves every blocking gap — one question at a time, each with **structured A/B/C options** describing the approach, risk posture, and trade-offs of each path, with one marked *(recommended)*.
* Includes a reference catalog of probing question patterns organized by assessment dimension (stakeholder intent, causal logic, evidence quality, decision architecture).

```
/frame <document>
```

### `/break` — Expose the weakness

Attempts to make the proposed system fail before reality does. Adversarial analysis without becoming contrarian for its own sake.

* **Premortem**: "It is six months later and this initiative failed badly" — works backward to specific, contextual failure chains.
* **Inversion**: what conditions would almost guarantee failure?
* **Dependency attacks** across people, process, technology, governance, sequencing, capacity, data, suppliers, handoffs, communications, adoption, controls, timeline, decision rights.
* **Break Report**: failure thesis, top failure paths, fragile assumptions, missing controls, contradictions, edge cases — findings prioritized as **Blocker / Major concern / Watch item / Observation**, each with a recommended response.
* **Grill to Readiness**: blockers and decisions requiring human judgment are interviewed one at a time until the report is *Ready to strengthen*.

```
/break <document>
/break FRAME-REVIEW.md
```

### `/fortify` — Build the margin of safety

Actively strengthens the plan by building **margin of safety** and **antifragility** into it, grounded in external knowledge. Fortify clusters Break findings into themes and produces targeted recommendations — each citing the framework, principle, or thought leader it draws from.

**Two-layer output**:

1. **Targeted Recommendations** (primary) — per Break theme: the weakness, the recommendation, the cited source with claim classification, the margin of safety control, the optionality preserved, and the learning loop.
2. **Strengthened Artifact** (secondary) — the revised plan incorporating every recommendation, with a change ledger, residual risks, validation matrix, and final verdict.

```
/fortify <document>
/fortify <document> BREAK-REVIEW.md
```

---

## Margin of Safety

Design beyond the minimum requirement so the plan can absorb unexpected stress. The form is weighted by Break priority:

| Break priority | Form | What it means |
|---|---|---|
| **Blocker** | **Redundancy** | A structurally independent backup path — executes without depending on the same person, process, or system. |
| **Major concern** | **Contingency Trigger** | An explicit trigger condition and a pre-agreed response. Not "monitor X" but "if X happens, do Y, and Z is accountable." |
| **Watch item** | **Graceful Degradation** | A defined partial-success path — a spectrum, not a binary launch/don't-launch cliff. |

## Antifragility

The plan gets stronger from stress, not just survives it:

| Mechanism | What it means |
|---|---|
| **Optionality** *(primary)* | Preserve future options rather than locking in irreversible decisions. Frame decisions as "at [milestone], choose between X and Y based on [observable criteria]" rather than "we will do X." |
| **Learning Loops** *(secondary)* | Every post-launch activity produces a documented improvement — reviews, incidents, and metrics feed concrete changes into the next cycle. |

---

## The Evidence Contract

Every skill follows a strict evidence contract:

* **Evidence hierarchy** — governing laws and official standards outrank unsupported common practice. A claim repeated by many websites is not a "best practice."
* **Claim classification** — every material claim is *Verified, Supported, Inferred, Assumed,* or *Unknown*. An inference is never presented as an established fact.
* **Source fit** — external frameworks apply only when they meaningfully govern the artifact and context.
* **Citation rule** — any recommendation grounded in an external standard, framework, or recognized source names that source.

See `skills/*/references/evidence-contract.md` for the full contract.

---

## Repository Structure

```
skills/
  frame/    SKILL.md + references/ (evidence-contract, grill-questions)
  break/    SKILL.md + references/ (evidence-contract)
  fortify/  SKILL.md + references/ (evidence-contract)
docs/
  INSTRUCTIONS_PM.md    Project Management guide
plugin.json             Plugin manifest (v0.2.0)
```

## Installation

Clone the repository and copy (or symlink) the folders under `skills/` into your agent's skills directory — e.g. `~/.agents/skills` or your IDE's skills folder. Each skill is self-contained.

```
git clone https://github.com/yosefdc7/frame-break-fortify.git
```

## Project Management Guide

See [INSTRUCTIONS_PM.md](docs/INSTRUCTIONS_PM.md) for a detailed guide on how Project Managers can use this triplet to validate assumptions, run premortems, and build antifragile project artifacts.

---

*By intentionally stressing the plan (Break) and rewriting the weaknesses (Fortify), your artifacts become resilient and antifragile.*
