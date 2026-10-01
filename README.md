# resumelens-dsl-jfcr-smt

## Project description

This repository implements the Domain-Specific Language (DSL) used internally
by **ResumeLens** to represent candidate résumé profiles. ResumeLens ingests
raw résumés, extracts structured candidate information from them, and needs
a formal, machine-readable representation of that information before it can
be validated and rendered for human review. This DSL is that representation:
it is defined with an EBNF grammar, implemented with [textX](https://textx.github.io/textX/),
and paired with tooling that parses a `.resume` file, validates its
structure, and generates a human-readable Markdown visualization of the
parsed candidate profile.

## Team

| Name | GitHub |
|---|---|
| Juan Felipe Castro Reyes | [@juanfelipecastroreyes](https://github.com/juanfelipecastroreyes) |
| Sebastian Mejía | [@Sebastian-mejia2023](https://github.com/Sebastian-mejia2023) |

## Language

A `.resume` file describes a single candidate profile as a sequence of
labeled blocks:

- `personal` — the candidate's name and location
- `contact` — email, GitHub username, and an optional phone number
- `experience` (repeatable) — a professional experience entry
- `education` (repeatable) — an education record
- `skill` (repeatable) — an informal skill tag
- `qualification` (repeatable) — a normalized skill with a proficiency level
  (`Beginner`, `Intermediate`, or `Expert`)
- `classification` — the final candidate profile classification

`personal`, `contact`, and `classification` are mandatory and appear exactly
once; `experience`, `education`, `skill`, and `qualification` are optional
and repeatable. The full formal specification (terminals, non-terminals, and
EBNF rules) lives in [`docs/grammar.md`](docs/grammar.md), and the classes
textX derives from the grammar are documented in
[`docs/metamodel.md`](docs/metamodel.md).

## Project structure

```
resumelens-dsl-jfcr-smt/
├── README.md
├── requirements.txt
├── grammar/
│   └── resume.tx            # textX grammar implementing the DSL
├── src/
│   ├── parser.py             # parses a .resume file and prints its model
│   ├── validator.py          # validates a .resume file against the grammar
│   └── markdown_generator.py # parses a .resume file and writes a Markdown profile
├── examples/                 # sample .resume files (valid, full profiles)
├── output/                   # generated Markdown output for each example
├── docs/
│   ├── grammar.md            # EBNF specification and design decisions
│   ├── metamodel.md          # textX-generated classes and relationships
│   ├── ai-usage.md           # log of AI-assisted decisions and how they were verified
│   └── diagrams/             # parse-tree diagrams for each example
└── tests/
    ├── valid/                # additional valid .resume cases
    └── invalid/               # .resume cases textX must reject, with the error they exercise
```

## Requirements

- Python 3.10+
- [textX](https://pypi.org/project/textX/) (listed in `requirements.txt`)

## Installation

```
git clone https://github.com/juanfelipecastroreyes/resumelens-dsl-jfcr-smt.git
cd resumelens-dsl-jfcr-smt
pip install -r requirements.txt
```

## Running the parser

```
python src/parser.py examples/resume_01.resume
```

To validate a file without printing its full model:

```
python src/validator.py examples/resume_01.resume
```

## Generating the Markdown visualization

```
python src/markdown_generator.py examples/resume_01.resume
```

This prints the generated Markdown to the terminal and writes it to
`output/resume_01.md`. Run it against `resume_02.resume` and
`resume_03.resume` to regenerate the other two example outputs.

## Example profiles

- **`resume_01.resume`** — a full backend-developer profile exercising
  repeated blocks: two experiences, one education record, two skills, and
  two qualifications.
- **`resume_02.resume`** — a minimal data-analyst profile with only the
  mandatory blocks (`personal`, `contact`, `classification`) and no phone
  number, experiences, education, skills, or qualifications.
- **`resume_03.resume`** — an extended machine-learning-engineer profile
  with three experiences, two education records, three skills, two
  qualifications, and the optional `phone` field.

## Authors

Juan Felipe Castro Reyes and Sebastian Mejía, for the *Computación y
Estructuras Discretas III* course (TextX / DSL assignment).
