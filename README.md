# Interactive Tile Map for Unreal Engine

<p align="center">
	<a href="https://www.fab.com/listings/1052edf8-7752-4cb7-8bab-a96e38d712ff" rel="noreferrer" target="_blank">Fab</a> |
  	<a href="https://gracesgames.com/InteractiveTileMap/" rel="noreferrer" target="_blank">Website</a>
</p>

Available on [Fab](https://www.fab.com/listings/1052edf8-7752-4cb7-8bab-a96e38d712ff)

Interactive Tile Map allows you to add interactive elements to your tile map without manually placing them. 
This will allow you to use the tile map editor as a level editor, thereby speeding up your level design process.

You define which tile is replaced by which actor or flipbook animation using the provided [Data Asset](https://dev.epicgames.com/documentation/en-us/unreal-engine/data-assets-in-unreal-engine) or the [Data Tables](https://dev.epicgames.com/documentation/en-us/unreal-engine/data-driven-gameplay-elements).
The tiles can be defined using TileIdentifier (TileSet + Index) or the Tile User Data Name.

This product is implemented as an ActorComponent and can be added to any actor (e.g. Paper Tile Map Actor). 
The replace function can be called at any time and only requires a PaperTileMapComponent to perform the logic on. 
It will replace all instances of the defined tiles with the corresponding actors and flipbooks.

Created using Blueprints, fully documented and easy to customize.

The project will be maintained, so feel free to get in touch to suggest changes, features or anything else.

## Features include:

- Replace tiles with actors and/or flipbooks
- Option to spawn flipbook actors or components as children of the tile map actor
- Respects both tile map actor transform and tile transform (e.g. rotation and flip values)
- Set up your desired replacements using Data Assets or Data Tables
- Specify specific layers to keep the performance high
- And much more

For a list of features, documentation and more please see the [website](https://gracesgames.com/InteractiveTileMap/)

![FeaturedImage](https://github.com/GracesGames/InteractiveTileMap/blob/main/Images/FeaturedImage.png)