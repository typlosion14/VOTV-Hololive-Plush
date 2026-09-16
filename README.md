# HololivePlush

A mod for **Voices of the Void** that adds a collection of **36 Hololive-themed plushies** to hunt
down, collect and decorate your base with.

Built for game version **a09n**.

## What it does

A new item shows up in the shop: the **Random Hololive Plush Bag**. Open it to get a random plush
from the collection. Your collection progress is saved with your game.

## The collection

### Halloween BeegSmol outfits

| Plush | Talent |
|---|---|
| Amelia Halloween Plush | Watson Amelia |
| Bae Halloween Plush | Hakos Baelz |
| Calliope Halloween Plush | Mori Calliope |
| Fauna Halloween Plush | Ceres Fauna |
| Gura Halloween Plush | Gawr Gura |
| Ina Halloween Plush | Ninomae Ina'nis |
| IRyS Halloween Plush | IRyS |
| Kiara Halloween Plush | Takanashi Kiara |
| Kronii Halloween Plush | Ouro Kronii |
| Mumei Halloween Plush | Nanashi Mumei |

### Talents

| Plush | Talent |
|---|---|
| Sana Plush | Tsukumo Sana |
| ???? | ???? |

### Mascots and fans

| Plush | Talent |
|---|---|
| Ankimo Plush | Tokino Sora's mascot |
| Baerat Plush | Hakos Baelz's fan |
| Bloom Plush | One of IRyS' mascots |
| Gloom Plush | One of IRyS' mascots |
| Boros Plush | Ouro Kronii's mascot |
| BreadDog Plush | Tsukumo Sana's mascot |
| Chattino Plush | Raora Panthera's fan |
| Chumbud Plush | Gawr Gura's fan |
| DeadBeat Figure | Mori Calliope's fan |
| Friend Plush | Nanashi Mumei's mascot |
| Gremurin Plush | Gigi Murin's fan |
| Jailbird Plush | Nerissa Ravencroft's fan |
| Kronies Plush | Ouro Kronii's fan |
| MrSqueaks Plush | Hakos Baelz's mascot |
| Nekko | Momosuzu Nene's fan |
| Nemu Plush | Ceres Fauna's mascot |
| Poyoyo Plush | Nakiri Ayame's mascot |
| Black SSRB | Shishiro Botan's fan |
| Camo SSRB | Shishiro Botan's fan |
| White SSRB | Shishiro Botan's fan |
| Sukonbu Plush | Shirakami Fubuki's friend |
| Takodachi Plush | Ninomae Ina'nis' fan |
| Teamate Plush | Watson Amelia's fan |
| Udin Plush | Kureiji Ollie's mascot |

## Installation (players)

1. Voices of the Void **a09n**.
2. Install **Fusion** by *NynrahGhost* — required, the mod will not load without it.
3. Drop the mod's `.pak` file into:

   ```
   <VotV install>/VotV/Content/Paks/LogicMods/
   ```

   Create the `LogicMods` folder if it does not exist yet.
4. Launch the game — the **Random Hololive Plush Bag** appears in the shop.

## Setup (reusing this project in Unreal)

This section is only needed if you want to **open, modify or rebuild the mod** in the Unreal
Editor. Players do not need any of it.

### Requirements

