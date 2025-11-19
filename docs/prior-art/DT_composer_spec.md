# DT-composer-spec.md
### Decision Themes — Design Decision Composer Specification (v0.1)
### Status: Public Prior Art Disclosure

---

# 1. Purpose

The **Design Decision Composer (DDC)** is the *assembly layer* of the Decision Themes architecture.  
It does not define values, semantics, or design logic. Instead:

> **The Composer selects and orchestrates VT, Dictionary, and DT modules into a single resolved Effective Theme.**

It acts as a declarative **build recipe** controlling:
- which logic modules (DTs) are included
- which platforms, modes, and voices are active
- how contextual overlays (device, a11y, dark mode) are applied
- which exporters produce final outputs

The Composer enforces **validity**, **ordering**, and **deterministic resolution**.

---

# 2. Responsibilities

The Composer has six primary responsibilities:

### 2.1 Reference Inputs
- one Value Theme (VT)
- one Dictionary (DTD)
- a list of DT modules

### 2.2 Declare Project-Level Decisions
These describe the *context* the design system must support:
- **platforms**: mobile, tablet, laptop, desktop
- **modes**: light, dark
- **accessibility levels**: WCAG-AA, WCAG-AAA
- **voices**: main, explanatory, code, etc.
- **export targets**: web, tokens, pdf, epub, app themes

### 2.3 Validate DT Compatibility
Using connector matching rules:
- all DT `requires` must be satisfied
- domains must match
- roles must be subset-compatible
- no dependency cycles allowed

### 2.4 Determine Composition Order
If no explicit order is set:
- perform a **topological sort** based on connector dependencies
- spine → voices → shared → overlays is the natural order

### 2.5 Resolve the Cascade
Sequentially apply:
1. VT
2. Dictionary semantics
3. DT logic (in dependency order)
4. Overlays (device, mode, a11y)

This produces a single **Effective Theme**.

### 2.6 Produce Final Outputs
Based on project decisions, exporters may generate:
- CSS
- JSON design tokens
- EPUB stylesheets
- PDF layout templates
- native app themes

---

# 3. Composer Document Structure

A Composer file is a structured JSON-like configuration.

### Conceptual Schema

```json
{
  "id": "DT-composer-<name>",
  "version": "0.1",

  "vt": "VT-<id>",
  "dictionary": "DT-dictionary-<id>",

  "decisions": {
    "platforms": ["mobile", "laptop"],
    "voices": ["main", "expl"],
    "modes": ["light", "dark"],
    "accessibility": ["wcag-aa"],
    "outputs": ["web", "tokens-json"]
  },

  "dts": [
    { "id": "DT-spine", "source": "DT-spine.json", "enabled": true },
    { "id": "DT-main-voice", "source": "DT-main-voice.json" },
    { "id": "DT-expl-voice", "source": "DT-expl-voice.json" },
    { "id": "DT-device-mobile", "source": "DT-device-mobile.json" }
  ],

  "compositionOrder": [],

  "validation": {
    "failOnMissingConnector": true,
    "warnOnUnusedDT": true,
    "failOnCycle": true
  }
}
```

---

# 4. Composition Algorithm

The Composer resolves a system in **five phases**.

## Phase 1 — Loading & Filtering
- load VT
- load Dictionary
- load DTs
- filter DTs based on project decisions

Examples:
- if `platforms = ["mobile"]`, disable desktop DTs
- if `voices = ["main"]`, disable explanatory DTs

## Phase 2 — Connector Validation
For each DT:
- check `requires` connectors
- ensure provider footprints satisfy subset rules
- detect missing dependencies

Invalid compositions result in warnings or errors.

## Phase 3 — Composition Ordering
If no explicit order:
- build dependency graph
- topological sort
- overlays bubble to the top

Cycles make the build invalid.

## Phase 4 — Cascade Execution
Apply:
- VT → Dictionary → DTs → overlays

This produces a deterministic **EffectiveDT**.

## Phase 5 — Export
Use chosen exporters to produce:
- CSS
- tokens.json
- epub.css
- pdf themes
- app styles

---

# 5. Example Composer (Book MVP)

```json
{
  "id": "DT-composer-book-mvp-demo",
  "version": "0.1",

  "vt": "VT-brand-demo",
  "dictionary": "DT-dictionary-book-mvp",

  "decisions": {
    "platforms": ["mobile", "laptop"],
    "voices": ["main"],
    "modes": ["light"],
    "accessibility": ["wcag-aa"],
    "outputs": ["web", "pdf"]
  },

  "dts": [
    { "id": "DT-spine", "source": "DT-spine.json" },
    { "id": "DT-main-voice", "source": "DT-main-voice.json" },
    { "id": "DT-device-mobile", "source": "DT-device-mobile.json" },
    { "id": "DT-device-laptop", "source": "DT-device-laptop.json" }
  ]
}
```

---

# 6. Novelty (Claims Protected by This Spec)

### Claim 1 — The Composer as a Declarative Build Layer
Selecting DT modules and design contexts through a separate, declarative configuration.

### Claim 2 — Dependency-Based DT Ordering
Topological resolution of DT modules based on typed connectors.

### Claim 3 — Contextual Overlays
Platforms, modes, accessibility, and export targets applied as Composer decisions.

### Claim 4 — Deterministic Cascade Assembly
Value → semantics → logic → overlays resolved into a single Effective Theme.

### Claim 5 — Unified Multi-Output Pipeline
A single resolved configuration exported to multiple formats.

---

# 7. Conclusion

The **Design Decision Composer** defines:

> a deterministic, declarative method for assembling modular logic units into a fully resolved, multi-context design system.

Publishing this document establishes the Composer as **public prior art**, protecting the architecture from proprietary patent claims.

