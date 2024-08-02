---
Layout: page
title: Documentation
permalink: /documentation/
---

# Documentation

***

# 1. Layers

To keep the tile replacement efficient, you should only iterate the tiles of the tile map layers that actually need replacements. For example, you do not need to iterate a static background layer if these tiles should not be replaced.

To facilitate this, the Replacement Settings allow you to set which tile map layers should be included (i.e. have a tile that needs replacing) and which tile map layers should be excluded (i.e. none of the tiles needs replacing). 

Determine which method you prefer. If you have only a few layers that need replacing, add these to the Included Layers but if you have a lot of layers that need replacing and a few that do not, use ExcludedLayers. If no layers are defined in either option, all layers are iterated. 

# 2. Tile Replacement

Steps to replace your tiles with actors and flipbooks:

## 2.1 Replacement method

Choose whether you want to replace the tiles based on Tile Identifier (Tile Set + Tile Index) or Tile User Data Name.

### 2.1a Tile Identifier

Determine the TileIndex of the tiles you want to replace. The easiest way to find the tile index is by selecting the tile in the [Tile Set Editor](https://dev.epicgames.com/documentation/en-us/unreal-engine/paper-2d-tile-sets-and-tile-maps-in-unreal-engine){:target="_blank"}{:rel="noreferrer"}.

__Insert Image here__

Open the ReplacementSettings Data Asset and add a new element to the Actor Mappings array if you want to replace the tile with an actor or the Flipbook Mappings array if you want to replace the tile with a flipbook.

Set the Tile Identifier data of the new element to the Tile Identifier of the tile you want to replace.

### 2.1b Tile User Data Name

Set up the User Data Name for each tile you want to replace by selecting the tile in the [Tile Set Editor](https://dev.epicgames.com/documentation/en-us/unreal-engine/paper-2d-tile-sets-and-tile-maps-in-unreal-engine){:target="_blank"}{:rel="noreferrer"} and filling in the User Data Name field. The User Data Name field can be found in the Single Tile Editor, by default in the bottom right corner.

__Insert Image here__

Select an name that is descriptive and easy to remember.

Open the Actor Mappings Data Table and add a new row if you want to replace the tile with an actor or open the Flipbook Mappings Data Table if you want to replace the tile with a flipbook.

Set the name of the new row to the User Data Name of the tile you want to replace.

## 2.2 Set up replacement data

#### Actor Replacement Data

- _Replacment Actor_: select the actor you want to replace the tile with from the actor drop down.

- _Offset_: set an offset for the actor location, or leave at (0,0,0) if the tile location should be used.

- _Scale_: set a scale for the actor to spawn.

- _Attach Actor to Tile Map_: Set whether the actor should be attached to the tile map.  
Leave this box checked for static actors i.e. actors with static position in the tile map like laser spikes.  
Uncheck it for dynamic actors i.e. actors that move on the tile map like enemies that patrol.

- _SpawnCollisionHandlingMethod_: Set the [SpawnCollisionHandlingMethod](https://docs.unrealengine.com/5.3/en-US/PythonAPI/class/SpawnActorCollisionHandlingMethod.html){:target="_blank"}{:rel="noreferrer"} for the actor to spawn.

- _Trigger OnActorSpawned Event_: Whether the Event 'On Actor Spawned' should be triggered when the actor is spawned. This event can be used as an event to do something on spawn for specific actors. The tile User Data Name is passed along.  
**Important**: make sure the actor implements the TileMapActor interface.  
An example use case is to fill the User Data Name with a color and use this event to set the color of the actor on spawn.

- _Clear Tile_: Whether the tile in the tile map should be cleared.  
Defaults to true as the spawned actor usually replaces the tile.

#### Flipbook Replacement Data

- _Creation Mode_: Whether the flipbook should be spawned as a PaperFlipbookActor or a PaperFlipbookComponent of the tile map actor.  
Choose PaperFlipbookComponent for flipbooks with a static position and scale (e.g. a torch on the wall).  
Choose PaperFlipbookActor for flipbooks that might move or change in size. This is more expensive and requires more manual bookkeeping.  
Settings marked with * indicate that they only affect Flipbooks spawned as a PaperFlipbookActor, not a PaperFlipbookComponent.  

- _Replacment Flipbook_: select the flipbook you want to replace the tile with from the flipbook drop down.

- _Offset_: set an offset for the flipbook location, or leave at (0,0,0) if the tile location should be used.

- _Scale_*: set a scale for the flipbook to spawn.  

- _Attach Actor to Tile Map_*: Set whether the actor should be attached to the tile map.  
Leave this box checked for static actors i.e. actors with static position in the tile map like laser spikes.  
Uncheck it for dynamic actors i.e. actors that move on the tile map like enemies that patrol.

- _SpawnCollisionHandlingMethod_*: Set the [SpawnCollisionHandlingMethod](https://docs.unrealengine.com/5.3/en-US/PythonAPI/class/SpawnActorCollisionHandlingMethod.html){:target="_blank"}{:rel="noreferrer"} for the actor to spawn.  

- _Trigger OnActorSpawned Event_*: Whether the Event 'On Actor Spawned' should be triggered when the actor is spawned. This event can be used as an event to do something on spawn for specific actors. The tile User Data Name is passed along.  
**Important**: make sure the actor implements the TileMapActor interface.  
An example use case is to fill the User Data Name with a color and use this event to set the color of the actor on spawn.

- _Clear Tile_: Whether the tile in the tile map should be cleared.  
Defaults to true as the spawned flipbook usually replaces the tile.

# 3 Clean-up tiles

Some objects on the tile map can consist of multiple tiles. From all these tiles only one needs to be replaced with the flipbook or actor.  
The other tiles should just be cleared, and this can be done with the Clear Tile Identifers or Clear Tile User Data list.  

In the example tile map, this is done for the Barrier, which consists of two tiles. The top tile is replaced with the actor while the bottom tile is cleared.

# 4 Store Transforms

If you want to find certain tile transforms to use these as, for example, spawn points, you can use the _Replace All and Store Transforms_ function. You can either provide the Tile Identifiers Transforms parameter or the User Data Transforms parameter, or both. 

The parameters can be variables in the calling actor and should be filled with the Tile Identifiers and User Data values of the tiles which Transforms you want to retrieve.

An example is given in BP_PaperTileMapActor which receives all transforms of the tiles with User Data _'ControlPanel'_ and then prints the transform to the output log.