---
Type: "#ProjectIdea"
Topic: Python
MOC Parent:
  - "[[OOP - (MOC)]]"
Other Links:
  - "[[OOP-Project-Coffee Machine]]"
---

**Idea:** A command-line habit tracker that stores daily check-ins and shows a streak count per habit — built entirely with OOP to practice class design on a real personal tool.

**Triggered by:** The Coffee Machine project — specifically the part about deciding what each class should own. Wanted to apply that same thinking to something I'd actually use.

**Rough plan:**
- `Habit` class — name, creation date, list of completion dates
- `HabitTracker` class — holds all habits, handles add/remove/check-in
- `Storage` class — reads and writes to a JSON file so data persists between sessions
- CLI interface in `main.py` — simple command loop (add, check, list, streak)
- Stretch: weekly summary view, colour-coded streaks in terminal

This probably belongs in a separate project vault once it gets past the idea stage. One note here is enough to know what the idea was and what triggered it.
