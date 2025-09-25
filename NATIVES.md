# Natives

## What are natives?

Natives are In-Game functions directly from GTA V, they are what rockstar and modders use to change/alter things in the game, like spawn cars, add explosions, teleportation, basically everything in the game is possible with natives.

## How do you call them?

The natives are split in to around 45 categorys, the main ones being PLAYER, PED, VEHICLE, MISC, ENTITY, GRAPHICS, HUD and NETWORK.
Just a quick note, in my menu i have decided not to add network, money and netshopping into my Lua API, because they are all for GTA Online, and my menu is a single-player free menu, so it would be a waste of time to add them.
To call natives, you would do something like
```lua
PLAYER.PLAYER_PED_ID() 
```
What does this do? This is YOUR ped handle inside the game. What is a ped you may ask? A ped is just an npc, short for Pedestrian. A handle is the ID of that ped that the game uses to identify things, you will be using handles a lot in scripting, they are everywhere, cars, peds, entitys, objects, pretty much every pyhsical interactable thing in GTA V. I wont go into to much depth about them, but you probably get the idea.

If you dont understand, I would recommend watching some tutorials to get an idea of what you will be working with. If you do have some idea, visit https://nativedb.scheenen.dev/natives that is probably the best native databases out there, he has provided you with a search bar, descriptions for over half of the natives, and pretty much every named native in GTA V, in a nice readble format, and all of the native names are up-to-date.
That is what I will provide for now, if you have any more questions visit the discord (Link in my bio), i will try answer as many as possible.
