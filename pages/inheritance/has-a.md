---
layout: default
title: Has-As
permalink: /inheritance/has-a/
---

# Composition and Aggregation (The "Has-A" Relationship)

The most common alternative to "Is-A" is the **"Has-A"** relationship, also known as **Object Composition**. This occurs when one object is built from or contains other objects. A computer has a CPU. A house has a roof.

"Has-A" relationships are categorized into two major subtypes, based on **lifetime ownership:**

## 1. Composition (The Strong "Has-A"/"Part-of")

**Composition** models a strong form of ownership where the part **cannot exist without the whole.** The complex object is solely responsible for managing the part's existenc.

|Conceptual Property|Composition|Real-World Example|
|-------------------|-----------|------------------|
|**Relationship**|Whole/Part|A **Body** has a **Heart**.|
|**Ownership**|**Strong:** The part is owned exclusively by the whole.|A heart is physically contained within one body.|
|**Lifetime**| **Dependent:** The part is created when the whole is created, and destroyed when the whole is destroyed.| If the body ceases to exist, the heart (as a functional component) also ceases to exist within the program's context.|

**Design Rule:** If the relationship between two objects is **"part-of"** (A is physically or logically a core component of B), use a composition.

## 2. Aggregation (The Weak "Has-A" / Shared Part)

**Aggregation** models a weaker form of ownership where the part **can exist independently of the whole.** The complex object keeps a reference or a pointer to the part, but is not responsible for its creation or destruction.

|Conceptual Property|Aggregation|Real-World Example|
|-------------------|-----------|------------------|
|**Relationship**|Whole/Part|A **Department** has a **Teacher.**|
|**Ownership**|**Weak/Shared:** The part can belong to multiple wholes or exist alone.|A teacher exists before being hired by a department and will exist after they leave.|
|**Lifetime**|**Independent:** The part's lifetime is managed externally.|If the department is closed, the teacher (the object) is not destroyed.|

**Design Rule:** If the relationship is **"has-a"** but the lifetime of the objects are **not tied** (e.g., membership, association), use Aggregation.

[← Confused? Back to Inheritance!](/inheritance/)        [Read on - Uses-A Relationships! →](/inheritance/uses-a/)
