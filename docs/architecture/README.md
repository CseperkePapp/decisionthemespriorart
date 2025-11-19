# Decision Themes — Architecture Documentation
### `docs/architecture/README.md`
### Version 0.1

This directory contains the **conceptual and theoretical foundations** of the Decision Themes architecture. These documents describe *why* the system is structured the way it is, and explain the mathematical, semantic, and logical principles behind each layer.

Unlike the `spec/` folder (which defines implementation contracts), the files here provide the **mental model** that guides all Decision Themes design and engineering.

---

# 📐 Purpose of the Architecture Folder

The documents in this directory:

- explain the core ideas behind the Decision Themes system
- describe the theoretical model (lattice, connectors, layering)
- map out how semantics, logic, and composition interact
- provide a stable intellectual foundation for implementers and tool authors
- help external developers understand *how* and *why* Decision Themes works

These files are essential reading for anyone implementing DCV, building tooling on top of DTS, or designing new DT modules.

---

# 📦 Contents

### **1. `DT-architecture-overview.md`**
High-level summary of the entire architecture:
- the five layers (VT → Dictionary → DTs → Composer → ET)
- core principles (determinism, semantics-first, composability)
- how data flows through the system

### **2. `DT-design-lattice-theory.md`**
Explains the **lattice model**:
- how DTs form forks, joins, and overlays
- why the system is structured as a DAG
- how users can build their own custom lattices

### **3. `DT-connector-theory.md`**
The conceptual basis for connector logic:
- typed connectors
- footprint structure
- subset compatibility
- why this model is safe and deterministic

### **4. `DT-layered-model.md`**
A breakdown of the five-layer Decision Themes model:
- raw values (VT)
- semantic roles (Dictionary)
- logic modules (DTs)
- declarative composition (Composer)
- resolved output (ET)

### **5. `DT-dictionary-role-system.md`**
Describes the semantic system at the heart of Decision Themes:
- how roles are defined
- why semantics live in the Dictionary, not DTs or VT
- relationship between semantic footprint and logic

### **6. `DT-composer-behavior.md`**
Explains the Composer's architectural responsibilities:
- selection of DT modules
- validation
- dependency graph creation
- cascade execution

---

# 🧭 Relationship to Other Documentation

### **`prior-art/`**
Legal and foundational disclosures that protect the system.

### **`spec/`**
Implementation-facing specifications (contracts and structures).

### **`architecture/`** (this folder)
Conceptual, theoretical, and systemic explanations.

### **`examples/`**
Reference JSON files showing VT, Dictionary, DTs, and Composer usage.

---

# 📚 How to Use These Documents

- Read `DT-architecture-overview.md` first — it sets the stage.
- Use `DT-layered-model.md` to understand the big picture.
- Use `DT-design-lattice-theory.md` and `DT-connector-theory.md` to design new DTs.
- Use `DT-dictionary-role-system.md` when defining semantic footprints.
- Use `DT-composer-behavior.md` to understand how compositions are resolved.

These documents form the **mental toolkit** behind all Decision Themes engineering.

---

# ✔️ Extending the Architecture

Additional files may be added as the system evolves:
- motion systems
- surface engines
- metadata DTs
- multi-Dictionary systems
- advanced lattice patterns

The architecture folder is the home for all conceptual expansions.
