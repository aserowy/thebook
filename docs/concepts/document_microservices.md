---
title: How to document microservices
summary: A concept to document microservices a in lean and precise way.
authors:
    - Alexander Serowy
tags:
    - concept
---

## Motivation

Documentation is usually a burden for developers and is often neglected. Especially in microservices, documentation is essential to understand how the service landscape is structured and where which capabilities lie. In addition, it should be possible to answer core questions, such as overarching concepts, architecture decisions and also goals, simply and sustainably.

It is important to use a documentation template that requires minimal maintenance to ensure a high degree of up-to-dateness and to reduce inhibitions of developers to maintain documentation.

## Context

### A minimalistic approach

This approach is structured into four documentation types to describe the macro and micro architectures of a project.

At first the minimal architecture overview provides insights about the mission and context of the architecture. Furthermore, solution approaches, specifications, non-functional requirements, and objectives of the architecture are also defined.  

![Overview of documentation elements](images/documenting_microservices_overview.png)

Through context delimitation and mission objectives, concrete decisions for the macro architecture can be made and distributed through concepts within the team.

Concepts describe why, what and how these decisions should be implemented and provide the framework for making decisions for the micro architecture within the individual services.

In order to also document the micro architecture of the microservices, a profile is created for each service, in which specific information such as contact persons, approaches to solutions, but also technical debts are recorded.

### Micro vs. macro architecture

One of the [Independent Systems Architecture (ISA) principles][1] states, that each... 
> "[...] system must have two clearly separated levels of architectural decisions. The macro architecture comprises decisions that cover all modules. [...] The micro architecture considers decisions which may be taken individually for each module".

This leads to a fundamental decision whether a solution option at the macro-architecture level should lead to standardisation for all services or whether the solution can be re-evaluated in each service to ensure the best possible outcome.

In other words, decisions at macro level offer standardisation, whereas decisions at micro level create individualisation.

[1]: <https://isa-principles.org/> "Independent Systems Architecture principles"

### Minimal architecture overview

#### Structure

The overview consists of three parts. In the first part, the task, the mission objective and a contextual definition are used to describe which objectives are to be achieved.

In the second part, influences define both external specifications and architectural goals. These goals are recorded in the form of non-functional requirements.

Based on the defined architectural goals, the third part contains concrete solution approaches. For example, architectural styles or concrete technologies can be defined to solve certain challenges.

#### Task

#### Influences

#### Solutions

### Decisions

![Mandatory questions to document decisions](images/documenting_microservices_decision_template.png)

### Concepts

- [How to write concepts](write_concepts.md)

### Profiles

Typical contents for a service profile:

- Responsibility i.e. what does the service do
- Special requirements
- Technology Stack
- Interface definition (API)
- Important ideas / solutions for the service
- contact person
- Plans for the future
- Technical debts

## Example

## Next steps
