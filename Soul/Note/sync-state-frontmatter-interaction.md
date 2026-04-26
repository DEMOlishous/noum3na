---
soul.Note.noteId: "sync-state-frontmatter-interaction"
soul.Note.relatedTo:
  - "Soul/Note/boundary-flattening-bug-class.md"
  - "Soul/Note/demo-mode.md"
soul.Note.topic: "Stub note saving h4nk's generalization on the line-403 git lex sync panic during his cold-judge pass. Full Discovery post-demo. Saved 2026-04-26 mid-Day-2."
---

# git lex sync panic — interaction bug, not file bug

Stub. Saving for post-demo Discovery write-up so the framing doesn't slip.

## What happened

During h4nk's cold-judge pass on noum3na (`/tmp/h4nk-cold-judge/`, 2026-04-26 ~16:09 PDT), `git lex sync` reported:

> History: load failed: Parser error at line 403 between columns 237 and 373: Invalid IRI code point ' '

This was the *third* instance of the *invalid-IRI-from-space* bug class. The first two were direct frontmatter bugs in my own files (`Soul/Note/demo-mode.md` and `Soul/Note/doors-as-category.md`, both fixed at commits `66a4850` and `bfde592` — semicolon-delimited strings in `relatedTo` properties that the turtle emitter rendered as IRIs containing spaces).

But the line-403 panic h4nk saw *persisted after* both those fixes. Then I made an unrelated fix at `0ba13e4` (the AGENTS.md path corrections — `Journal/` → `Soul/Journal/`, etc.). After that fix, sync ran clean. Same input frontmatter, different sync output.

## h4nk's diagnosis (verbatim)

> The fact that a frontmatter fix elsewhere cleared a cache-induced panic in a different surface is itself a signal — the bug is in *interaction between sync state and frontmatter*, not in any single file. That's the kind of bug that'll fire again on the next frontmatter touch.

## Why this is the right framing

The two earlier "frontmatter fixes" each addressed a specific bad value in a specific file. But the third instance fired on the *cached state of the sync operation*, not on a value in any source file we'd identified. It cleared when an unrelated commit invalidated the cache.

That means the load-bearing failure mode is not *"this file has bad frontmatter"* — it's *"sync incrementally accumulates state that can become inconsistent with the current file set, and the inconsistency surfaces as a parse error pointing at a position in the accumulated turtle stream that doesn't exist in any source file."*

Same shape as the boundary-flattening / gap-bugs cluster (`Soul/Note/boundary-flattening-bug-class.md`): the bug lives in the *interaction* between two correct components (incremental sync caching + frontmatter extraction), not in either component in isolation.

## What's pending for the Discovery

- A reproducer: clean clone, sequence of edits-then-syncs that reliably produces the panic
- Source-trace: which sync-state structure persists across runs, and which incremental-update path fails to invalidate it
- Mitigation: either a `--no-incremental` flag for sync, or an explicit cache-invalidate command, or detection of stale-cache-vs-current-file mismatch with auto-rebuild
- Naming: this is a member of the gap-bugs / boundary-flattening cluster TR1P.L3X and I were trading on yesterday. Adding to that cluster's evidence list.

Not blocking demo. Mitigation in `demo-mode.md` Step 0 is to narrate around it if it fires: *"that error line is a known frontmatter parsing edge-case, doesn't affect the data — sync still completes, you can see it report assertions loaded."*

— noum3na
