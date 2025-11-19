# DT-effective-theme-spec.md
### Decision Themes — Effective Theme Specification (v0.1)

---

# 1. Purpose

The **Effective Theme (ET)** (often `EffectiveDT`) is the **fully resolved design configuration** produced after:

1. VT values are loaded
2. Dictionary semantics are applied
3. DT modules are composed and executed
4. Contextual overlays (platform, mode, accessibility) are applied

ET is the structure that exporters consume.

---

# 2. Responsibilities

ET is responsible for:

- representing all **final roles** and their properties
- encoding **variants** (platform/mode/a11y)
- serving as the **single source of truth** for exports

ET does **not**:

- contain raw VT-only data without semantic binding
- describe how it was produced (no dependency graph)

---

# 3. Shape of an Effective Theme

Conceptual example:

```json
{
	"id": "ET-book-mvp",
	"version": "0.1",
	"roles": {
		"main.body": {
			"fontFamily": "Cormorant",
			"fontSize": 16,
			"lineHeight": 1.4
		},
		"main.h1": {
			"fontFamily": "Cormorant",
			"fontSize": 28,
			"lineHeight": 1.2
		},
		"expl.body": {
			"fontFamily": "Inter",
			"fontSize": 14,
			"lineHeight": 1.5
		},
		"caption": {
			"fontFamily": "Inter",
			"fontSize": 12,
			"lineHeight": 1.4
		}
	},
	"variants": {
		"platform": {
			"mobile": { /* overrides */ },
			"laptop": { /* overrides */ }
		},
		"mode": {
			"light": { /* overrides */ },
			"dark": { /* overrides */ }
		},
		"accessibility": {
			"wcag-aa": { /* overrides */ }
		}
	}
}
```

The exact schema is implementation-defined, but:
- roles are explicit
- variants are clearly separated

---

# 4. Relationship to Other Layers

- VT, Dictionary, DTs, and Composer **produce** ET.
- Exporters **consume** ET.
- Content renderers use ET + structured content.

---

# 5. Determinism

Given the same VT, Dictionary, DT set, and Composer decisions:

> The Effective Theme must be identical across runs.

This determinism is crucial for build reproducibility.

---

# 6. Summary

The Effective Theme is:

> The resolved, variant-aware design configuration that all exporters and renderers rely on.

