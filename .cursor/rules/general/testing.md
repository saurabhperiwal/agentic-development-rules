---
globs: ["**"]
---

# Testing Standards

## Testing Pyramid
- Unit tests: 80%+ coverage on business logic (calculations, data mapping, validation)
- Integration tests: API endpoints, database operations, service interactions
- E2E tests: Critical user journeys that span multiple systems

## Unit Test Pattern (Arrange-Act-Assert)
```
describe 'calculate_final_price':
  test 'applies percentage markup correctly':
    # Arrange
    base_price = 100
    markup_percent = 30

    # Act
    result = calculate_final_price(base_price, markup_percent)

    # Assert
    assert result == 130

  test 'handles zero base price': ...
  test 'handles zero markup': ...
```

## Test Naming
- `test_<unit>_<scenario>_<expected>` or `it('should <expected> when <scenario>')`
- Names should read like documentation of behavior

## Test Isolation
- Each test independent — no shared mutable state
- Mock external services (third-party APIs, browsers, external data sources)
- Use test fixtures for common data setup
- Reset database/state between integration tests

## Edge Cases to ALWAYS Test
- Null/nil/None/undefined inputs
- Zero values (0 is not the same as null/missing)
- Empty strings vs null vs missing keys
- Boundary values (min/max, off-by-one)
- Error paths (network failure, invalid data, missing records)

## What NOT to Test
- Third-party library internals
- Simple getters/setters with no logic
- UI layout details (test behavior, not pixels)
