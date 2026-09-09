# Contributing

This repository has exactly one contributor's work in it (mine), added over time, some of it drafted with AI assistance. This document is the mechanical checklist for adding to it — the policy those steps enforce lives in [`docs/PUBLICATION_BOUNDARY.md`](docs/PUBLICATION_BOUNDARY.md), and the rules for an AI collaborator specifically are in [`AGENTS.md`](AGENTS.md).

## Adding a new item

1. **Pick the right folder.** Don't create a new top-level folder for one item — `standards/`, `projects/`, `case-studies/`, or `docs/engineering-operating-system/` should already fit almost everything.
2. **Write it as a rewrite, not an export.** If the content started from a private source, the test is in `docs/PUBLICATION_BOUNDARY.md`.
3. **Run the checklist** in `docs/PUBLICATION_BOUNDARY.md` against the actual final text.
4. **Commit locally** with a message stating what was added.
5. **Review before publishing.** A local commit is not publication — see `AGENTS.md`'s publish-approval note. Pushing to a live remote is always a separate, deliberate step.

## Style

- Prefer plain Markdown over embedded HTML.
- Prefer describing a real result over claiming an unmeasured one.
- Keep each addition self-contained enough that a reader doesn't need private context to understand it — if it only makes sense with knowledge of the private repository, it isn't ready yet.

## Reporting a problem with existing content

Since this is a personal repository rather than a maintained open-source project, there's no issue template yet. If something here turns out to be wrong or should not have been published, that's a same-day fix, not a queued ticket.
