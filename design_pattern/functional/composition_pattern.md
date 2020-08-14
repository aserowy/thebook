# Composition pattern

## Reference implementation

Because of a narrow support for fp in c#, we need a helper to build a proper composition of functions.

```csharp
public static Func<T, TNextOut> Compose<T, TInitOut, TNextOut>(
    this Func<T, TInitOut> initial,
    Func<TInitOut, TNextOut> next)
{
    return x => next(initial(x));
}
```

With the given extension you can compose functions with output equals input.

```csharp
public async Task<IStepConfiguration> ResolveAsync(IDictionary<IVersion, IList<IStepConfiguration>> versions)
{
    var resolverFunc = GetVersionFunc().Compose(GetStepFunc());

    return resolverFunc(versions);
}

private static readonly Func<IDictionary<IVersion, IList<IStepConfiguration>>, IList<IStepConfiguration>>
    GetVersionFunc = versions => versions.FirstOrDefault().Value;

private static readonly Func<IList<IStepConfiguration>, IStepConfiguration>
    GetStepFunc = steps => steps?.FirstOrDefault();
```

For functions with multiple inputs you can use [Currying](currying_pattern.md) to reduce the count of inputs to one.

## Further reads

- <http://hamidmosalla.com/2019/04/25/functional-programming-in-c-sharp-a-brief-guide/>
