# dimarch-theme

> Sage — visual identity for DimArch OS

**Modern system. Old soul.**

Theme components for DimArch OS — Arch Linux + Hyprland.
Inspired by GNOME 2 and MATE. Built on Wayland in 2026.

---

## Palette

**One sage, five weathered materials.**

![DimArch Sage Palette](assets/palette.svg)

Sage is not one of six equal colours — it is the anchor. It carries every tier of text,
every interface state, and roughly 18% of what is on screen at any moment, against ~4%
for all five accents combined. It is also the loudest step in the palette, so the eye
reaches it first.

The accents are named after what they are made of, because a colour named by its hue has
nothing to defend it during a later cleanup:

| Family | Hue | Carries |
|---|---|---|
| **Sage** | 153° | brand, all text, every interface state |
| **Clay** | 0° | errors, deletions, broken links, critical load |
| **Ochre** | 36° | change, archives, duration, attention without alarm |
| **Lichen** | 88° | executables, Node, caffeine |
| **Patina** | 176° | links, documents, symlinks, cool weather |
| **Heather** | 334° | images, video, media, selection |

### The rule that holds it together

> **Sage marks state. Accents mark category.**

Sage means *what is happening* — active, selected, focused, successful. Accents mean
*what a thing is* — a file type, a language, a git status, a kind of signal. An accent
may never mark a state, and sage may never mark a category.

Without that rule the brand quietly decays. Measured across 53 roles, sage had drifted
down to 17% before it was written, and the theme stopped reading as Sage at all. With
it, sage holds 36% — and every one of those roles is something you interact with.

A practical consequence: **at rest the panel is entirely sage.** Colour appears only when
a module has something to report.

### Geometry

The palette occupies a warm arc from 334° to 176°, about 202° long. The range
**177–333° is deliberately empty** — no azure, no violet, no synthetic purple. Cold hues
were tried and rejected on a live test: next to a warm, low-saturation sage they read as
foreign rather than complementary.

Neighbour spacing is 26° / 36° / 52° / 65° / 23°, all clear of the 20° minimum.

Every accent works through **depth** rather than brightness. At sage's own lightness an
accent competes with it and reads dusty; darker and slightly more saturated, it grounds
the composition instead.

### Contrast

Measured against both grounds — `#0d1919` (chrome) and `#171b1b` (terminal).

- `base` and `bright` tiers clear **4.5:1**, the WCAG AA threshold for text
- `dim` tiers are for fills, borders and markers — **not for small text**
- `sage.dim` is the one exception at 4.89:1, doubling as the faded text tier

The light palette is not an inversion: every accent is recalculated for a cream ground
and verified against the darker of the two light surfaces.

---

## Colour tokens

`colors/palette.json` is the source of truth. It has two layers — `ramp` holds the hue
families, `role` maps meaning onto them. **Components reference roles, never ramp
entries.** That indirection is the point: to merge `link` into the brand green you would
first have to answer whether links should be indistinguishable from body text.

| File | Description |
|---|---|
| [`colors/palette.json`](colors/palette.json) | Source of truth — 22 ramp tokens, 63 roles, ANSI 16 |
| [`colors/sage-dark.css`](colors/sage-dark.css) | CSS custom properties + GTK3 `@define-color` fallback |
| [`colors/sage-light.css`](colors/sage-light.css) | Light variant — recalculated, not inverted |
| [`ROADMAP.md`](ROADMAP.md) | Component migration checklist |

### ANSI 16

The terminal protocol needs sixteen slots, filled from the palette. Slot 4 resolves to
lichen rather than a second near-identical cyan — blue and green previously sat on the
same hue (152° and 153°), so the terminal nominally had two colours and effectively one.

| Slot | Token | Slot | Token |
|---|---|---|---|
| 1 red | `clay.base` | 9 | `clay.bright` |
| 2 green | `sage.base` | 10 | `sage.bright` |
| 3 yellow | `ochre.base` | 11 | `ochre.bright` |
| 4 blue | `lichen.base` | 12 | `lichen.bright` |
| 5 magenta | `heather.base` | 13 | `heather.bright` |
| 6 cyan | `patina.base` | 14 | `patina.bright` |

Slots 0, 7, 8 and 15 are the neutrals. Slot 0 is structural — never a readable foreground.

---

## Components

| Component | Status |
|---|---|
| Waybar | ✅ themed |
| Ghostty | ✅ themed |
| rofi | ✅ themed |
| swaync | ✅ themed |
| swayosd | ✅ themed |
| hyprlock | ✅ themed |
| zathura | ✅ themed |
| yazi | ✅ themed |
| starship | ✅ themed |
| mpv / uosc | ✅ themed |
| swayimg | ✅ themed |
| herdr | ✅ themed |
| VSCode | ✅ themed |
| Obsidian | ✅ themed |
| GTK theme | 📋 planned |
| SDDM | 📋 planned |
| Telegram | 📋 planned |
| Firefox | 📋 planned |

Component configs live in [dmitrax/dimarch](https://github.com/dmitrax/dimarch); this
repository holds the values they consume. Migration of the themed components onto the
current palette is tracked in [`ROADMAP.md`](ROADMAP.md).

---

## Related repositories

| Repo | Description |
|---|---|
| [dmitrax/dimarch](https://github.com/dmitrax/dimarch) | Main installer, phase scripts, dotfiles |
| [dmitrax/dimarch-taskbar](https://github.com/dmitrax/dimarch-taskbar) | Bottom panel — Python + GTK4 |
| [dmitrax/dimarch-sddm-theme](https://github.com/dmitrax/dimarch-sddm-theme) | SDDM login theme — QML |

---

*DimArch OS — Personal Arch Linux setup by dmitrax*
