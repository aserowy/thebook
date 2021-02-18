---
title: How to version software with Semantic Versioning
authors:
  - Alexander Serowy
tags:
  - concept
---

## Motivation

Version numbers are used in practical terms by the consumer, or client, to identify or compare their copy of the software product against another copy, such as the newest version released by the developer. For the programmer or company, versioning is often used on a revision-by-revision basis, where individual parts of the software are compared and contrasted with newer or older revisions of those same parts, often in a collaborative version control system. [^1]

It is crucial that errors can be directly assigned to a specific software version. In this way, fixes and features can also be assigned to software versions. This traceability increases the overview for customers and developers. To make releases easier to plan, it is important to make future versions predictable. Semantic versioning serves as an example here.

## Context

Semantic versioning is a formal convention for specifying compatibility using a three-part version number: major version; minor version; and patch. The patch number is incremented for minor changes and bug fixes which do not change the software's application programming interface (API). The minor version is incremented for releases which add new, but backward-compatible, API features, and the major version is incremented for API changes which are not backward-compatible. For example, software which relies on version 2.1.5 of an API is compatible with version 2.2.3, but not necessarily with 3.2.4. [^1]

Semantic Versioning states, that a version changes under specific triggers. In short [^2]:

> Given a version number MAJOR.MINOR.PATCH, increment the:
>
> - MAJOR version when you make incompatible API changes,
> - MINOR version when you add functionality in a backwards compatible manner, and
> - PATCH version when you make backwards compatible bug fixes.

These triggers are not feasible in a software solution that is used by customers, for example. So to use semantic versioning, we have to redefine triggers for specific version changes.

In this type of software solution

`MAJOR changes when`

- new feature sets are added
- features are revised and are not backward compatible

`MINOR changes when`

- new features are added to existing feature sets
- features are revised and are backwards compatible

`PATCH changes when`

- fixes are provided

To ensure that these rules are used throughout the software lifecycle and are predictable for future releases, define these triggers as follows:

| Version | Reasons |
| ------- | ------- |
| MAJOR   | ...     |
| MINOR   | ...     |
| PATCH   | ...     |

## Step by step

In a banking context, a software solution is used to plan and control funds. Every year, the planning year is changed to enable planning for the coming year. These changes are made programmatically, as new regulations must also be implemented. In the middle of the year, the same changes are also made for the controlling.

In addition, new features and critical bug fixes are implemented and rolled out in parallel. For each rollout, several deployments are done in staging until all bugs are fixed and these features can be released.

In this situation, we define our triggers in such a way that they map the turn of the year and thus roughly indicate to the user via the version which adjustments have been released:

| Version | Reasons                                                       |
| ------- | ------------------------------------------------------------- |
| MAJOR   | planning year gets increased, controlling year gets increased |
| MINOR   | new features get integrated                                   |
| PATCH   | bugfixing                                                     |

## Extensions

Semantic versioning is not the only way to design software versions. It remains important that version numbers remain predictable and that references to features and fixes can be made.

[^1]: <https://en.wikipedia.org/wiki/Software_versioning>
[^2]: <https://semver.org/>
