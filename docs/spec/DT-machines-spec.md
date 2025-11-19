# DT-machines-spec.md
### Decision Themes — Machines Specification (Modeler, DTS, Renderer) (v0.1)

---

# 1. Purpose

The **three machines** are conceptual components that describe how Decision Themes integrates with content workflows:

1. **Machine A — Content Modeler**
2. **Machine B — Decision Themes Studio (DTS)**
3. **Machine C — Renderer**

They are not required to be separate executables, but they describe separated responsibilities.

---

# 2. Machine A — Content Modeler

**Inputs:**
- raw content (docs, markdown, XML, AI output)
- a design or editorial brief

**Responsibilities:**
- analyze document structure and semantics
- propose a suitable Dictionary footprint
- propose VT seeds (fonts, base sizes, color anchors)
- draft a Composer file (platforms, voices, outputs)

**Outputs:**
- VT candidate
- Dictionary candidate
- Composer draft
- optional semantic tagging for content

---

# 3. Machine B — Decision Themes Studio (DTS)

**Inputs:**
- VT
- Dictionary
- Composer draft
- DT library

**Responsibilities:**
- refine VT values
- edit/confirm Dictionary
- select and configure DT modules
- run validation (connectors, lattice integrity)
- resolve into an Effective Theme

**Outputs:**
- final VT
- final Dictionary
- final Composer
- Effective Theme (ET)

---

# 4. Machine C — Renderer

**Inputs:**
- Effective Theme (ET)
- structured / tagged content

**Responsibilities:**
- map content semantic roles to ET roles
- apply platform/mode/a11y variants
- generate final outputs (HTML, PDF, EPUB, app themes)

**Outputs:**
- user-facing artifacts (pages, screens, documents)

---

# 5. Summary

The three machines describe:

> A pipeline where content is analyzed into semantics (A), resolved into a design lattice (B), and rendered into final artifacts (C).

