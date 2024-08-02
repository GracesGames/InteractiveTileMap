---
layout: default
---

# Interactive Tile Map

Available in the [Unreal Engine Marketplace](https://www.unrealengine.com/marketplace/interactive-tile-map){:target="_blank"}{:rel="noreferrer"}

Interactive Tile Map allows you to add interactive elements to your tile map without manually placing them. 
This will allow you to use the tile map editor as a level editor, thereby speeding up your level design process.

You define which tile is replaced by which actor or flipbook animation using the provided [Data Asset](https://dev.epicgames.com/documentation/en-us/unreal-engine/data-assets-in-unreal-engine){:target="_blank"}{:rel="noreferrer"} or the [Data Tables](https://dev.epicgames.com/documentation/en-us/unreal-engine/data-driven-gameplay-elements){:target="_blank"}{:rel="noreferrer"}.
The tiles can be defined using TileInfo (TileSet + Index) or the Tile User Data Name.

This product can be added to any actor and only requires a PaperTileMapComponent to perform the replace logic. 
It will replace all instances of the defined tiles with the corrosponding actors and flipbooks.

Everything is done using Blueprints and allows customization.
 
The project will be maintained, so feel free to get in touch to suggest changes, features or anything else.

__Features include:__ 

- Replace tiles with actors and/or flipbooks
- Option to spawn flipbook actors or components as children of the tile map actor
- Respects both tile map actor transform and tile transform (e.g. rotation and flip values)
- Set up your desired replacements using Data Assets or Data Tables
- Specify specific layers to keep the performance high
- And much more

For a complete overview, see the [Features](https://gracesgames.com/InteractiveTileMap/features/) page 
<br/>

![FeaturedImage]({{ "/assets/images/FeaturedImage.png" | absolute_url }})