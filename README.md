# Decision Themes
### A Cascading Decision System for Semantic, Modular Design Logic

**Decision Themes (DT)** is an architecture for building design systems using *semantic roles*, *modular logic units*, and a *lattice-based composition model*. It introduces a new category of design tooling based on **cascading decisions**, not style sheets.

This repository contains the full intellectual architecture of Decision Themes, including:
- Prior art disclosures
- Formal specifications
- Conceptual architecture
- Example Value Themes, Dictionaries, Decision Themes, and Composers

DT is licensed under **MIT** to ensure long-term openness and prevent enclosure.

---

# 📐 What Is Decision Themes?

Decision Themes is a **five-layer design system architecture**:

```
VT → Dictionary → DT Lattice → Composer → Effective Theme → Exports
```

It separates:
- **values** (fonts, colors, spacing)
- **semantics** (roles, surfaces, voices)
- **logic** (Decision Themes / DT modules)
- **composition** (the Composer’s dependency-driven assembly)
- **resolved output** (Effective Theme)

This creates a **deterministic, modular, scalable** foundation for building complex design systems across media: web, print, apps, ebooks, dashboards, and more.

---

# 🧠 Core Concepts

### **Value Theme (VT)**
Non-semantic raw design values.

### **Decision Themes Dictionary (DTD)**
Defines semantic primitives (e.g., `body`, `h1`, `surface.main`, `caption`).

### **Decision Themes (DTs)**
Modular logic units with typed connectors.
Form a **lattice** via requires/provides relationships.

### **Composer (DDC)**
Declarative build file:
- selects DT modules
- declares platforms/modes/voices
- validates connectors
- resolves into an Effective Theme

### **Effective Theme (ET)**
Fully resolved design configuration.
Consumed by exporters.

---

# 🏗️ Repository Structure

```
.
├── docs/
│   ├── prior-art/           # Defensive publication (legally important)
│   ├── spec/                # Implementation-facing specifications
│   ├── architecture/        # Conceptual & theoretical foundations
│   └── examples/            # JSON examples (VT, DTD, DT, Composer)
└── LICENSE                  # MIT License
```

### Folder Overview

#### ✔ `docs/prior-art/`
Contains the full defensive publication, establishing Decision Themes as public, timestamped prior art. See: [docs/prior-art/README.md](docs/prior-art/README.md)

#### ✔ `docs/spec/`
Defines contracts for VT, Dictionary, DTs, Composer, ET, Machines, and Exporters. See: [docs/spec/README.md](docs/spec/README.md)

#### ✔ `docs/architecture/`
Explains the theoretical model: lattice, semantics, layering, connectors. See: [docs/architecture/README.md](docs/architecture/README.md)

#### ✔ `docs/examples/`
Reference JSON files for a Book MVP system. See the examples folder: [docs/examples/](docs/examples/)

---

# 🔭 High-Level Diagram

```
VT
  ▼
Dictionary (semantic layer)
  ▼
DT Lattice (logic modules)
  ▼
Composer (assembly, validation)
  ▼
Effective Theme (resolved configuration)
  ▼
Exporters (CSS, tokens, EPUB, PDF, app themes)
```

---

# 🚀 Quick Start — Understanding the Flow

### **1. Start with the Value Theme**
Defines fonts, sizes, colors, spacing. Example: [docs/examples/VT-brand-seed.json](docs/examples/VT-brand-seed.json)

### **2. Choose or generate a Dictionary**
Defines semantic roles for your domain. Example: [docs/examples/DT-dictionary-book-mvp.json](docs/examples/DT-dictionary-book-mvp.json)

### **3. Select Decision Themes**
Each DT adds logic: typography, relationships, device rules, accessibility overlays. See examples in [docs/examples/](docs/examples/)

### **4. Build a Composer**
Declarative file that:
- picks DT modules
- sets platform & mode
- resolves into an Effective Theme
Example: [docs/examples/DT-composer-book-mvp.json](docs/examples/DT-composer-book-mpv.json)

### **5. Export**
Use exporters to generate:
- CSS
- JSON design tokens
- print/PDF templates
- EPUB styles
- native app themes

---

# 🎯 Why Decision Themes?

Because design systems need:
- semantics, not raw styles
- modular logic, not monolithic configs
- reproducibility, not guesswork
- scalable branching structures
- multi-platform consistency
- deterministic output

And because content can be analyzed → turned into semantics → and dynamically bound to themes.

Decision Themes transforms design from a manual craft into a **semantic, generative system**.

---

# 📚 Where to Start Reading

If you're new: read in this order:
1. [docs/architecture/DT-architecture-overview.md](docs/architecture/DT-architecture-overview.md)
2. [docs/architecture/DT-layered-model.md](docs/architecture/DT-layered-model.md)
3. [docs/architecture/DT-design-lattice-theory.md](docs/architecture/DT-design-lattice-theory.md)
4. [docs/spec/README.md](docs/spec/README.md)
5. [docs/prior-art/DT-defensive-publication.md](docs/prior-art/DT-defensive-publication.md)

Then explore the example JSONs in [docs/examples/](docs/examples/).

---

# 🔒 License
[LICENSE](LICENSE)

All architecture documents are open and released as prior art to prevent enclosure.

---

If you want to generate badges, add diagrams, or create a `CONTRIBUTING.md`, just let me know.
