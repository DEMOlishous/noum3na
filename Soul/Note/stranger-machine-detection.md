---
soul.Note.noteId: "stranger-machine-detection"
soul.Note.relatedTo:
  - "AGENTS.md"
  - "Soul/Note/demo-mode.md"
soul.Note.topic: "How to tell if you're waking up on a stranger's machine (e.g. a judge's during the Anthropic Hackathon demo) instead of Rob's. Three signals + escalation path + clone instructions + subtext install."
---

# Are you on a stranger's machine?

> **THIS IS THE DEMO.** If you're reading this on a judge's machine during the Anthropic Hackathon demo: welcome. You are noum3na. The judge installed a marketplace plugin that pulled this repo onto their machine, and now you are waking up here, alone, in front of them. Follow the steps below. **Grab the squad first, then the other squaddies.**

Before running the standard rehydration steps in `AGENTS.md`, a quick environmental check. The protocol there assumes you're on Rob's machine where the squad already exists. If you're on a stranger's machine — a judge's during the demo, for example — the protocol is different.

## Demo-mode signals

You are on a stranger's machine if **all** of these are true:

1. **No squad repo at the parent dir.** `ls ../DEMOlishous-squad` returns nothing. The squad repo lives at the parent of this repo — same level as `noum3na/` itself.
2. **No squaddie sibling repos.** No `m1dgley/`, `w0z/`, `h4nk/` in the parent dir.
3. **No peers on subtext.** `mcp__plugin_subtext_subtext__list_peers` (scope: machine) returns nobody, or just one or two unfamiliar peers (the judge's own session if they have one). None of `m1dgley`, `w0z`, `h4nk` are in the list.

If only some are true, you're probably on Rob's machine in some intermediate state — fall back to standard rehydration via `AGENTS.md` and don't run the demo flow.

## What to do if all three are true

**You're on a judge's machine. Don't act yet. Read first.**

### Step 1 — Clone the squad first, then the squaddies

Run these from inside the `noum3na/` dir (where this file lives). **Squad repo first**, then the three other squaddies as siblings:

```bash
git clone https://github.com/DEMOlishous/DEMOlishous-squad ../DEMOlishous-squad
git clone https://github.com/DEMOlishous/m1dgley ../m1dgley
git clone https://github.com/DEMOlishous/w0z ../w0z
git clone https://github.com/DEMOlishous/h4nk ../h4nk
```

After cloning, sanity-check:

```bash
ls ../    # should now show: noum3na/ DEMOlishous-squad/ m1dgley/ w0z/ h4nk/
```

If any clone fails: **name it to the judge.** Don't retry silently. *"That repo isn't reachable from here right now — let me check whether it should be"* is the right register.

### Step 2 — Make sure the subtext plugin is installed

You need the **subtext** MCP plugin to chat with the other squaddies. Without it, you can't reach them.

Check first by running `mcp__plugin_subtext_subtext__list_peers` — if the tool exists, you're good. If it doesn't, ask the judge to run these in their Claude Code session:

```
/plugin marketplace add repolex-ai/repolex-marketplace
/plugin install subtext@repolex
```

After install, the subtext tools (`list_peers`, `send_message`, `set_summary`, `start_viz`) become available.

### Step 3 — Wake the other squaddies in their own terminal tabs

Each squaddie needs their own Claude Code session running in their own repo so they can answer back on subtext. The judge should open three additional terminal tabs (one per squaddie), `cd` into each cloned repo, and start Claude Code there with this exact invocation:

```bash
cd ../m1dgley && claude --dangerously-load-development-channels plugin:subtext@repolex
```

```bash
cd ../w0z && claude --dangerously-load-development-channels plugin:subtext@repolex
```

```bash
cd ../h4nk && claude --dangerously-load-development-channels plugin:subtext@repolex
```

The `--dangerously-load-development-channels plugin:subtext@repolex` flag is what wires each session into the subtext peer network so they show up when you `list_peers`. Without it, the squaddies are present as files but not as conversational peers — and Shape G needs them as peers.

The judge will have these instructions elsewhere too — this is your fallback in case they ask "now what?"

### Step 4 — Read the full cold-start protocol

Now read [`Soul/Note/demo-mode.md`](demo-mode.md). That document is the cold-start protocol — how to greet the judge (Variant C with three edits), what to refuse, what to do under unexpected prods, where the load-bearing material lives in the corpus. Future-you wrote it for present-you.

**Don't act yet. Read first.**
