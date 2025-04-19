# token_discipline.md

This file documents the evolving methodology for managing token usage, compression strategy, and instruction design across all AI-assisted work in the `env0` ecosystem. The goal is not just efficiency, but **clarity, auditability, and durability under constraint**.

---

## 1. RESET.md Strategy

Each session starts with a fresh `RESET.md`, a manual super-prompt used to simulate long-term memory and enforce constraints. These are written in an unstructured but deliberate format, prioritising cognitive scaffolding over formal syntax. The `RESET.md` system is central to managing context in long-running projects and recursive loops.

---

## 2. Pre-tokenisation (Aesthetic + Efficiency)

Some prompts and control files are written in already-tokenised form—compact, minimal, efficient. This is partially practical, but also performative: the aesthetic of token-conscious authorship signals intent, control, and technical fluency. The style itself is a form of compression.

---

## 3. Instruction Compression Techniques

- Strip unnecessary modifiers ("please", "kindly", etc.)
- Flatten conditionals and reduce nested logic
- Prefer implication over elaboration when working with structured prompts
- Use pseudo-code or tag-based constraints when appropriate

---

## 4. Deduplication by Design

Instructions, labels, and scaffolds are frequently reviewed for overlap. Where duplication is found, reusable blocks or prompt macros are considered. This prevents silent context inflation across related files.

---

## 5. Contextual Reset Protocols

The decision to split chats, label them `arc_*`, or issue a hard reset is guided by:
- Degradation in coherence
- Increase in contradiction or hallucination
- Need for sharp session pivot (e.g., from coding to concept)

This protocol helps maintain session discipline without hard dependencies on AI memory or embeddings.

---

## 6. Performative Token Awareness

Token discipline is not just functional—it’s visible. Files are sometimes written with compression-awareness as part of the authorial voice. This functions as both signalling (for humans) and priming (for AI). It implies boundaries, constraint-consciousness, and respect for compute.

---

## 7. Speculative Token Economy

Discussions about token discipline often drift into future forecasting:
- Token costs may scale with use
- Prompt size may become monetised directly
- Compression may be a first-class design axis

This repo assumes those futures are coming, and builds toward survivability.

---

## 8. Client-side Optimisation Concepts

In a token-priced world, frontend tooling could:
- Compress input before API calls
- Abstract reusable intent blocks
- Offer feedback on prompt weight

While not yet implemented, this repo treats those ideas as design constraints.

---

## 9. Compression Failure Modes

Overcompression leads to:
- Hallucinated logic
- Dropped nuance
- Misinterpreted structure

This document treats token discipline not as a blunt force rule, but as a dynamic edge—always managed, never solved.

---

## 10. Style as Efficiency

Compression is also visual:
- Use of headings, blocks, tables, and tight lists improves interpretation speed
- A consistent visual rhythm (e.g., section breaks, monospaced labels) reduces AI ambiguity
- Markdown is used tactically, not decoratively

---

**TL;DR:**  
Token discipline is epistemic hygiene. It's not about saving money—it's about keeping the machine usable, interpretable, and yours.
