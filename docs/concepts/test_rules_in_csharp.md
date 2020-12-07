---
title: How to test rules in C#
authors:
    - Alexander Serowy
tags:
    - concept
---

## Motivation

To test rules, it is useful to make test data of specific rules available to all other rules. This way not only positive but also negative tests can be performed for all rules.

## Context

In order to ensure that for individual rules the results for the test date and the respective rule are also run through when the test data is extended, the generation of test data and test results must be separated. Thus, leading to a resolver for test data only. The resolver returns a dictionary of test data type and data, to examine which test data resulted in e.g. failed tests.

To ensure reusability for tests the enumeration is implemented as an abstract class, which yields each key value pair and checks if the pair is specified in our test or fails otherwise.

In the test class a test data collection gets implemented and inherets from the given abstract class. It holds the relationship between test data type and expected result as an array of objects.

With ``Theory`` and ``ClassData(typeof())`` each yield can now be tested against the given test case.

## Step by step

At first we create the data resolver to generate test data with a test data type.

```csharp
internal sealed class AnalyzerMockTestDataResolver
{
    public IDictionary<AnalyzerMockTestDataType, IList<ISagaProfileAnalyzer>> Get()
    {
        return new Dictionary<AnalyzerMockTestDataType, IList<ISagaProfileAnalyzer>>
        {
            {AnalyzerMockTestDataType.NoSagasRegistered,  GetNoSagasRegistered()},
            {AnalyzerMockTestDataType.ValidAnalyzers,  GetValidAnalyzers()},
            {AnalyzerMockTestDataType.EqualAnalyzerIdentifier,  GetEqualAnalyzerIdentifier()},
            {AnalyzerMockTestDataType.EqualVersionIdentifier,  GetEqualVersionIdentifier()},
            {AnalyzerMockTestDataType.VersionWithoutSteps,  GetVersionWithoutSteps()}
        };
    }
    private static IList<ISagaProfileAnalyzer> GetNoSagasRegistered()
    {
        return new List<ISagaProfileAnalyzer>();
    }

    private static IList<ISagaProfileAnalyzer> GetValidAnalyzers()
    {
        var result = new List<ISagaProfileAnalyzer>();

        var analyzer01 = new SagaProfileAnalyzerMock("1");
        result.Add(analyzer01);

        analyzer01
            .AddVersion("1.1.0")
            .AddStep<SagaEvent01, SagaStep01Mock>()
            .AddStep<SagaEvent02, SagaStep02Mock>();
...
```

In order to ensure that all test data is passed through, we provide an abstract provider. This is used to deliver test data and test specific results.

```csharp
[SuppressMessage(
    "Naming",
    "CA1710:Identifiers should have correct suffix",
    Justification = "abstract class name should end with base")]
public abstract class AnalyzerMockTestDataCollectionBase : IEnumerable<object[]>
{
    internal abstract object[]? GetReturnValuesByDataType(AnalyzerMockTestDataType type);

    public IEnumerator<object[]> GetEnumerator()
    {
        var resolver = new AnalyzerMockTestDataResolver();
        foreach (var kvp in resolver.Get())
        {
            var values = GetReturnValuesByDataType(kvp.Key);
            if (values is null)
            {
                throw new KeyNotFoundException($"{GetType().Name} does not contain " +
                    $"return values for test data of type " +
                    $"{Enum.GetName(typeof(AnalyzerMockTestDataType), kvp.Key)}.");
            }

            var result = new List<object> { kvp.Value };
            result.AddRange(values);

            yield return result.ToArray();
        }
    }

    IEnumerator IEnumerable.GetEnumerator()
    {
        return GetEnumerator();
    }
}
```

Now we can use the base class and include it in our tests.

```csharp
public class MultipleVersionsWithEqualIdentifierRuleTests
{
    private MultipleVersionsWithEqualIdentifierRule CreateMultipleVersionsWithEqualIdentifierRule()
    {
        return new MultipleVersionsWithEqualIdentifierRule();
    }

    private class AnalyzerMockTestDataCollection : AnalyzerMockTestDataCollectionBase
    {
        internal override object[]? GetReturnValuesByDataType(AnalyzerMockTestDataType type)
        {
            return type switch
            {
                AnalyzerMockTestDataType.NoSagasRegistered => new object[] { 0, 0 },
                AnalyzerMockTestDataType.ValidAnalyzers => new object[] { 0, 0 },
                AnalyzerMockTestDataType.EqualAnalyzerIdentifier => new object[] { 0, 0 },
                AnalyzerMockTestDataType.EqualVersionIdentifier => new object[] { 0, 2 },
                AnalyzerMockTestDataType.VersionWithoutSteps => new object[] { 0, 0 },
                _ => null
            };
        }
    }

    [Theory]
    [ClassData(typeof(AnalyzerMockTestDataCollection))]
    internal void Validate(IList<ISagaProfileAnalyzer> analyzers, int countWarnings, int countExceptions)
    {
        // Arrange
        var multipleVersionsWithEqualIdentifierRule = CreateMultipleVersionsWithEqualIdentifierRule();

        // Act
        var (warnings, exceptions) = multipleVersionsWithEqualIdentifierRule.Validate(analyzers);

        // Assert
        Assert.Equal(countWarnings, warnings?.Count() ?? 0);
        Assert.Equal(countExceptions, exceptions?.Count() ?? 0);
    }
}
```

## Next steps

For a resuable structure you should use dependency injection to decouple test data generation and ``GetEnumerator()``.
