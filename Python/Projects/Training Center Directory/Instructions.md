# Project: Training Center Directory
## Instructions

## Scenario

Your company operates a network of training centers. The operations team needs a simple directory tool that can store essential information about each center and display a clear, human-readable summary for quick reference.

While all training centers share common details—such as a name and the number of attendees—some center types require additional information. In this project, you will model these relationships by building a small hierarchy of Python classes.

---

## Learning Objectives

By completing this project, learners will practice:

- Designing a base class and multiple child classes
- Using inheritance to reuse shared behavior
- Applying encapsulation using getters and setters
- Overriding built-in methods like `__repr__` to create meaningful object summaries

---

## Requirements (Concepts You’re Practicing)

### 1. Base Class: `TrainingCenter`

This class stores information common to all training centers.

#### Attributes

- `center_name` (string)
- `tier` (string — one of `"intro"`, `"intermediate"`, or `"advanced"`)
- `attendee_count` (integer)

#### Methods

- Getters for all attributes
- A setter for `attendee_count` that validates input
- A `__repr__` method that returns a clean, readable summary of the object

---

### 2. Child Class: `IntroCenter`

Represents entry-level training centers and adds rules related to participant dismissal or pickup.

#### Additional Attribute

- `release_rule` (string)  
  Example: `"Release only to listed contacts after 4 PM"`

#### Behavior

- Overrides `__repr__` to include the release rule

---

### 3. Child Class: `AdvancedCenter`

Represents advanced training centers that offer specialized tracks or teams.

#### Additional Attribute

- `tracks` (list of strings)  
  Example: `["Red Team", "Threat Hunting"]`

#### Behavior

- Adds a getter for `tracks`
- Overrides `__repr__` to include available tracks

---

### 4. Child Class: `IntermediateCenter`

Represents intermediate-level centers.

- Does not introduce any new attributes or methods
- Inherits all behavior directly from `TrainingCenter`

---

## Suggested Build Steps

1. Create the `TrainingCenter` base class.
2. Add an initializer that accepts:
   - `center_name`
   - `tier`
   - `attendee_count`
3. Store these values as instance attributes.
4. Implement getters for each attribute.
5. Implement a setter for `attendee_count` that:
   - Accepts only integers
   - Rejects values less than zero
6. Implement `__repr__` to summarize the object.
7. Create a test instance of `TrainingCenter` and print it.
8. Create `IntroCenter` inheriting from `TrainingCenter`.
9. Its initializer should accept:
   - `center_name`
   - `attendee_count`
   - `release_rule`
10. Call the parent initializer using `super()` and force `tier="intro"`.
11. Add a getter for `release_rule`.
12. Override `__repr__` to include the release rule.
13. Create `IntermediateCenter` inheriting from `TrainingCenter` with no additional attributes.
14. Create `AdvancedCenter` inheriting from `TrainingCenter`.
15. Its initializer should accept:
   - `center_name`
   - `attendee_count`
   - `tracks`
16. Add a getter for `tracks` and override `__repr__`.
