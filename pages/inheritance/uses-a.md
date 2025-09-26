---
layout: default
title: Uses-As
permalink: /inheritance/uses-a/
---

# Association and Dependencies

Beyond ownership (Composition and Aggregation), there are even looser relationships objects can have:

## 3. Association (General "Uses-A" or "Knows-Of")

**Association** is a very general relationship where two objects interact, but neither is necessarily a "part" of the other.

* **Example:** A **Doctor** and a **Patient**. They interact closely, but the Patient is not a part of the Doctor, nor is the Doctor a part of the Patient. They have entirely independent lives.
* The relationship can be **unidirectional** (A knows about B, but B doesn't know about A) or **bidirectional** (Doctor knows Patient, and Patient knows Doctor).

## 4. Dependency ("Temporary Uses-A")

A **Dependency** is the weakest form of relationship, usually transient and temporary. It occurs when one object **uses the functionality of another object to accomplish a specific task, but does not store a link (attribute/member) to it.**

* **Example:** A **Calculator** object needs a **Logger** object to write a message about an error. The Calculator temporarily uses the Logger within a single function call. Once the function finishes, the Calculator has no memory or link to the Logger object.

**Design Principle:** When deciding between Inheritance ("Is-A") and Composition ("Has-A"), programmers oftn follow the principle: **"Prefer composition over inheritance."** This is because composition creates flexible code that is less tightly coupled and easier to change later on.

[← Confused? Back to Has-A Relationships!](/inheritance/has-a/)    [And now, some examples! →](/inheritance/examples/)
