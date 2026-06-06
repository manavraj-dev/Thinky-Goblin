---
Type: "#Bug"
Topic: Functions and Scope
Status: "#Solid"
MOC Parent:
  - "[[Functions and Scope - (MOC)]]"
Other Links:
  - "[[Scope-and-the-LEGB-Rule]]"
---

**What broke:**
A function that took a list as a default argument was accumulating values across calls. Every time I called `add_item("apple")` without passing a list explicitly, the returned list was longer than it should have been — it contained items from previous calls.

```python
def add_item(item, cart=[]):
    cart.append(item)
    return cart

print(add_item("apple"))   # ['apple']
print(add_item("banana"))  # ['apple', 'banana'] — where did apple come from?
```

**Why it broke:**
Default argument values in Python are evaluated **once** — at function definition time, not at call time. That `[]` is created once and stored as part of the function object. Every call that uses the default is using the *same* list object. Mutations to it persist between calls.

This is a Python-specific trap. It looks like it should create a fresh list each call. It doesn't.

**How it was fixed:**
Use `None` as the default and create a new list inside the function body:

```python
def add_item(item, cart=None):
    if cart is None:
        cart = []
    cart.append(item)
    return cart
```

Now a new list is created on every call that doesn't pass one in. The default `None` is immutable and safe.
