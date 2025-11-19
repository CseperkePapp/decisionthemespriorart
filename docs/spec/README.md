# Decision Themes — Specification Overview
### `docs/spec/README.md`
### Version 0.1

This folder contains the **formal specifications** for all parts of the Decision Themes architecture. These documents define the contracts, responsibilities, and invariants of each layer in the system, independent of any implementation.

The specs in this directory complement the **prior-art documentation**, but are written in a more practical, implementer-focused style.

---

# 📐 Purpose of the `spec/` Folder

The documents here define:
- what each architectural layer is responsible for
- how the layers interact
- what structures are required
- which invariants implementers must respect
- the boundaries between semantic, logical, and output layers

They describe the **stable contracts** of the Decision Themes system.

These specs:
- are implementation-agnostic
- can be used by developers implementing the engine
- can be referenced by DTS UI developers
- remain aligned with the defensive-publication documents

---

# 📦 Included Specifications

### **1. `DT-vt-spec.md` — Value Theme Specification**
Defines the structure and purpose of the **raw value layer**:
- fonts, colors, spacing seeds, breakpoints
- non-semantic, stable anchors
- consumed by Dictionary and DT modules

### **2. `DT-dt-spec.md` — Decision Theme Module Specification**
High-level spec describing DT modules:
- logic modules with typed connectors
- require/provide structure
- domain-specific transformations

### **3. `DT-effective-theme-spec.md` — Effective Theme Specification**
Defines the final resolved design configuration:
- explicit role definitions
- variant structure for platform/mode/a11y
- input for exporters and renderers

### **4. `DT-machines-spec.md` — Three-Machine Pipeline**
Describes the three conceptual machines:
- Machine A: Content Modeler
- Machine B: DTS Editor
- Machine C: Renderer

These clarify how Decision Themes integrates with content workflows.

### **5. `DT-export-spec.md` — Export Layer Specification**
Defines how the Effective Theme is translated into artifacts:
- CSS
- JSON tokens
- EPUB/PDF styles
- app theme formats

Exporters must be stateless and must not modify the Effective Theme.

---

# 🧭 Relationship to Other Documentation

### **`prior-art/`**
Contains the legal/architectural disclosures that protect the system’s novelty.

### **`spec/`** (this folder)
Implementation-focused contracts.

### **`architecture/`**
Conceptual and theoretical descriptions: lattice theory, layering, semantics.

### **`examples/`**
JSON examples showing VT, Dictionary, DT modules, and Composer usage.

Together, these folders form the full Decision Themes documentation set.

---

# ✔️ How to Use These Specs

- Engine developers use them to implement the DCV logic.
- DTS UI developers use them to understand valid structures and constraints.
- External implementers can build compatible engines or exporters.
- They serve as a baseline for versioning and change tracking.

The specs should remain stable; extensions should be additive and versioned.

---

# 📣 Next Steps

If new layers or modules are introduced (e.g., motion, grid systems, metadata DTs), add new spec files here.

The `spec/` folder is the authoritative location for Decision Themes contracts.
