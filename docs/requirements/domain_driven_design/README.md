---
title: Domain driven design
authors:
    - Alexander Serowy
---

## Refactoring methods

| Refactoring | Use case |
| --- | --- |
| [Eric Evan's bubbles](eric_evans_bubbles.md) | Used to add requirements in a separate bounded context without having to modify the architecture. |
| [Extract bounded contexts](extract_bounded_contexts.md) | Cutting out an identified bounded context from an existing architecture. |
| [Nick Tune's toolbox](nick_tunes_toolbox.md) | Holistic iterative approach, with which a complete roadmap including evaluation of refactorings can be created. |

## Glossary

| Phrase                        | Meaning |
| --- | --- |
| Anti Corruption Layer (ACL)   | Abstraction, to distinguish a bounded context from legacy. Here, the data should not simply be passed through, but transferred into models that make sense in the context. |
| Bounded Context               | Global processes are cut in Bounded Context. Two questions to define the boundaries of the context: Is a requirement in the same Ubiquitous Language? Does this increase the complexity excessively? |
| Ubiquitous Language           | Language spoken by experts in the domain/subdomain. No translations are enforced! |

## Further reads

- <https://github.com/ddd-crew>
