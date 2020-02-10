# C#
## Async/await
- https://devblogs.microsoft.com/dotnet/configureawait-faq/

## Code style (per project)
- https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/
- https://docs.microsoft.com/de-de/visualstudio/code-quality/install-fxcop-analyzers?view=vs-2019

## Profiling
- https://medium.com/@maxnalsky/optimizing-garbage-collection-in-a-high-load-net-web-service-3bb620b444a7

## Testing
- [Mocking ILogger<>](https://chrissainty.com/unit-testing-ilogger-in-aspnet-core/)
  - Using custom LoggerAdapter as abstraction
  - Adapter calls extension methods of ILogger
  - Concrete implementation which can be mocked by e.g. moq
