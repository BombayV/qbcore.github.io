# Server-Sided Functions and Usage

The following info contains every server sided function in QBCore framework and how to use it. It also contains some basic info on what it does.

?> **Important information** - All the following functions required QBCore object which is called through the import in the fxmanifest or the export. If you don't know yet about importing the QBCore object, we recommend reading the [fxmanifest documentation](./other/fxmanifest?id=qbcore-fxmanifest-introduction)

## QBCore.Functions.GetCoords

**Usage -** Returns a player's coords in a vector4 format.

**Parameters -**

|  source  |
| :----: |
| number   |

**Returns -**  *Vector*

```lua
local coords = QBCore.Functions.GetCoords(coords)
print(coords.x, coords.y, coords.z, coords.w) -- x, y, z, w
```

## QBCore.Functions.GetIdentifier

**Usage -** Returns the player's identifier based on type or config.

**Parameters -**

|  source  || idtype  |
| :----: || :----: |
| number   || string |

**Returns -**  *String*

```lua
local identifier = QBCore.Functions.GetIdentifier(source, 'license')
print(identifier) -- 'license:1234567890123'
```

## QBCore.Functions.GetSource

**Usage -** Checks for players in the server and matches them up by identifier.

**Parameters -**

|  identifier  |
| :----: |
| string   |

**Returns -**  *Number*

```lua
local targetId = QBCore.Functions.GetSource('license:1234567890123')
print(targetId) -- 1
```

## QBCore.Functions.GetPlayer

**Usage -** Gets the designated player and returns them (used for getting player data).

**Parameters -**

|  source  |
| :----: |
| number   |

**Returns -**  *Table*

```lua
local Player = QBCore.Functions.GetPlayer(source)
print(json.encode(Player)) -- Table with all possible data
```

## QBCore.Functions.GetPlayerByCitizenId

**Usage -** Finds a specific player from the list of players in the server by their citizen id.

**Parameters -**

|  citizenid  |
| :----: |
| number   |

**Returns -**  *Table*

```lua
local Player = QBCore.Functions.GetPlayerByCitizenId(citizenid)
print(json.encode(Player)) -- Table with all possible data
```

## QBCore.Functions.GetPlayerByPhone

**Usage -** Finds a specific player from the list of players in the server by phone number.

**Parameters -**

|  phoneNumber  |
| :----: |
| number   |

**Returns -**  *Table*

```lua
local Player = QBCore.Functions.GetPlayerByPhone(phoneNumber)
print(json.encode(Player)) -- Table with all possible data
```

## QBCore.Functions.GetPlayers

**Usage -** Returns a table of players currently in the server (use for onesync).

**Parameters -** None

**Returns -**  *Table*

```lua
local players = QBCore.Functions.GetPlayers()
for _, v in pairs(players) do
    print(json.encode(v))
end
```

## QBCore.Functions.GetQBPlayers

**Usage -** Returns an array of QB Player class instances currently in the server.

**Parameters -** None

**Returns -**  *Array*

```lua
local players = QBCore.Functions.GetQBPlayers()
for _, v in pairs(players) do
    -- Do something
end
```

## QBCore.Functions.GetPlayersOnDuty

**Usage -** Returns a table of players with a job currently in the server (use for onesync).

**Parameters -** None

**Returns -**  *Table & Number*

```lua
local players, count = QBCore.Functions.GetPlayersOnDuty('police')
print(count) -- 3
for _, v in pairs(players) do
    print(json.encode(v))
end
```

## QBCore.Functions.GetDutyCount

**Usage -** Returns the number of players on duty with a job.

**Parameters -** None

**Returns -**  *Number*

```lua
local count = QBCore.Functions.GetDutyCount('police')
print(count) -- 3
```

## QBCore.Functions.GetBucketObjects

**Usage -** Returns the objects related to buckets, first returned value is the player buckets , second one is entity buckets.

**Parameters -** None

**Returns -**  *Table & Table*

```lua
local playersBucket, entitiesBuckets = QBCore.Functions.GetBucketObjects()
-- Loop through them
```

## QBCore.Functions.SetPlayerBucket

**Usage -** Will set the provided player id / source into the provided bucket id. Returns a boolean if it was successful or not.

**Parameters -**

|  source  ||  bucket  |
| :----:   || :----:   |
| number   || number   |

**Returns -**  *Boolean*

```lua
local newBucket = QBCore.Functions.SetPlayerBucket(source, 5)
if newBucket then
    -- Do something
end
```

## QBCore.Functions.GetPlayersInBucket

**Usage -** Returns array with all the players in the passed bucket.

**Parameters -**

|  bucket  |
| :----:   |
| number   |

**Returns -**  *Table/Boolean*

```lua
local players = QBCore.Functions.GetPlayersInBucket(5)
for k, v in pairs(players) do
    -- Do something
end
```

## QBCore.Functions.GetEntitiesInBucket

**Usage -** Returns array with all the entities (not players) in the passed bucket.

**Parameters -**

|  bucket  |
| :----:   |
| number   |

**Returns -**  *Table/Boolean*

```lua
local players = QBCore.Functions.GetEntitiesInBucket(5)
for k, v in pairs(players) do
    -- Do something
end
```

## QBCore.Functions.IsPlayerInBucket

**Usage -** Returns if passed player is in the passed bucket.

**Parameters -**

|  source  ||  bucket  |
| :----:   || :----:   |
| number   || number   |

**Returns -**  *Boolean*

