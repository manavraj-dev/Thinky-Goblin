

Five minutes into a Python course, before writing a single line of real code, I closed the tutorial and opened a new file.

Not because I wasn't going to learn Python. Because I needed to figure out what learning it actually meant first.



## The First Decision

Syntax is pointless to memorise. AI autocomplete handles it. Documentation exists. So I drew a line early: never note syntax. Only what clicked. Only what confused me. Only the mental models I built that aren't written anywhere else.

That one rule cut roughly 80% of what most people write down. What remained was worth keeping.

---

## The Type System

A bug is not a concept. A concept is not a pattern. An observation is not a research question.

These things feel different — they need different structures. So I wrote a template for each one with exact required fields. A bug needs: what broke, why it broke, how it was fixed. A concept needs: what it is, why it matters, an example in my own words. A pattern is about recognition across contexts, not explanation. Different thing entirely.

Nothing optional that should be required.

---

## MOCs — The Spine

Every concept note links up to exactly one MOC. Every MOC links down to all its children.

That bidirectionality means the graph isn't decorative — it's a real path. Start at a MOC and walk the entire domain. Start at a concept and immediately know where you are. No orphans. No floating ideas. Everything has a home.

The single-MOC rule is a deliberate constraint. It forces a decision: what is this note *primarily* about? Distributing a note across multiple MOCs feels flexible but produces graphs that look connected without being navigable and reduces clarity when you drop down from MOC layer later.

---

## Status as a Record of Use

Understanding has stages. First encounter: `#Seedling`. Applied somewhere new: `#Growing`. Can explain it without re-reading: `#Solid`.

Promotion is triggered by use, not by how confident you feel in the moment. In the moment you always feel more confident than you are.

---

## The Research Queue

Sometimes you hit something and you can feel the gap. The Python memory model. What actually happens when two names point to the same object in memory.

So instead of pretending — park it. Name the question precisely. A vague question stays vague forever. A precise question has an answer you can go find. (or maybe you need vague for intuitive purposes..depends..)

---

## The Overhead Note

There will be sessions where maintaining this feels like more work than the learning itself. I wrote a whole note about it.

I kept the constraints anyway. The failure mode of a loose system — orphaned notes, meaningless links, no way back in — is worse than occasional maintenance debt. That's a vault that becomes useless quietly, without you noticing until it's already gone.

---

## What This Is

I didn't build this out of fear of forgetting.

I built it because I saw the shape of what I'd need. Before I'd written any real code. The architecture only makes sense because the learning is real — the links aren't decorative, the types aren't bureaucracy. Every constraint is there because I thought it through and decided it earned its place.

The Python notes in this repo are a working example, not the point. The point is the skeleton. Build your own domain on top of it and the structure will hold.