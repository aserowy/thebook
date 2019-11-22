# Dependency inversion principle
## Definition
Dependency Inversion is the strategy of depending upon interfaces or abstract functions and classes, rather than upon concrete functions and classes. This principle is the enabling force behind component design.

> No dependency should target a concrete class. - Robert C. Martin

## Guidelines
- Use dependency injection (IoC) with interfaces
- Use only construcor injection
- Only use "new" in your methods for logic containing classes if control over the object life cycle is needed
- Avoid the service locator anti pattern
