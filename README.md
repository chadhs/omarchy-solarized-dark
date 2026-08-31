# Solarized Dark for Omarchy

A [Solarized Dark](https://ethanschoonover.com/solarized/) theme for
[Omarchy](https://omarchy.org/), built on the canonical 16-color Solarized
palette (eight monotones, eight accents) by Ethan Schoonover.

Companion theme: [omarchy-solarized-light](https://github.com/chadhs/omarchy-solarized-light)
— the two share accent values and mirrored monotone assignments, so switching
between them keeps the same feel, per Solarized's dual-mode design.

![Solarized Dark preview](preview.png)

## Install

```bash
omarchy theme install https://github.com/chadhs/omarchy-solarized-dark.git
```

Or clone it wherever you like and copy/symlink it to
`~/.config/omarchy/themes/solarized-dark/`, then:

```bash
omarchy theme set solarized-dark
```

### Update

Pull the latest changes into an installed clone and re-apply it:

```bash
omarchy theme update          # pulls all git-installed themes
omarchy theme set solarized-dark
```

## Palette

| Solarized | Hex       | Omarchy role |
|-----------|-----------|--------------|
| base03    | `#002b36` | `background`, terminal color 0 |
| base02    | `#073642` | `selection`, `lighter_background`, `hyprland_inactive_border` |
| base01    | `#586e75` | `muted` (comments, disabled text, bright black) |
| base00    | `#657b83` | `dark_foreground` |
| base0     | `#839496` | `foreground` (body text) |
| base1     | `#93a1a1` | `light_foreground`, `bright_foreground` (cursor) |
| yellow    | `#b58900` | `yellow` |
| orange    | `#cb4b16` | `orange` |
| red       | `#dc322f` | `red` |
| magenta   | `#d33682` | `magenta` |
| violet    | `#6c71c4` | `brown` (8th accent slot) |
| blue      | `#268bd2` | `accent`, `blue` |
| cyan      | `#2aa198` | `cyan`, second active-border gradient stop |
| green     | `#859900` | `green` |

### Design notes

- Text pairing follows Schoonover's own reading pairs rather than a new
  hierarchy: `base03:base0` for body text on the plain background and
  `base02:base1` for text on highlighted surfaces (selection, raised panels,
  cursorline). The L\*a\*b lightness difference between the two pairs is
  identical by design.
- `darker_background` shades (`#002028`, `#00151b`) are base03 darkened
  toward black, keeping the hue, for sinks/floats; `lighter_background` is
  base02, the canonical highlighted-surface tone.
- The Hyprland active border is the blue→cyan gradient (`rgba(268bd2aa)
  rgba(2aa198aa) 45deg`) rendered at ~67% alpha for a softer focus
  highlight over the base03 background; the inactive border is base02.
- Accents are kept identical between the dark and light themes, matching
  Solarized's terminal palettes, so syntax colors don't shift between modes.

## Recommended window look

Omarchy themes can't set Hyprland's decoration, so the window look this
theme was designed against — slightly rounded corners and a thin 1px
border to match the softened focus highlight — is a one-time user config.
Add to `~/.config/hypr/looknfeel.lua`:

```lua
hl.config({
  decoration = {
    rounding = 8,
  },
})

hl.config({
  general = {
    border_size = 1,
  },
})
```

Hyprland reloads on save; validate with `hyprctl reload` followed by
`hyprctl configerrors`.

## Backgrounds

Three generated, palette-only wallpapers in `backgrounds/`:

1. `1-ripples.png` — cyan quarter-circle arcs rippling out of the
   bottom-right corner, fading as they spread (default)
2. `2-ribbon.png` — translucent blue and cyan diagonal bands sweeping
   across the base03 background
3. `3-orbit.png` — blue disc with concentric cyan orbit rings in the
   top-right, on the base03 background
4. `4-ridge.png` — calm low-poly landscape: a single faceted sky
   over three gently rolling ridges, a round blue moon, and hairlines along
   the ridges sweeping through all eight Solarized accents — red, orange,
   yellow, green, and cyan on the far ridge; blue, violet, and magenta on
   the mid ridge. This is also the wallpaper used for the theme previews.

Cycle with `omarchy theme bg next`, or add your own to
`~/.config/omarchy/backgrounds/solarized-dark/`.

## Scope

`colors.toml` is the source of truth: Omarchy generates the terminal configs
(Alacritty, Foot, Kitty, Ghostty), Hyprland border colors, Neovim, btop,
VS Code, and shell/bar theming from it at `omarchy theme set` time. This repo
ships only palette-derived color data and imagery.

## Credits

- [Solarized](https://ethanschoonover.com/solarized/) palette by Ethan
  Schoonover (MIT).
- Role mapping informed by the same reading-pair approach used in the
  [Solarized theme for T3 Code](https://github.com/chadhs/dotfiles/tree/master/utils/t3-code/themes/solarized).
