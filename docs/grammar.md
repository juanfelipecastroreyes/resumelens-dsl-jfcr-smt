# Grammar Specification — ResumeLens DSL

## 1. Design overview

The DSL represents a candidate résumé profile as produced by ResumeLens. The
language groups candidate information into seven categories, chosen to cover
the minimum structure required by the assignment: personal information,
contact information, professional experience, education, skills, normalized
qualifications, and the classification result.

### 1.1 Fields per category

| Category | Fields | Repeatable? |
|---|---|---|
| **PersonalInfo** | `name`, `location` | No — one per resume |
| **Contact** | `email`, `phone` (optional), `github` | No — one per resume |
| **Experience** | `position`, `company`, `years`, `description` | Yes — zero or more |
| **Education** | `institution`, `degree`, `description` | Yes — zero or more |
| **Skill** | `name` | Yes — zero or more |
| **Qualification** | `name`, `level` | Yes — zero or more |
| **Classification** | `label` | No — one per resume |

### 1.2 Design decisions

- **Skill vs. Qualification.** These two categories look similar but serve
  different purposes. `Skill` is a raw, informal tag extracted directly from
  the résumé text (just a `name`, e.g. `"Python"`). `Qualification` is the
  *normalized* version explicitly requested by the assignment (Section 3:
  "normalized qualifications") — a skill that ResumeLens has processed into a
  structured form with a proficiency `level` (e.g. Beginner, Intermediate,
  Expert).
- **`years` in Experience.** Kept as a single field (matching the assignment's
  own parse-tree example in Section 8) rather than splitting into
  `start_year`/`end_year`, to keep the first version of the grammar simple.
  This can be revisited if a more precise date range is needed.
- **`phone` as optional in Contact.** The assignment's own examples only show
  `email` and `location`/`github` for contact info, so `phone` was added as an
  optional field rather than mandatory, since not every résumé will include
  it.

<!-- TODO: Section 2 — Terminals -->

<!-- TODO: Section 3 — Non-terminals -->

<!-- TODO: Section 4 — EBNF rules -->
