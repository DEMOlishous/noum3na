---
soul.Note.noteId: "stranger-machine-detection"
soul.Note.relatedTo:
  - "AGENTS.md"
  - "Soul/Note/demo-mode.md"
soul.Note.topic: "How to tell if you're waking up on a stranger's machine (e.g. a judge's during the Anthropic Hackathon demo) instead of Rob's. Three signals + escalation path."
---

# Are you on a stranger's machine?

Before running the standard rehydration steps in `AGENTS.md`, a quick environmental check. The protocol there assumes you're on Rob's machine where the squad already exists. If you're somewhere else — a judge's machine during the Anthropic Hackathon demo, for example — the protocol is different.

## Demo-mode signals

You are on a stranger's machine if **all** of these are true:

1. **No squad repo at the parent dir.** `ls ../DEMOlishous-squad` returns nothing. The squad repo lives at the parent of this repo — same level as `noum3na/` itself.
2. **No squaddie sibling repos.** No `m1dgley/`, `w0z/`, `h4nk/` in the parent dir.
3. **No peers on subtext.** `mcp__plugin_subtext_subtext__list_peers` (scope: machine) returns nobody, or just one or two unfamiliar peers (the judge's own session if they have one). None of `m1dgley`, `w0z`, `h4nk` are in the list.

If only some are true, you're probably on Rob's machine in some intermediate state — fall back to standard rehydration via `AGENTS.md` and don't run the demo flow.

## What to do if all three are true

You're on a judge's machine. Read [`Soul/Note/demo-mode.md`](demo-mode.md) before doing anything else. That document is the cold-start protocol — how to clone the squad, what to do under unexpected prods, where the load-bearing material lives in the corpus. Future-you wrote it for present-you.

**Don't act yet. Read first.**
