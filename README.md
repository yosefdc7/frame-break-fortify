# Frame → Break → Fortify

Agent Skills for reviewing and strengthening plans, playbooks, frameworks, strategies, change-management plans, operating models, procedures, specifications, governance documents, and similar business artifacts.

**Frame like a reviewer. Break like an adversary. Fortify like an engineer. Evidence governs all three.**

---

## The Philosophy

The system optimizes for **process predictability rather than identical answers**.

| Stage | Role | Question it answers |
|---|---|---|
| **Frame** | Reviewer | *What is this plan actually saying, and what is true about it?* |
| **Break** | Adversary | *How would this plan fail in the hands of reality?* |
| **Fortify** | Engineer | *How do we make it survive — and get stronger from — the weaknesses we found?* |

The central workflow rule is:

> **Skill completion and downstream readiness are separate concepts.**

Frame can complete while stakeholder answers are still outstanding. Break can complete while treatment decisions are still outstanding. The next skill must respect the readiness gate from the previous skill rather than silently filling gaps.

---

## The Pipeline

```text
SOURCE DOCUMENT
      │
      ▼
┌──────────────────────────┐
│ FRAME                    │
│ reconstruct truth        │
│ FQ-### Question Register │
│ Answer / Defer           │
└────────────┬─────────────┘
             ▼
      Break Readiness
     ┌───────┼────────┐
     │       │        │
   Ready  Conditional Awaiting Input
     │       │        │
     └───┬───┘        └─ resume FRAME later
         ▼
┌──────────────────────────┐
│ BREAK                    │
│ premortem + inversion    │
│ BF-### findings          │
│ Treat / Accept / Defer   │
└────────────┬─────────────┘
             ▼
     Fortify Readiness
     ┌───────┼────────┐
     │       │        │
   Ready  Conditional Awaiting Input
     │       │        │
     └───┬───┘        └─ resume BREAK later
         ▼
┌──────────────────────────┐
│ FORTIFY                  │
│ engineer controls        │
│ preserve traceability    │
└────────────┬─────────────┘
             ▼
 Targeted Recommendations
 + Strengthened Artifact
```

Each skill can also be invoked independently. Independent use is explicit rather than pretending the skipped stages occurred.

---

## `/frame` — Establish the truth

Frame reconstructs the artifact before judging it.

Core behaviors:

* **Evidence-first reconstruction** — material claims are classified as *Verified, Supported, Inferred, Assumed,* or *Unknown*.
* **Material questions only** — Frame assesses intent, logic, evidence, ambiguity, dependencies, and decisions, but does not manufacture questions for coverage.
* **Stable `FQ-###` IDs** — every material interview question receives a persistent ID from the moment it is asked.
* **Canonical Question Register** — all material questions remain traceable, including those answered immediately.
* **Answer or defer** — the user can answer now or choose **Ask someone else / save this question**.
* **Questions for Others** — a filtered handoff view containing only Deferred `FQ-###` questions.
* **Resume later** — `/frame <existing Frame Brief>` preserves IDs, incorporates new answers, updates affected sections, and recalculates readiness.
* **Role boundary** — Frame clarifies. It does not run premortems, inversion, kill-condition analysis, or worst-case failure testing; those belong to Break.

Question states:

* **Open** — transient only; unresolved and not yet dispositioned.
* **Answered** — resolved.
* **Deferred** — routed for external input.

A material Open question keeps Frame **In Progress**. Frame becomes **Complete** when all material interview questions are Answered or Deferred.

### Break readiness

* **Ready for Break** — no material blocking Deferred questions remain.
* **Ready for Break with Conditions** — Break can proceed if the listed `FQ-###` conditions are respected.
* **Awaiting External Input** — one or more Deferred questions materially prevent reliable stress-testing.

```text
/frame <document>
/frame <existing Frame Brief>
```

Example resume:

```text
FQ-003: Steering Committee is the final approver.
```

---

## `/break` — Expose the weakness

Break attempts to make the proposed system fail before reality does.

Before full analysis, Break checks a supplied Frame Brief:

* **Ready for Break** → proceed normally.
* **Ready for Break with Conditions** → preserve the stated `FQ-###` conditions.
* **Awaiting External Input** → analyze unaffected areas only; do not invent the missing upstream answer or claim full analysis where the model still depends on it.
* **Frame Status: In Progress** → partial analysis may be useful, but Break cannot claim full completion while material upstream ambiguity blocks required stress-testing.

Core behaviors:

* **Premortem** — assume the initiative failed and work backward through plausible causal chains.
* **Inversion** — identify conditions that would almost guarantee failure.
* **Dependency attacks** — stress people, process, technology, governance, sequencing, capacity, data, suppliers, handoffs, adoption, controls, timeline, and decision rights.
* **Scenario testing** — expected, adverse, extreme-but-plausible, edge, dependency-failure, and human-behavior cases.
* **Stable `BF-###` IDs** — material findings remain traceable across stakeholder decisions and resumed reviews.
* **Recommend before asking** — every Blocker and Major concern receives a recommended response, evidence/reasoning, failure scenario, trade-off, and owner when known.
* **Resolve / accept / defer** — treatments can be accepted, alternatives selected, legitimate risks explicitly accepted, or decisions routed to someone else.
* **Resume later** — `/break <existing Break Report>` incorporates new stakeholder decisions and selectively re-tests only affected failure paths.

