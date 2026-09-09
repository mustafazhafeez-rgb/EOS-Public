# Agent Instructions

This file is for any AI collaborator (this one or a future one, in this session or a new one) working on this repository. Read this before adding, editing, or removing anything.

## The one rule that overrides everything else here

**Read [`docs/PUBLICATION_BOUNDARY.md`](docs/PUBLICATION_BOUNDARY.md) before touching any content file.** It is not background reading — it is the acceptance test every change in this repository must pass before it is committed, let alone published.

## What you have standing authority to do

- Add, edit, or reorganize files **inside this repository's own root** (`C:/Users/musta/eos-public`), consistent with the Publication Boundary.
- Create local commits.
- Propose new folders, restructure existing placeholder content, and improve this repository's own documentation about itself.

## What you do not have standing authority to do, ever, without a separate and explicit instruction for that specific action

- **Publish anything.** Adding a git remote, running `git push`, or using the GitHub API/`gh` CLI to create or update a live, public repository is **not** implied by "build," "update," "add to," or "improve" this repository. It requires its own explicit go-ahead, named as such, every time.
- **Copy content from the private knowledge base or the Agent Gateway codebase directly into this repository.** Reading either for research is fine (this domain is registered as allowed to read `PERSONAL_KNOWLEDGE` and `GATEWAY_INFRASTRUCTURE`); writing their content here verbatim is not — see the Publication Boundary's "nothing enters by copying" rule.
- **Perform a broad re-audit of the private repository.** A specific, narrow audit question about one candidate addition is fine; re-deriving the whole boundary/architecture question that `docs/PUBLICATION_BOUNDARY.md` already answers is not — that work has been done once and should be extended, not repeated.
- **Migrate the knowledge base in bulk**, or add more than one real content item in a single pass without the human reviewing each one. Grow this repository the way the private one grows itself: one reviewed addition at a time, not a batch import.

## How to add something

1. Identify the specific private source material (if any) this addition is derived from.
2. Draft the public version as a **rewrite**, not an excerpt — see the Publication Boundary for the difference.
3. Run the practical checklist in `docs/PUBLICATION_BOUNDARY.md` against the actual drafted text, not against your intent.
4. Place it in the correct existing folder (`standards/`, `projects/`, `case-studies/`, `docs/engineering-operating-system/`) rather than inventing a new top-level folder for one item.
5. Commit locally, with a message that says what was added and which private source (if any) it was derived from — for the human's own later review, not for public display.
6. Stop there. Publication is a separate, explicit, later decision.

## If you are ever unsure

Default to **not adding it yet**, and say so plainly, rather than resolving the ambiguity yourself. This mirrors the private knowledge base's own standing discipline: a documented "not yet, and here's what would change that" is a complete and acceptable answer.
