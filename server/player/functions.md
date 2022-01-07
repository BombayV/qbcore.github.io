# Player Functions Server

In order to perform functions like adding money or removing it, we will need to get the player first.
```lua
local _src = source
local Player = QBCore.Functions.GetPlayer(_src)

-- Example
--Player.Functions.AddMoney('bank', 500)
```
!> **Important** - Just like getting the `PlayerData` server side, we need to get the player first as shown above. We specify the source of the player which is the "player id" of a player. This will allow us to trigger functions on the user we passed in.

## QBCore.Functions.SetJob

**Usage -** Sets a player's job and returns a boolean if was successful or not.

**Parameters -**

|  job   ||  grade   |
| :----:    || :----:    |
| string    || string    |

**Returns -**  *Boolean*

```lua
local newJob = QBCore.Functions.SetJob('police', '0')
if newJob then
    -- Do something
end
```