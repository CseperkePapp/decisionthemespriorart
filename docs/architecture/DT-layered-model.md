# DT-layered-model.md
### Decision Themes — Layered Model (v0.1)

Decision Themes uses a **strictly layered model** where each layer enriches the previous one.

---

# 1. Layers

### ● Layer 1 — VT
Raw design values.

### ● Layer 2 — Dictionary
Semantic roles.

### ● Layer 3 — DTs
Logic transformations.

### ● Layer 4 — Composer
Assembly and validation.

### ● Layer 5 — ET
Final resolved output.

---

# 2. Data Flow
VT → DTD → DTs → Composer → ET → Exports.

Each step adds meaning or logic without overwriting lower-layer information.

---

# 3. Benefits
- separation of concerns
- predictable outputs
- easier debugging
- user-defined lattices

