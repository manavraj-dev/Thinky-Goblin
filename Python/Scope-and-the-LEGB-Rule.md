---
Type: "#Concept"
Topic: Functions and Scope
Status: "#Growing"
MOC Parent:
  - "[[Functions and Scope - (MOC)]]"
Other Links:
  - "[[Default-Mutable-Arguments]]"
---

**What is it:**
When Python sees a variable name, it doesn't just look for it anywhere — it searches in a specific order: Local → Enclosing → Global → Built-in. That's the LEGB rule. Python walks up that chain and stops at the first match it finds. If nothing matches, you get a `NameError`.

**Why it matters:**
Most scope bugs come from assuming Python searches differently than it does. If you assign a variable inside a function, that variable is local to that function — even if a global with the same name exists. This creates silent, confusing bugs where you're sure you've defined something but the function acts like it hasn't. Knowing LEGB tells you exactly which version of a name Python will use at any point in the code.

**Example in my own words:**
```python
x = "global"

def outer():
    x = "enclosing"
    def inner():
        print(x)  # prints "enclosing" — found in Enclosing scope before Global
    inner()

outer()
```

The inner function doesn't define `x`, so Python steps out to the enclosing scope (`outer`'s local scope) and finds it there. It never reaches global. If `outer` didn't define it either, Python would step out again to global and print `"global"`.

The trap: if you *assign* to `x` inside `inner`, Python treats `x` as local to `inner` for the entire function — even lines before the assignment. That causes an `UnboundLocalError` that looks baffling until you understand why.
