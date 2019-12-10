# Builder pattern
## Sample implementation
```csharp
public class Validator<TClass>
{
    private List<Predicate<TClass>> _rules;        
  
    public ValidatorEngine AddRule(Predicate<TClass> rule)
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
```
## Further reads
- https://www.pmichaels.net/2018/01/27/using-builder-pattern-validation/