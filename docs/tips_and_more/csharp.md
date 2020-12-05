---
title: C#
authors:
    - Alexander Serowy
---

## Async/await

- <https://devblogs.microsoft.com/dotnet/configureawait-faq/>

## Code metrics

<https://docs.microsoft.com/en-us/visualstudio/code-quality/how-to-generate-code-metrics-data?view=vs-2019>

Both configurations - .editorconfig and CodeMetricsConfig.txt - should get added to the solution. Name of metrics configuration must match exactly 'CodeMetricsConfig.txt'. Add links of both files in each project and ensure the metrics configuration is added as additional file.

Excerpt from an .editorconfig:

```ini
# Remove the line below if you want to inherit .editorconfig settings from higher directories
root = true

# C# files
[*.cs]

# CA1303: Do not pass literals as localized parameters
dotnet_diagnostic.CA1303.severity = none

# CA1501: Avoid excessive inheritance
dotnet_diagnostic.CA1501.severity = warning

# CA1502: Avoid excessive complexity
dotnet_diagnostic.CA1502.severity = warning

# CA1505: Avoid unmaintainable code
dotnet_diagnostic.CA1505.severity = warning

# CA1506: Avoid excessive class coupling
dotnet_diagnostic.CA1506.severity = warning
...
```

Example of CodeMetricsConfig.txt:

```txt
CA1501: 3
CA1502: 15
CA1505: 40
CA1506: 9
```

It should get added that these numbers can barely reached in test projects. A second metric configuration for test projects is a wise decision. In specific cases e.g. AutoMapper-Profiles class coupling cannot be reached as well.

## Code style (per project)

- <https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/>
- <https://docs.microsoft.com/de-de/visualstudio/code-quality/install-fxcop-analyzers?view=vs-2019>

## Profiling

- <https://medium.com/@maxnalsky/optimizing-garbage-collection-in-a-high-load-net-web-service-3bb620b444a7>

## Testing

- [Emailing in dev with smtp4dev](https://github.com/rnwood/smtp4dev)
- [Mocking ILogger<>](https://chrissainty.com/unit-testing-ilogger-in-aspnet-core/)
  - Using custom LoggerAdapter as abstraction
  - Adapter calls extension methods of ILogger
  - Concrete implementation which can be mocked by e.g. moq
