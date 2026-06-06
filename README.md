# Obsidian Knowledge Base — Learning Vault

A structured knowledge base built alongside learning programming languages. Every note earns its place, every link is intentional, and the system is designed so any topic can be re-entered months later without losing context.

---
## Context

This started as a personal problem — I wanted to learn Python seriously and couldn't find a note-taking approach that didn't eventually collapse into a graveyard of disconnected files. So before writing any actual notes, I spent 3 days designing the system that would hold them.

I was 17 when I built this, with no prior exposure to PKM tools or frameworks. Everything here came from thinking through failure modes and other styles of questioning: what makes a note useless, what makes a graph unnavigable, what makes a system require more upkeep than it's worth.


The Python folder is a working demo. The vault grows as the learning does — the architecture is designed to hold at any size.

For more context, refer to  `About.md`

## Quick Start

1. Clone the repo and open the folder in Obsidian via **File → Open folder as vault**
2. Read `PRINCIPLES.md` (philosophy) and `VAULT_DESIGN.md` (architecture)
3. Browse `Python/` to see a working example
4. Use a template from `Principles-Templates/Templates/` to write your first note

---

## What This Is

An Obsidian vault built around four core ideas:

- **MOCs (Maps of Content)** — hub notes that organise a domain and provide a consistent re-entry point
- **Typed notes** — every note declares its type (`#Concept`, `#Bug`, `#Pattern`, etc.) so its role is always clear
- **Bidirectional YAML linking** — concept notes point up to their MOC; MOCs list their children; related notes link sideways. The graph is a byproduct of structure, not the goal. The graph comes into play functionally when relearning, revisiting or tracing paths is required. If that is the case simply turn on arrows, place your cursor over an MOC and watch the path unfold.
- <img width="1448" height="1086" alt="img" src="https://github.com/user-attachments/assets/d2129117-2bbf-4d0c-9fe1-18a25278e49a" />

- **Written principles** — explicit rules governing what gets noted, how notes are written, and how the system scales

## What This Is Not

This is not a syntax database, or a course transcript. It is a record of how understanding developed — what clicked, what confused, what needed more work. The linking architecture means every topic has a defined entry point, so returning after a gap means picking up from a specific note rather than starting over.

---

## How to Read This Repo

| File              | Contents                                                                 |
| ----------------- | ------------------------------------------------------------------------ |
| `PRINCIPLES.md`   | What gets noted, note-writing format, status system, and note-type rules |
| `VAULT_DESIGN.md` | MOC hierarchy, YAML schemas, linking rules, tag system, and health check |
| `Python/`         | A mini-working example — real notes, real MOCs, real linking             |
| `Templates/`      | One template per note type to get started                                |

Start with `VAULT_DESIGN.md` for the architecture. Start with `PRINCIPLES.md` for the reasoning. Go straight to `Python/` to see it in practice.

---

## Why It's Built This Way

Most note-taking systems degrade because they have no enforced rules. Notes accumulate without structure, links multiply without meaning, and the system becomes harder to use than simply starting from scratch. This vault has explicit constraints at every level — what qualifies as a note, how notes connect, when a note is considered understood — so it remains navigable as it grows.

---

## Tips

- Enable arrows in Obsidian's graph view, then hover over an MOC to retrace your steps.
- Assign distinct colours to different domains (Python, JavaScript, etc.) in graph settings
- Run the vault health check weekly — the criteria are in `VAULT_DESIGN.md`
- When in doubt about a linking or tagging decision, `PRINCIPLES.md` and `VAULT_DESIGN.md` are the reference
