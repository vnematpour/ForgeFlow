
# ADR-0002: Enforce Module Boundaries and Data Ownership

- Status: Accepted
- Date: 2026-11-11

## Context

ForgeFlow consists of multiple business modules.
Each module must own its business rules and data.

Uncontrolled dependencies and direct access to another
module's internal data can lead to tight coupling.

## Decision

- Each module owns its domain model and database tables.
- Modules communicate through explicit contracts.
- Direct access to another module's internal implementation
  is prohibited.
- In-process communication is the default.
- Cross-module foreign keys are avoided.
- Integration events are used when asynchronous
  communication is required.

## Consequences

### Positive
- Better encapsulation.
- Explicit module dependencies.
- Improved testability.
- Easier future extraction of modules.

### Negative
- Additional contracts must be maintained.
- Cross-module queries require deliberate design.
- Event-driven workflows introduce eventual consistency.
