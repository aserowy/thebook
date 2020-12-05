---
title: Azure DevOps
authors:
    - Alexander Serowy
---

## Common mistakes

### Predefined variables

Using predefined values in variables will not get resolved for name. The following snipped will resolve in "$(Build.SourceBranchName).11" in dev ops.

```yaml
name: $(majorMinorVersion).$(patchVersion)

variables:
  majorMinorVersion: '$(Build.SourceBranchName)'
  patchVersion: $[counter(variables['majorMinorVersion'], 10)]
```

Because variables will get determined at runtime (except expressions) you should use the predefined variable directly. Thus, the resolved name on a branch named "1.0" would be "1.0.11".

```yaml
name: $(Build.SourceBranchName).$(patchVersion)

variables:
  majorMinorVersion: '$(Build.SourceBranchName)'
  patchVersion: $[counter(variables['majorMinorVersion'], 10)]
```
