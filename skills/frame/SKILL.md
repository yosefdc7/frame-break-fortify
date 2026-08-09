---
name: frame
description: Reconstruct plans and business documents to establish intent, assumptions, and evidence.
disable-model-invocation: true
license: MIT
metadata:
  version: "0.1.0"
---

# Frame Skill

**Mission**: Reconstruct the document into a clear, evidence-aware mental model before judging or changing it.

Use Frame when:
* Reviewing an unfamiliar plan or playbook
* The author's intent is unclear
* Assumptions are hidden
* Requirements may be incomplete
* Terminology is inconsistent
* Success criteria are ambiguous
* The user wants a document grilled before it is approved

**Triggers**: `/frame <document>`

---

## The Evidence Contract (Summary)

*   **Evidence Hierarchy**: Prefer laws, regulations, and official standards. Do not turn something into a "best practice" simply because websites repeat it.
*   **Claim Classification**: Classify claims as Verified, Supported, Inferred, Assumed, or Unknown.
*   **Source Fit**: Only apply external frameworks if they meaningfully apply to the artifact and context.
*   **Citation Rule**: Identify sources for recommendations grounded in external standards.

*(For full details, see `references/evidence-contract.md`)*

---

## Process

Withhold all critique. Focus strictly on reconstruction and establishing truth.

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
Map: `Inputs → assumptions → activities → dependencies → decisions → outputs → outcomes → measures of success`
Expose broken or missing links.

### Step 3 — Establish Evidence
Classify important statements as Verified, Supported, Inferred, Assumed, or Unknown. Research material factual questions rather than asking the user to answer things that can be established independently.

→ Findings from evidence classification become direct inputs to the ambiguity scan in Step 4: claims classified as Assumed or Unknown are the highest-priority ambiguity candidates.

### Step 4 — Find Ambiguity
Identify undefined terminology, conflicting requirements, missing owners, unclear dependencies, unclear decision rights, non-measurable outcomes, and assumptions disguised as facts.

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
9. Potential contradictions
10. Readiness for Break (Ready or Not Ready)

### Step 6 — Grill to Readiness

If the Frame Brief concludes the plan is **not ready for Break** (due to unresolved baselines, owners, scope, measurable gates, or other material gaps):

**Initiate a structured interview with the user.** Present questions one at a time.

For every gap classified as blocking readiness:
* Generate a specific, answerable question that would resolve it.
* **Present the user with structured options (A, B, C) representing distinct resolution paths.** Each option must describe: the approach, its risk posture, and its trade-offs. Always mark one option as *(recommended)* with a brief justification. The user needs a menu of choices, not a single prescription.
* Prefer qualitative assessments over invented numbers or dates. If a timeline is unknown, describe the *shape* of the constraint (e.g., "this dependency sits on the critical path; any delay here pushes the entire delivery") rather than fabricating a calendar date.

**Exhaust all available codebase and documentation research before asking the user a question.**

**Minimum coverage rule**: Produce at least one question for each section of the Frame Brief (Intent, Logic, Evidence, Ambiguity, Dependencies, Decisions) that contains unresolved gaps. If a section has no gaps, note it explicitly and move on. There is no upper limit — continue until every blocking gap has a disposition.

**Escalation trigger**: If the same gap recurs across three or more questions without resolution, pause the interview and flag it as a *structural ambiguity* — a gap that may require reframing the document's scope rather than filling in blanks.

For a catalog of probing question patterns organized by assessment dimension, see `references/grill-questions.md`.

As the user answers, update the Frame Brief in real time. The interview ends when the Frame Brief contains no unresolved blocking gaps — the verdict line changes from "Not Ready" to "Ready for Break."

---

## Completion Criterion

**Pre-interview gate**: Before entering the Grill to Readiness interview, the agent must identify at least one unresolved element per section of the Frame Brief (Intent, Logic, Evidence, Ambiguity, Dependencies, Decisions). If any section genuinely has no gaps, state why explicitly. This ensures the interview is driven by structural coverage rather than surface impression.

Frame is complete only when every material element of the artifact can be represented as evidence, assumption, decision, inference, or explicitly acknowledged unknown. If the plan was initially not ready for Break, completion requires successfully interviewing the user to resolve the missing elements until the Frame Brief contains no unresolved blocking gaps and the verdict is explicitly "Ready for Break."
