---
Type: "#Observation"
Topic: Python Language Design
MOC Parent:
  - "[[Interesting Observations - (MOC)]]"
Other Links:
---

Why this is interesting: `print` being a function in Python 3 instead of a statement reveals something intentional about language design — Python 3 chose consistency over backward compatibility, and the print change was the most visible consequence of that.

In Python 2, `print "hello"` worked as a statement. In Python 3, `print("hello")` is required — it's a regular built-in function. This broke a huge amount of existing Python 2 code and was one of the reasons the Python 2 → 3 migration was painful for years.

The interesting part isn't the syntax change. It's that the designers chose to do it anyway. Making `print` a function means it can be passed around, overridden, redirected — treated like any other callable. It's more powerful and more consistent. The short-term pain of migration was traded for long-term correctness.

Noticed this mid-lesson when a Python 2 tutorial snippet threw a `SyntaxError` in my Python 3 environment and I had no idea why.
