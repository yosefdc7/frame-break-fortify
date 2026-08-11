---
name: solution-explore
description: Project Manager solution exploration skill. Grill the problem and constraints, ground the exploration in reliable sources, and generate materially different solution options without prematurely ranking them.
disable-model-invocation: true
license: MIT
metadata:
  version: "0.1.0"
---

# Project Manager: Solution Explore

**Mission**: Turn an unclear problem into a well-grounded set of genuinely different solution options. Understand first, research second, diverge third. Do not rank or select a winner; that belongs to `solution-decide`.

Use when the user has a problem, goal, opportunity, or requirement but has not yet committed to a solution.

**Triggers**:
* `/explore <problem or context>`
* `/explore <existing Solution Options>` to resume

---

## Core Flow

`GRILL → GROUND → DIVERGE`

The skill should ask only questions that could materially change the problem definition, constraints, solution space, or later decision criteria.

---

## Step 1 — GRILL the Problem

Reconstruct:
* **Problem** — what is happening now and why it matters
* **Desired outcome** — what should be different
* **Scope / exclusions**
* **Users / stakeholders**
* **Hard constraints** — a viable solution must satisfy them
* **Preferences** — important but negotiable
* **Assumptions** — believed true but not established
* **Unknowns** — missing information that could change the solution space
* **Decision criteria** — factors likely to matter later when choosing

Do not treat a preference as a hard constraint without evidence.

### Grilling method

For every material ambiguity, create a stable `EQ-###` question.

Ask questions one at a time when interaction is needed.

When genuine interpretations or paths exist, use:
* **A. Recommended interpretation** — when evidence supports one
* **B. Alternative**
* **C. Another materially different interpretation** — only when real
* **D. Ask someone else / save this question**

The user may always provide a custom answer.

If the user chooses D or does not know:
1. mark the question **Deferred**;
2. record the suggested respondent when reasonably inferable;
3. classify it as **Blocking** or **Non-blocking** for exploration; and
4. continue with unaffected work.

Do not manufacture questions for coverage. If the problem is already sufficiently clear, move on.

---

## Step 2 — GROUND the Exploration

Ask how the user wants to ground the solution space:

* **A. Provide sources** — upload/share internal playbooks, approved PPMs, policies, studies, standards, reference architectures, product requirements, or other trusted material.
* **B. Search for reliable sources** — research authoritative sources and existing solution patterns.
* **C. Hybrid** — use supplied sources first, then research gaps.

When researching:
1. prefer governing requirements, official standards, primary institutional sources, peer-reviewed research, systematic reviews, authoritative first-party documentation, and credible existing implementations;
2. prefer primary sources over summaries;
3. check applicability to the actual context;
4. distinguish **Reliable**, **Supporting**, and **Weak** sources;
5. do not present repeated web opinion as a best practice;
6. never fabricate a source or pretend it was retrieved.

If search/retrieval tools are unavailable, ask the user to provide sources or clearly label the exploration as **Reasoning-only / Not externally grounded**.

User approval is not required for every source before exploration can continue. However, make the material sources that influenced the solution options visible so the user can challenge them.

---

## Step 3 — DIVERGE into Solution Options

Generate **materially different solution archetypes**, not minor variants of the same idea.

Good divergence might include:
* adopt an existing solution;
* customize an open-source solution;
* build a thin internal solution;
* extend an existing internal platform;
* change the process rather than add technology;
* use a managed/commercial solution;
* combine approaches when the hybrid is materially distinct.

Do not force a fixed number of options. Prefer a small set of credible, distinct approaches over a long brainstorm.

Every viable option receives a stable `SO-###` ID.

For each option capture:
* **Approach**
* **How it solves the problem**
* **Best fit / when it works well**
* **Main advantages**
* **Main trade-offs**
* **Hard-constraint fit** — Meets / Unclear / Fails
* **Key dependencies**
* **Evidence / source basis**
* **Important unknowns**

If an option clearly violates a hard constraint, either exclude it or keep it only as **Non-viable under current constraints** when showing it teaches something useful.

### Boundary

`solution-explore` must **not rank the options, choose a winner, or force convergence**.

It may say which options are viable enough to pass to `solution-decide`.

---

## Resume

When given an existing Solution Options artifact:
1. preserve existing `EQ-###` and `SO-###` IDs;
2. incorporate new answers, constraints, sources, or context;
3. re-open only affected parts of the exploration;
4. add new options only when new information materially expands the solution space;
5. do not restart completed work unnecessarily.

---

## Output — Solution Options

Produce a concise artifact containing:

### 1. Problem
* Problem
* Desired outcome
* Scope / exclusions

### 2. Constraints
* Hard constraints
* Preferences
* Assumptions
* Unknowns

### 3. Decision Criteria
Factors likely to matter when selecting later.

### 4. Grounding
Material reliable/supporting sources and important limitations.

### 5. Solution Options
For each `SO-###`: approach, fit, advantages, trade-offs, dependencies, evidence, and unknowns.

### 6. Questions for Others
Deferred `EQ-###` items only.

### 7. Exploration Status
Use:
* **Ready for Decision** — enough viable, distinct options and decision criteria exist for comparison.
* **Ready for Decision with Conditions** — comparison can proceed if listed assumptions/unknowns remain explicit.
* **Needs More Input** — missing information materially prevents a credible solution set.

---

## Completion Criterion

Exploration is complete when:
* the problem and desired outcome are clear enough to generate solutions responsibly;
* hard constraints are separated from preferences and assumptions;
* material unknowns are explicit or deferred;
* the exploration is grounded in visible evidence when reliable sources are available;
* the solution set contains credible, materially different approaches; and
* the skill stops before ranking or recommending a winner.

The goal is not to produce many ideas. The goal is to produce the **right solution space** for a high-quality decision.