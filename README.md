# StatsPills

A mod for **Voices of the Void** that adds two purchasable pills which permanently slow down
how fast you get hungry and tired.

Built for game version **a09n**.

## What it does

Two new items show up in the shop, **350 points each**:

| Pill | Effect |
|---|---|
| **Hunger Pill** | Reduces the rate at which you lose hunger by `0.2` per pill |
| **Sleep Pill** | Reduces the rate at which you get tired by `0.2` per pill |

The effect stacks up to **5 doses per pill type**: at 5 doses the corresponding drain rate reaches
`0`, so you stop losing hunger (or getting tired) entirely. Taking a 6th pill does nothing and
prints `Maximum number of pills taken`.

Doses are **persistent** — they are written to the save file (`Bp_PillSave`, keys
`hungerPillTaken` / `sleepPillTaken`) and re-applied on load by `ModActor`, so the bonus survives
quitting the game.

## Installation (players)

1. Voices of the Void **a09n**.
2. Install **Fusion** by *NynrahGhost* — required, the mod will not load without it.
3. Drop the mod's `.pak` file into:

   ```
   <VotV install>/VotV/Content/Paks/LogicMods/
   ```

   Create the `LogicMods` folder if it does not exist yet.
4. Launch the game — the two pills appear in the shop at 350 points each.

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

2. Clone this repo **at the root of that same Unreal project** — only `Content/Mods/StatsPills/`
   and `VotV.uproject` are versioned here, the game project itself is not:

   ```
   <VotV Project>/
     VotV.uproject
     Content/
       Mods/
         StatsPills/   <- this repo
   ```

3. Open the project in the Unreal Editor and package the mod through its `PrimaryAssetLabel`,
   then install the resulting `.pak` as described above.

## Contents

| Asset | Role |
|---|---|
| `ModActor` | Mod entry point — reads the save and applies `hungerDraining` / `sleepDraining` |
| `BP_PillConsumable` | Hunger Pill (consumable actor) |
| `BP_PillSleep` | Sleep Pill (consumable actor) |
| `Bp_PillSave` | SaveGame object tracking doses taken |
| `PILL_ONE`, `PILL_TWO` | Pill meshes |
| `RED`, `BLUE`, `WHITE` | Materials |
| `PrimaryAssetLabel` | Packaging label (mod chunk) |
| `_Content/main/datatables/_list_props` | Item definitions (display name, description, mesh) |
| `_Content/main/datatables/_list_store` | Shop entries and prices (350 each) |
