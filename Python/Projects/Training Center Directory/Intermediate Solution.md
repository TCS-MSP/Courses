# Training Center Directory
## Below is the Intermediate Code Solution
Beneath the code are a few comments to help bring readers up to speed.

```python
class TrainingCenter:
    VALID_TIERS = {"intro", "intermediate", "advanced"} // By convention, ALL_CAPS_WITH_UNDERSCORES is used for constants

    def __init__(self, center_name: str, tier: str, attendee_count: int):
        self._center_name = center_name
        self._tier = tier
        self.attendee_count = attendee_count  # uses setter for validation

        if self._tier not in self.VALID_TIERS:
            raise ValueError(f"tier must be one of {sorted(self.VALID_TIERS)}")

    # --- Getters via @property ---
    @property
    def center_name(self) -> str:
        return self._center_name

    @property
    def tier(self) -> str:
        return self._tier

    @property
    def attendee_count(self) -> int:
        return self._attendee_count

    # --- Setter with validation ---
    @attendee_count.setter
    def attendee_count(self, value: int):
        if not isinstance(value, int):
            raise TypeError("attendee_count must be an integer")
        if value < 0:
            raise ValueError("attendee_count cannot be negative")
        self._attendee_count = value

    def __repr__(self) -> str:
        return (
            f"<TrainingCenter name={self.center_name!r}, "
            f"tier={self.tier!r}, attendees={self.attendee_count}>"
        )


class IntroCenter(TrainingCenter):
    def __init__(self, center_name: str, attendee_count: int, release_rule: str):
        super().__init__(center_name=center_name, tier="intro", attendee_count=attendee_count)
        self._release_rule = release_rule

    @property
    def release_rule(self) -> str:
        return self._release_rule

    def __repr__(self) -> str:
        base = super().__repr__()
        return f"{base[:-1]}, release_rule={self.release_rule!r}>"


class IntermediateCenter(TrainingCenter):
    def __init__(self, center_name: str, attendee_count: int):
        super().__init__(center_name=center_name, tier="intermediate", attendee_count=attendee_count)


class AdvancedCenter(TrainingCenter):
    def __init__(self, center_name: str, attendee_count: int, tracks: list[str]):
        super().__init__(center_name=center_name, tier="advanced", attendee_count=attendee_count)
        self._tracks = list(tracks)  # copy to avoid external mutation

    @property
    def tracks(self) -> list[str]:
        return list(self._tracks)  # defensive copy

    def __repr__(self) -> str:
        base = super().__repr__()
        return f"{base[:-1]}, tracks={self._tracks!r}>"


# --- Quick sanity tests ---
if __name__ == "__main__":
    generic = TrainingCenter("Downtown Lab", "intermediate", 22)
    print(generic)

    intro = IntroCenter("Onboarding Hub", 18, "Release only to listed contacts after 4 PM")
    print(intro)

    mid = IntermediateCenter("Skills Workshop", 30)
    print(mid)

    adv = AdvancedCenter("Red Ops Center", 12, ["Red Team", "Threat Hunting", "Forensics"])
    print(adv)

    # update attendee count (setter validation)
    adv.attendee_count = 14
    print("Updated:", adv)
```

## 1️⃣ Is `__repr__` Something We Created, or Something Built In?

**Short answer:**  
👉 `__repr__` is built into Python — when we define it ourselves, we are overriding it.

### What’s Going On?

Every Python object automatically inherits a default `__repr__` method from Python’s base `object` class.

Example:

```python
class Demo:
    pass

d = Demo()
print(d)
````

Output looks like:

    <__main__.Demo object at 0x10a3f9d90>

That unreadable string comes from Python’s **default `__repr__` implementation**.

### Why Override `__repr__`?

When you define:

```python
def __repr__(self):
    return "some string"
```

You are replacing Python’s default behavior with something more human‑readable.

### Important Clarifications

*   You are **not inventing** `__repr__`
*   You are **customizing** a method Python already calls automatically when:
    *   `print(object)` is used
    *   `str(object)` is called
    *   the object appears in the Python interpreter

✅ Built‑in method  
✅ Overridden intentionally  
✅ Very common teaching example

***

## 2️⃣ What Are All These “Advanced‑Looking” Things?

Let’s break them down one at a time, without assuming prior exposure.

***

### A) `@property` and Decorators (Why They’re Overkill Here)

You may see code like this:

```python
@property
def center_name(self):
    return self.center_name
```

#### What Is This Doing?

The `@property` decorator allows a method to be accessed like an attribute:

```python
obj.center_name   # looks like a variable
```

Instead of:

```python
obj.get_center_name()
```

#### Why Skip This for Beginners?

*   It hides what’s really happening
*   It introduces decorators, which are a separate mental model
*   Early learners benefit from explicit getter and setter methods

✅ Your instinct is correct: don’t use decorators yet

***

### B) Type Hints (`-> str`, `: int`, `list[str]`)

Examples:

```python
def __repr__(self) -> str:
```

```python
def __init__(self, center_name: str, attendee_count: int):
```

#### What Are These?

These are **type hints**. They:

*   Do **not** change how the code runs
*   Exist for:
    *   IDE autocomplete
    *   Static analysis
    *   Documentation

Python does **not** enforce them unless additional tooling is used.

#### Why They’re Inappropriate Here

For beginner to intermediate learners:

*   They distract from core concepts
*   They look like strict syntax rules (but aren’t)
*   They raise questions like:
    > “Does Python enforce this?”

✅ Safe to remove entirely  
✅ Concepts remain 100% intact

***

### C) That Weird f‑String with `!r`

Example:

```python
f"<TrainingCenter name={self.center_name!r}, "
f"tier={self.tier!r}, attendees={self.attendee_count}>"
```

This is an advanced f‑string feature.

#### What Does `!r` Mean?

`!r` tells Python to format the value using `repr()` instead of `str()`.

Example:

```python
name = "Main Center"

print(f"{name}")
# Main Center

print(f"{name!r}")
# 'Main Center'
```

So:

*   `!r` adds quotes around strings
*   It is mainly used for debugging, not student projects

✅ No need to expose beginners to this  
✅ Normal f‑strings are already sufficient

***

### D) Multi‑Line f‑Strings

Example:

```python
return (
    f"<TrainingCenter name={self.center_name!r}, "
    f"tier={self.tier!r}, attendees={self.attendee_count}>"
)
```

This works because Python automatically joins strings inside parentheses.

While valid and clean Python, for beginners:

*   It can look mysterious
*   Single‑line strings are usually clearer and easier to read
