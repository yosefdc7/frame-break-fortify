# Frame → Break → Fortify

Agent Skills for reviewing and strengthening plans, playbooks, frameworks, strategies, change-management plans, operating models, procedures, specifications, governance documents, and similar business artifacts.

**Frame like a reviewer. Break like an adversary. Fortify like an engineer. Evidence governs all three.**

---

## The Philosophy

The system optimizes for **process predictability rather than identical answers** — the agent takes the same rigorous process every run, whatever the artifact.

| Stage | Role | Question it answers |
|---|---|---|
| **Frame** | Reviewer | *What is this plan actually saying, and what is true about it?* |
| **Break** | Adversary | *How would this plan fail in the hands of reality?* |
| **Fortify** | Engineer | *How do we make it survive — and get stronger from — the failures we found?* |

Frame reconstructs the artifact, researches what it can establish independently, and interviews the user only for material unresolved gaps. A question can be **answered now, deferred to someone else, or resumed later**. Frame can therefore complete its reconstruction even when external stakeholder input is still outstanding. Break continues the adversarial interview when human judgment is required. Fortify is an **engineer, not a compiler** — it adds controls, contingencies, and design principles the original plan never contained, grounded in external knowledge.

---

## The Pipeline

```
                    ┌────────────────────────────────┐
  your document ──▶ │  /frame                        │
                    │  reconstruct intent, logic,    │
                    │  evidence                      │
                    │  → Grill material gaps         │
                    │    A/B/C resolution paths      │
                    │    D = ask someone else        │
                    └──────────────┬─────────────────┘
                                   ▼  Frame Brief
                         ┌─────────┴─────────┐
                         │                   │
                         ▼                   ▼
                  Ready for Break     Awaiting External Input
                         │                   │
                         │          FQ-### questions routed
                         │                   │
                         │          answers obtained later
                         │                   │
                         │          /frame existing brief
                         │                   │
                         └─────────┬─────────┘
                                   ▼
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

Reconstructs the document into a clear, evidence-aware mental model before judging or changing it. Withholds all critique and turns missing information into explicit, resumable questions rather than forcing the current user to know every answer.

* **Evidence-first reconstruction** — every material claim is classified as *Verified, Supported, Inferred, Assumed,* or *Unknown* against an evidence hierarchy that prefers governing laws and official standards over repeated web claims.
* **Ambiguity scan** — surfaces undefined terminology, conflicting requirements, missing owners, unclear dependencies, unclear decision rights, non-measurable outcomes, assumptions disguised as facts, and external decisions that still need confirmation.
* **Material questions only** — Frame assesses Intent, Logic, Evidence, Ambiguity, Dependencies, and Decisions, but asks only questions that could materially change the artifact or its readiness for stress-testing.
* **Grill with defer option** — questions are asked one at a time. When genuine resolution choices exist, Frame offers **A/B/C options** with risk posture and trade-offs plus **D. Ask someone else / save this question**. The user may also provide a custom answer.
* **Stable `FQ-###` IDs** — each material question receives a permanent identifier so stakeholders can answer later without reproducing the full question.
* **Questions for Others** — deferred questions are captured in the Frame Brief with the question, why it matters, suggested respondent role, Blocking/Non-blocking classification, status, and eventual answer. Questions may be grouped by likely respondent for easy handoff through email, chat, or meetings.
* **Resume later** — running `/frame` on an existing Frame Brief resumes the prior review, preserves question IDs, incorporates newly supplied answers, updates affected assumptions/evidence/dependencies/decisions, and recalculates readiness without restarting completed work.
* **Frame Brief** — executive interpretation, intended outcomes, logic/operating model, key assumptions, dependencies, evidence ledger, unknowns, decisions requiring confirmation, Questions for Others, potential contradictions, Frame status, and Break readiness.
* **Separate completion from readiness** — Frame can be **Complete** even when external answers are still outstanding. Break readiness is reported separately as:
  * **Ready for Break** — no material blocking questions remain.
  * **Ready for Break with Conditions** — unresolved questions remain but meaningful stress-testing can proceed under stated conditions.
  * **Awaiting External Input** — one or more deferred/open questions materially prevent reliable stress-testing.

```
/frame <document>
/frame <existing Frame Brief>
```

Example continuation:

```
FQ-003: Steering Committee is the final approver.
```

Frame incorporates the answer into the existing brief, closes `FQ-003`, updates affected sections, and recalculates readiness.

### `/break` — Expose the weakness

Attempts to make the proposed system fail before reality does. Adversarial analysis without becoming contrarian for its own sake.

