# Client-Sided Functions and Usage

The following info contains every client sided function in QBCore framework and how to use it. It also contains some basic info on what it does.

?> **Important information** - All the following functions required QBCore object which is called through the import in the fxmanifest or the export. If you don't know yet about importing the QBCore object, we recommend reading the [fxmanifest documentation](../other/fxmanifest/fxmanifest?id=qbcore-fxmanifest-introduction).

## QBCore.Functions.GetPlayerData

**Usage -** Perhaps the most used function in the framework. This functions returns the players data of the current source which, since its used client side, is automatically the client or player. It can be used with modifiers on the end starting with a "." (period).

**Parameters -**

|    cb   |
| :----: |
| function  |

**Returns -**  *Table*

```lua
-- Example 1
local Player = QBCore.Functions.GetPlayerData()

-- Example 2
QBCore.Functions.GetPlayerData(function(Player)
    print(Player.citizenid)
end)
```

## QBCore.Functions.GetCoords

**Usage -** Returns an entity's coords and heading in a vector4 table.

**Parameters -**

|    entity     |
| :----:    |
| number  |

**Returns -**  *Vector*

```lua
-- Example 1
local coords = QBCore.Functions.GetCoords(PlayerPedId())
print(coords.x, coords.y, coords.z, coords.w) -- x, y, z, w
```

## QBCore.Functions.HasItem

**Usage -** Returns if a player has the passed item.

**Parameters -**

|    item     |
| :----:    |
| string  |

**Returns -**  *Boolean*

```lua
-- Example 1
local hasPhone = QBCore.Functions.HasItem('phone')
if hasPhone then
    -- Do something
end
```
## QBCore.Functions.DrawText

**Usage -** Draws text on screen.

**Parameters -**

|    x     ||    y     ||   width   ||  height  ||    scale     ||    r     ||    g     ||    b     ||    a     ||    text     |
| :----:    || :----:    || :----:    || :----:    || :----:    || :----:    || :----:    || :----:    || :----:    || :----:    |
| number  || number  || number  || number  || number  || number  || number  || number  || number  || string  |

**Returns -**  *Nothing*

```lua
-- Example 1
CreateThread(function()
    while true do
        QBCore.Functions.DrawText(0.5, 0.5, 0.5, 0.5, 1.0, 1.0, 1.0, 1.0, 1.0, 'Displays a message')
        Wait(0)
    end
end)
```
## QBCore.Functions.DrawText3D

**Usage -** Draws text in the 3D plane.

**Parameters -**

|    x     ||    y     ||    z     ||    text     |
| :----:    || :----:    || :----:    || :----:    |
| number  || number  || number  || string  |

**Returns -**  *Nothing*

```lua
-- Example 1
CreateThread(function()
    while true do
        -- These are just examples. They may not be the best practices.
        local coords = GetEntityCoords(PlayerPedId())
        QBCore.Functions.DrawText3D(coords.x, coords.y, coords.z, 'Displays a message')
        Wait(0)
    end
end)
```
## QBCore.Functions.CreateBlip

**Usage -** Creates a blip on the map.

**Parameters -**

|    coords     ||    sprite     ||    display     ||    scale     ||    color     ||    shortRange     ||    title     |
| :----:    || :----:    || :----:    || :----:    || :----:    || :----:    || :----:    |
| vector  || number  || number  || number  || number  || boolean  || string  |

**Returns -**  *Nothing*

```lua
-- Example 1
local coords = GetEntityCoords(PlayerPedId())
QBCore.Functions.CreateBlip(coords, 120, 3, 1.0, 7, false, 'Am I here!')

```
## QBCore.Functions.RequestAnimDict

**Usage -** Request the anim dictionary for the specified parameter.

**Parameters -**

|    animDict     |
| :----:    |
| string  |

**Returns -**  *Nothing*

```lua
-- Example 1
QBCore.Functions.RequestAnimDict('anim@amb@nightclub@dancers@solomun_entourage@')

```
## QBCore.Functions.LoadModel

**Usage -** Request the model of an entity.

