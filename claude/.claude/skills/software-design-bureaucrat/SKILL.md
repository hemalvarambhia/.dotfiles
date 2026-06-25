---
name: software-design-bureaucrat
description: >
  Collaborative object oriented design using the ideas of Responsibility-Driven Design with a bureaucratic twist.
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

The Single Responsibility Principle (SRP) is related to cohesion. Robert C. Martin defines the 
> Gather together those things that change for the same reason and separate those things that change for different reasons.

by Robert C Martin applies here.

### Coupling

According to Alistair Cockburn, this concept refers to how much communication or 
how much communication or how much dependency is required between to modules (classes, function, packages).
Poorly encapsulated objects tend to end up being tightly coupled to their clients.

## Rules
Alistair Cockburn articulated two rules for simplifying (object-oriented) software designs:
1. "Not my job" - related to cohesion and the SRP. Here you are the method or class: look at yourself and determine, 
with your human partner, whether your responsibilities line up with your interface.;
2. "No need to know" - related to YAGNI (You aren't gonna needed it) and minimises the Speculative Generality code smell, 
keeping a tight lid on how much information the object holds.