* **Premortem** — "It is six months later and this initiative failed badly" — works backward to generate specific, contextual failure chains rather than generic risks.
* **Inversion** — what conditions would almost guarantee failure? The inverse exposes design requirements that may be absent.
* **Dependency attacks** — stress across people, process, technology, governance, sequencing, capacity, data, suppliers, handoffs, communications, adoption, controls, timeline, decision rights. Looks for failure *propagation*, not merely isolated risks.
* **Scenario testing** — expected, adverse, extreme-but-plausible, edge case, dependency failure, human-behavior failure.
* **Break Report** — failure thesis, top failure paths, fragile assumptions, missing controls, contradictions, edge cases — findings prioritized as **Blocker / Major concern / Watch item / Observation**, each with a recommended response, trade-off, and decision owner.
* **Grill to Readiness** — blockers and decisions requiring human judgment are interviewed one at a time until the report is *Ready to strengthen*.

```
/break <document>
/break FRAME-REVIEW.md
```

### `/fortify` — Build the margin of safety

Actively strengthens the plan by building **margin of safety** and **antifragility** into it. An engineer, not a compiler — it adds controls, contingencies, and design principles the original plan never contained, grounded in external knowledge (frameworks, principles, thought leaders).

Fortify clusters Break findings into **themes** (shared root causes) and produces one targeted recommendation per theme, then incorporates all recommendations into a strengthened artifact.

**Margin of Safety** — design beyond the minimum so the plan absorbs unexpected stress. The form is weighted by Break priority:

| Break priority | Form | What it means |
|---|---|---|
| **Blocker** | **Redundancy** | A structurally independent backup path — executes without depending on the same person, process, or system. |
| **Major concern** | **Contingency Trigger** | An explicit trigger condition and a pre-agreed response. Not "monitor X" but "if X happens, do Y, and Z is accountable." |
| **Watch item** | **Graceful Degradation** | A defined partial-success path — a spectrum, not a binary launch/don't-launch cliff. |

**Antifragility** — the plan gets stronger from stress, not just survives it:

| Mechanism | What it means |
|---|---|
| **Optionality** *(primary)* | Preserve future options rather than locking in irreversible decisions. Frame decisions as "at [milestone], choose between X and Y based on [observable criteria]." |
| **Learning Loops** *(secondary)* | Every post-launch activity produces a documented improvement — reviews, incidents, and metrics feed concrete changes into the next cycle. |

**Two-layer output**:

1. **Targeted Recommendations** (primary) — per Break theme: the weakness, the recommendation, the cited source with claim classification, the margin of safety control, the optionality preserved, and the learning loop.
2. **Strengthened Artifact** (secondary) — the revised plan incorporating every recommendation, with a change ledger, residual risks, validation matrix, and final verdict.

```
/fortify <document>
/fortify <document> BREAK-REVIEW.md
```

---

## The Evidence Contract

Every skill follows a strict evidence contract:

* **Evidence hierarchy** — governing laws and official standards outrank unsupported common practice. A claim repeated by many websites is not a "best practice."
* **Claim classification** — every material claim is *Verified, Supported, Inferred, Assumed,* or *Unknown*. An inference is never presented as an established fact.
* **Source fit** — external frameworks apply only when they meaningfully govern the artifact and context.
* **Citation rule** — any recommendation grounded in an external standard, framework, or recognized source names that source.

See `skills/*/references/evidence-contract.md` for the full contract.

---

## How They Work Together

| You bring | Frame produces | Break produces | Fortify produces |
|---|---|---|---|
| A draft plan | Frame Brief (intent, evidence, gaps, deferred questions) | Break Report (failure paths, priorities) | Targeted Recommendations + Strengthened Artifact |
| A playbook | Reconstructed logic + assumptions + routed questions | Fragile assumptions + missing controls | Margin of safety controls + contingencies |
| A change-management strategy | Stakeholder map + decision register + external questions | Premortem chains + contradiction analysis | Optionality + learning loops per theme |
| A governance document | Evidence ledger + ambiguity list + Questions for Others | Edge cases + dependency failures | Graceful degradation paths + scorecards |

Frame interviews the user when it finds material gaps, but does not require the current user to personally resolve every question. Deferred questions become explicit stakeholder follow-ups and can be resumed later. Break stress-tests once the Frame Brief is sufficiently ready. Fortify flags decisions it cannot make for you as **Decision Required** — it proceeds with the recommendation and lets you choose.

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

See [INSTRUCTIONS_PM.md](docs/INSTRUCTIONS_PM.md) for a detailed guide on how Project Managers can use this triplet to validate assumptions, run premortems, and build resilient project artifacts.

---

*Three roles, one pipeline: review the truth, stress-test the weakness, engineer the strength.*
