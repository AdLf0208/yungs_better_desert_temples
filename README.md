# YUNG's Better Desert Temples — a Horizon port

**YUNG's Better Desert Temples** is a Minecraft mod. Redesigns & enhances vanilla's desert temples. This repository is a **port of it to [Horizon](https://github.com/horizon-rust/horizon)**, the Rust engine for Minecraft Java 26.3. It carries the complete source of the port plus the content files it ships, and installs as a single `.hmod` package.

Upstream: [YUNG-GANG/YUNGs-Better-Desert-Temples](https://github.com/YUNG-GANG/YUNGs-Better-Desert-Temples) — licence **LGPL-3.0-only**.

| | |
|---|---|
| Upstream mod | YUNG's Better Desert Temples ([source](https://github.com/YUNG-GANG/YUNGs-Better-Desert-Temples)) |
| Ported to | Horizon 0b14f8a, Minecraft Java 26.3, mod API `0.2` |
| Package | `betterdeserttemples.hmod` (install it with the Horizon launcher) |
| Licence | **LGPL-3.0-only** — the upstream mod's licence; see [Licence and credit](#licence-and-credit) |

## What this port implements

The port's behaviour is recorded in the repository's `notes.md` (the campaign's per-mod record); this slice ships what that file describes.

## Not yet ported

- `lime_banner_processor` / `red_banner_processor` — 52 + 8 placeholders stay
- `armor_stand_processor` — the 2 armour stands keep the armour the template
- `item_frame_processor` — the 66 item frames show their placeholder item
- `pharaoh_processor` — the tomb's husk keeps its NBT without the pharaoh's
- `sponge_processor` — 80 % of the sponges become a plain unlit candle and 20 %
- `purpur_pillar_processor` / `quartz_pillar_processor` — the pillar block
- `yellow_stained_glass_processor` — the layer becomes sandstone (exact), but
- `acacia_wood_processor` — the distribution is exact; the mod's "waterlogged

## Installing

1. Install the [Horizon launcher](https://github.com/horizon-rust/horizon/releases) (0.2.70 or newer).
2. Add `betterdeserttemples.hmod` to the instance's mods.
3. The package is pinned to a specific Horizon build; the launcher checks that pin.

## Licence and credit

YUNG's Better Desert Temples was created by its upstream authors; the code, models and assets in the original mod
remain theirs and are used here under **LGPL-3.0-only**. The Rust in this repository is a clean-room
rewrite for Horizon, not a translation of the original source.

- `LICENSE` — the upstream licence text.
- `LICENSE-NOTICE.md` — what this port carries and where it came from.
- The upstream project: https://github.com/YUNG-GANG/YUNGs-Better-Desert-Temples

## Technical details

```
horizon-mod.toml   package manifest (id, version, api, [native] pin)
Cargo.toml         the crate; depends on `horizon-mod-api` from the fetched SDK
src/               lib.rs (the one `impl Hooks`), runtime.rs (pure logic + tests), glue
assets/ data/      the content the package ships
tools/             content generators and the e2e scenario
```

- Build: `cargo horizon-mod build` (packages; it does not compile against the game).
- Test: `cargo test`, `cargo clippy --all-targets -- -D warnings`.
- In-game: `ports/tools/launcher-game.sh run betterdeserttemples` in the campaign tree, or install the
  `.hmod` and play; the harness scenario is `tools/e2e.sh`.

This repository is generated from the campaign's port at `ports/betterdeserttemples/`; the port's own
`notes.md` is the full record (decisions, traps, evidence).
