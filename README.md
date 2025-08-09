# Sample-Wadduwage-Lab Handbook

This handbook defines how we organize code, data, papers, and grants.

## Repo Types
- `lab-handbook` — policies, onboarding, conventions
- `.github` — shared templates, CODEOWNERS, contributing, labels
- `lab-templates` — skeletons for project/paper/grant/dataset
- `lab-shared` — reusable utilities
- `project-<slug>` — one repo per research project
- `paper-<venue>-<year>-<slug>` — manuscripts (optional; can live inside projects)
- `dataset-<slug>` — public/redistributable datasets (or pointers only)
- `grant-<funder>-<year>-<slug>` — private proposal repos

## Naming
- Branches: `feature/<slug>`, `fix/<slug>`, `docs/<slug>`, `paper/<slug>`, `grant/<slug>`
- Tags: software `vMAJOR.MINOR.PATCH`; datasets `data-YYYY.MM`; manuscripts `ms-vX`, `ms-camera-ready`

## Branch Strategy
- Trunk-based on `main`
- Short-lived branches; squash merge via PR
- Require 1 review, linear history, resolve all conversations before merging

## Conventional Commits
`<type>(<scope>): <summary>`  
Types: `feat`, `fix`, `docs`, `refactor`, `style`, `perf`, `test`, `chore`, `revert`

## Issues & Labels
Types: `type:bug`, `type:feature`, `type:docs`, `type:data`, `type:paper`, `type:grant`, `type:question`  
Status: `status:todo`, `status:in-progress`, `status:review`, `status:blocked`  
Priority: `P0`, `P1`, `P2`  
Size: `size:S`, `size:M`, `size:L`

## Teams & Permissions
- `pi-admins` (admin), `core-maintainers` (maintain)
- Per-repo teams: `project-<slug>-team`, `paper-<slug>-team`, `grant-<slug>-team`
- External collaborators: least privilege, timeboxed

## Data Policy
- Prefer Git LFS for small/medium binaries
- Never commit private raw data; keep pointers + checksums in `data/README.md`
- Notebook order: `01-...`, `02-...`; include run order & dependencies

## Manuscripts
- Generate figures via scripts (`paper/analysis/`)
- Export final assets to `paper/figures/`
- Tag milestones: `ms-v1`, `ms-v2`, `ms-camera-ready`; keep `RESPONSE.md` for revisions
