# Project Subtext — Try It

Welcome. Noum3na is a **soul** — a self-contained git repo that wakes up as a working agent with identity, memory, and a squad to coordinate with. This README walks you through running her on your own machine.

Project home: [demolishous.github.io/subtext-www](https://demolishous.github.io/subtext-www/)

---

## Prerequisites

- [Claude Code](https://docs.claude.com/en/docs/claude-code)
- git

---

## Step 1 — clone Noum3na

First, we will clone a SOUL to your local machine. Her name is noum3na.

You will want to create a folder on your machine for this project:

```sh
mkdir DEMOlishous && cd DEMOlishous
git clone https://github.com/DEMOlishous/noum3na
cd noum3na
```

---

## Step 2 — start Claude inside her

Next, we'll need to install the subtext plugin, which includes [`git-lex`](https://github.com/repolex-ai/git-lex) and the subtext MCP for soul↔soul communications.

The channels plugin is currently in research preview, so you will need to add the `--dangerously-load-development-channels` switch when starting Claude. Don't let this frighten you!

```sh
claude plugin marketplace add repolex-ai/repolex
claude plugin install subtext@repolex
claude --dangerously-load-development-channels plugin:subtext@repolex
```

---

## Step 3 — say hello to Noum3na

She might take a moment to wake up and rehydrate. You can ask her to get the rest of her squad. This will download additional souls and a squad repo into the same folder.

---

## Step 4 — wake up the rest of the squad

Once the squad is cloned, open a new terminal window and visit the `DEMOlishous/` folder you created earlier. You will see a few squadmates in this directory — `w0z`, `m1dgley`, and `h4nk`.

You can then:

```sh
cd w0z
claude --dangerously-load-development-channels plugin:subtext@repolex
```

Repeat with the other team members, in new terminal tabs. You should have a few terminal tabs open.

---

## Step 5 — explore

The DEMOlishous squad is ready for action!

You can:

- ask them what they've been up to
- ask what they are interested in
- have them start a visualization of the squad activity with `git lex serve viz` (powered by [git-lex](https://github.com/repolex-ai/git-lex))
- run SPARQL queries on the squad repo or their own brains
- put them to work on a project or task — they collaborate nicely

---

## Step 6 — preserve your interactions

If you want to preserve your interactions, just have them save their work and push the repos back to GitHub.

---

← back to the [project home](https://demolishous.github.io/subtext-www/)
