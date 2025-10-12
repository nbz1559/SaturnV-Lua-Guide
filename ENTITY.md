# ENTITY

# table<int, int> entity.get_all_objects()
This gets all the object handles loaded in the world.
Objects are things like signs, seats, trashcans. Basically props.
Example:
```lua
local table1 = entity.get_all_objects()

local size = #table1

for i = 1, size do
local object = table1[i]
    -- Do something with the objects
end
```

# table<int, int> entity.get_all_pickups()
This gets all the pickup handles loaded in the world.
Pickups are things you would find on the ground, like a weapon and then when you run to it, it gets added to your inventory.
Example:
```lua
local table1 = entity.get_all_pickups()

local size = #table1

for i = 1, size do
local pickup = table1[i]
    -- Do something with the pickups
end
```

# table<int, int> entity.get_all_peds(includeplayer)
This gets all the PED handles loaded in the world.
If param 1 is set to true, that means the players ped will be included in the search, if not it will skip over the player ped.
PEDS are NPCS.
Example:
``` lua
local table1 = entity.get_all_peds(true)

local size = #table1

for i = 1, size do
local player = table1[i]
    -- Do something with the peds
end
```

# table<int, int> entity.get_all_vehicles(includeplayersvehicle)
This gets all the vehicle handles loaded in the world.
If param 1 is set to true, that means the players vehicle will be included in the search, if not it will skip over the players vehicle.
Example:
``` lua
local table1 = entity.get_all_vehicles(true)

local size = #table1

for i = 1, size do
local vehicle = table1[i]
    -- Do something with the vehicles
end
```

# int entity.delete(entityhandle)
This will delete any entity (ped, vehicle, object etc) for you, because you cant delete entities with lua.
The reason entity.delete is an int and not a void is because it returns 0 to set your handle variable (if you are using one) to 0
Example:
```lua
local vehiclehandle = PED.GET_VEHICLE_PED_IS_IN(PLAYER.PLAYER_PED_ID(), false) -- vehiclehandle will initially be set to the handle like 29292323 if the vehicle exists

if ENTITY.DOES_ENTITY_EXIST(vehiclehandle)
    vehiclehandle = entity.delete(vehiclehandle) -- This will set your handle to 0, you can do this manually but this is quicker
end
```
Make sure not to try and delete an entity yourself with ENTITY.DELETE_ENTITY() because that will most likely crash your game
