# Project Management Guide: Frame → Break → Fortify

As a Project Manager or Change Manager, you are frequently handed drafts (playbooks, processes, project plans, change impact assessments) from technical or business leads and told to "manage it." 

The hardest part of your job isn't tracking the schedule—it's **interrogating these drafts for hidden risks and validating their assumptions** without having to be a subject matter expert in the underlying domains.

The **Frame → Break → Fortify** skill triplet transforms you from a "schedule tracker" into a strategic **Risk Analyst and Architect**. It provides a rigorous, objective, and non-confrontational framework to tear down a stakeholder's messy draft, validate every assumption, and rebuild it into an airtight, executable artifact.

---

## 1. Validating Assumptions (The Core Goal)

PMs constantly battle "optimism bias," where stakeholders present their assumptions as guaranteed facts.

*   **The Problem**: A stakeholder claims "The engineering team will finish the API by Tuesday."
*   **The Solution**: The `/frame` skill explicitly demands an **Evidence Ledger**. It forces the agent to classify every material claim in the draft as *Verified, Supported, Inferred, Assumed,* or *Unknown*. 
*   **The Result**: It immediately isolates risky assumptions (like the API delivery date) so they can be tested, preventing the project from being built on a house of cards.

## 2. Validating Project Plans & Frameworks

Project plans fail mostly due to unmapped dependencies and unrealistic sequencing.

*   **The Problem**: A schedule looks good on paper but ignores external vendor bottlenecks.
*   **The Solution**: The `/break` skill specifically instructs the agent to **"Attack the Dependencies"** (sequencing, capacity, suppliers, handoffs). 
*   **The Result**: By forcing a "Premortem" (assuming the project failed catastrophically six months from now and working backward), you can validate if the schedule is realistic and if the framework actually holds up when an edge case occurs.

## 3. Validating Change Impact & Change Management Plans

Change management artifacts are notorious for containing "fluff" and untestable goals.

*   **The Problem**: A change management plan has a goal to "Ensure stakeholders are aligned" or "Users understand the new tool."
*   **The Solution**: The `/fortify` skill directly targets this weakness. It clusters `/break` findings into themes and produces **targeted recommendations grounded in external knowledge** — each with a cited source and a margin of safety control (**Redundancy** for Blockers, **Contingency Triggers** for Major Concerns, **Graceful Degradation** for Watch Items). It also mandates replacing vague completion language with **observable criteria**.
*   **The Result**: It forces you to upgrade *"users understand the change"* to *"affected users demonstrate the required process during readiness validation."* Furthermore, `/break` explicitly tests for "human-behavior failures," which is the root cause of most failed change management plans.

## 4. Validating Playbooks & Processes

A playbook is only useful if it survives contact with reality and actual users.

*   **The Problem**: A process workflow looks perfect on a flowchart but fails in practice due to poor handoffs.
*   **The Solution**: The `/frame` skill reconstructs the logic as `Inputs → activities → handoffs → outputs`. This visually exposes broken handoffs. 
*   **The Result**: Then, `/break` applies "Inversion" (*What conditions would guarantee this process fails?*) to find the missing controls in the playbook before it is ever published.

---

## The Mental Models Behind the Magic

Instead of just trying to "think harder," this triplet acts as an operating system for established critical thinking principles:

1. **FRAME (First Principles & Steel-Manning)**: You rebuild the plan from fundamental truths (Verified facts vs Assumptions), ensuring you are evaluating the strongest possible version of the plan, rather than attacking a poorly understood straw man.
2. **BREAK (Inversion & Falsifiability)**: Charlie Munger's "Invert, always invert." By looking at the problem backward, you instantly spot missing requirements and hidden risks. You subject the plan to rigorous attempts to prove it wrong.
3. **FORTIFY (Margin of Safety & Antifragility)**: You build a margin of safety into the plan by explicitly establishing controls and contingencies. By intentionally stressing the plan (Break) and rewriting the weaknesses (Fortify), your artifacts become resilient and antifragile.
