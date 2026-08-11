# Changelog

Notable changes to **Frame → Break → Fortify** are recorded here.

The repository's `SKILL.md` files remain the source of truth for behavior. Changes that are already committed but not yet released under a new plugin version stay under **Unreleased**.

## Unreleased

### Added
- FRAME deferred-question workflow with stable `FQ-###` IDs, a canonical Question Register, `Questions for Others`, and resume support.
- BREAK deferred-decision workflow with stable `BF-###` IDs, accepted-risk handling, external decision handoff, and selective resume.
- Readiness gates between FRAME → BREAK and BREAK → FORTIFY.
- FORTIFY Direct Mode for strengthening without pretending a formal BREAK analysis occurred.
- FORTIFY source-grounding workflow: user-provided sources, AI-searched candidate sources, or a hybrid path.
- Stable `FS-###` source IDs and resumable source validation.
- Lean Source Register with separate **Quality** (`Governing`, `Reliable`, `Supporting`, `Weak`) and **Use** (`Approved`, `Candidate`, `Rejected`).
- FORTIFY → BREAK feedback path when new governing or reliable evidence invalidates an existing `BF-###` treatment.

### Changed
- `Open` is now transient in FRAME and BREAK; completed reviews require terminal dispositions for material questions/findings.
- FRAME and BREAK completion are separated from downstream readiness.
- FRAME clarification questions are kept reconstructive; premortem, inversion, kill-condition, and worst-case failure testing belong to BREAK.
- FORTIFY chooses controls by the actual failure mechanism instead of mechanically mapping severity to one control type.
- AI-found material design-basis sources require user validation before use.
- User approval no longer upgrades source quality.
- Reasoning-only material FORTIFY recommendations remain provisional when external grounding is materially needed.
- BREAK can reopen the same `BF-###` when later source evidence invalidates an earlier treatment instead of creating a duplicate finding.
- Shared Evidence Contract updated and aligned across all three skills.
- README and PM guide simplified; `SKILL.md` files and their references are explicitly normative.

### Fixed
- Removed stale `Think-Break-Build` wording from the shared Evidence Contract.
- Closed gaps where BREAK could ignore FRAME readiness or FORTIFY could silently override unresolved upstream decisions.
- Prevented AI-searched candidate sources from being treated as approved or reliable by default.
- Prevented reasoning-only recommendations from supporting an unjustified fully `Ready` verdict when material evidence is still required.

## 0.2.0 — 2026-08-09

### Added
- Rebranded the workflow to **Frame → Break → Fortify**.
- Added the Project Management guide.
- Added Grill to Readiness behavior for FRAME and BREAK.
- Added FRAME structured A/B/C resolution options and clarification-question patterns.
- Redesigned FORTIFY around margin of safety, optionality, learning loops, targeted recommendations, and a strengthened artifact.
- Added the shared Evidence Contract.

### Changed
- FORTIFY moved from a compiler-style rewrite into an evidence-aware engineering role.
- README redesigned around the three-stage pipeline and balanced responsibilities across FRAME, BREAK, and FORTIFY.
- Plugin version set to `0.2.0`.
