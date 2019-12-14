# Strategy pattern
## Sample implementations
### Coupling with factory and di
The given strategy interface contains two methods. ValidFor describes - in this example with an enum - if the strategy should be used. This validation could be a predicate for example as well.
GetDistanceInSecondsAsync describes the encapsulated business logic for this concrete strategy.
```csharp
internal interface IDistanceQueryStrategy
{
    FirstResponderWayResolverStrategy ValidFor { get; }

    Task<DistanceResult> GetDistanceInSecondsAsync(CoordinateDto origin, params CoordinateDto[] waypoints);
}
```
With dependency injection, we bind multiple concrete strategies to the same interface. Thus, we can get a complete collection of all concrete implementations with one call in our service.
```csharp
services.AddTransient<IDistanceQuery, DistanceQuery>();
services.AddTransient<IDistanceQueryStrategy, GoogleDistanceQueryStrategy>();
services.AddTransient<IDistanceQueryStrategy, LinearDistanceQueryStrategy>();
```
In the given example a default strategy is configured to enable a robust behavior. In addition the concrete enum value is method injected. This could also be addressed within the query, to reduce the method signature (as long as we have additional information regarding the resolvement).
```csharp
internal class DistanceQuery : IDistanceQuery
{
    private readonly IDictionary<FirstResponderWayResolverStrategy, IDistanceQueryStrategy> _strategies;

    public DistanceQuery(IEnumerable<IDistanceQueryStrategy> strategies)
    {
        _strategies = strategies.ToDictionary(strategy => strategy.ValidFor, strategy => strategy);
    }

    public Task<DistanceResult> GetDistanceInSecondsAsync(
        FirstResponderWayResolverStrategy strategy,
        CoordinateDto origin,
        params CoordinateDto[] waypoints)
    {
        var strategyToUse = FirstResponderWayResolverStrategy.GoogleDistanceResolver
        if (_strategies.ContainsKey(strategy))
        {
            strategyToUse = strategy;
        }

        return _strategies[strategyToUse].GetDistanceInSecondsAsync(origin, waypoints);
    }
}
```
### Method injection
The interface is used to abstract concrete implementations. 
```csharp
public interface IStepStrategy
{
    IVersion Version { get; }
    int Index { get; }

    public Task<IEnumerable<ICommand>> RunAsync(IEvent event);
}
```
With this abstraction a concrete implementation for this logic can be injected at runtime. 
```csharp
public async Task<IEnumerable<ICommand>> RunAsync(IEvent event, IStepStrategy step)
{
    var commands = await step
        .RunAsync(event)
        .ConfigureAwait(false);

    if (commands is null)
    {
        return Enumerable.Empty<ICommand>();
    }

    await _store
        .AddReferencesAsync(commands)
        .ConfigureAwait(false);

    return commands;
}
```

## Further reads
- https://www.oodesign.com/strategy-pattern.html
