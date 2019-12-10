# Interface segregation principle
## Definition
ISP splits interfaces that are very large into smaller and more specific ones so that clients will only have to know about the methods that are of interest to them.

Such shrunken interfaces are also called role interfaces. ISP is intended to keep a system decoupled and thus easier to refactor, change, and redeploy.

> [...] no client should be forced to depend on methods it does not use. - Robert C. Martin

## Guidelines
- Avoid big interfaces like eight methods and more (Every now and then there are useful exceptions)
- Try to implement interfaces with LSP and SRP in mind
