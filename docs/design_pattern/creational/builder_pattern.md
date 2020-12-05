---
title: Builder pattern
authors:
    - Alexander Serowy
---

## Sample implementation

The given implementation abuses the builder pattern for validation. Thus, you can easily chain validation steps and reuse the configured validator object.

```csharp
public class Validator<TClass>
{
    private IList<Predicate<TClass>> _rules = new List<Predicate<TClass>>();
  
    public Validator<TClass> AddRule(Predicate<TClass> rule)
    {
        _rules.Add(rule);
  
        return this;
    }

    public bool Validate(TClass obj)
    {
        foreach (var func in _rules)
        {
            if (!func(obj))
            {
                return false;
            }
        }

        return true;
    }
}
```

## Further reads

- <https://www.pmichaels.net/2018/01/27/using-builder-pattern-validation/>
