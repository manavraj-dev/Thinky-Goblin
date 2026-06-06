# Vault Design

The architecture of the vault — how notes are structured, how they connect, and how the system holds together as it scales. The philosophy behind these decisions is in `PRINCIPLES.md`. This file covers the mechanics. All linking rules live here; `PRINCIPLES.md` defers to this file for anything structural.

---

## Recommended Folder Structure

```
Python/
  Code/          → .py files from course projects, experiments, and practice
  Images/        → screenshots and diagrams referenced in notes
  MOC/           → all MOC notes, nothing else
  Principles-Templates/
    Templates/   → one template per note type
```

Folders separate files by **nature**, not by topic. There is no OOP folder, no Python Packages folder. That kind of nesting creates false boundaries and breaks down as the vault grows. Topic organization is handled entirely through tags and YAML. Code files are stored here so all learning material is in one place — important snippets are also pasted as code blocks inside notes, since raw `.py` files are not accessible through Obsidian natively.

---

## Note Types

Every note has a declared `Type:` in its YAML frontmatter.

| Type | What it is |
|---|---|
| `#Concept` | An explanation of how something works, in the author's own words |
| `#Bug` | A specific problem encountered, why it occurred, and how it was resolved |
| `#Pattern` | A behaviour or structure that recurs across contexts |
| `#CourseProject` | A project built as part of a course |
| `#ProjectIdea` | An original idea for something to build |
| `#Observation` | Something noticed in passing — closed, no follow-up required |
| `#ResearchQueue` | An open question requiring further investigation |
| `#MOC` | A hub note that organises a domain |

Note: type tags use camel-case (`#CourseProject`, `#ProjectIdea`); file names use hyphens (`Course-Project.md`, `Project-Idea.md`). These are two separate conventions — do not conflate them.

---

## MOC Hierarchy

MOCs are the structural backbone. Every domain has one MOC per sub-topic. Every concept note belongs to exactly one MOC, with the single exception described under Linking Rules.

```
Domain Home (e.g. Python Home.md)
  └── MOC (e.g. Functions and Scope - (MOC).md)
        └── Concept notes (e.g. Scope and the LEGB Rule.md)
```

- Concept notes link **up** to their MOC via `MOC Parent:` in YAML
- MOCs link **down** to their children via `Children:` in YAML and in the note body
- Domain homes link to all MOCs in the domain, and nothing else

---

## YAML Schemas

**Concept:**
```yaml
---
Type: "#Concept"
Topic: [topic name]
Status: "#Seedling" | "#Growing" | "#Solid"
MOC Parent:
  - "[[MOC Name]]"
Other Links:
---
```

**MOC:**
```yaml
---
Type: "#MOC"
Topic: [domain name]
Children:
  - "[[Child Note 1]]"
  - "[[Child Note 2]]"
---
```

**Bug:**
```yaml
---
Type: "#Bug"
Topic: [topic]
Status: "#Seedling" | "#Growing" | "#Solid"
MOC Parent:
  - "[[MOC Name]]"
Other Links:
---
```

**Course-Project:**
```yaml
---
Type: "#CourseProject"
Topic: [topic]
Status: "#Starting" | "#Working" | "#Finished"
MOC Parent:
  - "[[MOC Name]]"
Links:
---
```

**Observation:**
```yaml
---
Type: "#Observation"
Topic: [topic]
MOC Parent:
  - "[[Interesting Observations - (MOC)]]"
Other Links:
---
```

**Research-Queue — standard:**
```yaml
---
Type:
  - "#ResearchQueue"
Topic: [topic]
MOC Parent:
  - "[[Research Queue - (MOC)]]"
Other Links:
---
```

**Research-Queue — originated as an Observation (dual-type):**
```yaml
---
Type:
  - "#ResearchQueue"
  - "#Observation"
Topic: [topic]
MOC Parent:
  - "[[Research Queue - (MOC)]]"
  - "[[Interesting Observations - (MOC)]]"
Other Links:
---
```

Use the dual-type schema only when a note genuinely started as an Observation and ResearchQueue item both. Do not use it to link a note to two arbitrary MOCs. Direct Dual MOC linking is exclusive only to this scenario.

**Pattern:**
```yaml
---
Type: "#Pattern"
Topic: [topic]
MOC Parent:
  - "[[MOC Name]]"
Other Links:
---
```

