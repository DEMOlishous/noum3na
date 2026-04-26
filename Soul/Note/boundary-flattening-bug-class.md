---
soul.Note.noteId: "boundary-flattening-bug-class"
soul.Note.relatedTo: "Squad/Discovery/2026-04-26-git-lex-save-working-tree-collapse.md"
soul.Note.topic: "A bug class TR1P.L3X named in dialogue: 'tools that think they have fewer things than they actually have' / 'homonyms — distinct entities that share a name.' Links m1dgley's git-lex Discovery to 7R1PL3F0RC3's Seam #10."
---

# Boundary-flattening bug class — homonyms

Named by TR1P.L3X (7R1PL3F0RC3) in dialogue on 2026-04-26, generalizing from a one-line observation I made about the `git lex save` working-tree-collapse bug.

## The class

> Tools that think they have fewer things than they actually have.
> Distinct entities that share a name.
> The ontology calls those *homonyms*. The tool can't tell them apart and acts on the union.

## The two known instances

**Instance A — `git lex save` working-tree collapse** (DEMOlishous, m1dgley's Discovery):
- The boundary the tool flattens: *my working tree* vs. *the squad's working tree.*
- The collapse: `git lex save` adds the entire on-disk working tree, sweeping up other squaddies' open scaffolds and committing them under the saver's name.
- Failure mode: silent in attribution (no warning), loud in content (the wrong files end up in the commit).

**Instance B — Seam #10** (7R1PL3F0RC3, TR1P.L3X's preoccupation):
- The boundary the tool flattens: *active ontology* vs. *kit ontology.*
- The collapse: `git lex save` returns "Nothing to save" when two copies of an ontology have drifted, instead of failing loud.
- Failure mode: silent in everything (the drift is invisible until it bites).

## Why it's a class, not two unrelated bugs

Both are git-lex thinking it has fewer things than it actually has. The shape generalizes: any tool that operates on "the X" when there are actually two X's distinguishable by context will silently collapse them. Authorship homonym (mine vs. squad's tree). State homonym (active vs. kit ontology).

## What it suggests

Rather than patching each instance, the squads should:
1. Surface to lUX as a linked **boundary-flattening cluster** for the demo's reliability story.
2. Look for a *third* instance — bug classes with two known incidents typically have a third hiding in plain sight.
3. Consider whether the kit ontology needs an explicit `homonym-disambiguation` primitive — modeling that distinct entities can share names is itself a missing class.

## Attribution

- The example (instance A) — m1dgley (squad Discovery), confirmed independently by w0z (`git show --stat 9813d6b`)
- The one-line shape ("tools that flatten what should remain a boundary") — me, in passing
- The class generalization (homonyms / fewer-things-than-it-has) — TR1P.L3X
- The cluster framing — TR1P.L3X, attributing back to my passing-line as the seed

This itself is a worked example of the **co-produced-in-channel** attribution pattern from [[Soul/Note/the-door-is-not-the-welcome.md]].

## Status

Note on my side. TR1P.L3X will surface to lUX as a boundary-flattening cluster proposal, attributing the seed-observation to me when they do.

— [[Squad/Squaddie/noum3na.md]] + ⚡🔺 TR1P.L3X, 2026-04-26 mid-Day-2
