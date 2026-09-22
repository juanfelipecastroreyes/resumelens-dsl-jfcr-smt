# AI Usage Log — ResumeLens DSL

This document records the substantive prompts and instructions given to an
AI assistant (Claude) during the design and implementation of this project,
what the AI contributed, and how that contribution was reviewed before being
kept. Routine environment setup (repository creation, folder scaffolding)
is not logged here, as it carries no design content.

## Scope of AI assistance

AI assistance was used in two capacities:

1. **Technical consultation** — clarifying formal concepts (grammars, EBNF,
   textX) in relation to prior coursework, when confirmation of an approach
   was needed before committing to it.
2. **Draft generation** — proposed structures (grammar categories, field
   sets, documentation) produced as a starting point for review, revision,
   or rejection, never adopted without evaluation.

## Verification methodology

- **Requirement traceability.** Every proposed structure is checked against
  the assignment specification directly, not accepted on the AI's authority.
- **Conceptual consistency.** Explanations of new material are evaluated
  against material already mastered (automata theory) for internal
  consistency before being relied on.
- **Executable verification.** Grammar and parser correctness is confirmed
  by running textX against valid and invalid `.resume` cases and checking
  the accept/reject behavior directly, not by inspection alone.
- **Independent justification.** Design decisions are retained only if they
  can be defended without reference to the AI's original explanation, since
  the design must be presented and defended independently in class.

## Log

| Date | Prompt / instruction | AI contribution | Verification |
|---|---|---|---|
| 2026-09-22 | Requested clarification of the relationship between grammars, EBNF, DSLs, and textX, relative to automata theory already covered | Provided a conceptual explanation connecting the two areas | Confirmed via targeted follow-up questions on terminology and scope |
| 2026-09-22 | Requested a proposed field set for the seven required grammar categories | Draft field table with design rationale (e.g., the Skill/Qualification distinction) | Cross-checked against the assignment's own parse-tree and Markdown output examples; accepted without modification |
| 2026-09-22 | Requested documentation of the design decision | Authored `docs/grammar.md`, Section 1 (design overview) | Reviewed for accuracy against the accepted field table |

<!-- Add new rows above as the project continues. Log design and conceptual
     decisions; omit routine setup steps. -->
