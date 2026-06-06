# Vault Principles

The rules that govern the vault. Before writing any note, check here. The system stays useful at 5,000 notes for the same reason it worked at 50 — consistent constraints applied from the start.

---

## What Gets Noted

**Note:**
- How a concept clicked, in your own words — especially confusing, foundational, or nuanced ideas
- Mental models and analogies you constructed
- Patterns worth recognising — not syntax, but recurring behaviours and structures
- Project ideas triggered by something you learned
- Observations and open research questions

**Skip:**
- Syntax — use documentation or a search engine
- Content the course or tutorial already wrote down
- Verbatim summaries of what an instructor said

---

## Workflow

```
Learn → Code along → Something clicks or breaks → Open Obsidian → One note per concept
```

Most sessions produce no note. Some produce several. Both are correct.

---

## Note Format

Every concept note follows this structure:

```
What is it
Why it matters
Example in my own words
```

Add sections only when the concept genuinely requires them.

**Code rule:** Only include code if removing it would make the note unclear. When code is included, reduce it to the minimum lines that demonstrate the point. A note that is entirely code with no prose is a poor note.

---

## Linking Rules

Full linking rules — MOC hierarchy, YAML schemas, the single-responsibility rule, crossover notes, and exceptions — live in `VAULT_DESIGN.md`. That is the canonical reference.

Summary:
- Concept notes link **up** to one MOC parent via `MOC Parent:` in YAML
- MOCs link **down** to their children via `Children:` in YAML and in the note body
- Crossover notes stay in their primary MOC; the secondary MOC gets a `## Practical Application` pointer
- `#Observation` and `#ResearchQueue` are the only note types permitted to link to two MOC parents

	# **Doing this manually creates system overhead, use Data view to link children in MOC.** 
	
When in doubt about any linking decision, open `VAULT_DESIGN.md`.

---

## Status Promotion

Every `#Concept` and `#Bug` note starts as `#Seedling`. Promotion is triggered by use, not by confidence.

| From | To | Trigger |
|---|---|---|
| `#Seedling` | `#Growing` | Applied or encountered the concept outside the original lesson |
| `#Growing` | `#Solid` | Can explain it without re-reading the note; seen it in a real context |

For `#CourseProject` notes: `#Starting` → `#Working` → `#Finished` as work progresses.

---

## Tag System

Every note carries two tags: a **type** and a **status** (where applicable).

### Type Tags

| Tag | Use |
|---|---|
| `#Concept` | How something works |
| `#Bug` | A problem encountered, diagnosed, and fixed |
| `#Pattern` | A behaviour or structure that recurs across contexts |
| `#CourseProject` | A project built as part of a course |
| `#ProjectIdea` | An original idea to build |
| `#Observation` | Something noticed in passing — closed, no follow-up required |
| `#ResearchQueue` | An open question requiring further investigation |
| `#MOC` | A hub note — not a concept note |

### Status Tags

**Concepts and Bugs:** `#Seedling` → `#Growing` → `#Solid`

**Course Projects:** `#Starting` → `#Working` → `#Finished`

MOC, Pattern, Observation, ResearchQueue, and ProjectIdea notes carry no status tag.

---

## Note-Type Rules

### Observation Notes
Parent MOC: `[[Interesting Observations - (MOC)]]`. These are closed — something noticed while doing something else, written down and left.

Required at the top of the body:
```
Why this is interesting: [one sentence]
```

### Research Queue Notes
Parent MOC: `[[Research Queue - (MOC)]]`. These are open — a gap in understanding that needs follow-up.

Required at the top of the body:
```
Why this is interesting: [one sentence]
Open question: [what specifically needs to be understood]
```

Without these lines, the note loses its purpose the moment you step away from it.

**Dual-type case:** A ResearchQueue note that originated as an Observation carries both types in YAML. See `VAULT_DESIGN.md` for the exact schema.

### MOC Notes
An MOC is not an index. Every MOC must include a short paragraph explaining how its children relate to each other. A list of links with no prose is not a hub.

Required structure:
```markdown
One paragraph: what this domain covers and how the notes relate.

## Notes
- [[Note A]] — one-line description
- [[Note B]] — one-line description

## Practical Application
- See [[CrossoverNote]] for [what it demonstrates in this domain]
```

### Course Project Notes
Every CourseProject note must have a goal statement and a checklist before work begins.

```markdown
**Goal:** [one sentence — what is being built and why]

**Checklist:**
- [ ] Component or step
```

Without this, returning to a half-started project means reconstructing the intent from scratch.

### Pattern Notes
A Pattern note captures a recurring behaviour or structure, not an explanation of how a single concept works. It is about recognition across contexts.

Required at the top:
```
Pattern: [one sentence describing what recurs]
Seen in: [list of contexts]
```

### Project Idea Notes
A ProjectIdea note captures an original build idea with enough detail to re-enter it cold.

Required structure:
```markdown
**Idea:** [one sentence]
**Triggered by:** [what lesson or concept sparked it]
**Rough plan:** [bullet list, even if vague]
```

These notes typically belong in a separate project vault once work begins. One note here is sufficient to record the idea and its origin.

---

## Vault Home Rule

Each domain has one home note at its root (e.g. `Python Home.md`). It links to every MOC in the domain and nothing else. When a second domain is added, create a vault-level `Home.md` linking to all domain homes.

---

## Templates

All templates live in `Principles-Templates/Templates/`. One template per note type. Delete anything that does not apply to the specific note. If a new note type is added, define its constraints here and add its schema to `VAULT_DESIGN.md` before creating notes of that type.
