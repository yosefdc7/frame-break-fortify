---
name: think
description: Reconstruct plans and business documents to establish intent, assumptions, and evidence.
disable-model-invocation: true
license: MIT
metadata:
  version: "0.1.0"
---

# Think Skill

**Mission**: Reconstruct the document into a clear, evidence-aware mental model before judging or changing it.

Use Think when:
* Reviewing an unfamiliar plan or playbook
* The author's intent is unclear
* Assumptions are hidden
* Requirements may be incomplete
* Terminology is inconsistent
* Success criteria are ambiguous
* The user wants a document grilled before it is approved

**Triggers**: `/think <document>`

---

## The Evidence Contract (Summary)

*   **Evidence Hierarchy**: Prefer laws, regulations, and official standards. Do not turn something into a "best practice" simply because websites repeat it.
*   **Claim Classification**: Classify claims as Verified, Supported, Inferred, Assumed, or Unknown.
*   **Source Fit**: Only apply external frameworks if they meaningfully apply to the artifact and context.
*   **Citation Rule**: Identify sources for recommendations grounded in external standards.

*(For full details, see `references/evidence-contract.md`)*

---

## Process

Do not critique yet. Focus on reconstruction and establishing truth.

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

### Step 4 — Find Ambiguity
Identify undefined terminology, conflicting requirements, missing owners, unclear dependencies, unclear decision rights, non-measurable outcomes, and assumptions disguised as facts.

### Step 5 — Grill Decisions
For genuine unresolved decisions, ask the user **one question at a time**.
Always provide a recommendation and explain the trade-offs.
Do not ask the user a question merely because you have not performed enough legwork.

### Step 6 — Produce the Think Brief
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
10. Recommendation: ready or not ready for Break

---

## Completion Criterion

Think is complete only when every material element of the artifact can be represented as evidence, assumption, decision, inference, or explicitly acknowledged unknown. Explicitly document any remaining ambiguity as an 'Unknown' rather than omitting it.
