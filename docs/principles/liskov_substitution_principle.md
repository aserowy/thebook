---
title: Liskov substitution principle
authors:
    - Alexander Serowy
---

## Definition

If S is a subtype of T, then objects of type T may be replaced with objects of type S (i.e. an object of type T may be substituted with any object of a subtype S) without altering any of the desirable properties of the program (correctness, task performed, etc.).

It is a semantic rather than merely syntactic relation, because it intends to guarantee semantic interoperability of types in a hierarchy, object types in particular.

> ### Prominent violation
>
> System.Array implements the ICollection\<T\> interface.
> Calling Add() throws a NotSupportedException at runtime.

## Guidelines

Implementing an interface/base class should lead to two questions:

- Is every member/method suitable for each concrete implementation?
- Is the naming of the interface/base class open enough for later implementations?
