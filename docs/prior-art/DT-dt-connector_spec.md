# DT-dt-connector-spec.md
### Decision Themes — Decision Theme Connector Specification (v0.1)
### Status: Public Prior Art Disclosure

---

# 1. Purpose

A **Decision Theme (DT)** is a modular logic unit that composes into a larger design system through **typed connectors**.  
Connectors define how DT modules attach to:

- the Dictionary (semantic layer)
- other DTs (logic layers)
- the overall lattice (the system's structural graph)

This specification protects the **connector-based compositional model** as prior art.

---

# 2. DT Overview

Each Decision Theme file contains:

```
id
version
requires[]   // typed connectors
provides[]   // typed connectors
logic        // transformation rules (structure-agnostic)
metadata
```

DT modules do not contain raw values (VT) or define new roles (Dictionary).  
They operate *between* semantics and resolution.

---

# 3. Connector Concept

A connector is a **typed dependency edge**. It establishes:

- what the DT *needs* (requires)
- what the DT *exposes* (provides)
- how it fits into the DT lattice
- how it interacts with other logic modules

### Connector fields

```
id: string                     // e.g. "typography.main"
domain: string                 // "typography", "surface", etc.
direction: "requires" | "provides"
footprint:
  roles: string[]              // e.g. ["body", "h1", "h2"]
  properties?: string[]        // optional attributes
required: boolean              // mandatory or optional
roleHint?: "spine" | "voice" | "shared" | "overlay"
```

---

# 4. Footprint Model

The **footprint** defines the structural shape of the connector.

## 4.1 Roles
Semantic identifiers from the Dictionary:
- `body`, `h1`, `h2`
- `main.body`, `expl.body`
- `surface.main`, `surface.sidebar`

## 4.2 Optional Properties
Examples:
- `size`, `lineHeight`, `weight`
- `color`, `contrast`
- `spacing`, `gap`

## 4.3 Domain
Each connector belongs to exactly one domain:
- typography
- surfaces
- spacing
- color
- motion
- or custom user domains

---

# 5. Compatibility Rule (Subset Match)

A DT’s **requires** connector can attach to a **provides** connector when:

```
provider.domain == consumer.domain
consumer.roles ⊆ provider.roles
consumer.properties ⊆ provider.properties (if defined)
```

This is the “Lego brick” rule:
- a DT needing a 2×2 footprint can sit on a 4×4 footprint
- but not the other way around

This ensures **valid, safe, deterministic composition**.

---

# 6. DT Archetypes

DTs fall into four structural types:

## 6.1 Spine DT
Defines system-wide foundation logic: scales, grids, baseline rules.

## 6.2 Voice DT
Defines variant logic for semantic voices: main, explanatory, code, etc.

## 6.3 Shared Relationship DT
Bridges across voices: captions, hints, chips, labels, meta-elements.

## 6.4 Overlay DT
Applies contextual variation:
- device-specific
- accessibility (WCAG)
- mode (dark/light)
- print/export overlays

---

# 7. Logical Flow in a DT

## 7.1 Input
A DT receives:
- semantic roles (provided earlier)
- VT values
- logic context (platform, mode, etc.)

## 7.2 Processing
The DT’s `logic` block defines:
- derivations
- scaling
- constraints
- relationships
- transformations

## 7.3 Output
A DT publishes new or refined roles through `provides` connectors.

---

# 8. Connector Role in the Lattice

Connectors control the formation of the **DT lattice**:

## 8.1 Forking
Multiple DTs require the same semantic footprint.

```
DT-base
 ├─ DT-main
 └─ DT-expl
```

## 8.2 Joining
A DT depends on multiple branches.

```
DT-main ───►
            DT-shared
DT-expl ───►
```

## 8.3 Overlays
Device/mode/a11y DTs sit above the join.

## 8.4 Integrity
The Composer validates:
- missing connectors
- domain mismatches
- footprint mismatches
- dependency cycles

---

# 9. Minimal DT File Example

```json
{
  "id": "DT-main-voice",
  "version": "0.1",

  "requires": [
    {
      "id": "typography.spine",
      "domain": "typography",
      "direction": "requires",
      "footprint": {
        "roles": ["body", "h1", "h2"]
      },
      "required": true,
      "roleHint": "voice"
    }
  ],

  "provides": [
    {
      "id": "typography.main",
      "domain": "typography",
      "direction": "provides",
      "footprint": {
        "roles": ["main.body", "main.h1", "main.h2"]
      }
    }
  ],

  "logic": {}
}
```

---

# 10. Novelty (Claims Protected by This Spec)

### Claim 1 — Typed Connectors for Logic Composition
Connectors with roles/properties/domains define structured module compatibility.

### Claim 2 — Subset-Based Compatibility Rule
Modules compose only when the required footprint is a subset of the provided footprint.

### Claim 3 — Modular Logic Lattice
DTs form branches, merges, and overlays via typed connectors.

### Claim 4 — Semantic to Logic Layer Separation
Semantic roles are defined in the Dictionary; DTs define logic.

### Claim 5 — Overlays as Logic Modules
Contextual layers (device, accessibility, modes) expressed as DT modules.

---

# 11. Conclusion

The Decision Themes connector system defines:

> A typed, deterministic method for assembling modular logic units into a custom constraint-based design lattice.

This document establishes the connector model as **public prior art**, preventing exclusive patent claims.

