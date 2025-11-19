# DT-defensive-publication.md
### Decision Themes – Defensive Publication (v0.1)
### Status: Public Prior Art Disclosure (MIT License)
### Date: 2025

---

# 1. Purpose of This Publication

This document discloses the architecture, mechanisms, workflows, and module interactions of **Decision Themes**, a system for constructing **custom design lattices** using:

- Value Themes (VT)
- Decision Themes Dictionaries (DTD)
- Decision Themes (DTs)
- a Design Decision Composer (DDC)
- and a multi-stage content → design → output pipeline

This publication is released as **public prior art**, preventing any third party from claiming exclusive patent rights on the concepts or mechanisms described.

---

# 2. Summary of the System

Decision Themes introduces a **five-layer design system architecture**:

1. **Value Theme (VT)**  
   Raw values only (typefaces, colors, spacing seeds, etc.).

2. **Decision Themes Dictionary (DTD)**  
   *First semantic layer*: defines roles, surfaces, semantic primitives.

3. **Decision Themes (DTs)**  
   Modular logic modules that attach via typed connectors and form a constraint-based lattice.

4. **Design Decision Composer (DDC)**  
   Declarative build recipe that selects DTs, platforms, modes, accessibility, outputs.

5. **Effective Theme (ET)**  
   Fully resolved, deterministic configuration produced after validation & cascade.

Additionally, Decision Themes enables:

- content-aware dictionary generation
- connector-based dependency validation
- deterministic multi-context exports (CSS, tokens, PDF, EPUB, app themes)
- a complete three-machine pipeline: Modeler → DTS → Renderer

---

# 3. Architecture Overview

## 3.1 Layered Flow

```
VT  →  Dictionary  →  DT Lattice  →  Composer  →  Effective Theme  →  Exports
```

- VT defines raw values.  
- Dictionary defines semantic primitives.  
- DTs define relationships and constraints.  
- Composer selects and assembles DTs into a coherent system.  
- ET is the final, resolved configuration used for rendering.

---

# 4. Value Theme (VT)

The VT contains **raw inputs** with no semantics:

- typefaces
- base sizes
- scale ratios
- spacing seeds
- color anchors (paper, ink, accent)
- breakpoints
- surface anchors

VT is the bottom of the system.

---

# 5. Dictionary (Decision Themes Dictionary, DTD)

The Dictionary is the **first semantic layer**.

### Responsibilities:

- **Requires** specific VT anchors
- **Provides** semantic primitives:
  - text roles (`body`, `h1`, `code.block`, `caption`)
  - surface roles (`surface.main`, `surface.sidebar`)
  - semantic colors (`primary`, `secondary`, `accent`)
- Defines the **semantic footprint** (role set)
- Provides **connector metadata** used by DTs

The Dictionary defines *meaning*, not logic or appearance.

---

# 6. Decision Themes (DTs)

DTs are **modular logic units** attaching to the Dictionary or other DTs via typed connectors.

Each DT defines:

- a list of **requires** connectors
- a list of **provides** connectors
- a **footprint** (roles + optional properties)
- transformation logic (relationships, derivations, constraints)

DTs compose into a **lattice**:

- forks: multiple DTs depending on one parent
- joins: DTs requiring multiple branches
- overlays: device, mode, accessibility layers

DTs are ordered via dependency resolution (topological sort).

---

# 7. Connector System

Connectors encode compatibility between modules.

### Connector fields:

```
id: string
domain: string                 // typography, surfaces, color, spacing…
direction: "requires" | "provides"
footprint:
  roles: string[]              // semantic roles
  properties?: string[]        // optional attributes
required: boolean
```

### Compatibility rule:

A DT’s requires connector attaches to a provider connector if:

1. domains match  
2. required roles ⊆ provided roles  
3. required properties ⊆ provided properties (if defined)

This subset rule ensures safe composition (Lego-like).

---

# 8. Decision Themes Lattice (DAG)

When assembled, DTs form a **dependency DAG**:

- Dictionary at the base
- Spine DT
- Voice DTs (main/expl/code)
- Shared relationship DTs (caption/hint/chip)
- overlays (mobile/tablet/dark/WCAG)

The lattice expresses design logic mathematically through:

- inheritance
- specialization
- branching
- joining
- contextual overlays

The Composer ensures the DAG is valid (no cycles, no missing dependencies).

---

# 9. Design Decision Composer (DDC)

The Composer is the **assembly layer**.

### It declares:

- which DTs are included
- which platforms, modes, voices, accessibility levels
- which outputs (web/pdf/epub/app)
- optional composition order
- validation rules

### The Composer performs:

- connector validation
- dependency graph resolution
- cascade execution
- multi-output generation

This produces a deterministic **Effective Theme**.

---

# 10. Effective Theme (ET)

The ET contains the **fully resolved design system**:

- typography (all roles and variants)
- surfaces
- colors
- spacing
- device-specific adjustments
- mode-specific variants
- accessibility overlays

It is ready for export into:

- CSS
- JSON tokens
- EPUB stylesheets
- app theme files
- PDF typesetting engines

ET is deterministic: same inputs = same ET.

---

# 11. Three-Machine Pipeline

The system includes an end-to-end workflow:

### Machine A — **Content Modeler**

- analyzes content (doc/XML/markdown/AI output)
- proposes a Dictionary
- seeds VT values
- generates a Composer draft
- outputs semantic tagging for content

### Machine B — **Decision Themes Studio (DTS)**

- refine VT
- refine Dictionary (optional)
- select/configure DTs
- generate Effective Theme
- preview variants (mobile/main, laptop/expl, etc.)

### Machine C — **Content Renderer**

- maps content semantics → Effective Theme roles
- applies platform/mode/a11y variations
- generates final artifacts (HTML/PDF/EPUB/app themes)

---

# 12. Example Domain-Specific Dictionaries

To support different domains:

- Book MVP: `body`, `h1`, `button`
- Brand Guide: 5-colors, surfaces, heading/body
- Markdown: `h1–h6`, `paragraph`, `blockquote`, `code.block`
- Educational Book:
  - main/expl voices
  - captions, hints, chips
  - sidebars, exercises, warnings

Each Dictionary defines a unique semantic footprint.  
The DT lattice adapts to that footprint automatically.

---

# 13. Novelty Claims (Protected by This Publication)

### Claim 1 — Dictionary as semantic layer
A dictionary between raw tokens and logic modules.

### Claim 2 — Connector-based module assembly
Using typed footprints and subset matching.

### Claim 3 — Custom design lattices
A composable DAG of DT logic modules.

### Claim 4 — Composer as assembly layer
Declarative selection of DTs, platforms, modes, accessibility, outputs.

### Claim 5 — Deterministic cascade resolution
Value→semantic→logic→context pipeline.

### Claim 6 — Content-driven dictionary generation
Semantic extraction from content to propose design primitives.

### Claim 7 — Multi-modal export
Single Effective Theme generating multiple formats.

These claims are released as public, timestamped prior art under MIT License.

---

# 14. Conclusion

Decision Themes defines:

- a new architecture
- a new set of layers
- a new compositional model
- a new semantic abstraction
- a new lattice logic
- a new pipeline
- and a new connector contract

for building **custom, domain-specific design systems** through deterministic composition.

This document establishes those mechanisms as **unambiguously public prior art**.

