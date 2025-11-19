# DT-vt-spec.md
### Decision Themes — Value Theme Specification (v0.1)

---

# 1. Purpose

The **Value Theme (VT)** is the **raw value layer** of the Decision Themes architecture.

It contains:
- typefaces
- sizes and scale ratios
- spacing units
- color anchors
- breakpoint values
- any other primitive values needed by higher layers

VT is intentionally **non-semantic**: it does not define roles, logic, or relationships.

---

# 2. Responsibilities

The VT is responsible for:

1. Providing stable, named value anchors:
	 - `fonts.primary`, `fonts.secondary`, `fonts.mono`
	 - `sizes.base`, `sizes.scaleRatio`
	 - `colors.paper`, `colors.ink`, `colors.accent`
	 - `spacing.baseline`

2. Remaining independent from domain semantics (no `body`, `h1`, `surface.main` here).

3. Acting as the input to:
	 - Dictionaries (which add semantics)
	 - DT logic modules (which derive styles)

---

# 3. Shape of a VT Document (Conceptual)

```json
{
	"id": "VT-<name>",
	"version": "0.1",
	"fonts": {
		"primary": "...",
		"secondary": "...",
		"mono": "..."
	},
	"sizes": {
		"base": 16,
		"scaleRatio": 1.25,
		"lineHeightBase": 1.4
	},
	"colors": {
		"paper": "#ffffff",
		"ink": "#111111",
		"accent": "#6a4df5"
	},
	"spacing": {
		"baseline": 4
	},
	"breakpoints": {
		"mobile": 480,
		"tablet": 768,
		"laptop": 1024,
		"desktop": 1440
	}
}
```

Implementations may extend this with more domains (motion, borders, shadows, etc.).

---

# 4. Relationship to Other Layers

- **Dictionary** depends on VT to fill semantic roles.
- **DT logic** may read VT values directly for calculations.
- **Composer** references a single VT per composition.

The VT is the lowest layer and has no dependencies.

---

# 5. Invariants

- No semantic role names appear in VT.
- VT must be stable enough that multiple compositions can reuse it.
- VT should be small and focused; higher complexity lives in Dictionary and DTs.

---

# 6. Summary

The Value Theme is:

> A stable, non-semantic container for raw design values that higher layers interpret and transform.

