# ReShade + RenoDX setup (SDR)

My ReShade configuration for Crimson Desert: the **Verdant Ember 1.6** preset with tweaks to make faces look less harsh and nights darker, plus the RenoDX add-on settings that go with it.

| File | What it is |
|------|------------|
| `Verdant Ember - RenoDX SDR.ini` | The ReShade preset (the effects stack). |
| `ReShade.ini` | ReShade's own config, which also holds the **RenoDX** settings in `[renodx-preset1]`. |

## Requirements

- **ReShade 6.8.0 with add-on support** (the "Addon" build). RenoDX will not load in the normal build.
- **RenoDX for Crimson Desert** (`renodx-crimsondesert.addon64`) in the game's `bin64/` folder.
- The shader packs the preset uses (prod80, SweetFX, qUINT, LocalContrastCS, AmbientLight, pCamera, SuperDepth3D).
- The game set to **SDR**. This preset is not meant for HDR.

## Install

1. Copy both `.ini` files into `Crimson Desert/bin64/`, next to `dxgi.dll`.
2. Edit `EffectSearchPaths` and `TextureSearchPaths` in `ReShade.ini` to point at your own shader folder. Mine are absolute paths under my home directory.
3. On Linux/Proton, set this Steam launch option so Wine loads ReShade's `dxgi.dll`:

   ```
   WINEDLLOVERRIDES="d3dcompiler_47=n;dxgi=n,b" %command%
   ```

`AutoSavePreset=1` is on, so ReShade overwrites these files while the game is running. Close the game before editing them by hand.

## Changes from Verdant Ember 1.6

### Preset (faces)

| Effect | Setting | Original | Mine |
|--------|---------|----------|------|
| FakeHDR | HDRPower | 1.28 | 1.10 |
| LocalContrastCS | Strength | 0.40 | 0.18 |
| Selective Color v2 | Reds: cyan / black | 0.45 / 0.15 | 0.15 / 0.05 |
| Selective Color v2 | Oranges: saturation | 0.222 | 0.10 |
| Contrast Brightness Saturation | sat_r | -0.20 | -0.10 |
| Color Balance | Highlights blue shift | 0.55 | 0.25 |

### Preset (nights)

Lowering FakeHDR made dark scenes brighter. This darkens them again:

| Effect | Setting | Original | Mine |
|--------|---------|----------|------|
| Shadows Midtones Highlights | Shadow Adjustments: Brightness | 0.30 | 0.011 |

### RenoDX

| Setting | Original | Mine |
|---------|----------|------|
| Sharpening | 20 | 8 |
| Purkinje Effect | Off | On (cooler, less saturated nights) |
| Auto Exposure Darkness | 42 | 20 (had no visible effect for me) |

## Credits

- **Verdant Ember – Gritty Medieval ReShade Overhaul** — <https://www.nexusmods.com/crimsondesert/mods/87>
- **RenoDX** — <https://github.com/clshortfuse/renodx>
- **ReShade** — <https://reshade.me>