**Parameters -**

|    modelName     |
| :----:    |
| string  |

**Returns -**  *Nothing*

```lua
-- Example 1
QBCore.Functions.LoadModel('adder')

```
## QBCore.Functions.Notify

**Usage -** Send a notification to the client.

**Parameters -**

|    text     ||    textype     ||    length     |
| :----:    || :----:    || :----:    |
| string/table  || string  || number  |

**Returns -**  *Nothing*

```lua
-- Example 1
QBCore.Functions.Notify('Awesome notification!', 'primary', 10000)

QBCore.Functions.Notify({text = 'Awesome notification!', caption = 'Awesome caption!'}, 'primary', 10000)

```
## QBCore.Functions.TriggerCallback

**Usage -** Trigger a callback from the server.

**Parameters -**

|    name     ||    cb     ||    ...     |
| :----:    || :----:    || :----:    |
| string  || function  || varargs  |

**Returns -**  *Nothing*

```lua
-- Example 1
QBCore.Functions.TriggerCallback('qbcore:coolCallback', function(name)
    print(name)
end)

```
## QBCore.Functions.Progressbar

**Usage -** Creates a progress bar for the client.
name, label, duration, useWhileDead, canCancel, disableControls, animation, prop, propTwo, onFinish, onCancel)
**Parameters -**

|name||label||duration||useWhileDead||canCancel||disableControls||animation||prop||propTwo||onFinish||onCancel|
| :----:    || :----:    || :----:    || :----:    || :----:    || :----:    || :----:    || :----:    || :----:    || :----:    || :----:    |
| string  || string  || number  || boolean  || boolean  || boolean  || string  || string  || string  || cb  || cb  |

**Returns -**  *Nothing*

```lua
-- Example 1
QBCore.Functions.Progressbar('progressbarone', 'Cool progress bar!', true, false, true, '', '', function(onFinish)
    if onFinish then
        -- Do something
    end
end, function(onCancel)
    if onCancel then
        -- Do something
    end
end)

```
## QBCore.Functions.GetVehicles

**Usage -** Returns all the game pool vehicles.

**Parameters -** *Nothing*

**Returns -**  *Table*

```lua
-- Example 1
local vehicles = QBCore.Functions.GetVehicles()

```
## QBCore.Functions.GetObjects

**Usage -** Returns all the game pool objects.

**Parameters -** *Nothing*

**Returns -**  *Table*

```lua
-- Example 1
local objects = QBCore.Functions.GetObjects()

```
## QBCore.Functions.GetPlayers

**Usage -** Returns all the game pool players.

**Parameters -** *Nothing*

**Returns -**  *Table*

```lua
-- Example 1
local players = QBCore.Functions.GetPlayers()

```
## QBCore.Functions.GetPeds

**Usage -** Returns all the game pool peds.

**Parameters -**

|    ignoreList     |
| :----:    |
| table  |

**Returns -**  *Table*

```lua
-- Example 1
-- You can add pass a table with an ignore list
local peds = QBCore.Functions.GetPeds()

```

## QBCore.Functions.GetClosestPed

**Usage -** Get the closest ped to the client.

**Parameters -**

|    coords     ||    ignoreList     |
| :----:    || :----:    |
| vector  || table  |

**Returns -**  *Number & Number*

```lua
-- Example 1
-- You can add pass a table with an ignore list
local closestPed, closestDist = QBCore.Functions.GetClosestPed(GetEntityCoords(PlayerPedId()))
if closestDist < 3 then
    -- Do something
end

```
## QBCore.Functions.IsWearingGloves

**Usage -** Returns if client is wearing gloves.

**Parameters -** *Nothing*

**Returns -**  *Boolean*

```lua
-- Example 1
local isWearingGloves = QBCore.Functions.IsWearingGloves()
if isWearingGloves then
    -- Do something
end
```
## QBCore.Functions.GetClosestPlayer

**Usage -** Returns the closest the player to the passed coords.

**Parameters -**

|    coords     |
| :----:    |
| vector  |

