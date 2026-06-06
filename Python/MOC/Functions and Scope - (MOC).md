---
Type: "#MOC"
Topic: Functions and Scope
Children:
  - "[[Scope-and-the-LEGB-Rule]]"
  - "[[Default-Mutable-Arguments]]"
---

Functions in Python have more going on beneath the surface than the syntax suggests. This MOC covers the mechanics that trip people up — how Python resolves names, how default arguments can silently mutate across calls, and how the star operator unpacks arguments in ways that feel like magic until you understand what's actually happening. These are the notes that came from moments of genuine confusion, not from following along.

## Notes
- [[Scope-and-the-LEGB-Rule]] — how Python decides which variable you mean at any given line
- [[Default-Mutable-Arguments]] — why using a list as a default argument is a trap, and what's actually going on
