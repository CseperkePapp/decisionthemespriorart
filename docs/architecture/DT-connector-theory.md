# DT-connector-theory.md
### Decision Themes — Connector Theory (v0.1)

The connector system enforces typed compatibility between logic modules.

---

# 1. Purpose of Connectors
- regulate DT dependencies
- ensure safe logic composition
- encode domain semantics during composition

---

# 2. Connector Structure
A connector has:
- `id`
- `domain`
- `direction` (requires/provides)
- `footprint.roles`
- `footprint.properties`

---

# 3. Subset Compatibility
A `requires` connector attaches to a compatible `provides` connector if:
- domains match
- required roles ⊆ provided roles
- required properties ⊆ provided properties

This forms the foundation of the lattice.

---

# 4. Connector Categories
- **semantic connectors** (from Dictionary)
- **logic connectors** (from DTs)
- **overlay connectors** (from contextual DTs)

---

# 5. Connector Behavior in the Composer
- validation
- dependency graph building
- ordering
- error detection for missing or incompatible connectors

