# DT-architecture-overview.md
### Decision Themes — Architecture Overview (v0.1)

The Decision Themes architecture is built on a **layered, semantic-to-logical pipeline**, enabling domain-specific, modular, and reproducible design systems.

---

# 1. The Five Layers

1. **Value Theme (VT)** — raw, non-semantic values
2. **Dictionary (DTD)** — semantic footprint (roles, surfaces, voices)
3. **Decision Themes (DTs)** — modular logic units forming a lattice
4. **Composer (DDC)** — declarative assembly and validation
5. **Effective Theme (ET)** — final resolved configuration

---

# 2. Core Architectural Principles

### 2.1 Explicit Semantics
Semantics live in Dictionaries, not in VT or DTs.

### 2.2 Logic via Composition
DTs stack into a dependency-resolved lattice via connectors.

### 2.3 Determinism
Same inputs → same ET.

### 2.4 Contextual Overlays
Platform, mode, and accessibility overlays are treated as DTs.

### 2.5 Non-destructive Pipeline
Each layer enriches but never mutates lower layers.

---

# 3. Architecture in Practice

- VT provides the stable primitives.
- DTD defines meaning.
- DTs encode domain logic.
- Composer assembles and resolves.
- ET powers exporters and renderers.

This separation ensures clarity, scalability, and reusability.

