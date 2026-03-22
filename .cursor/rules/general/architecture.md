---
globs: ["**"]
---

# Architecture & SOLID Principles

## SOLID (Non-Negotiable)
- **Single Responsibility**: Each module/function has ONE reason to change. If the description needs "and", split it.
- **Open/Closed**: Extend behavior through composition/strategy, not by modifying existing functions.
- **Liskov Substitution**: Subtypes must be substitutable. Avoid type-checking branching (`instanceof`, `typeof` switches).
- **Interface Segregation**: Small, focused interfaces/contracts. Clients depend only on what they use.
- **Dependency Inversion**: Depend on abstractions, not concrete implementations. Inject dependencies.

## Clean Architecture Layers
```
Presentation (routes, controllers, UI) → Application (use cases, orchestration) → Domain (entities, business rules) → Infrastructure (DB, external APIs, file I/O)
```
- Dependencies point INWARD only
- Domain layer knows nothing about infrastructure
- Controllers/handlers are thin — delegate to services

## Separation of Concerns
- Controllers/handlers: request parsing, input validation, response formatting
- Service layer: business logic, orchestration, transactions
- Repository/data layer: database queries, data mapping
- Client/adapter layer: external API communication

## Design Patterns to Apply Where Appropriate
- **Adapter**: Wrap third-party APIs behind a stable interface
- **Strategy**: Swap algorithms at runtime (pricing, sorting, auth providers)
- **Observer**: Event-driven communication between decoupled components
- **Facade**: Simplify complex subsystem interactions behind a clean API
- **Factory**: Encapsulate complex object creation logic

## Code Organization
- Group by feature/domain, not by technical layer
- Shared code in a common package/module with proper types
- Each file should be under 200 lines — split if larger
- No circular dependencies between modules
