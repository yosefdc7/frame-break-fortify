# Frame → Break → Fortify

Agent Skills for reviewing and strengthening plans, playbooks, frameworks, strategies, change-management plans, operating models, procedures, specifications, governance documents, and similar business artifacts.

## The Philosophy

The system optimizes for **process predictability rather than identical answers**.

1. **Frame** — Understand and establish the truth.
2. **Break** — Stress-test and expose weakness.
3. **Fortify** — Strengthen with margin of safety and antifragility.

Evidence governs all three skills.

## The Skills

Each skill can be used independently or in sequence.

### `/frame`
**Mission**: Reconstruct the document into a clear, evidence-aware mental model before judging or changing it.
**Usage**: `/frame <document>`

### `/break`
**Mission**: Attempt to make the proposed system fail before reality does. Adversarial analysis without becoming contrarian for its own sake.
**Usage**: `/break <document>` or `/break FRAME-REVIEW.md`

### `/fortify`
**Mission**: Actively strengthen the plan by building **margin of safety** and **antifragility** into it, grounded in external knowledge. Fortify is an engineer, not a compiler — it clusters Break findings into themes and produces targeted recommendations (cited sources, Redundancy / Contingency Triggers / Graceful Degradation, optionality, learning loops), then a strengthened artifact.
**Usage**: `/fortify <document>` or `/fortify <document> BREAK-REVIEW.md`

## The Evidence Contract

Every skill follows a strict evidence contract. We prioritize governing laws and standards over unsupported common practice, and we classify claims as Verified, Supported, Inferred, Assumed, or Unknown.

## Project Management Guide

See [INSTRUCTIONS_PM.md](docs/INSTRUCTIONS_PM.md) for a detailed guide on how Project Managers can use this triplet to validate assumptions, run premortems, and build antifragile project artifacts.

---
*Frame like a reviewer. Break like an adversary. Fortify like an architect. Evidence governs all three.*
