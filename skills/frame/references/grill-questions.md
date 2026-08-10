# Grill Questions — Clarification Patterns by Dimension

A catalog of question patterns for the Frame skill's structured interview. These are clarification patterns, not a mandatory script.

Frame uses them only when the corresponding part of the artifact contains a material unresolved gap. The purpose is to reconstruct intent, logic, evidence, dependencies, and decision architecture — not to stress-test failure. Premortems, inversion, kill conditions, worst-case analysis, and failure propagation belong to Break.

---

## Dimension A: Stakeholder Intent & Decision Context

Maps to Frame Brief sections: *Executive interpretation, Intended outcomes, Decisions requiring confirmation*

### Q1. Stakeholder Outcome Map
Which stakeholders are expected to benefit from this plan, which stakeholders must change behavior or give up an existing way of working, and which outcomes matter to each group?

*Why this matters*: A plan can describe a single organizational objective while different stakeholders are optimizing for different outcomes. Frame should make those differences explicit before Break evaluates their consequences.

### Q2. Sponsor Dependency
Which parts of this plan depend specifically on the authority, relationships, or interpretation of the current sponsor, and which are established through documented organizational policy or governance?

*Why this matters*: This distinguishes documented organizational commitments from decisions or assumptions that currently depend on one individual. Frame records the dependency; Break later tests its fragility.

### Q3. Success Interpretation
How will the named stakeholders determine whether the work has succeeded, and are those criteria explicitly represented in the document?

*Why this matters*: This exposes differences between stated objectives and the actual decision criteria stakeholders intend to use without yet judging whether those criteria are good or resilient.

---

## Dimension B: Causal Logic & Dependencies

Maps to Frame Brief sections: *Logic / operating model, Key assumptions, Dependencies*

### Q4. Outcome Linkage
For each important desired outcome, which activities, outputs, assumptions, and dependencies are expected to produce it?

*Why this matters*: This reconstructs the causal chain and exposes missing links without asking whether the chain will fail. Break is responsible for attacking the reconstructed chain.

### Q5. Control Boundary
Walk backward from the desired outcome through each dependency chain. At which link does the logic shift from "within our control" to "requires someone else's decision, permission, capacity, or delivery"?

*Why this matters*: Most plans contain external control boundaries that are easy to hide inside apparently seamless process language. Frame should identify exactly where those handoffs occur and who is expected to own them.

### Q6. Material Assumption Register
Which assumptions must be true for the operating model to work as written, what evidence currently supports each one, and who could confirm the assumptions that remain unverified?

*Why this matters*: This creates a clean assumption register for later stress-testing. Frame should not rank assumptions by catastrophic impact; that is Break's role.

---

## Dimension C: Evidence Quality & Epistemic Clarity

Maps to Frame Brief sections: *Evidence ledger, Unknowns, Potential contradictions*

### Q7. Evidence Boundary
For the claims carrying the most weight in the plan, what evidence supports each classification, and what part remains interpretation rather than directly established fact?

*Why this matters*: This separates evidence from inference without turning Frame into a challenge exercise. The goal is accurate classification, not to prove the claim wrong.

### Q8. Missing Evidence
What specific evidence, record, approval, metric, or stakeholder answer is still required to move any material claim from Assumed or Unknown to a stronger classification?

*Why this matters*: This converts vague uncertainty into an answerable information need that can be researched, answered now, or routed through an `FQ-###` question.

---

## Dimension D: Readiness & Decision Architecture

Maps to Frame Brief sections: *Decisions requiring confirmation, Question Register, Readiness for Break*

### Q9. Decision Reversibility
Which decisions are reversible at low cost and which become difficult to reverse once implementation begins? Are those decision properties documented or only implied?

*Why this matters*: Frame captures the decision structure so Break can later test the risk created by sequencing, commitment, and reversibility.

### Q10. Decision Ownership
For each material unresolved decision, who has the authority to make it, what input do they require, and is that ownership explicit in the source artifact?

*Why this matters*: This identifies missing decision rights and makes deferred questions easier to route without forcing the current user to know every answer.

### Q11. Break Readiness Gap
What remaining unanswered question, if any, prevents us from accurately describing the artifact's intent, operating logic, evidence base, dependencies, or decision rights?

*Why this matters*: This is a readiness clarification question, not a failure test. If the answer belongs elsewhere, save it as an `FQ-###` item and classify whether it blocks Break.

---

## Usage Notes

* These are question **patterns**, not a script.
* Assess all Frame dimensions, but ask only questions tied to material unresolved gaps.
* Do not ask a question merely to achieve section or dimension coverage.
* Adapt wording to the specific artifact under review.
* Prefer questions that produce facts, definitions, ownership, evidence, assumptions, or explicit decisions.
* If a question starts asking what would guarantee failure, what would make the plan collapse, what the worst case is, or what would force abandonment, move that analysis to Break.
* All questions use qualitative framing unless the source artifact already provides meaningful dates, numbers, thresholds, or scoring methods.