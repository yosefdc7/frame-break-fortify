---
name: solution-decide
description: Project Manager solution decision skill. Verify the decision basis, filter options against hard constraints, compare trade-offs, rank viable solutions, and recommend a direction with clear conditions.
disable-model-invocation: true
license: MIT
metadata:
  version: "0.1.0"
---

# Project Manager: Solution Decide

**Mission**: Turn a credible set of solution options into a transparent decision. Filter first, compare second, recommend last. Do not invent precision or hide trade-offs.

Use after `solution-explore`, or whenever the user already has multiple solution options to compare.

**Triggers**:
* `/decide <Solution Options>`
* `/decide <options + context>`
* `/decide <existing Solution Decision>` to resume

---

## Core Flow

`VERIFY → FILTER → COMPARE → RECOMMEND`

The skill should converge. It should not reopen broad ideation unless the supplied options are materially incomplete.

---

## Step 1 — VERIFY the Decision Basis

Before ranking, confirm that the decision is comparable.

Check:
* Are the options materially different?
* Are hard constraints explicit?
* Are important decision criteria known?
* Are important assumptions or evidence gaps visible?
* Are the options described consistently enough for fair comparison?

If a missing answer could materially change the ranking, ask only that decision-specific question.

Use stable `DQ-###` IDs for material decision questions.

When genuine choices exist, use:
* **A. Recommended interpretation**
* **B. Alternative**
* **C. Another materially different interpretation** — only when real
* **D. Ask someone else / save this question**

Do not repeat the full problem interview from `solution-explore`.

If important comparison evidence is missing and reliable research can establish it, research before asking the user. Never fabricate evidence.

---

## Step 2 — FILTER by Hard Constraints

Hard constraints are **gates, not scoring factors**.

For each option classify:
* **Pass** — meets the hard constraints
* **Unclear** — evidence is insufficient
* **Fail** — violates a hard constraint

A failed option is not allowed to win because it scores highly elsewhere.

Keep an option with an Unclear constraint fit in the comparison only when the uncertainty is explicit and does not make the ranking misleading.

---

## Step 3 — COMPARE the Viable Options

Use only criteria that matter to the decision.

Typical criteria may include:
* outcome / requirement fit;
* simplicity;
* implementation effort;
* time to value;
* operating effort;
* flexibility;
* integration fit;
* maintainability;
* reversibility;
* adoption/change impact;
* risk;
* cost — when the user wants it considered.

Do not force every criterion into every decision.

### Default comparison method

Prefer qualitative comparison over invented numeric precision:
* **Strong**
* **Moderate**
* **Weak**

Use numeric weights/scores only when:
* the user requests them; or
* meaningful quantitative inputs already exist.

Never invent weights and then present the result as objective.

### Trade-off analysis

For each serious candidate state:
* **You gain**
* **You give up**
* **Best when**
* **Avoid when**

For the top two options explicitly state:
* **SO-X beats SO-Y when...**
* **SO-Y beats SO-X when...**

This conditional comparison is more important than the raw ranking.

---

## Step 4 — RECOMMEND

Rank only viable options.

Provide:
* **Recommended option** — one clear choice when evidence supports it
* **Why it ranks first**
* **Main trade-off**
* **Runner-up**
* **Choose the runner-up instead if...**
* **Confidence** — High / Medium / Low
* **What could change the recommendation**
* **Next validation** — only when useful before commitment

Do not hide behind “it depends.” Explain what it depends on and still recommend a direction when the evidence supports one.

If evidence is too weak to responsibly rank the leading options, say **Decision Not Ready**, identify the smallest missing validation, and do not manufacture a winner.

---

## Evidence Rules

Use supplied grounding from `solution-explore` where available.

When additional research is required:
* prefer governing requirements, official standards, primary institutional sources, peer-reviewed research, systematic reviews, authoritative first-party documentation, and credible implementation evidence;
* distinguish reliable evidence from supporting or weak evidence;
* state important applicability limitations;
* never fabricate a source or pretend it was retrieved.

A recommendation should be traceable to:
* hard constraints;
* decision criteria;
* solution evidence;
* stated trade-offs; and
* explicit user priorities or decisions.

---

## Resume

When given an existing Solution Decision:
1. preserve `SO-###` option references and existing `DQ-###` questions;
2. incorporate new evidence, constraint changes, stakeholder answers, or updated options;
3. re-run only the affected filters/comparisons;
4. explain if and why the ranking changed;
5. do not restart the entire decision unnecessarily.

---

## Output — Solution Decision

Produce a concise artifact containing:

### 1. Decision
What is being selected and the desired outcome.

### 2. Hard-Constraint Filter
For each option: Pass / Unclear / Fail, with the reason.

### 3. Comparison
A simple trade-off matrix using the decision's material criteria.

### 4. Ranking
Rank viable options only.

### 5. Recommendation
* Recommended option
* Why
* Main trade-off
* Runner-up
* Choose runner-up instead if
* Confidence

### 6. What Could Change the Decision
Only material uncertainties, assumptions, or pending `DQ-###` items.

### 7. Next Validation
The smallest useful prototype, spike, research task, or stakeholder decision before commitment, when needed.

---

## Decision Status

Use:
* **Ready to Decide** — evidence supports a defensible recommendation.
* **Ready with Conditions** — recommendation is usable if explicit conditions remain visible.
* **Decision Not Ready** — missing information could materially reverse the ranking.

---

## Completion Criterion

Decision analysis is complete when:
* hard constraints have been applied as gates;
* surviving options are compared on meaningful criteria;
* trade-offs are explicit;
* ranking avoids false precision;
* the recommendation explains why the winner beats the runner-up;
* material uncertainty is visible; and
* the next validation is specified only when it would materially improve the decision.

The goal is not to create a perfect scorecard. The goal is to make a **defensible, explainable decision**.