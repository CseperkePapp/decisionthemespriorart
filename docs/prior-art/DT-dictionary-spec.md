# DT-dictionary-spec.md
### Decision Themes — Dictionary Specification (v0.1)
### Status: Public Prior Art Disclosure

---

# 1. Purpose of the Dictionary

A **Decision Themes Dictionary (DTD)** is the **first semantic layer** above the Value Theme (VT).  
It defines the **semantic footprint** — the named roles, surfaces, and conceptual units that Decision Themes (DTs) attach to.

The Dictionary does **not** define styles or logic.  
It defines **meaning**.

By establishing semantic primitives, the Dictionary enables reusable, modular design logic across different content types, devices, and outputs.

---

# 2. Responsibilities of the Dictionary

A Dictionary performs three functions:

## 2.1 Requires VT Anchors
It declares which raw values from the VT it depends on. Examples:

- typography base (font families, base size, scale ratio, line-height seed)
- spacing base (baseline grid, spacing units)
- color anchors (paper, ink, accent)
- surface anchors
- breakpoints

These required anchors establish the foundation for its semantic definitions.

## 2.2 Provides Semantic Roles
The Dictionary defines the **semantic primitives** used throughout the design system, such as:

- text roles: `body`, `h1`, `h2`, `code.inline`, `caption`
- voice roles: `main.body`, `expl.body`
- surface roles: `surface.main`, `surface.sidebar`, `surface.warning`
- semantic color roles: `primary`, `secondary`, `accent`
- structural roles: `blockquote`, `example.title`, `info-chip`

These roles act as the "Lego studs" that DTs attach to.

## 2.3 Defines the Footprint
The Dictionary defines the **expected surface area** (footprint) for DTs:

- which roles exist
- their domain categories (typography, surfaces, color, spacing)
- optional properties (size, weight, lineHeight, elevation, contrast, etc.)

DTs must match parts of this footprint using subset-based connector rules.

---

# 3. Connector Metadata

Each role exposed by the Dictionary is accompanied by a **provides connector**, describing:

```
id: string               // e.g. "typography.spine"
domain: string           // "typography", "surface", "color"
footprint: {
  roles: string[]        // e.g. ["body", "h1", "h2"]
  properties?: string[]  // e.g. ["size", "lineHeight", "weight"]
}
direction: "provides"    // Dictionary only provides
required: false           // connectors exposed for DTs
```

This metadata enables:

- DT module validation
- compatibility checks
- deterministic composition ordering
- safe assembly of custom lattices

---

# 4. Structure of a Dictionary File (Conceptual)

A Dictionary file contains:

```json
{
  "id": "DT-dictionary-<name>",
  "version": "0.1",

  "requires": [
    { "id": "typography.base", "roles": ["base"], "properties": ["size", "scale"] },
    { "id": "color.anchors", "roles": ["paper", "ink", "accent"] },
    { "id": "spacing.base", "roles": ["baseline"] }
  ],

  "provides": [
    { "id": "typography.spine", "roles": ["body", "h1", "h2"] },
    { "id": "surface.main", "roles": ["surface.main"] },
    { "id": "color.semantic", "roles": ["primary", "secondary", "accent"] }
  ],

  "roles": {
    "body": {},
    "h1": {},
    "h2": {},
    "surface.main": {},
    "primary": {},
    "secondary": {},
    "accent": {}
  }
}
```

No logic.  
No styling.  
No DT decisions.  
Just semantics.

---

# 5. Relationship to Other Layers

## 5.1 Relationship to VT
- Dictionary depends on VT.
- VT provides the raw values that fill the Dictionary's semantic structure.

## 5.2 Relationship to DTs
- DTs rely on Dictionary-provided semantic primitives.
- No DT can refer to a role absent from the Dictionary footprint.

## 5.3 Relationship to Composer
- Composer does not define semantics.
- Composer selects which DTs operate over the Dictionary's footprint.

## 5.4 Relationship to Effective Theme
- Effective Theme is built through:
  - VT values
  - Dictionary semantics
  - DT logic
  - Composer decisions

---

# 6. Example Dictionaries (Conceptual)

## 6.1 Book MVP Dictionary
Roles:
- `body`, `h1`, `button`

Requires:
- typography.base
- spacing.baseline
- color.ink/paper
- breakpoints: mobile/laptop

## 6.2 Brand Guide Dictionary
Roles:
- `primary`, `secondary`, `accent`, `neutral`
- `brand.body`, `brand.heading`
- `surface.main`, `surface.inverse`

## 6.3 Markdown Dictionary
Roles:
- `h1–h6`, `paragraph`, `blockquote`, `code.inline`, `code.block`, `link`, `list.item`

## 6.4 Educational Book Dictionary
Roles:
- `main.body`, `main.h1`, `expl.body`, `caption`, `hint`, `chip`
- `surface.sidebar`, `surface.example`, `surface.warning`

Each Dictionary defines a **different semantic footprint**, but operates on the same engine.

---

# 7. Novelty (Claims Protected by This Spec)

### Claim 1 — The Dictionary as a Semantic Layer
A dictionary between raw values and logic modules.

### Claim 2 — Typed Semantic Footprints
Dictionaries define footprints (roles + properties) that DTs must match.

### Claim 3 — Semantic/Logic Layer Separation
Dictionaries define meaning; DTs define logic.

### Claim 4 — Cross-Dictionary Design Lattices
The same DT engine can operate across different Dictionary footprints.

### Claim 5 — Content-Driven Dictionary Generation
Dictionaries may be synthesized by analyzing content structure.

---

# 8. Conclusion

The **Decision Themes Dictionary** is:

> The first semantic layer that defines roles and primitives which design logic attaches to.

Publishing this spec establishes it as **prior art**, preventing exclusive ownership by any party.