- **ghostMapping** — [modestimpala/VotV_ghostmap](https://github.com/modestimpala/VotV_ghostmap),
  the recreated VotV asset library used for ghost-referencing (GUID-matched structs, interfaces
  and materials). It is required to open and build this mod, since the blueprints reference the
  game's own assets and datatables.

### Steps

1. Get the ghostmapping (Unreal Editor **closed**):

   ```bash
   git lfs install
   git clone https://github.com/modestimpala/VotV_ghostmap.git
   ```

   Drag its `Content` folder into your mod project's base directory so it merges with the
   existing `Content/`.

2. Clone this repo **at the root of that same Unreal project** — only `VotV.uproject`, `Config/`,
   `Content/Mods/HololivePlush/` and `ThunderstoreAssets/` are versioned here, the game project
   itself is not:

   ```
   <VotV Project>/
     VotV.uproject
     Config/
     Content/
       Mods/
         HololivePlush/   <- this repo
     ThunderstoreAssets/
   ```

3. Open the project in the Unreal Editor and package the mod through its `PrimaryAssetLabel`,
   then install the resulting `.pak` as described above.
   `Config/DefaultPakFileRules.ini` keeps any skeletal mesh, skeleton or physics asset out of the
   pak — the plush blueprints only use the `*Static` meshes.

## Contents

| Asset / folder | Role |
|---|---|
| `ModActor` | Mod entry point |
| `BP_RandomPlushBag` | Random Hololive Plush Bag — gives a random plush when opened |
| `Bp_HololivePlushSave` | SaveGame object tracking the collection progress |
| `<Plush>/` (e.g. `Amelia/`, `SSRB/`) | One folder per plush: blueprint (`BP_*`), static mesh (`*Static`), textures and materials |
| `PlushBag/` | Loot bag mesh and material |
| `CouncilRysPlushies_Tex`, `CouncilRysPlushies_Tex_Mat` | Shared texture and material for the Council/IRyS plushies |
| `PrimaryAssetLabel` | Packaging label (mod chunk) |
| `_Content/main/datatables/_list_props` | Item definitions (display name, description, mesh) |
| `_Content/main/datatables/_list_store` | Shop entry for the plush bag |
| `ThunderstoreAssets/` | Thunderstore package: `manifest.json`, `icon.png`, `README.md`, `CHANGELOG.md`, built `.pak` |

## Credits

All 3D models come from [Sketchfab](https://sketchfab.com). Huge thanks to their authors!

- This work is based on ["Smol HoloMyth Halloween Costumes!"](https://sketchfab.com/3d-models/smol-holomyth-halloween-costumes-1e2305d63e084c1e966630496b6deb5b) by [Seafoam](https://sketchfab.com/seafoam) licensed under [CC-BY-NC-4.0](http://creativecommons.org/licenses/by-nc/4.0/)
- This work is based on ["BeegSmol Halloween Costumes! - Hololive EN"](https://sketchfab.com/3d-models/beegsmol-halloween-costumes-hololive-en-c74fd24b9c7b4d939c24e1123077b33e) by [Seafoam](https://sketchfab.com/seafoam) licensed under [CC-BY-NC-4.0](http://creativecommons.org/licenses/by-nc/4.0/)
- This work is based on ["Hololive Council + IRyS Plushies"](https://sketchfab.com/3d-models/hololive-council-irys-plushies-0c24e6bd692a4b9d9d4259590253dc81) by [Seafoam](https://sketchfab.com/seafoam) licensed under [CC-BY-NC-4.0](http://creativecommons.org/licenses/by-nc/4.0/)
- This work is based on ["BEEGSmol CouncilRyS! - Hololive EN"](https://sketchfab.com/3d-models/beegsmol-councilrys-hololive-en-5517f50fd178493fa29b075d870351bd) by [Seafoam](https://sketchfab.com/seafoam) licensed under [CC-BY-NC-4.0](http://creativecommons.org/licenses/by-nc/4.0/)
- This work is based on ["Poyoyo - Nakiri Ayame / Hololive"](https://sketchfab.com/3d-models/poyoyo-nakiri-ayame-hololive-4a94cbf2174b4658932b5b307da7294a) by [Nekupaska](https://sketchfab.com/nekubaba213) licensed under [CC-BY-4.0](http://creativecommons.org/licenses/by/4.0/)
- This work is based on ["Jailbird"](https://sketchfab.com/3d-models/jailbird-db9826f6a54e4c7fbba0eaea2821ab7f) by [scootscoot](https://sketchfab.com/sc00tsc00t) licensed under [CC-BY-4.0](http://creativecommons.org/licenses/by/4.0/)
- This work is based on ["Udin"](https://sketchfab.com/3d-models/udin-f9aab4d50449491e8ce45dd1f9ff70f7) by [Hasksoft](https://sketchfab.com/Hasksoft) licensed under [CC-BY-4.0](http://creativecommons.org/licenses/by/4.0/)
- This work is based on ["Chumbud, Shrimp"](https://sketchfab.com/3d-models/chumbud-shrimp-a7efd84e6ead4d0e9eb97d01d3040f64) by [Mr.Lime](https://sketchfab.com/Mr_Lime_2) licensed under [CC-BY-4.0](http://creativecommons.org/licenses/by/4.0/)
- This work is based on ["[Hololive EN] Kronies"](https://sketchfab.com/3d-models/hololive-en-kronies-bd273e37223c4a7fb1e492fad1e6ac5b) by [Welloy](https://sketchfab.com/hiwelloy) licensed under [CC-BY-4.0](http://creativecommons.org/licenses/by/4.0/)
- This work is based on ["[Hololive EN] Baelz's Baerats"](https://sketchfab.com/3d-models/hololive-en-baelzs-baerats-135917bbf3744448b74d82f2d887a5f0) by [Welloy](https://sketchfab.com/hiwelloy) licensed under [CC-BY-4.0](http://creativecommons.org/licenses/by/4.0/)
- This work is based on ["Hololive - Ankimo"](https://sketchfab.com/3d-models/hololive-ankimo-e594cbcc97034d55a52f41871813b070) by [KirbyDX](https://sketchfab.com/kirbydx) licensed under [CC-BY-4.0](http://creativecommons.org/licenses/by/4.0/)
- This work is based on ["Gremurin Hololive Gigi Murin"](https://sketchfab.com/3d-models/gremurin-hololive-gigi-murin-5f691ed53916419c94f7e2802644d054) by [ruru](https://sketchfab.com/ruuru_dayo) licensed under the [Sketchfab Free Standard license](https://sketchfab.com/licenses)
- This work is based on ["Chattini Model"](https://sketchfab.com/3d-models/chattini-model-ec2d67dc5838471f8d1837d904384d2e) by [GustavoMagno](https://sketchfab.com/GustavoMagno) licensed under [CC-BY-4.0](http://creativecommons.org/licenses/by/4.0/)
- This work is based on ["Fubuki Shirakami Sukonbu"](https://sketchfab.com/3d-models/fubuki-shirakami-sukonbu-f4eda326e94f4614b3e7f5aec57816a2) by [Ikxi](https://sketchfab.com/Ikxi) licensed under [CC-BY-NC-4.0](http://creativecommons.org/licenses/by-nc/4.0/)
- This work is based on ["Nene's Mandrakes_Hololive"](https://sketchfab.com/3d-models/nenes-mandrakes-hololive-d168c04013534be094c0adfb641454ec) by [Armored Interactive](https://sketchfab.com/ychiang6) licensed under [CC-BY-4.0](http://creativecommons.org/licenses/by/4.0/)
- This work is based on ["SSRBs_2.0_Hololive"](https://sketchfab.com/3d-models/ssrbs-20-hololive-62cc3ea9db7749a29a5dc4fcf48598b4) by [Armored Interactive](https://sketchfab.com/ychiang6) licensed under [CC-BY-4.0](http://creativecommons.org/licenses/by/4.0/)
- This work is based on ["AmexGators"](https://sketchfab.com/3d-models/amexgators-7499917deb1c47f6b50bb6806852531b) by [MrLagr6](https://sketchfab.com/MrLagr6) licensed under [CC-BY-4.0](http://creativecommons.org/licenses/by/4.0/)
- This work is based on ["Deadbeat"](https://sketchfab.com/3d-models/deadbeat-12a4d2cf83f0406ca91d46a6e8485c53) by [BunnyGame](https://sketchfab.com/BunnyGameTW) licensed under [CC-BY-NC-4.0](http://creativecommons.org/licenses/by-nc/4.0/)
- This work is based on ["Takodachi_Rigged_Hololive"](https://sketchfab.com/3d-models/takodachi-rigged-hololive-fdc37694dcd24bb18184b5ed69fd760a) by [Armored Interactive](https://sketchfab.com/ychiang6) licensed under [CC-BY-4.0](http://creativecommons.org/licenses/by/4.0/)
- This work is based on ["(XB1101 - 09) Bag O' Loot (Normal Test)"](https://sketchfab.com/3d-models/xb1101-09-bag-o-loot-normal-test-5ccbf4f2c72642a69c4ac8853f6972f2) by [Jotham Bate](https://sketchfab.com/Jovakiin) licensed under [CC-BY-4.0](http://creativecommons.org/licenses/by/4.0/)
