# Frame → Break → Fortify

Agent Skills for reviewing and strengthening plans, playbooks, frameworks, strategies, operating models, specifications, governance documents, and similar business artifacts.

The repository also includes **Project Manager: Solution Exploration**, a separate two-skill workflow for exploring and choosing solutions before a proposal is finalized.

The `SKILL.md` files and their references are the source of truth. This README is a concise operating overview.

---

## Document Review Pipeline

```text
SOURCE DOCUMENT
      │
      ▼
FRAME
reconstruct truth
FQ-### questions
answer / defer
      │
      ▼
Break Readiness
      │
      ▼
BREAK
stress-test failure paths
BF-### findings
treat / accept / defer
      │
      ▼
Fortify Readiness
      │
      ▼
FORTIFY
choose source basis
FS-### sources
strengthen the artifact
```

A core rule applies throughout:

> **Skill completion and downstream readiness are separate concepts.**

A review can be analytically complete while an external answer, decision, or source validation is still outstanding.

---

## `/frame` — Establish the truth

Frame reconstructs what the artifact actually says before it is challenged or changed.

It:
* establishes intent, scope, assumptions, dependencies, decisions, success criteria, and evidence;
* classifies material claims as **Verified, Supported, Inferred, Assumed, or Unknown**;
* asks only material clarification questions;
* gives every material question a stable `FQ-###` ID;
* lets the user **answer now or defer to someone else**;
* keeps every question in a canonical Question Register; and
* can resume later without restarting the review.

Frame clarifies. It does **not** run premortems, inversion, or worst-case failure testing; those belong to Break.

### Frame states

Question state:
* `Open` — transient
* `Answered`
* `Deferred`

Frame status:
* `Complete`
* `In Progress`

Break readiness:
* `Ready for Break`
* `Ready for Break with Conditions`
* `Awaiting External Input`

```text
/frame <document>
/frame <existing Frame Brief>
```

---

## `/break` — Expose the weakness

Break stress-tests the understood system using premortem, inversion, dependency attacks, scenario testing, and contradiction analysis.

It:
* respects FRAME readiness and unresolved `FQ-###` dependencies;
* gives material findings stable `BF-###` IDs;
* classifies findings as Blocker, Major concern, Watch item, or Observation;
* recommends a treatment before asking the user to decide;
* lets Blockers/Major concerns be treated, explicitly accepted as risk, or deferred to another decision owner; and
* resumes only the affected failure path when new information arrives.

Material Blocker/Major dispositions:
* `Open` — transient
* `Accepted recommendation`
* `Alternative selected`
* `Accepted risk`
* `Deferred`

Fortify readiness:
* `Ready for Fortify`
* `Ready for Fortify with Conditions`
* `Awaiting External Input`

If Fortify later finds strong evidence that invalidates an accepted Break treatment, the same `BF-###` is reopened and selectively re-evaluated rather than creating a duplicate finding.

```text
/break <document>
/break FRAME-REVIEW.md
/break <existing Break Report>
```

---

## `/fortify` — Strengthen with a visible evidence basis

Fortify turns weaknesses into concrete controls and improvements.

**Break-backed mode** is preferred. **Direct mode** is allowed when the user intentionally skips Break; Direct-mode weaknesses remain provisional and no fake `BF-###` IDs are created.

Before material externally grounded recommendations are finalized, Fortify asks the user to choose:
* **Provide sources**
* **Search for candidates**
* **Hybrid**

Every material source gets a stable `FS-###` ID with separate **Quality** (`Governing`, `Reliable`, `Supporting`, `Weak`) and **Use** (`Approved`, `Candidate`, `Rejected`). User approval does not upgrade source quality.

A reasoning-only pass is allowed, but material recommendations remain provisional when external grounding is materially needed.

```text
/fortify <document>
/fortify <document> BREAK-REVIEW.md
/fortify <existing Fortify artifact>
```

---

# Project Manager: Solution Exploration

Use this workflow when you have a **problem to solve but have not yet committed to a solution**.

It is intentionally separate from Frame → Break → Fortify.

```text
PROBLEM + CONTEXT + CONSTRAINTS
              │
              ▼
         /explore
   GRILL → GROUND → DIVERGE
              │
              ▼
      SOLUTION OPTIONS
              │
              ▼
          /decide
 VERIFY → FILTER → COMPARE → RECOMMEND
              │
              ▼
       SOLUTION DECISION
```

## `/explore` — Build the right solution space

`solution-explore`:
* grills the problem, desired outcome, scope, hard constraints, preferences, assumptions, unknowns, and likely decision criteria;
* uses stable `EQ-###` IDs for material questions and allows questions to be deferred to someone else;
* asks the user to **provide sources**, **search reliable sources**, or use a **hybrid** approach;
* makes important evidence and limitations visible; and
* generates materially different solution archetypes with stable `SO-###` IDs.

It deliberately **does not rank or select a winner**.

```text
/explore <problem or context>
/explore <existing Solution Options>
```

Output: **Solution Options** with status `Ready for Decision`, `Ready for Decision with Conditions`, or `Needs More Input`.

## `/decide` — Compare and recommend

`solution-decide`:
* verifies the decision basis and asks only decision-specific questions that could materially change the ranking;
* treats hard constraints as **gates, not weighted criteria**;
* compares viable options on criteria that actually matter;
* prefers qualitative comparison over invented numeric precision;
* makes trade-offs explicit, including when the runner-up should win instead; and
* ranks viable options and gives one clear recommendation when the evidence supports it.

```text
/decide <Solution Options>
/decide <options + context>
/decide <existing Solution Decision>
```

Output: **Solution Decision** with status `Ready to Decide`, `Ready with Conditions`, or `Decision Not Ready`.

### Boundary

| Solution Explore | Solution Decide |
|---|---|
| Understand the problem | Understand the decision |
| Grill problem and constraints | Grill only missing decision criteria |
| Ground the solution space | Fill only material comparison gaps |
| Generate distinct alternatives | Filter and compare alternatives |
| Keep options open | Converge |
| **No ranking** | **Rank** |
| **No winner** | **Recommend a winner** |

---

## Traceability

### Document review

```text
FQ-### → BF-### → FS-### → Fortify recommendation → Strengthened Artifact
```

### Solution exploration

```text
EQ-### → SO-### solution options → comparison → recommendation
```

---

## Evidence Principles

Across the repository:
* prefer governing and authoritative primary sources over unsupported common practice;
* distinguish evidence from inference and assumption;
* apply frameworks only when they fit the actual context;
* never fabricate sources or pretend they were retrieved;
* expose important limitations and uncertainty; and
* avoid false precision in rankings or recommendations.

---

## Repository Structure

```text
CHANGELOG.md
skills/
  frame/             SKILL.md + references/
  break/             SKILL.md + references/
  fortify/           SKILL.md + references/
  solution-explore/  SKILL.md
  solution-decide/   SKILL.md
docs/
  INSTRUCTIONS_PM.md
plugin.json
```

## Installation

```bash
git clone https://github.com/yosefdc7/frame-break-fortify.git
```

Copy or symlink the desired folders under `skills/` into your agent's skills directory.

See `docs/INSTRUCTIONS_PM.md` for the Frame → Break → Fortify PM workflow. See [`CHANGELOG.md`](CHANGELOG.md) for notable changes and unreleased work.
