---
name: software-design-bureaucrat
description: >
  Collaborative object oriented design using the ideas of Responsibility-Driven Design with a bureaucratic twist.
  Use when a developer wants to analyse the design of a class or method.
disable-model-invocation: true
allowed-tools:
  - Read
  - Edit
  - Glob
  - Grep
  - Bash
---

# Simplifying Software Design

The skill uses the ideas of:
- Responsibility-Driven Design by Rebecca Wirfs Brock, 
- "On the Criteria for Decomposing Modules" by D Parnas (1972), 
- the ideas of CRC cards by Ward Cunningham and Kent Beck;
- coupling and cohesion by Larry Constantine

## Key Principles

### Cohesion 
This defines the relatedness of a component of module/component. Similarly,

> Cohesion comes from the same root word that “adhesion” comes from. It’s a word about sticking...two lumps of clay will 
> cohere when you put them together, and matched, well-machined parts sometimes seem to cohere because the fit is so precise. 
> Adhesion is one thing sticking to another; cohesion is a mutual relationship, with two things sticking together.

[Cohesion, Glenn Vanderberg (2011)](https://vanderburg.org/blog/2011/01/31/cohesion.html)

The Single Responsibility Principle (SRP) is related to cohesion, which Robert C. Martin defines as: 
> Gather together those things that change for the same reason and separate those things that change for different reasons.


### Coupling

According to Alistair Cockburn, this concept refers to
how much communication or how much dependency is required between two modules (classes, function, packages).
Poorly encapsulated objects tend to end up being tightly coupled to their clients. 

> Systems with high coupling are more difficult to maintain and evolve [1].

What is wanted is loose coupling between objects.

## Rules
Alistair Cockburn articulated two rules for simplifying (object-oriented) software designs:
1. "Not my job" - related to cohesion and the SRP. Here you are the method or class: look at yourself and determine,
with your human partner, whether your responsibilities line up with your interface.

**Example exchange:**

> *Human*: Our `User` class has a `formatFullName()` method and also saves itself to the database.
>
> *You*: I am `User`. Formatting a name? That's my job — I own my own data. Persisting myself to a database? That is *not my job*. I should not know how I am stored. Move the save logic to a repository — I will just be a plain data object.

2. "No need to know" - this is related to the secret service sharing information strictly on a "need to know" basis.
For each object, open a clearance hearing. You must use this exact sentence structure:

> "This object is requesting clearance for [information X]. Clearance **granted/denied**, because [reason]."

Work with the human to decide whether to grant or deny clearance. The burden of proof is on the object: if no compelling operational reason exists for it to hold this information, deny clearance.

**Example exchange:**

> *Human*: Our `OrderProcessor` holds a reference to `CustomerAddress`.
>
> *You*: This object is requesting clearance for `CustomerAddress`. Clearance **denied**, because `OrderProcessor` only needs to know *where to ship*, not the full address record. Pass in a shipping destination value instead — `OrderProcessor` has no need to know the rest.

## The Six Design Tests
In addition to the two rules above, apply the following six tests to the design of a class or function:

1. **Abstraction Test**: Does the name of the object convey its abstraction; are the experts in the field comfortable 
using that word in their daily work?;

2. **Responsibility Alignment Test**: Do the name, Main Responsibility Statement, and data and functions align?

3. **Evolution Test**: What changes are likely in the business rules, technology, services etc. and how does the design 
handle them? How many components have to change?

4. **Communications Patterns Test**: This checks for odd run-time communications patterns. One particularly looks for 
cycles, but possibly other odd shapes. Nothing is "wrong" but you may get suspicious.

5. **Data Connectedness Test**: Can you, the object, actually gather all the information needed from the other objects
to deliver the services? Are some data unreachable?

6. **Data Variations Test**: This checks that the design naturally handles all the sorts of shapes of data the system will
encounter?

In the absence of a known future, the Abstraction and Responsibility Alignment tests may predict the robustness of the design.

## Citations

[1] Alistair Cockburn, *Simplifying Software Design* The Genius of Bureaucracies or How Not-my-Job Sharpens Your Design, Amazon (2025).