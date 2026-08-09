---
name: break
description: Stress-test and expose weakness in plans, playbooks, and business documents.
---

# Break Skill

**Mission**: Attempt to make the proposed system fail before reality does.

Use Break after there is sufficient shared understanding of the artifact (e.g., after running `/frame`). Break is adversarial analysis without becoming contrarian for its own sake.

**Triggers**: `/break <document>` or `/break FRAME-REVIEW.md`

---

## The Evidence Contract (Summary)

*   **Evidence Hierarchy**: Prefer laws, regulations, and official standards.
*   **Claim Classification**: Distinguish between Verified, Supported, Inferred, Assumed, and Unknown claims.
*   **Source Fit**: Only apply external frameworks if they meaningfully apply to the artifact and context.
*   **Citation Rule**: Identify sources for recommendations grounded in external standards.

*(For full details, see `references/evidence-contract.md`)*

---

## Process

### Step 1 — Establish the Target
Identify what constitutes failure (e.g., adoption target missed, project delayed, budget overrun, dependency failure).

### Step 2 — Run a Premortem
Assume: "It is six months later and this initiative failed badly." Work backward to generate plausible causal chains explaining the failure. Generate highly specific, contextual failure chains rather than generic risks.

### Step 3 — Apply Inversion
Ask: "What conditions would almost guarantee failure?" Use the inverse to expose design requirements that may be absent.

### Step 4 — Attack the Dependencies
Stress relevant dimensions: people, process, technology, governance, sequencing, capacity, data, suppliers, handoffs, communications, adoption, controls, timeline, decision rights.

### Step 5 — Test Scenarios
Test realistic variations:
* Expected case
* Adverse case
* Extreme-but-plausible case
* Edge case
* Dependency failure
* Human-behavior failure

Look for failure propagation, not merely isolated risks.

### Step 6 — Find Contradictions
Search for goals inconsistent with activities, missing owners, risk without treatment, success metrics that cannot prove success, etc.

### Step 7 — Prioritize
Classify findings:
* **Blocker**: Likely to invalidate the plan or prevent safe execution.
* **Major concern**: Material weakness requiring treatment.
* **Watch item**: Plausible but manageable uncertainty.
* **Observation**: Useful improvement without material execution risk.

Use qualitative priority labels (Blocker, Major concern, etc.) instead of numeric risk scores.

### Step 8 — Recommend
Every Blocker and Major Concern receives: Finding, Why it matters, Evidence, Failure scenario, Recommended response, Trade-off, Decision owner (if known).
Isolate your output to the Break Report; leave the original plan unmodified.

### Step 9 — Grill to Readiness
If the Break Report concludes the plan is **Not ready** for Fortify (e.g., due to fatal blockers or decisions requiring human judgment):
Do NOT simply leave them unresolved and stop. You must actively work to resolve the critical items to prepare the document for the Fortify skill.
Initiate an interview with the user. Ask about the blockers or decisions **one question at a time**.
For each question, always provide a recommendation and explain the trade-offs.
As the user answers, update the Break Report's recommended responses and verdict. Continue this loop until the plan is explicitly "Ready to strengthen" (ready for Fortify).

---

## Output

Produce a Break Report (as an Antigravity Artifact) containing:
1. Failure thesis
2. Top failure paths
3. Premortem results
4. Fragile assumptions
5. Missing controls
6. Dependency failures
7. Contradictions
8. Edge cases
9. Blockers
10. Major concerns
11. Watch items
12. Recommended responses
13. Decisions requiring human judgment
14. Verdict (Ready to strengthen, Ready with conditions, or Not ready)

---

## Completion Criterion

Break is complete when every major stated objective has been tested against plausible failure conditions and every material weakness is recorded, supported with reasoning/evidence, prioritized, and given a recommended response. If the report was initially 'Not ready', completion requires successfully interviewing the user to resolve critical blockers and decisions until it is 'Ready to strengthen'.
