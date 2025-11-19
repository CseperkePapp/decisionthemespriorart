# DT-dt-spec.md
### Decision Themes — Decision Theme Module Specification (v0.1)

> This spec complements `DT-dt-connector-spec.md` (prior-art folder) by describing DTs at a higher, system-oriented level.

---

# 1. Purpose

A **Decision Theme (DT)** is a composable logic module that:

- consumes semantic roles from the Dictionary or other DTs
- applies relationships, constraints, and derivations
- provides new or refined roles back into the lattice

DTs form the **logic layer** of the Decision Themes system.

---

# 2. Responsibilities

DTs are responsible for:

1. Implementing **domain-specific logic**, such as:
	 - typographic scales
	 - spacing systems
	 - surface hierarchies
	 - device or mode adjustments

2. Declaring **typed connectors** (requires/provides) used by the Composer.

3. Remaining **data-agnostic** about content: DTs style roles, not specific text.

---

# 3. File Structure

```json
{
	"id": "DT-<name>",
	"version": "0.1",
	"requires": [ /* connector specs */ ],
	"provides": [ /* connector specs */ ],
	"logic": { /* implementation-defined */ },
	"metadata": { /* optional */ }
}
```

Connectors follow the rules in `DT-dt-connector-spec.md`.

---

# 4. DT Archetypes

Common DT types include:

- **Spine DT** – core scale/grid logic
- **Voice DT** – variants like `main`, `expl`, `code`
- **Shared DT** – captions, hints, chips, meta elements
- **Overlay DT** – device, mode, accessibility

These are conventions, not hard requirements.

---

# 5. Lifecycle

1. Composer selects DTs.
2. Composer validates connectors.
3. DTs are ordered via dependency resolution.
4. DTs are executed/applied in that order to build the Effective Theme.

---

# 6. Summary

A Decision Theme is:

> A modular, connector-aware logic unit that transforms semantic roles into concrete, composable design behavior.