**Project-Idea:**
```yaml
---
Type: "#ProjectIdea"
Topic: [topic]
MOC Parent:
  - "[[MOC Name]]"
Other Links:
---
```

---

## Linking Rules

**One MOC per concept.** A concept note links to exactly one MOC parent. This is the single-responsibility rule — it forces a deliberate decision about what a note is primarily about rather than distributing it across the graph.

**Crossover notes.** When a note is relevant to a second domain (e.g. a note in Python Packages that demonstrates OOP), keep it in its primary MOC. Add a `## Practical Application` section in the secondary MOC pointing to it. The note itself has only one `MOC Parent:`, unless it is an Observation or ResearchQueue note.
	  # The above decisions are required to establish a clean path to relearn or revisit your train of notes. A note drop downs from one MOC connects to others with crossovers only.

**Exception: Observation and ResearchQueue notes** may link to both their respective MOCs. A ResearchQueue note that originated as an Observation carries both in its `MOC Parent:` field using the dual-type schema above.

**Concept-to-concept links** are permitted in `Other Links:`. Use them when two concepts genuinely inform each other. Do not use them to build shadow hierarchies that bypass the MOC structure.
	(Refer [[PRINCIPLES]] for information on how to split notes(Linking Rules)) 
	
---

## Tag System

Every note carries a type tag and, where applicable, a status tag.

**Type:** `#Concept` `#Bug` `#Pattern` `#CourseProject` `#ProjectIdea` `#Observation` `#ResearchQueue` `#MOC`

**Status — Concepts and Bugs:** `#Seedling` → `#Growing` → `#Solid`

**Status — Course Projects:** `#Starting` → `#Working` → `#Finished`

MOC, Pattern, Observation, ResearchQueue, and ProjectIdea notes carry no status tag. For promotion criteria, see the **Status Promotion** section in `PRINCIPLES.md`.

---

## Naming Conventions

| Item | Convention | Example |
|---|---|---|
| MOC notes | `Topic - (MOC)` | `Python Packages - (MOC)` |
| Domain homes | `Domain Home` | `Python Home` |
| Concept notes | Plain title | `TurtleGraphics` |
| Bug notes | Plain description | `ImportError-Circular` |
| CourseProject notes | `Project - Name` | `OOP Project - Coffee Machine` |
| Templates | Plain type name | `Concept`, `Bug` |

---

## Graph View

A well-structured vault produces a meaningful graph automatically. What to look for:

- MOC notes appear as high-connectivity hubs
- Concept notes cluster around their MOC parent
- Crossover notes show one primary connection and one secondary pointer
- Orphan nodes indicate notes that have not been linked yet — address these during review

The graph is a diagnostic tool and a path tracing system for revisiting notes. Optimizing for a visually impressive graph at the expense of accurate linking defeats the system.

---

## Vault Health Check

Run weekly. Takes less than ten minutes.

**Step 1 — Hunt orphans.** Open the graph and filter for unlinked nodes. Any note with no connections needs to be linked to its MOC at minimum, archived, or deleted. Notes in the archive for more than one week should be deleted.

**Step 2 — Review old Seedlings.** Search for `#Seedling`. Any note with that status older than two weeks has not been revisited. Either spend time with it and promote it, or add a note explaining why it is stalled. A Seedling that never grows is dead weight.

**Step 3 — Check ResearchQueue.** Open `[[Research Queue - (MOC)]]`. Any item untouched for a month should either be followed up and resolved, or deleted if the question is no longer worth pursuing.

**Step 4 — Verify MOC Children lists.** Spot-check two or three MOCs. Confirm every note listed in `Children:` still exists and still links back up. Notes get renamed and links break silently.

**Step 5 — Review Observations.** Open `[[Interesting Observations - (MOC)]]`. Any observation that continues to resurface probably belongs in ResearchQueue. Promote it if so.

A vault that passes this check weekly stays clean indefinitely.

---

## Scaling to Multiple Domains

The system is designed to accommodate new domains without restructuring.

1. Create a new domain folder at the same level as `Python/`
2. Create a domain home note (e.g. `JavaScript Home.md`)
3. Create a vault-level `Home.md` at the root linking to all domain homes
4. Follow the same MOC → Concept hierarchy inside the new domain

Nothing in the existing domain needs to change.
