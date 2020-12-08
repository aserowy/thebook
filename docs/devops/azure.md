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

## Links

`Nuget`

- <https://docs.microsoft.com/en-us/azure/devops/pipelines/artifacts/nuget?view=azure-devops&tabs=yaml>
- <https://medium.com/@dan.cokely/creating-nuget-packages-in-azure-devops-with-azure-pipelines-and-yaml-d6fa30f0f15e>

`Tags`

- [How to use tags as variable in yaml.](https://stackoverflow.com/questions/56575840/git-tag-name-in-azure-devops-pipeline-yaml)

`Testing`

- [Testing azure functions in CI/CD](https://www.davideguida.com/testing-azure-functions-on-azure-devops-part-1-setup/)

`Versioning`

- [Why you should not use r:rev as patch.](https://stackoverflow.com/questions/54718866/azure-pipeline-nuget-package-versioning-scheme-how-to-get-1-0-revr/56111209#56111209)