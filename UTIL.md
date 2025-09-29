# Util

## util.joaat("model name")
What is joaat?
joaat is short for 'Jenkins on at a time' and is a hashing algorithm which takes strings like shown above and turns them into a 32 bit integer (unsigned int) used in programs like GTA V for storing models as a unique hash
You would use joaat when spawning models, since you cant create models with strings in GTA V. Here is an example on how to make a spawn vehicle function where you currently are in c++ and lua.
C++:
```cpp
void SPAWN_VEHICLE(const char* modelname) {
    uint32_t model = JOAAT(modelname);
    if (STREAMING::IS_MODEL_IN_CDIMAGE(model)) {
        Vector3 p_coords = ENTITY::GET_ENTITY_COORDS(PLAYER::PLAYER_PED_ID(), true);
        int heading = ENTITY::GET_ENTITY_HEADING(PLAYER::PLAYER_PED_ID());
        LOAD_MODEL(model); // You must define this function
        VEHICLE::CREATE_VEHICLE(model, p_coords.x, p_coords.y, p_coords.z, heading, false, false, true);
        STREAMING::SET_MODEL_AS_NO_LONGER_NEEDED(model); // Calling this unloads the model from memory, freeing ram
    }
}
```

Lua:
```lua
function SPAWN_VEHICLE(modelname)
    local model = util.joaat(modelname) -- I have provided you with a function here
    if STREAMING.IS_MODEL_IN_CDIMAGE(model) then
        local p_coords = ENTITY.GET_ENTITY_COORDS(PLAYER.PLAYER_PED_ID(), true)
        local heading = ENTITY.GET_ENTITY_HEADING(PLAYER.PLAYER_PED_ID())
        LOAD_MODEL(model)  -- You must define this function
        VEHICLE.CREATE_VEHICLE(model, p_coords.x, p_coords.y, p_coords.z, heading, false, false, true)
        STREAMING.SET_MODEL_AS_NO_LONGER_NEEDED(model) -- Calling this unloads the model from memory, freeing ram
    end
end

```
