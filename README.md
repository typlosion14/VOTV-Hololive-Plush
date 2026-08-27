# StatsPills

Mod pour **Voices of the Void** (Unreal Engine).

Des pilules consommables qui agissent sur les stats du joueur (sommeil, sauvegarde, etc.).

## Contenu

| Asset | Role |
|---|---|
| `ModActor` | Point d'entree du mod |
| `BP_PillConsumable` | Blueprint de base des pilules |
| `BP_PillSleep`, `Bp_PillSave` | Effets specifiques |
| `PILL_ONE`, `PILL_TWO` | Meshes / assets des pilules |
| `RED`, `BLUE`, `WHITE` | Materiaux |
| `PrimaryAssetLabel` | Label de packaging (chunk du mod) |
| `_Content/main/datatables/` | Entrees dans les datatables du jeu (props, store) |

## Installation (developpement)

Le depot se clone **a la racine du projet Unreal de VotV** : seul
`Content/Mods/StatsPills/` est versionne, le projet du jeu ne l'est pas.

```
<VotV Project>/
  Content/
    Mods/
      StatsPills/   <- ce depot
```

Ouvrir ensuite le projet dans l'editeur Unreal et packager le mod via son
`PrimaryAssetLabel`.