**Returns -**  *Number & Number*

```lua
-- Example 1
local closestPlayer, closestDist = QBCore.Functions.GetClosestPlayer(GetEntityCoords(PlayerPedId()))
if closestDist < 3 then
    -- Do something
end
```
## QBCore.Functions.GetPlayersFromCoords

**Usage -** Returns all the players cloest the coords and less the the passed distance.

**Parameters -**

|    coords     ||    distance     |
| :----:    || :----:    |
| vector  || number  |

**Returns -**  *Table*

```lua
-- Example 1
local players = QBCore.Functions.GetPlayersFromCoords(GetEntityCoords(PlayerPedId()), 3)
for k, v in pairs(players) do
    -- Do something with the values
end
```
## QBCore.Functions.GetClosestVehicle

**Usage -** Returns the closest vehicle to coords.

**Parameters -**

|    coords     |
| :----:    |
| vector  |

**Returns -**  *Number & Number*

```lua
-- Example 1
local closestVehicle, closestDist = QBCore.Functions.GetClosestVehicle(GetEntityCoords(PlayerPedId()))
if closestDist < 3 then
    -- Do something
end
```
## QBCore.Functions.GetClosestObject

**Usage -** Returns the closest object to coords.

**Parameters -**

|    coords     |
| :----:    |
| vector  |

**Returns -**  *Number & Number*

```lua
-- Example 1
local closestObject, closestDist = QBCore.Functions.GetClosestObject(GetEntityCoords(PlayerPedId()))
if closestDist < 3 then
    -- Do something
end
```
## QBCore.Functions.GetClosestBone

**Usage -** Returns the closest bone to entity.

**Parameters -**

|    entity     ||    list     |
| :----:    || :----:    |
| number  || table  |

**Returns -**  *Number, Vector & Number*

```lua
-- Example 1
local boneList = {-- Bones here}
local bone, coords, dist = QBCore.Functions.GetClosestBone(PlayerPedId(), boneList)
if dist < 3 then
    -- Do something
end
```
## QBCore.Functions.GetBoneDistance

**Usage -** Returns the closest vehicle to coords.

**Parameters -**

|    entity     ||    type     ||    bone     |
| :----:    || :----:    || :----:    |
| number  || number  || number  |

**Returns -**  *Number*

```lua
-- Example 1
local dist = QBCore.Functions.GetBoneDistance(PlayerPedId(), 1, bone)
if dist < 3 then
    -- Do something
end

```
## QBCore.Functions.AttachProp

**Usage -** Creates a prop and returns the prop entity.

**Parameters -**

|    ped     ||    model     ||    boneId     ||    x     ||    y     ||    z     ||    xR     ||    yR     ||    zR     ||    vertex     |
| :----:    || :----:    || :----:    || :----:    || :----:    || :----:    || :----:    || :----:    || :----:    || :----:    |
| number  || string  || number  || number  || number  || number  || number  || number  || number  || boolean  |

**Returns -**  *Number*

```lua
-- Example 1
local prop = QBCore.Functions.AttachProp(PlayerPedId(), 'prop_cs_tablet', 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, true)
if prop then
    -- Do something
end
```
## QBCore.Functions.SpawnVehicle

**Usage -** Spawns a vehicle depending on arguments.

**Parameters -**

|    model     ||    cb     ||    coords     ||    isNetworked     |
| :----:    || :----:    || :----:    || :----:    |
| string  || function  || vector  || boolean  |

**Returns -**  *Nothing*

```lua
-- Example 1
QBCore.Functions.SpawnVehicle('adder', function(vehicle)
    -- Do something
end, GetEntityCoords(PlayerPedId()), true)

```
## QBCore.Functions.DeleteVehicle

**Usage -** Deletes vehicle based on argument.

**Parameters -**

|    vehicle     |
| :----:    |
| number  |

**Returns -**  *Nothing*

```lua
-- Example 1
QBCore.Functions.DeleteVehicle(GetVehiclePedIsIn(PlayerPedId(), false))

```
## QBCore.Functions.GetPlate

