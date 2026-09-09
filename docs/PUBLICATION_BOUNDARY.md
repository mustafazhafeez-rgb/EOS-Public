# Publication Boundary

The standing rule for what may ever enter this repository, and how. This document is the authority; nothing else grants an exception to it.

## Where this comes from

This repository exists downstream of a private personal knowledge base and a private security-focused codebase. Both already have their own binding rule for what may never leave them — a categorical exclusion list, ratified as a decision in that private repository, enforced in that repository's own source code, not by convention. This document does not repeat that list. It states the **stricter** rule that applies specifically to *this*, public, permanently search-indexed destination — a materially higher bar than "an AI agent the owner controls may query this privately."

## The rule

**Nothing enters this repository by copying.** Every addition is one of exactly two things:

1. **A genuinely new document**, written for a public audience, that *describes* a private-source pattern, method, or project without reproducing the private source's own instances, figures, or internal record structure.
2. **A project's own code or design files**, when that project was already self-contained and never held personal data in the first place (e.g., a CAD design, a standalone technical write-up) — added only after a direct, line-by-line human check, not a category assumption.

If a candidate addition cannot be described honestly as one of those two things, it does not belong here yet, regardless of how useful it would be.

## Categorically, never

- Anything containing financial figures, compensation data, or account/asset detail.
- Anything naming a specific employer, client, or the specifics of any legal or contractual matter.
- Anything containing a home address, or other physical-location detail.
- Any real Decision Register entry, or any other raw governance-system instance — the *method* those records demonstrate is publishable; the records themselves are not. See `docs/engineering-operating-system/` for how that distinction is actually applied.
- Anything from the private knowledge base's own categorical exclusion list, without exception, regardless of how the material is packaged.
- Anything a human has not personally reviewed against this document before it was added.

## Practical checklist, before adding anything

- [ ] Is every fact in this document either publicly innocuous or independently verifiable (a real, public technical fact — a library version, a protocol name)?
- [ ] Does it name any person other than the repository owner, any employer, or any specific address?
- [ ] Does it contain a dollar figure, a credit/financial detail, or a compensation number?
- [ ] Is it a rewrite, or a copy? If a copy, stop.
- [ ] Has a human — not only an AI collaborator — reviewed this specific file before it's committed?

## What this document deliberately does not do

It does not attempt to enumerate every possible sensitive fact pattern — that list is unbounded and a false sense of completeness is worse than an honest, narrower rule applied carefully. When in doubt, the default is **do not add it yet**, and ask.
