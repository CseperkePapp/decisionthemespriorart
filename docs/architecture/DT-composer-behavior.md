# DT-composer-behavior.md
### Decision Themes — Composer Behavior (v0.1)

The Composer defines how selected DT modules are assembled into a resolved design system.

---

# 1. Declarative Decisions
The Composer specifies:
- platforms
- modes
- accessibility levels
- voices
- outputs

---

# 2. Validation Behavior
- checks connector compatibility
- enforces domain consistency
- blocks cycles
- emits warnings for unused modules

---

# 3. Cascade Behavior
Execution order:
1. VT
2. Dictionary
3. DT logic
4. contextual overlays

---

# 4. Output Behavior
Produces the **Effective Theme**, which is:
- deterministic
- variant-aware
- ready for export

---

# 5. Extensibility
New DT modules can be added without modifying existing Composer logic, as long as connectors validate.

