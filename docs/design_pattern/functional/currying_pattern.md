---
title: Currying pattern
authors:
    - Alexander Serowy
---

With Currying you can reduce the number of inputs of a function. This can get handy to e.g. reduce inputs to one and be able to compose different functions.

```csharp
private static readonly Func<
    IVersionResolver,
    Func<IDictionary<IVersion, IList<IStepConfiguration>>, IList<IStepConfiguration>>>
        GetVersionFunc = versionResolver => (versions) => versionResolver.GetVersion(versions);
```
