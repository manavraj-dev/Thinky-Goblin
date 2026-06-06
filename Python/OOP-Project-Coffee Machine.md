---
Type: "#CourseProject"
Topic: OOP
Status: "#Finished"
MOC Parent:
  - "[[OOP - (MOC)]]"
Links:
---

**Goal:** Build a simulated coffee machine in Python using OOP — separate classes for the machine, menu, and money handling — to force real use of class design instead of just understanding it theoretically.

**Checklist:**
- [x] Define a `MenuItem` class with name, cost, and ingredient requirements
- [x] Define a `Menu` class that holds all items and can find an item by name
- [x] Define a `CoffeeMaker` class that tracks resources and checks/processes orders
- [x] Define a `MoneyMachine` class that handles payment and tracks profit
- [x] Wire all classes together in `main.py` with a run loop
- [x] Handle edge cases: insufficient resources, wrong payment, quit and report commands

**What this project actually taught:**
The interesting part wasn't the individual classes — it was deciding what each class should *own*. The `CoffeeMaker` shouldn't know about money. The `MoneyMachine` shouldn't know about ingredients. Keeping those boundaries clean is what OOP is actually for. Every time I wanted to reach across a class boundary and grab something directly, that was a sign the interface needed a method instead.

The run loop in `main.py` ended up being the place where all four classes talk to each other — which felt right. The machine coordinates; the classes do their own thing.
