---
name: frame
description: Reconstruct plans and business documents to establish intent, assumptions, evidence, unresolved questions, and readiness for stress-testing.
disable-model-invocation: true
license: MIT
metadata:
  version: "0.2.0"
---

# Frame Skill

**Mission**: Reconstruct the document into a clear, evidence-aware mental model before judging or changing it, while turning missing information into explicit questions that can be answered now or routed to the right person later.

Use Frame when:
* Reviewing an unfamiliar plan or playbook
* The author's intent is unclear
* Assumptions are hidden
* Requirements may be incomplete
* Terminology is inconsistent
* Success criteria are ambiguous
* Important answers may sit with other stakeholders
* The user wants a document grilled before it is approved or stress-tested

**Triggers**:
* `/frame <document>`
* `/frame <existing Frame Brief>` to resume a prior review

---

## Core Principle

Frame must distinguish between:

1. **Discovering that information is missing**, and
2. **Obtaining the missing information**.

Discovering the exact question, why it matters, and who is likely to know the answer is a successful Frame outcome even when the current user cannot answer it immediately.

A material Frame question may be:
* **Open** — transient; currently unresolved and not yet dispositioned
* **Answered** — resolved during the current review or a later resume
* **Deferred** — explicitly saved for another person or team

`Open` is not a terminal disposition. A material question must become **Answered** or **Deferred** before Frame Status can become Complete.

A deferred question is not just an Unknown. It is a known information need with a clear question and a disposition.

---

## The Evidence Contract (Summary)

* **Evidence Hierarchy**: Prefer laws, regulations, official standards, primary documentation, and authoritative internal sources. Do not turn something into a "best practice" simply because websites repeat it.
* **Claim Classification**: Classify material claims as Verified, Supported, Inferred, Assumed, or Unknown.
* **Source Fit**: Only apply external frameworks if they meaningfully apply to the artifact and context.
* **Citation Rule**: Identify sources for recommendations grounded in external standards or frameworks.

*(For full details, see `references/evidence-contract.md`)*

---

## Process

Withhold critique. Focus strictly on reconstruction, clarification, and establishing truth. Frame should expose what the plan says and what remains unknown; Break is responsible for adversarial failure testing.

### Step 1 — Establish Intent
Determine:
* Problem being solved
* Desired outcomes
* Scope
* Exclusions
* Stakeholders
* Intended users
* Governing constraints

### Step 2 — Reconstruct the Logic
Map:

`Inputs → assumptions → activities → dependencies → decisions → outputs → outcomes → measures of success`

Expose broken or missing links, but do not redesign or stress-test the artifact.

### Step 3 — Establish Evidence
Classify important statements as Verified, Supported, Inferred, Assumed, or Unknown.

Research material factual questions before asking the user when the answer can reasonably be established from available code, documentation, supplied files, authoritative internal sources, or reliable external sources.

Claims classified as Assumed or Unknown become the highest-priority inputs to the ambiguity scan in Step 4.

### Step 4 — Find Ambiguity
Identify material gaps such as:
* Undefined terminology
* Conflicting requirements
* Missing owners
* Unclear dependencies
* Unclear decision rights
* Non-measurable outcomes
* Assumptions disguised as facts
* Missing baselines or success gates
* External approvals or stakeholder decisions not yet obtained

Assess every Frame dimension, but only create interview questions for gaps that could materially change intent, scope, assumptions, dependency logic, evidence classification, decision rights, success criteria, or readiness for Break.

Do not manufacture questions simply to satisfy coverage.

### Step 5 — Produce the Frame Brief
Generate a persistent Frame Brief containing:

1. Executive interpretation
2. Intended outcomes
3. Logic / operating model
4. Key assumptions
5. Dependencies
6. Evidence ledger
7. Unknowns
8. Decisions requiring confirmation
9. Question Register
10. Questions for Others
11. Potential contradictions
12. Frame status
13. Readiness for Break

#### Question Register

Every material interview question receives a stable ID using the format `FQ-###` from the moment it is first asked, regardless of whether it is answered immediately or deferred.

Do not renumber existing IDs when the Frame Brief is updated.

For every material question record:
* **ID**
* **Question**
* **Why it matters**
* **Status** — Open, Answered, or Deferred
* **Answer** — when supplied
* **Blocking?** — Blocking or Non-blocking while unresolved
* **Suggested respondent** — role or team when reasonably inferable; otherwise `To be identified`

The Question Register is the canonical question history. Answered questions remain in it for traceability.

#### Questions for Others

This is a filtered handoff view of the Question Register containing only questions currently marked **Deferred**.

For each deferred question include:
* **FQ ID**
* **Question**
* **Why it matters**
* **Suggested respondent**
* **Blocking?**
* **Status**
* **Answer** — blank until supplied

Group unresolved questions by likely respondent when useful so the user can directly copy them into email, chat, meeting notes, or another handoff.

Prefer respondent roles over invented names. Do not require due dates unless the source artifact or user explicitly provides them.

### Step 6 — Grill to Readiness

