# Open-closed principle
## Definition
A class is closed, since it may be compiled, stored in a library, baselined, and used by client classes. But it is also open, since any new class may use it as parent, adding new features. When a descendant class is defined, there is no need to change the original or to disturb its clients. 

> Software entities [..] should be open for extension, but closed for modification. - Betrand Meyer

## Guidelines
- Switch cases and „if else if“ chains should be kept at a bare minimum
- Use pattern, e.g. strategy, to avoid inheritance
- Try to anticipate future extensions, but keep KISS and YAGNI in mind
- Don't overestimate your ability to anticipate
