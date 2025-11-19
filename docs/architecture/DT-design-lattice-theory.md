# DT-design-lattice-theory.md
### Decision Themes — Design Lattice Theory (v0.1)

The Decision Themes lattice is a **directed acyclic graph (DAG)** representing design logic composition.

---

# 1. What is the Lattice?
A lattice is a set of DT modules connected by typed connectors that form:
- **forks** (parallel branches)
- **joins** (merged logic)
- **overlays** (contextual layers)

The result is a structured hierarchy of design decisions.

---

# 2. Roles of the Lattice
- Enforces safe composition
- Ensures valid relationships between logic modules
- Allows users to build *custom* design logic topologies

---

# 3. Types of Nodes

### 3.1 Spine
Base system logic — type scales, baseline grids.

### 3.2 Voices
Main, explanatory, code, freeform.

### 3.3 Shared Elements
Captions, hints, chips.

### 3.4 Device Layers
Mobile, tablet, laptop, desktop.

### 3.5 Accessibility Layers
WCAG-AA, WCAG-AAA.

---

# 4. Mathematical Constraints
- No cycles (DAG enforcement)
- Connectors must satisfy subset match
- Domain consistency required

---

# 5. Custom Lattices
Users may define arbitrary branching structures as long as connectors validate.

The lattice is a **logic fabric**, not a fixed template.

