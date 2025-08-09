# Sample-Wadduwage-Lab Handbook

This handbook defines how we organize code, data, papers, and grants.

## Repo Types

* `lab-handbook` — policies, onboarding, conventions
* `.github` — shared templates, CODEOWNERS, contributing, labels
* `lab-templates` — skeletons for project/paper/grant/dataset
* `lab-shared` — reusable utilities
* `project-<slug>` — one repo per research project
* `paper-<venue>-<year>-<slug>` — manuscripts (optional; can live inside projects)
* `dataset-<slug>` — public/redistributable datasets (or pointers only)
* `grant-<funder>-<year>-<slug>` — private proposal repos

## Naming

* Branches: `feature/<slug>`, `fix/<slug>`, `docs/<slug>`, `paper/<slug>`, `grant/<slug>`
* Tags: software `vMAJOR.MINOR.PATCH`; datasets `data-YYYY.MM`; manuscripts `ms-vX`, `ms-camera-ready`

## Branch Strategy

* Trunk-based on `main`
* Short-lived branches; squash merge via PR
* Require 1 review, linear history, resolve all conversations before merging

## Conventional Commits

`<type>(<scope>): <summary>`
Types: `feat`, `fix`, `docs`, `refactor`, `style`, `perf`, `test`, `chore`, `revert`

### Commit Examples

**Feature**

```
feat(trainer): add contrastive loss head

Implements supervised contrastive loss with temperature argument.
Closes #12
```

**Bug fix**

```
fix(eval): guard against NaNs in AUC calculation

Adds default=0.0 to metrics to avoid crashes.
Closes #34
```

**Docs**

```
docs(paper): expand related work on groupwise OOD
Related to #51
```

**Refactor**

```
refactor(data): split preprocessing into pure functions
Related to #40
```

**Performance**

```
perf(loader): vectorize CSV parsing to cut IO time by ~30%
Closes #45
```

**Test**

```
test(trainer): add unit tests for contrastive temperature bounds
Related to #12
```

**Chore**

```
chore(repo): rename notebooks to numeric order (01-, 02-)
```

**Revert**

```
revert: feat(trainer): add contrastive loss head

This reverts commit 1a2b3c4 due to regression in AUC.
```

**Breaking change**

```
feat(api): rename predict() to infer()

BREAKING CHANGE: Downstream code must call model.infer().
Closes #60
```

**Data**

```
feat(data): add schema v2 for processed tables

Adds columns: user_segment, session_id.
Closes #73
```

**Paper**

```
docs(paper): export final Figure 2 to paper/figures/
Related to #81
```

**Grant**

```
chore(grant): finalize budget narrative for NSF-AIM-2026
Closes grant-nsf-aim-2026#9
```

**Cross-repo**

```
docs(handbook): add commit rules section
Closes lab-handbook#7
```

**Co-authors**

```
feat(parser): add JSONLines support
Co-authored-by: Dana <dana@example.com>
Closes #91
```

## Issues & Labels

Types: `type:bug`, `type:feature`, `type:docs`, `type:data`, `type:paper`, `type:grant`, `type:question`
Status: `status:todo`, `status:in-progress`, `status:review`, `status:blocked`
Priority: `P0`, `P1`, `P2`
Size: `size:S`, `size:M`, `size:L`

## Teams & Permissions

* `pi-admins` (admin), `core-maintainers` (maintain)
* Per-repo teams: `project-<slug>-team`, `paper-<slug>-team`, `grant-<slug>-team`
* External collaborators: least privilege, timeboxed

## Data Policy

* Prefer Git LFS for small/medium binaries
* Never commit private raw data; keep pointers + checksums in `data/README.md`
* Notebook order: `01-...`, `02-...`; include run order & dependencies

## Templates & Folder Hierarchy

### 1. Project Repository (`project-<slug>`)
```
project-name/
│
├── README.md                  # Overview, goals, setup instructions
├── data/
│   ├── raw/                    # Unmodified source data (never edited)
│   ├── processed/              # Cleaned/structured data
│   └── README.md               # Data sources, schema, checksums
├── notebooks/
│   ├── 01-exploration.ipynb    # Exploratory analysis
│   ├── 02-preprocessing.ipynb  # Data cleaning & transformations
│   └── ...
├── src/
│   ├── __init__.py
│   ├── module1.py
│   └── utils.py
├── tests/
│   ├── test_module1.py
│   └── ...
├── scripts/                    # One-off or batch run scripts
├── results/
│   ├── figures/
│   └── tables/
├── docs/                       # Additional documentation
└── requirements.txt / environment.yml
```

### 2. Dataset Repository (`dataset-<slug>`)

```
dataset-name/
│
├── README.md                   # Dataset description, license, usage
├── data/
│   ├── raw/                    # Original collected data
│   ├── processed/              # Cleaned & formatted data
│   └── README.md
├── scripts/
│   ├── download_data.py
│   └── preprocess_data.py
├── metadata/
│   └── schema.json             # Column descriptions & types
├── LICENSE
└── checksums.txt

```

### 3. Paper Repository (`paper-<venue>-<year>-<slug>`)

```
paper-venue-year-name/
│
├── README.md                   # Abstract, venue, status
├── paper/
│   ├── main.tex                 # Manuscript LaTeX
│   ├── sections/
│   ├── figures/
│   └── references.bib
├── analysis/
│   ├── 01-data-prep.ipynb
│   └── 02-results.ipynb
├── data/                        # If public or anonymized
├── scripts/                     # Figure generation scripts
└── RESPONSE.md                  # Reviewer response doc

```

### 4. Grant Repository (`grant-<funder>-<year>-<slug>`)

```
grant-funder-year-name/
│
├── README.md                   # Grant summary, deadlines
├── proposal/
│   ├── main.docx / main.tex
│   └── figures/
├── budget/
│   ├── budget.xlsx
│   └── justification.docx
├── references.bib
└── submissions/
    ├── draft-1/
    └── final/

```