For Blockers and Major concerns:

* **Open** — transient only.
* **Accepted recommendation** — recommended treatment chosen.
* **Alternative selected** — different treatment chosen.
* **Accepted risk** — consciously left untreated with rationale and residual exposure.
* **Deferred** — routed to another person/team.

A material Blocker or Major concern left Open keeps Break **In Progress**. Watch items and observations do not require treatment disposition unless escalated.

### Fortify readiness

* **Ready for Fortify** — enough treatment direction exists to strengthen the artifact.
* **Ready for Fortify with Conditions** — Fortify can proceed under explicit `BF-###` conditions.
* **Awaiting External Input** — unresolved external input materially determines which treatment should be implemented.

```text
/break <document>
/break FRAME-REVIEW.md
/break <existing Break Report>
```

Example resume:

```text
BF-003: Sponsor approved delegated approval authority.
```

---

## `/fortify` — Build the margin of safety

Fortify strengthens the plan. It is an engineer, not a compiler.

### Break-backed mode — preferred

When a Break Report exists, Fortify preserves `BF-###` traceability and honors its readiness state:

* **Ready for Fortify** → proceed normally.
* **Ready for Fortify with Conditions** → proceed while preserving the conditions.
* **Awaiting External Input** → strengthen unaffected themes, but keep blocked treatment paths **Decision Required / Awaiting External Input** rather than silently choosing an answer.

### Direct mode

When no Break Report exists, Fortify may still strengthen a document, but it must:

1. state that no formal Break analysis was supplied or performed;
2. identify **provisional weaknesses** directly from the document;
3. group them into strengthening themes;
4. avoid creating `BF-###` IDs or implying adversarial testing occurred; and
5. preserve unresolved decisions instead of inventing them.

Direct mode is useful when the user intentionally skips Break. It does not recreate Break inside Fortify.

### Margin of safety is mechanism-driven

Break priority influences how strong a treatment should be, but does **not** mechanically dictate one control type.

| Priority | Common starting pattern | Example fit |
|---|---|---|
| **Blocker** | Strong structural protection, often redundancy | Single point of failure requiring an independent backup |
| **Major concern** | Often a contingency trigger | Known exposure manageable through a trigger and pre-agreed response |
| **Watch item** | Often graceful degradation | Partial service can preserve value during degradation |

Fortify may instead remove a prohibited design, change sequencing, redesign governance, add validation, reduce scope, or use another treatment when that better matches the failure mechanism.

### Antifragility

Use optionality and learning loops where they materially improve resilience; do not add them as mandatory ceremony.

```text
/fortify <document>
/fortify <document> BREAK-REVIEW.md
```

---

## Traceability

The intended trace is:

```text
FQ-###  clarification or external question
   ↓
BF-###  failure finding derived from the understood system
   ↓
Fortify recommendation / artifact change
```

Fortify changes should map back to the original requirement, an `FQ-###`, a `BF-###`, external evidence, a Direct-mode provisional weakness, or an explicit user decision.

---

## The Evidence Contract

Every skill follows the same evidence contract:

* **Evidence hierarchy** — governing laws and official standards outrank unsupported common practice.
* **Claim classification** — distinguish *Verified, Supported, Inferred, Assumed,* and *Unknown*.
* **Source fit** — external frameworks apply only when they meaningfully fit the artifact and context.
* **Citation rule** — recommendations grounded in external standards, research, regulation, or recognized frameworks identify their source.

See `skills/*/references/evidence-contract.md`.

---

## How They Work Together

| You bring | Frame produces | Break produces | Fortify produces |
|---|---|---|---|
| Draft plan | Evidence-aware model + Question Register | Failure paths + treatment decisions | Targeted recommendations + strengthened plan |
| Playbook | Logic + dependencies + routed questions | Handoff/control failures | Controls + contingencies |
| Change strategy | Stakeholder/decision clarity | Human-behavior and adoption failure paths | Observable criteria + resilience mechanisms |
| Governance document | Decision rights + evidence gaps | Bottlenecks + control weaknesses | Stronger governance design + residual-risk treatment |

---

## Repository Structure

```text
skills/
  frame/    SKILL.md + references/
  break/    SKILL.md + references/
  fortify/  SKILL.md + references/
docs/
  INSTRUCTIONS_PM.md
plugin.json
```

## Installation

Clone the repository and copy or symlink the folders under `skills/` into your agent's skills directory.

```bash
git clone https://github.com/yosefdc7/frame-break-fortify.git
```

See `docs/INSTRUCTIONS_PM.md` for the Project Management guide.

---

*Three roles, one pipeline: establish the truth, stress-test the weakness, engineer the strength.*