# StellarWarfareModEditor
## Setup
1. Install Unity Editor with exactly this version [2020.2.0b7](https://unity3d.com/unity/beta/2020.2.0b7) (You need Unity Hub to login. Check the version while creating the Editor Project.)
2. Import the unity [package](https://github.com/MrBoneCrash/StellarWarfareModEditor/blob/main/SWEditor_4.unitypackage).

## Ship Modification

### Edit
1. Go to Assets/Resources/Mod and open the ModExample prefab (you can rename it)
1. Add all needed things (models, textures, …) to this folder
1. Dont change the scale of a gameobject
1. Add your mesh as child of the „Mesh“ game object
1. Add your mesh to the MeshCollider on the root object
1. Place the TurretSlot[1..5] on the positions where the turrets should be (Dont rotate them, even below the ship, this will be detected automatically. Make sure the Turrets are not inside the mesh collider.)
1. TurretSlot count can be 1 – 5, ModuleSlot count can be 1 – 4
1. Placement of the ModuleSlots should be inside of the model
1. Place ImpactPoint[1..5] on places on your ship where it should be targeted (cockpit, thrusters, …) (Should be exactly 5)
1. Enable the MeshRenderer on the shield and fit the size.
1. Move, duplicate or edit the engineFlames as you like.
1. Set the height of the selection circle.

### Textures
If you have color variants, add the textures to the mod folder.
The textures should have the same name followed by a color postfix.

#### Available Colors:
- Blue
- Black
- Grey
- Red
- White
- Yellow
- Azure
- Green

#### Structure:
- Standart texture name: Texture_Blue
- Variant texture name: Texture_Red
- Variant texture name: Texture_Green
- ...

### Config
1. Edit the config.json (versions are not relevant at the moment)
1. The shipModifications.json is a list of objects which are individual ships

```
{
  Name: Name of the ShipFrame ingame,
  Description: Description of the ShipFrame ingame,
  NameOfObject: Name of the prefab you edited,
  ShipBaseStats: { Object defining the stats of the ShipFrame
    Health: float,
    Speed: float,
    TurnRate: float,
    Acceleration: float,
    MetalCost: float,
    PowerCost: float,
    BuildTime: float – Time in seconds,
    ShipClass: string - [ Harvester | Corvette | Frigate | Cruiser | Destroyer | Battlecruiser | Super Battlecruiser ],
    ThumbNail: string – Name of the thumbnail file
  },
  UnitProperties: { Object defining properties of the ShipFrame
    UnitType: „Unit“ – Only unit available at the moment,
    ArmorType: string – [ Light | Medium | Heavy ]
  },
  BuiltInModules: string[] - List of built-in modules - [ Composite Shield | Laser Shield | Mammoth Shield | Modular Shield | Shield Booster | Shield Generator | Shield Module | Strengthened bulkheads | Structural integrity enhancer | Toughnax | Reload cycler | Reload optimization | Simplified construction | Coolant capacitators | Heatsinks | Recycled materials | Recycled plating | Smart constructing | Illion Cells | Recycled powercells | Arphlax | Impact enhancer | Roanoke Arcor | Weapon booster | Glassius Lens | Optic sensor | Arteus enhancer | Engine booster ]
}
```

## Module Modification

1. The modulesModification.json is a list of objects which are individual modules

```
{
	"Name": Name of the Module,
	"Description": Description of the Module,
	"Flavour": Story Description of the Module,
	"FlatBonuses": {
		"Health": 0,
		"Speed": 0,
		"WeaponRange": 0,
		"WeaponDamage": 0,
		"NumProjectilesPerSalvo": 0,
		"MetalCostReduction": 0,
		"PowerCostReduction": 0,
		"ShieldHealth": 0
	},
	"PercentageBonuses": {
		"Health": 0,
		"Speed": 0,
		"WeaponCoolDown": 0,
		"WeaponRange": 0,
		"WeaponDamage": 0,
		"NumProjectilesPerSalvo": 0,
		"MetalCostReduction": 0,
		"PowerCostReduction": 0,
		"BuildTimeReduction": 0,
		"ShieldRegeneration": 0,
		"ShieldValueBasedOnHP": 0
	}
}
```

## Finalisation
1. Make sure all needed files (only needed files !!!) are in Assets/Resources/Mod
1. Click on StellarWarfareEditor/Build Mod (Menu at the top)
1. Get your mod file from Assets/ModExport (you may have to update the folder after generation (ctrl + r))
1. Name your mod.unity3d file, this will be the ingame name of your mod. (ExampleMod.unity3d)
1. Put the mod into %Documents%/TenseGames/StellarWarfare/Mods/

## Notes
Muliplayer games can only be played when all players have the same mods.
Modded modules can also be used as built-in module of modded ships. 
If you find a bug, please let us know in the report-bugs channel
