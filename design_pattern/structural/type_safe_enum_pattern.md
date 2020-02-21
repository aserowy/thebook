# Type safe enum pattern
## Reference implementation
```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; private set; }

    public int Id { get; private set; }

    protected Enumeration(int id, string name)
    {
        Id = id;
        Name = name;
    }

    public override string ToString() => Name;

    public static IEnumerable<T> GetAll<T>() where T : Enumeration
    {
        var fields = typeof(T).GetFields(BindingFlags.Public |
                                         BindingFlags.Static |
                                         BindingFlags.DeclaredOnly);

        return fields.Select(f => f.GetValue(null)).Cast<T>();
    }
    
    public static T FromString<T>(string name) where T : Enumeration
    {
        return GetAll<T>().Single(r => string.Equals(r.Name, name, StringComparison.OrdinalIgnoreCase));
    }

    public static T FromValue<T>(int value) where T : Enumeration
    {
        return GetAll<T>().Single(r => r.Value.Equals(value));
    }

    public override bool Equals(object obj)
    {
        var otherValue = obj as Enumeration;

        if (otherValue == null)
            return false;

        var typeMatches = GetType().Equals(obj.GetType());
        var valueMatches = Id.Equals(otherValue.Id);

        return typeMatches && valueMatches;
    }

    public int CompareTo(object other) => Id.CompareTo(((Enumeration)other).Id);
}
```
## Usage


## Further reads
- https://docs.microsoft.com/en-us/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/enumeration-classes-over-enum-types
- https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/
- https://ardalis.com/enum-alternatives-in-c
