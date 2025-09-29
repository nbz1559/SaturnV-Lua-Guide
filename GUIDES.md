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

