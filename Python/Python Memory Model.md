---
Type:
  - "#ResearchQueue"
Topic: Python Internals
MOC Parent:
  - "[[Research Queue - (MOC)]]"
Other Links:
  - "[[Default-Mutable-Arguments]]"
  - "[[MutationVsReassignment-Pattern]]"
---

Why this is interesting: The mutable default argument bug only makes sense if you understand that Python variables are labels pointing to objects in memory — not boxes containing values — and I don't fully have that mental model yet.

Open question: What exactly happens in CPython's memory when you do `a = []`, `b = a`, then `b.append(1)`? Where does the list object live, how do both names point to it, and when does Python create a new object vs reuse an existing one? Also: what is reference counting and how does Python decide when to free memory?