```lua
local inBucket = QBCore.Functions.IsPlayerInBucket(source, 5)
if inBucket then
    -- Do something
end
```

## QBCore.Functions.CreateCallback

**Usage -** Creates a useable callback.

**Parameters -**

|  name  ||   cb   |
| :----: || :----: |
| string   ||  data  |
| name   ||   cb   |

**Returns -**  *An useable callback which can then be trigger in the client*

```lua
QBCore.Functions.CreateCallback = function(name, cb)
	QBCore.ServerCallbacks[name] = cb
end
```

## QBCore.Functions.TriggerCallback

**Usage -** Triggers a useable callback that has been created.

**Parameters -**

|  name  || source  ||   cb   ||   ...   |
| :----: || :----: || :----: || :----: |
| string   || number ||  data  ||  arguments  |
| name   || source   ||   cb   ||   varargs   |

**Returns -**  *Data from the already created callback*

```lua
QBCore.Functions.TriggerCallback = function(name, source, cb, ...)
	if QBCore.ServerCallbacks[name] ~= nil then
		QBCore.ServerCallbacks[name](source, cb, ...)
	end
end
```

## QBCore.Functions.CreateUseableItem

**Usage -** Makes an item useable.

**Parameters -**

|  item  || cb  |
| :----: || :----: |
| string   || data |
| item name   || cb   |

**Returns -**  *An specified item with useability*

```lua
QBCore.Functions.CreateUseableItem = function(item, cb)
	QBCore.UseableItems[item] = cb
end
```

## QBCore.Functions.CanUseItem

**Usage -** A check to make sure the item has been created as useable.

**Parameters -**

|  item  |
| :----: |
| string   |
| item name   |

**Returns -**  *If specified item is useable*

```lua
QBCore.Functions.CanUseItem = function(item)
	return QBCore.UseableItems[item] ~= nil
end
```

## QBCore.Functions.UseItem

**Usage -** Uses an item.

**Parameters -**

|  source  || item  |
| :----: || :----: |
| number  || string |
| source   || item name   |

**Returns -**  *Uses an item*

```lua
QBCore.Functions.UseItem = function(source, item)
	QBCore.UseableItems[item.name](source, item)
end
```

## QBCore.Functions.Kick

**Usage -** Kicks a player with parameters for a reason (add your discord link to config).

**Parameters -**

|  source  || reason  ||   setKickReason   ||   deferrals   |
| :----: || :----: || :----: || :----: |
| number   || string ||  bool  ||  bool  |

**Returns -**  *Nothing*

```lua
QBCore.Functions.Kick(source, 'Testing kick function', false, deferrals)
```
## QBCore.Functions.IsWhitelisted

**Usage -** Checks the whitelist table in the database for a matching identifier.

**Parameters -**

|  source  |
| :----: |
| number   |

**Returns -**  *Boolean*

```lua
local isWhitelisted = QBCore.Functions.IsWhitelisted(source)
if isWhitelisted then
    -- Do something
end
```

## QBCore.Functions.AddPermission

**Usage -** Allows you to give a player elevated permissions while in the server.

**Parameters -**

|  source  || permission  |
| :----: || :----: |
| number   || string |

**Returns -** *Nothing*

```lua
QBCore.Functions.AddPermission(source, 'god')
```

## QBCore.Functions.RemovePermission

**Usage -** Allows you to remove a players permissions while in the server.

**Parameters -**

|  source  |
| :----: |
| number   |

**Returns -** *Nothing*

```lua
QBCore.Functions.RemovePermission(source)
```

## QBCore.Functions.HasPermission

**Usage -** Checks the players permission level and returns true or false.

**Parameters -**

|  source  || permission  |
| :----: || :----: |
| number   || string |

**Returns -**  *Boolean*

```lua
local hasPerms = QBCore.Functions.HasPermission(source, 'god')
if hasPerms then
    -- Do something
end
```

## QBCore.Functions.GetPermission

**Usage -** Returns the players permission level.

**Parameters -**

|  source  |
| :----: |
| number   |

**Returns -**  *String*

```lua
local perms = QBCore.Functions.GetPermission(source)
if perms == 'god' then
    -- Do something
end
```

## QBCore.Functions.IsOptin

**Usage -** Checks whether the staff member is opted in or out and returns true or false.

**Parameters -**

|  source  |
| :----: |
| number   |

**Returns -**  *Boolean*

```lua
local isOptIn = QBCore.Functions.IsOptin(source)
if isOptIn then
    -- Do something
end
```

## QBCore.Functions.ToggleOptin

**Usage -** Allows a staff member to opt in or out of receiving reports or being included in the staff chat (basically go off duty as staff).

**Parameters -**

|  source  |
| :----: |
| number   |

**Returns -**  *Nothing*

```lua
QBCore.Functions.ToggleOptin(source)
```

## QBCore.Functions.IsPlayerBanned

**Usage -** Checks the bans table in the database for a matching identifier.

**Parameters -**

|  source  |
| :----: |
| number   |

**Returns -**  *Boolean & String*

```lua
local isBanned, banMessage = QBCore.Functions.IsPlayerBanned(source)
if isBanned then
    print(banMessage)
end
```

## QBCore.Functions.IsLicenseInUse

**Usage -** Checks the bans table in the database for a matching identifier.

**Parameters -**

|  source  |
| :----: |
| number   |

**Returns -**  *Boolean*

```lua
local isLicenseUsed = QBCore.Functions.IsLicenseInUse('license:1234567890123')
if isLicenseUsed then
    -- Do something
end
```