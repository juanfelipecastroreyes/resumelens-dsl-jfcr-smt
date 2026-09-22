# AI Usage Log — ResumeLens DSL

This document records the key design decisions and instructions developed
with AI assistance (Claude) during this project, and how those decisions
were verified before being adopted.

## Scope of AI assistance

1. **Conceptual framing** — situating grammars, EBNF, and textX-based DSL
   implementation within the formal language theory covered in this course.
2. **Draft generation** — proposed structures (grammar categories, field
   sets, documentation) produced as a starting point for review, revision,
   or rejection, never adopted without evaluation.

## Verification methodology

- **Requirement traceability.** Every proposed structure is checked against
  the assignment specification directly, not accepted on the AI's authority.
- **Conceptual consistency.** New material is evaluated against material
  already mastered (automata theory) for internal consistency before being
  relied on.
- **Executable verification.** Grammar and parser correctness is confirmed
  by running textX against valid and invalid `.resume` cases and checking
  the accept/reject behavior directly, not by inspection alone.
- **Independent justification.** Design decisions are retained only if they
  can be defended without reference to the AI's original explanation, since
  the design must be presented and defended independently in class.

## Key decisions

| Date | Instruction | Decision reached | Verification |
|---|---|---|---|
| 2026-09-22 | Requested a proposed field set for the seven required grammar categories | Adopted field table distinguishing `Skill` (informal tag) from `Qualification` (normalized, with proficiency level), per assignment Section 3 | Cross-checked against the assignment's own parse-tree and Markdown output examples |

<!-- Add a new row only for decisions that shape the grammar's structure or
     the project's approach — not routine or incremental edits. -->
