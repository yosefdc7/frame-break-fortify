# Project Management Guide: Frame → Break → Fortify

Use this workflow when you are handed a plan, playbook, process, strategy, governance model, or similar artifact and need to understand it, challenge it, and improve it without pretending you personally know every answer.

The practical rule is:

> **You do not need to know or decide everything. The skills should make missing information, decisions, and evidence explicit and resumable.**

---

## 1. FRAME — Understand Before Challenging

Run `/frame` first when the artifact is unfamiliar, ambiguous, assumption-heavy, or missing decision context.

Frame should establish:
* intent and outcomes;
* scope and exclusions;
* operating logic;
* assumptions and evidence;
* dependencies and handoffs;
* decision rights; and
* measurable success criteria.

### Questions you cannot answer

Every material question gets an `FQ-###` ID.

You can:
* answer it now; or
* choose **Ask someone else / save this question**.

Deferred questions go into **Questions for Others**.

Example:

```text
FQ-004 — Who has final production approval authority?
Suggested respondent: Sponsor / Governance Lead
Blocking: Yes
Status: Deferred
```

When you get the answer later:

```text
FQ-004: CTOO Steering Committee owns final approval.
```

Run `/frame` on the existing Frame Brief. It should update `FQ-004` rather than restart the interview.

### FRAME boundary

FRAME clarifies. BREAK attacks.

Do not use FRAME for premortems, inversion, worst-case failure chains, or failure propagation.

---

## 2. BREAK — Stress-Test What FRAME Established

When a Frame Brief exists, BREAK must respect its readiness result.

* **Ready for Break** — proceed normally.
* **Ready for Break with Conditions** — proceed while preserving the listed `FQ-###` conditions.
* **Awaiting External Input** — test unaffected areas only; do not invent the missing answer.

BREAK uses:
* premortem;
* inversion;
* dependency attacks;
* adverse and edge scenarios;
* human-behavior failure; and
* contradiction analysis.

Material findings receive `BF-###` IDs.

For Blockers and Major concerns, BREAK recommends a response before asking you to decide.

You can:
* accept the recommendation;
* choose an alternative;
* explicitly accept a legitimate risk; or
* choose **Ask someone else / save this decision**.

Example:

```text
BF-006 — Steering Committee cadence is too slow for the release model.
Recommended response: Establish delegated approval for predefined low-risk releases.
Disposition: Deferred to Sponsor
```

When the Sponsor responds:

```text
BF-006: Delegated approval approved for predefined low-risk releases.
```

Run `/break` on the existing Break Report. BREAK should re-test only the affected approval path.

---

## 3. FORTIFY — Strengthen Using a Visible Source Basis

FORTIFY converts weaknesses into concrete controls and improvements.

### First choose the source path

FORTIFY asks:

```text
A. I will provide approved sources
B. Search for reliable candidates and let me validate them
C. Hybrid — use my sources first, then search for gaps
```

Good source examples:
* approved internal PPMs/playbooks;
* organizational policies and standards;
* industry standards;
* recognized methodologies/frameworks;
* peer-reviewed studies or systematic reviews;
* authoritative first-party documentation; and
* governing legal or regulatory requirements.

If search tools are unavailable, FORTIFY should not invent sources. Provide files or links instead.

### Keep source quality separate from approval

Every material source receives an `FS-###` ID.

FORTIFY records:

**Quality**
* `Governing`
* `Reliable`
* `Supporting`
* `Weak`

**Use**
* `Approved`
* `Candidate`
* `Rejected`

Example:

```text
FS-002
Source: Internal Release Governance Standard
Quality: Reliable
Use: Approved
Supports: BF-006
```

A source being **Approved** does not automatically make it **Reliable**. FORTIFY should still assess authority and fit.

Material externally grounded recommendations should use applicable **Governing** sources or **Reliable + Approved** sources.

### Reasoning-only is provisional

You can ask FORTIFY for a reasoning-only pass, but material recommendations that still need external grounding remain provisional.

They should not be presented as:
* industry best practice;
* externally validated; or
* fully Ready when the missing evidence materially affects the design.

### Resume source validation later

If you need to validate candidate sources with PMO, Legal, Architecture, Risk, or another SME, return later with the IDs.

Example:

```text
FS-003: Approved.
FS-004: Reject; use another standard.
```

Run `/fortify` on the existing Fortify artifact. It should preserve the source IDs and continue from that state.

---

## 4. When FORTIFY Finds Evidence That Changes BREAK

Sometimes a strong source discovered during FORTIFY invalidates a treatment already accepted in BREAK.

Example:

```text
BF-006 treatment:
Delegated approval

FS-005:
Mandatory policy says this release class cannot use delegated approval.
```

FORTIFY should **not** implement the conflicting treatment.

Instead it should mark:

```text
BF-006 — Reopen in Break — Source Conflict
Conflicting source: FS-005
```

Then run BREAK again on the existing Break Report.

BREAK should:
* reuse `BF-006`;
* preserve the old decision as history;
* re-test only that treatment path; and
* obtain a new disposition.

This avoids duplicate findings and keeps the audit trail intact.

---

## 5. Read the Statuses Correctly

### FRAME

**Frame Status**
* `Complete`
* `In Progress`

**Break Readiness**
* `Ready for Break`
* `Ready for Break with Conditions`
* `Awaiting External Input`

### BREAK

**Break Status**
* `Complete`
* `In Progress`

**Fortify Readiness**
* `Ready for Fortify`
* `Ready for Fortify with Conditions`
* `Awaiting External Input`

### FORTIFY

**Fortify Status**
* `Complete`
* `Awaiting Source Validation`
* `In Progress`

**Final Verdict**
* `Ready`
* `Ready with conditions`
* `Not ready`

Do not confuse analytical completion with readiness for the next decision or stage.

---

## 6. End-to-End Example

```text
FRAME
FQ-004: Who owns production approval?
→ Deferred to Sponsor
→ Sponsor answers later
→ Ready for Break

BREAK
BF-006: Approval cadence is a release bottleneck
→ Delegated approval recommended
→ Sponsor approves
→ Ready for Fortify

FORTIFY
User chooses Search for candidates
FS-001: Reliable + Approved governance source
FS-002: Supporting + Approved research
→ strengthen approval controls
→ trace changes to BF-006 and FS-001
```

If `FS-003` later proves delegation is prohibited:

```text
FORTIFY
→ BF-006 Reopen in Break — Source Conflict

BREAK
→ reuse BF-006
→ select a compliant treatment

FORTIFY
→ resume only the affected recommendation
```

---

## Working Mental Model

```text
FRAME
What is true and what do we still need to know?

BREAK
How can this fail and what treatment decision is needed?

FORTIFY
What reliable basis should we use, and how should the artifact be strengthened?
```

The goal is a plan where you can trace **what was unclear (`FQ`) → what could fail (`BF`) → what evidence guided the fix (`FS`) → what changed**.