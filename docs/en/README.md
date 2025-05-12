# SKinLoader - Plant Skin Loading System
**Languages:**
[English](docs/en/README.md) | [简体中文](docs/zh-CN/README.md) 
The Plant Skin Loader allows players to add custom skins to in-game plants through simple file operations. By creating folders in a specified directory and placing asset bundles, players can add switchable skins to corresponding plants in the almanac.

## Directory Structure Specification

```
SkinLoader/
├── 0/               # 0 represents Peashooter's Almanac ID
│   └── Peashooter   # Packaged AssetBundles
├── 1/
│   └── SunFlower
├── 2/
│   └── CherryBomb
├── 3/
│   └── WallNut
└── .../             # Other PlantIDs
    └── ...          # Corresponding plant asset bundles
```

## Quick Start Guide

### Prerequisites

1. Obtain or create plant prefabs:
   - Can be extracted from original game assets
   - Can be custom created
   - Must contain two critical components:
     * Prefab - The in-game plant display
     * Preview - The card display version

2. Use the [AssetBundles-Browser tool](https://github.com/Unity-Technologies/AssetBundles-Browser.git) for packaging

### Example: Adding Peashooter Skin

1. Create an AssetBundle containing:
   - `PeaShooterPrefab`
   - `PeaShooterPreview`
2. Name the bundle exactly: `Peashooter`
3. Place in directory structure:
   ```
   SkinLoader/0/Peashooter
   ```
4. The game will automatically detect and add skin-switching functionality

## Detailed Creation Process

### 1. Building Plant Prefabs

Unity workflow:

1. Create new Unity project and install AssetBundles-Browser
2. Essential components:
   - **Animator Controller** requirements:
     * Must include idle and shoot animations
     * Special plants require unique animations (e.g., Chomper's bite)
     * Add Float parameter "Speed" to all animations
   - **Prefab** requirements:
     * Must contain Shadow and Shoot objects
     * Multi-projectile plants need Shoot1, Shoot2, etc.

### 2. Creating Card Previews

Simple preview creation:
1. Create empty GameObject named "PlantName+Preview" (e.g., "PeashooterPreview")
2. Add Sprite Renderer component
3. Drag desired sprite into the component

### 3. Packaging Assets

After prefab completion:
1. Package using AssetBundles-Browser
2. Output location: `AssetBundles/StandaloneWindows`

### 4. Automatic Skin Registration

Final steps:
1. Verify AssetBundle name exactly matches plant name
2. Create PlantID-named folder in SkinLoader
3. Place asset bundle in the folder
4. Launch game to see skins automatically appear

## Important Notes

- Ensure all naming is precise
- Animator Controller parameters must be complete
- AssetBundles must include both Prefab and Preview
- File paths are case-sensitive
- Test skins in-game before distribution