# DT-dictionary-role-system.md
### Decision Themes — Dictionary Role System (v0.1)

The Dictionary defines the **semantic interface** for the entire system.

---

# 1. Role Types
- text roles (`body`, `h1`, `code.block`)
- voice roles (`main.body`, `expl.body`)
- surface roles (`surface.main`, `surface.sidebar`)
- semantic colors (`primary`, `accent`)

---

# 2. Why Roles Matter
Roles:
- establish meaning independent of logic or styling
- act as the anchors DTs operate on
- define the system’s semantic footprint

---

# 3. Relationship to VT
The Dictionary **requires** VT anchors to bind semantic roles to raw values.

---

# 4. Relationship to DTs
DTs can only transform roles that exist in the Dictionary.

