# Util

## int util.joaat()

Example:
```
ped_hash = util.joaat("S_M_Y_COP_01")
```

## void util.load_model(model)

Example:
```
util.load_model(util.joaat("S_M_Y_COP_01"))
local cop = PED.CREATE_PED(6, util.joaat("S_M_Y_COP_01"), 123, 456, 789, 50, false, true)
STREAMING.SET_MODEL_AS_NO_LONGER_NEEDED(util.joaat("S_M_Y_COP_01")
-- Do something with the ped/cop you made
```