If material gaps remain, initiate a structured interview with the user.

Present questions **one at a time**.

Each material question must receive a stable `FQ-###` ID and enter the Question Register before it is presented.

For every material question:
* Generate a specific, answerable clarification question.
* When there are genuine resolution choices, present structured **A / B / C** options representing distinct paths.
* Each option should explain the approach, risk posture, and trade-offs.
* Mark one option as **(recommended)** only when Frame has enough evidence to recommend one without crossing into adversarial redesign.
* Always allow the user to provide a custom answer.
* Always provide an additional path: **D. Ask someone else / save this question**.

When the user answers:
1. Mark the question **Answered**.
2. Record the answer in the Question Register.
3. Update affected assumptions, evidence, dependencies, decisions, unknowns, and readiness.

When the user chooses D, says they do not know, or asks to save the question for another person:
1. Mark the question **Deferred**.
2. Keep it in the Question Register and surface it under **Questions for Others**.
3. Infer the likely respondent role only when reasonably clear.
4. Classify it as Blocking or Non-blocking.
5. Do not ask another question merely to identify the respondent unless respondent ownership itself is materially necessary.
6. Continue to the next material gap.

Do not force a deferred question to be answered in the current session.

Prefer qualitative assessments over invented numbers or dates. If a timeline is unknown, describe the shape of the constraint rather than fabricating a calendar date.

**Research-first rule**: Exhaust reasonably available codebase, document, internal-source, and authoritative external research before asking the user a factual question that can be established independently.

**Coverage rule**: Assess Intent, Logic, Evidence, Ambiguity, Dependencies, and Decisions. If a section has no material gaps, move on. Question only material unresolved gaps.

**Role-boundary rule**: Frame may clarify assumptions, dependencies, decision rights, and evidence requirements, but must not run premortems, inversion, kill-condition analysis, worst-case failure analysis, or other adversarial stress tests reserved for Break.

**Escalation trigger**: If the same gap repeatedly reappears without becoming more answerable, flag it as a **structural ambiguity**. Structural ambiguity may require reframing the artifact's scope rather than asking more variants of the same question.

For probing question patterns, see `references/grill-questions.md`.

As the user answers or defers questions, update the Frame Brief in real time.

The interview ends when every material question is **Answered** or **Deferred**. A material question left **Open** means the Frame review remains In Progress.

---

## Step 7 — Resume a Frame Brief

When Frame receives an existing Frame Brief, treat it as a continuation of prior work rather than automatically starting a new review.

On resume:
1. Preserve all existing `FQ-###` IDs and Question Register entries.
2. Inspect **Questions for Others** and any Open questions first.
3. Detect newly supplied answers from the user or updated artifact.
4. Close resolved questions by changing their status to **Answered** and recording the answer.
5. Reclassify any affected assumptions, evidence, unknowns, dependencies, decisions, contradictions, and success criteria.
6. Identify new questions only when the new information materially creates a new ambiguity or dependency.
7. Do not repeat questions already answered.
8. Do not restart completed Frame work unless the underlying artifact materially changed.
9. Recalculate Readiness for Break.

The user may answer by ID, for example:

`FQ-003: Steering Committee is the final approver.`

Frame should incorporate that answer without requiring the full original question to be repeated.

---

## Status Model

Frame completion and Break readiness are separate concepts.

### Frame Status

Use:
* **Complete** — every material element is represented as evidence, assumption, inference, decision, unknown, or a material question that is Answered or Deferred; no material question remains Open
* **In Progress** — material reconstruction is incomplete or at least one material question remains Open

Deferred questions do **not** prevent Frame Status from becoming Complete.

### Readiness for Break

Use exactly one of:

* **Ready for Break** — no material blocking deferred questions remain.
* **Ready for Break with Conditions** — unresolved deferred questions remain, but they do not prevent meaningful stress-testing. Clearly list the conditions and `FQ-###` IDs.
* **Awaiting External Input** — one or more deferred questions materially prevent reliable stress-testing. List the blocking `FQ-###` IDs.

If Frame Status is **In Progress**, do not report the artifact as Ready for Break.

Do not label the entire Frame review incomplete merely because another stakeholder still owes an answer; route the question as Deferred instead.

---

## Completion Criterion

Frame is complete when every material element of the artifact can be represented as one of:
* Verified evidence
* Supported evidence
* Inference
* Assumption
* Decision
* Explicitly acknowledged Unknown
* Answered question
* Deferred question

Every material interview question must have a terminal disposition: **Answered** or **Deferred**. `Open` is transient and prevents completion.

Frame does **not** require the current user to personally obtain every answer before producing the Frame Brief.

A completed Frame Brief may legitimately end with **Awaiting External Input** when blocking questions have been identified and routed for follow-up.

When those answers become available, the user can run Frame again on the existing Frame Brief. Frame must resume from the saved Question Register, incorporate the new answers, and recalculate readiness without restarting the review.

The goal is not to eliminate every unknown immediately. The goal is to make every material unknown explicit, answerable, routed when necessary, and safe to resume later.