**Usage -** Returns the plate of passed vehicle.

**Parameters -**

|    vehicle     |
| :----:    |
| number  |

**Returns -**  *Number*

```lua
-- Example 1
local plate = QBCore.Functions.GetPlate()
print(plate) -- XXXXXXXX

```
## QBCore.Functions.SpawnClear

**Usage -** Usage.

**Parameters -**

|    coords     ||    radius     |
| :----:    || :----:    |
| number  || number  |

**Returns -**  *Boolean*

```lua
-- Example 1
local vehiclesNearby = QBCore.Functions.SpawnClear(GetEntityCoords(PlayerPedId()), 3.0)
if not vehiclesNearby then
    -- Do something
end

```
## QBCore.Functions.GetVehicleProperties

**Usage -** Returns all the vehicle properties of a vehicle. Read [here](https://github.com/qbcore-framework/qb-core/blob/main/client/functions.lua#L423) for more details about all the properties.

**Parameters -**

|    vehicle     |
| :----:    |
| number  |

**Returns -**  *Table*

```lua
-- Example 1
local vehicleProps = QBCore.Functions.GetVehicleProperties(GetVehiclePedIsIn(PlayerPedId(), false))
print(json.encode(vehicleProps)) -- Table of all the properties
print(vehicleProps.plate) -- XXXXXXXX

```
## QBCore.Functions.SetVehicleProperties

**Usage -** Sets the vehicle properties of a vehicle.

**Parameters -**

|    vehicle     |
| :----:    |
| number  |

**Returns -**  *Nothing*

```lua
-- Example 1
local props = {
    plate = '1234ABCD'
}
QBCore.Functions.SetVehicleProperties(props)

```
## QBCore.Functions.LoadParticleDictionary

**Usage -** Loads a dictionary of a particle effect (ptfx).

**Parameters -**

|    dict     |
| :----:    |
| string  |

**Returns -**  *Nothing*

```lua
-- Example 1
QBCore.Functions.LoadParticleDictionary('scr_playerlamgraff')

```
## QBCore.Functions.StartParticleAtCoord

**Usage -** Starts a particle at specified coords.

**Parameters -**

| dict ||ptfxName||looped||coords||rotation||    scale     ||    alpha     ||    color     ||    duration     |
| :----:    || :----:    || :----:    || :----:    || :----:    || :----:    || :----:    || :----:    || :----:    |
| string  || string  || boolean  || vector  || number  || number  || number  || table  || number  |

**Returns -**  *Number*

```lua
-- Example 1
local rgb = {
    r = 1.0,
    g = 1.0,
    b = 1.0
}
local particle = QBCore.Functions.StartParticleAtCoord('scr_xs_celebration', 'scr_xs_money_rain', true, GetEntityCoords(PlayerPedId()), 0.0, 1.0, 1.0, rgb, 5000)
if particle then
    -- Do something
end

```
## QBCore.Functions.StartParticleOnEntity

**Usage -** Starts a particle on a specific entity.

**Parameters -**

|   dict   ||   ptfxName   ||   looped   ||   entity   ||   bone   ||   offset   ||rotation||scale||alpha||color||evolution||duration|
|:----:  ||:----:  ||:----:  ||:----:  ||:----:  ||:----:  ||:----:  ||:----:  ||:----:  ||:----:  ||:----:  ||:----:  |
|string||string||boolean||number||number||number||number||number||number||table||table||duration|

Dict, ptName, looped, entity, bone, offset, rot, scale, alpha, color, evolution, duration

**Returns -**  *Number*

```lua
-- Example 1
local rgb = {
    r = 1.0,
    g = 1.0,
    b = 1.0
}
local evolution = {
    name = 'name',
    amount = 1.0
}
local particle = QBCore.Functions.StartParticleOnEntity('scr_xs_celebration', 'scr_xs_money_rain', true, PlayerPedId(), bone, 0.0, 0.0, 1.0, 1.0, rgb, evolution, 5000)
if particle then
    -- Do something
end

```