---
Type: "#Pattern"
Topic: Functions and Scope
MOC Parent:
  - "[[Functions and Scope - (MOC)]]"
Other Links:
  - "[[Default-Mutable-Arguments]]"
  - "[[Scope-and-the-LEGB-Rule]]"
---

Pattern: Bugs that look like scope problems are often mutation problems — you're changing a shared object instead of creating a new one.

Seen in:
- Default mutable arguments (`[]` as function default, shared across calls)
- Passing a list into a function and modifying it in-place — the caller's list changes
- Copying a list with `b = a` and then being surprised that modifying `b` changes `a`
- Dictionary updates inside loops where all iterations reference the same dict

Why it matters:
Python separates the idea of a name (a variable) from the object it points to. Reassignment (`x = something_new`) only changes what the name points to — it doesn't touch the original object. Mutation (`.append()`, `[key] = value`) changes the object itself, which affects everyone pointing to it. Confusing these two operations causes bugs that are hard to trace because nothing looks wrong at the point of failure — the problem is always somewhere upstream.

The quick test: ask "am I changing the object or replacing the name?" If changing the object, ask "who else is pointing to this?"
