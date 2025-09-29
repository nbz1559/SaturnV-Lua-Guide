# Guides
Welcome to the guides for using lua in GTA V With SaturnV
Below are some short to lengthy guides on how to use functions in GTA that could be helpful for your modding creations

## Spawning Models
When spawning a model, you ALWAYS have to load the model in, if using ```PLAYER.SET_PLAYER_MODEL()``` for example, not loading in the model will cause the game to crash because the game is reading invalid (non-existent) memory because no model has been loaded to memory, meaning there is no memory to read off of.
To load in a model, you need to call ```STREAMING.REQUEST_MODEL(model)``` to request the model in memory. Heres a short LOAD_MODEL example function in lua.
```lua
function LOAD_MODEL(model)
if STREAMING.IS_MODEL_VALID(model) then
STREAMING::REQUEST_MODEL(model); -- Request the model in memory
-- I suggest making a timeout feature to wait for the model to load. Usually it will only take a couple of milliseconds to load, it all depends on your PC
else
-- Notify the user that an invalid model has been chosen
end
end
```
That is a very basic function, with no timeout feature as i haven't added a yield feature yet

After loading the model, you can then go on to create it. Be sure after you are done to call ```STREAMING.SET_MODEL_AS_NO_LONGER_NEEDED(model)``` to free it from ram to save memory

## Notifications and HUD
Have you wonderned how to send notifications and more to the user with natives? Heres how.

## Sending notifications (The ones above the mini-map)
That type of notification is called 'THEFEED'
To send one you do this,
```lua
function SEND_NOTIFICATION(text)
    HUD.BEGIN_TEXT_COMMAND_THEFEED_POST("STRING") -- Other types are avalible, see https://nativedb.scheenen.dev/natives for more info
    HUD.ADD_TEXT_COMPONENT_SUBSTRING_PLAYER_NAME(text)
    HUD.END_TEXT_COMMAND_THEFEED_POST_TICKER(false, false)
end
```
Param 1 for END_TEXT_COMMAND_THEFEED_POST_TICKER is called blink
Param 2 for END_TEXT_COMMAND_THEFEED_POST_TICKER is p1

## Sending help commands
Help commands are the notifications in the top left that play a 'ding' sound effect
To send one you do this,
```lua
function SEND_HELP_COMMAND(text, loop, ping, ms)
    HUD.BEGIN_TEXT_COMMAND_DISPLAY_HELP("STRING") -- Other types are avalible, see https://nativedb.scheenen.dev/natives for more info
    HUD.ADD_TEXT_COMPONENT_SUBSTRING_PLAYER_NAME(text)
    HUD.END_TEXT_COMMAND_DISPLAY_HELP(0, loop, ping, ms)
end
```
Param 1 for END_TEXT_COMMAND_DISPLAY_HELP is always 0
Param 2 for END_TEXT_COMMAND_DISPLAY_HELP is a bool value which when sets to true loops the notification
Param 3 for END_TEXT_COMMAND_DISPLAY_HELP is if it should play that 'ding' sound effect
Param 4 for END_TEXT_COMMAND_DISPLAY_HELP is how many milliseconds to display that notification for, eg 1000 ms = 1 second

## Sending help text in the bottom center
Help text in the bottom center of the screen is what GTA uses to direct you on what to do in missions, like 'Go to Dr Friedlanders office'
To send one you do this,
```lua
function PRINT_HELP_TEXT(text, ms, instant)
    HUD.BEGIN_TEXT_COMMAND_PRINT("STRING") -- Other types are avalible, see https://nativedb.scheenen.dev/natives for more info
    HUD.ADD_TEXT_COMPONENT_SUBSTRING_PLAYER_NAME(text)
    HUD.END_TEXT_COMMAND_PRINT(ms, instant)
end
```
Param 1 for END_TEXT_COMMAND_PRINT is how many milliseconds to display that help print for, eg 1000 ms = 1 second
Param 2 for END_TEXT_COMMAND_PRINT is if it should show up instantly, i haven't tested on what it looks like showing up not instantly (Param 2 set to false), I would recommend setting it to true

# Entitys
Entitys are things in the game that are not apart of the map and can be interacted with, like NPCS, Vehicles, Street lights, benches etc.
NPCS Are called Peds (Short for Pedestrian)
Vehicles are called Vehicles
Benches, bins and props for example are called Objects
Things on the ground you can pickup (Like weapons) are called Pickups

## Peds
Peds are NPCS in the game, you also have your own personal ped which you can obtain through ```PLAYER.PLAYER_PED_ID()```, that gives you the handle to your ped which you can control with that

To create a ped, you can either call ```CREATE_PED``` or ```CREATE_PED_INSIDE_VEHICLE```
Here are examples for both of those
CREATE_PED:
```lua
function SPAWN_PED(type, model, x, y, z, heading)
LOAD_MODEL(model) -- You will need to make your own load model function
CREATE_PED(type, model, x, y, z, false, false)
STREAMING.SET_MODEL_AS_NO_LONGER_NEEDED(model)
end
```
The last 2 params for CREATE_PED are related to online so you can set them to false by default if you want, or you can use them its up to you
'type' is the ped type for that ped. I will get to those a bit later but if you want a list now, here is one https://alloc8or.re/gta5/doc/enums/ePedType.txt
'model' is the model for the ped, you can get it by using util.joaat("S_M_Y_COP_01") for example, that will give you the model for the standard cop.
