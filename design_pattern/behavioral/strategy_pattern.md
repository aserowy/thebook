# Strategy pattern
## Sample implementations
### Coupling with factory and di

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