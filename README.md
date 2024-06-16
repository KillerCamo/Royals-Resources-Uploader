# Minecraft Dungeons Mod Kit

This is a set of tools to make it easier to work on mods for Minecraft Dungeons. The tools will only run on Windows.

The original repo can be found [here](https://github.com/Dokucraft/Dungeons-Mod-Kit/tree/master) made by the Dokucraft team.

## Prerequisites

These need to be installed in order to use the tools:

- [Python 3.8+](https://www.microsoft.com/en-us/p/python-38/9mssztt1n39l)
- Unreal Engine 4.22

You can download Unreal Engine for free through the Epic Games Store app, just **make sure to select version 4.22.x**. Using a different version of UE4 will cause all sorts of strange issues.

# Item Instance Blueprint/MeleeWeaponGearInstance

Item BP's will use and change variables from the `MeleeWeaponGearItemInstance` class file, this file has the foundation variables as well as the UStructs for both the `ItemId` and `ConfiguredAttackVariants` variables
this class file will **directly** be used (any weapon instance is a child of this class) which means all the variables should be defined from the class file rather than the child file.

**Please note** this class file is reversed engineered and __cannot__ be found by extracting game code.

## Breakdown for an Instance BP File
- `ConfiguredAttackVariants` - this is an array of a class file that has all the data for the name, attack sequence, slot, pushback, etc. 
- `GearActor` - This is an object path of the weapon that is currently the weapon instance
- `OverrideAnimationInstance` - some weapons use an animation override which is an animation blueprint generated class
- `InventoryDropSound` is an asset path to the sound file
- `ItemIdName` Name variable
- `bIsBigWeapon` this is used for pretty much one weapon in the game, default value is false
- `ItemId`  should be a single referencing struct with a Name field called `SerializedId` 
- `RootComponent` should be null -> this seems not like a value thing but like an actual thing relating to the  SCS `RootNodes` field
- `PrimaryActorTick` and `bAllowTickBeforeBeginPlay` are built in values in the actor class

## Other Notes
- Default values do not show up in files unless a struct array has no values set


