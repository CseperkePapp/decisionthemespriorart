# DT-export-spec.md
### Decision Themes — Export Specification (v0.1)

---

# 1. Purpose

The **export layer** describes how an Effective Theme is transformed into concrete artifacts consumable by runtimes, build systems, or design tools.

Exports are **downstream** of ET and must not modify the design logic.

---

# 2. Export Targets

Common export targets include:

- **CSS**
	- variables, utility classes, or component tokens
- **Design Tokens JSON**
	- W3C design token-style structures
- **EPUB / eBook styles**
	- CSS for digital reading systems
- **PDF / print layout templates**
	- styles for typesetting engines
- **Native app themes**
	- token maps for iOS/Android/desktop frameworks

---

# 3. Requirements

Exporters must:

1. Treat ET as read-only input.
2. Express variants (platform/mode/a11y) in a predictable way.
3. Avoid embedding business logic — they are format translators.

---

# 4. Example: Tokens Export (Conceptual)

```json
{
	"typography": {
		"main.body": {
			"fontFamily": { "value": "Cormorant" },
			"fontSize": { "value": 16, "unit": "px" },
			"lineHeight": { "value": 1.4 }
		}
	},
	"color": {
		"ink": { "value": "#111111" },
		"paper": { "value": "#ffffff" }
	}
}
```

---

# 5. Relationship to Other Layers

- Exports sit **after** ET.
- Adding new export formats does not change VT/Dictionary/DT/Composer.
- Exporters can be swapped or extended without altering the design logic.

---

# 6. Summary

The export layer is:

> A family of stateless translators from Effective Theme to runtime or document formats.

