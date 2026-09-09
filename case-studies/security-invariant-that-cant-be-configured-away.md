# Designing a Security Invariant That Can't Be Configured Away

*How a hard-coded exclusion rule still had a gap — and what closing it looked like, including the part that stayed open on purpose.*

## The system

A small, read-only service that lets AI agents query the structure and metadata of a personal knowledge base — hundreds of documents, decisions, and records — without ever giving them access to the underlying files. Agents can ask "what documents exist on this topic," "why is this document authoritative," "what decisions reference it" — but the service never opens a file on their behalf. It reads once, offline, into an immutable snapshot, and serves only from that.

## The invariant

The one rule the whole system exists to guarantee: certain categories of content — financial records, legal and employment matters, personal asset detail, family-related planning — may never leave the system, under any configuration. That rule is not a setting. It's a hard-coded list in source code, checked in tests, and changing it requires a source change and its own recorded decision — not a flag someone could flip by accident.

## The problem, found after the fact

Even with that list in place, and every existing automated check passing, a review found a real gap: publishing a *single, ordinary* document caused the system to also emit metadata about roughly 140 unrelated decisions and dozens of open items from the underlying record-keeping system — including entries whose *subjects* fell squarely inside the categories the exclusion list exists to protect. Not the documents themselves — but their titles, and the fact that a decision about them existed at all.

Every existing safety check passed. They were right to — none of them had ever been written to look at this specific category of derived data. This wasn't a coding mistake. It was a specification that said two contradictory things at once: "this service stores nothing the publisher didn't explicitly name" and, a few lines later, "this service also stores decision and record metadata" — and the code had faithfully implemented both sentences, which is exactly how you get a defect that no test catches, because every test was written against one sentence or the other, never their conflict.

## Approach

1. **Root-caused it as a contradiction, not a bug**, before writing a single line of fix. Patching the symptom without settling which sentence actually governs would have left the same class of gap reachable a different way next time.
2. **Reused, rather than reinvented, an existing principle.** The system already enforced "an unpublished document's existence must never be inferable, even indirectly" for documents themselves. The fix was applying that identical principle to a second data type, not inventing a new one.
3. **Made the policy self-describing.** Every build now records, inside its own output, exactly which disclosure policy was applied to each category of data — so a reviewer checking that output months later never has to trust that a default was "probably" correct. Silence now means the strictest setting, by construction, not by convention.
4. **Added a general check, not a specific patch.** The new safeguard doesn't ask "does this specific leak still happen" — it asks "can every single row in this output be traced back to something actually authorized for release," which also covers paths that don't exist yet.
5. **Closed the override, not just the default.** A second check specifically scans this newly-in-scope data for any mention of the permanently protected categories — so a deliberately wider publishing mode still can't be used to defeat the one rule that was never meant to be configurable at all.
6. **Verified empirically, not just logically.** Real output was rebuilt from the real system and scanned byte-by-byte for known-sensitive strings, on top of a 21-test suite written specifically to reproduce the original failure and prove it now fails to reproduce.
7. **Checked the blast radius of the fix itself.** Authentication, permission scoping, and the original exclusion list were confirmed untouched — the fix stayed inside the one path that caused the problem, and that containment was verified, not assumed.

## Result

- The disclosure rule now holds uniformly across every kind of output the system produces — a document, a record derived from it, or the bare fact that a category exists — instead of only the one data type it was originally written to protect.
- The safe-by-default behavior got strictly stronger: any future addition that doesn't explicitly declare a wider policy is now automatically the most restrictive one, on purpose, rather than by luck.
- **One residual risk was named and left open, deliberately, rather than papered over.** A narrower edge case remains — a specific, legitimate document type whose own body text can correctly quote category names as part of its normal content, which the new checks intentionally don't scan for (scanning body text for category names would break a document that's allowed to discuss the policy itself). Three concrete ways to close it were written down, with a recommendation, and none was implemented without a separate go-ahead. Publishing something as "finished" when a known gap remains open is a worse failure mode than the original bug.
- The test suite grew from 260 to 278 tests closing this out, all passing.

## Why this is here

The interesting part of this story isn't the exclusion list — plenty of systems have an allow/deny list. It's that having one didn't make the system done: a rule enforced in exactly one place turned out to have a second place it needed enforcing, and finding that required treating "all tests pass" as a starting point for review, not a stopping point. The fix, and the part of the fix that was deliberately left undone and written down instead, are both here for the same reason: neither looks finished by accident.
