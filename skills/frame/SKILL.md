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

Frame therefore never forces the user to personally resolve every gap. A material question may be:
* **Answered** — resolved during the current review
* **Deferred** — explicitly saved for another person or team
* **Open** — unresolved and not yet routed

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

Withhold critique. Focus strictly on reconstruction, clarification, and establishing truth.

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

Expose broken or missing links, but do not yet redesign the artifact.

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
Generate an Antigravity Artifact containing:

1. Executive interpretation
2. Intended outcomes
3. Logic / operating model
4. Key assumptions
5. Dependencies
6. Evidence ledger
7. Unknowns
8. Decisions requiring confirmation
9. Questions for Others
10. Potential contradictions
11. Frame status
12. Readiness for Break

#### Questions for Others

Every material unanswered question that is deferred must receive a stable ID using the format `FQ-###`.

Do not renumber existing IDs when the Frame Brief is updated.

For each deferred question record:
* **ID**
* **Question**
* **Why it matters**
* **Suggested respondent** — role or team when reasonably inferable; otherwise `To be identified`
* **Blocking?** — Blocking or Non-blocking
* **Status** — Deferred, Open, or Answered
* **Answer** — blank until supplied

Prefer respondent roles over invented names.

At the end of the section, group unresolved questions by likely respondent when useful so the user can directly copy the questions into email, chat, meeting notes, or another handoff.

Do not require due dates unless the source artifact or user explicitly provides them.

### Step 6 — Grill to Readiness

If material gaps remain, initiate a structured interview with the user.

Present questions **one at a time**.

Each question must have a stable `FQ-###` ID from the moment it is first asked.

For every material question:
* Generate a specific, answerable question.
* When there are genuine resolution choices, present structured **A / B / C** options representing distinct paths.
* Each option should explain the approach, risk posture, and trade-offs.
* Mark one option as **(recommended)** when Frame has enough evidence to recommend one.
* Always allow the user to provide a custom answer.
* Always provide an additional path: **D. Ask someone else / save this question**.

When the user chooses D, says they do not know, or asks to save the question for another person:
1. Mark the question **Deferred**.
2. Record it under **Questions for Others**.
3. Infer the likely respondent role only when reasonably clear.
4. Classify it as Blocking or Non-blocking.
5. Do not ask another question merely to identify the respondent unless respondent ownership itself is materially necessary.
6. Continue to the next material gap.

Do not force a deferred question to be answered in the current session.

Prefer qualitative assessments over invented numbers or dates. If a timeline is unknown, describe the shape of the constraint rather than fabricating a calendar date.

**Research-first rule**: Exhaust reasonably available codebase, document, internal-source, and authoritative external research before asking the user a factual question that can be established independently.

**Coverage rule**: Assess Intent, Logic, Evidence, Ambiguity, Dependencies, and Decisions. If a section has no material gaps, note that internally and move on. Question only material unresolved gaps.

**Escalation trigger**: If the same gap repeatedly reappears without becoming more answerable, flag it as a **structural ambiguity**. Structural ambiguity may require reframing the artifact's scope rather than asking more variants of the same question.

For probing question patterns, see `references/grill-questions.md`.

As the user answers or defers questions, update the Frame Brief in real time.

The interview ends when every material question has a disposition: **Answered, Deferred, or Open**.

---

## Step 7 — Resume a Frame Brief

When Frame receives an existing Frame Brief, treat it as a continuation of prior work rather than automatically starting a new review.

On resume:
1. Preserve all existing `FQ-###` IDs.
2. Inspect **Questions for Others** first.
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
* **Complete** — every material element is represented as evidence, assumption, inference, decision, unknown, or an explicit question with a disposition.
* **In Progress** — material gaps have not yet been reconstructed or dispositioned.

Deferred questions do **not** prevent Frame Status from becoming Complete.

### Readiness for Break

Use exactly one of:

* **Ready for Break** — no material blocking questions remain.
* **Ready for Break with Conditions** — unresolved questions remain, but they do not prevent meaningful stress-testing. Clearly list the conditions.
* **Awaiting External Input** — one or more deferred or open questions materially prevent reliable stress-testing. List the blocking question IDs.

Do not label the entire Frame review incomplete merely because another stakeholder still owes an answer.

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
* Open question

Every material unanswered question must have a clear disposition.

Frame does **not** require the current user to personally obtain every answer before producing the Frame Brief.

A completed Frame Brief may legitimately end with **Awaiting External Input** when blocking questions have been identified and routed for follow-up.

When those answers become available, the user can run Frame again on the existing Frame Brief. Frame must resume from the saved question state, incorporate the new answers, and recalculate readiness without restarting the review.

The goal is not to eliminate every unknown immediately. The goal is to make every material unknown explicit, answerable, owned or routed, and safe to resume later.
