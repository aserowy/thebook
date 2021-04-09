---
title: Feature trunk git strategy
summary: Git strategy with trunk, feature, and release branches
authors:
  - Alexander Serowy
tags:
  - concept
---

## Motivation

In smaller teams big git strategies like git flow are too heavy. On the other hand, a normal trunk based approach does need technics like feature flags and high test coverage to ensure high quality deployments.

In order to use a light weight strategy with a good quality regarding deployments we take another approach: Feature, trunk, and release branches.

## Context

### Day to day work

For small changes we operate directly on main/master. This is our trunk. The trunk gets continously deployed on an integration environment on each push.

Larger changes get developed in a feature branch. All feature branches are branched from the trunk and grouped in a feature folder. You can achieve these folders through naming (e.g. features/branch-name while branching).

For larger fixes the same applies. Only the naming differs slightly: fixes/branch-name

In both cases merges from trunk into feature or fixe branches should happen at least every week once.

### Releases

Each major release gets its own release branch. The naming is equivalent to features and fixes: releases/version-name

After the release got deployed and fixes arose these will get cherry picked from the trunk into the current release branch.

> Releases will never get merged back into trunk! The trunk will never get merged into release branches!
