# Nord Light theme for ARGVUS

Official ARGVUS Light theme, `nord-light`, with its Sticky and Float variants.

[![CI](https://github.com/argvus/argvus-theme-nord-light/actions/workflows/ci.yml/badge.svg)](https://github.com/argvus/argvus-theme-nord-light/actions/workflows/ci.yml)
[![Release](https://github.com/argvus/argvus-theme-nord-light/actions/workflows/release.yml/badge.svg)](https://github.com/argvus/argvus-theme-nord-light/actions/workflows/release.yml)
[![License](https://img.shields.io/badge/License-GPL--3.0-blue.svg)](LICENSE)

## Fidelity to the upstream palette

Nord Light is **not** an official palette separate from Nord. It is an ARGVUS
Light interpretation built from the official Nord palette (`nord0`-`nord15`,
values unchanged) and Nord's bright-ambiance recommendations. Every color that is
not an exact Nord value is an ARGVUS-derived mapping and is listed below.

## Theme identity

| Field | Value |
| --- | --- |
| Theme ID | `nord-light` (Float variant: `nord-light-float`, a geometry mode of the same palette) |
| Display name | Nord Light |
| Mode | `light` |
| Default highlight | `#5E81AC` (`nord10`) |
| Package | `argvus-theme-nord-light` |
| Wallpaper | `/usr/share/backgrounds/argvus/abstract/light/nord-light-abstract-light.jxl` |

## Palette

Official Nord values used directly:

| Role | Value |
| --- | --- |
| Background | `nord6` `#ECEFF4` |
| Alternate surface | `nord5` `#E5E9F0` |
| Surface | `nord4` `#D8DEE9` |
| Text | `nord0` `#2E3440` |
| Muted text | `nord1` `#3B4252` (titles), `nord3` `#4C566A` (dim/subtle text) |
| Accent | `nord10` `#5E81AC` |
| Accent alternate | `nord9` `#81A1C1` (inactive selection) |
| Cyan | `nord7` `#8FBCBB` |
| Error / danger / warning / success / special | `nord11` `#BF616A` / `nord12` `#D08770` / `nord13` `#EBCB8B` / `nord14` `#A3BE8C` / `nord15` `#B48EAD` |

ARGVUS-derived tokens (`mix(A, B, p)` is `p` percent of `B` over `A`):

| Token | Hex | Formula | Use |
| --- | --- | --- | --- |
| Card | `#E8ECF2` | `mix(nord6, nord5, 50%)` | card and panel surfaces |
| Hover | `#DEE4EC` | `mix(nord5, nord4, 50%)` | hovered rows |
| Border | `#7D8696` | `mix(nord4, nord3, 65%)` | input and panel borders, 3:1 on every surface |
| Faint | `#9CA2AF` | `mix(nord3, nord6, 50%)` | faint, placeholder and disabled decoration |
| Accent dark | `#547296` | `mix(nord10, nord0, 20%)` | pressed accent |
| Critical tint | `#CF939A` | `mix(nord11, nord6, 35%)` | critical notification background |

## Contrast

Measured with WCAG 2.x against the surfaces the theme uses:

| Pair | Ratio | Note |
| --- | ---: | --- |
| `nord0` on `nord6` (body text) | 10.84 | meets 4.5:1 |
| `nord3` on `nord6` (dim text) | 6.40 | meets 4.5:1 |
| `nord6` on `nord10` (primary button text) | 3.50 | use bold text at button size (14px or larger) |
| Border on `nord6`, `nord5`, card | 3.18, 3.01, 3.10 | meets 3:1 |
| `nord10` on `nord6` (focus ring, icons) | 3.50 | meets 3:1 |
| `nord0` on critical tint | 4.93 | meets 4.5:1 |

Known limitations (documented, not hidden):

- `nord10` on `nord4` is 2.98:1. Do not use the accent as small text on a `nord4`
  surface; use it for icons, borders and large text.
- `nord0` on `nord12` (danger fill) is 4.39:1. Use the fill for badges with bold
  text.
- `nord13` (warning), `nord14` (success) and `nord7` (cyan) are fills, not text.
  As text on the background they are 1.35:1, 1.77:1 and 1.81:1, so the theme
  writes text on them in `nord0` (8.00:1 and 6.13:1).
- Disabled and placeholder text use the faint token and are exempt from WCAG
  text ratios.

## Build and install

On Arch Linux or a compatible distribution:

```sh
sudo pacman -S --needed base-devel git shellcheck
make validate
make build
make install
```

`make build` creates a deterministic local source archive in
`build/artifacts/` and a package in `build/dist/`. `make install` requires
`sudo` and installs the one package found in that directory.

Metadata only:

```sh
make validate
makepkg -p packaging/arch/remote/PKGBUILD --printsrcinfo
```

See [packaging/arch/README.md](packaging/arch/README.md) for the difference
between the local and release PKGBUILDs.

## Layout

The payload in `src/` is copied to the package root (`cp -a src/. pkgdir/`).
`src/usr/...` installs under `/usr/`, and `src/etc/...` installs under `/etc/`.
Nothing that mirrors `/` lives outside `src/`. The installed wallpaper is the
author's `.jxl`, copied byte for byte.

## Documentation

- [DEVELOPMENT.md](DEVELOPMENT.md): layout, checks and releases
- [CONTRIBUTING.md](https://github.com/argvus/.github/blob/main/CONTRIBUTING.md): contribution workflow
- [SECURITY.md](https://github.com/argvus/.github/blob/main/SECURITY.md): private vulnerability reports
- [Code of Conduct](https://github.com/argvus/.github/blob/main/policies/CODE_OF_CONDUCT.md) — community standards
- [AI usage policy](https://github.com/argvus/.github/blob/main/policies/IA_USAGE.md) — rules for AI-assisted contributions

## License

SPDX: `GPL-3.0-only`. See [LICENSE](LICENSE).
