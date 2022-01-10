# Player Functions Server

In order to perform functions like adding money or removing it, we will need to get the player first.
```lua
local _src = source
local Player = QBCore.Functions.GetPlayer(_src)

-- Example
--Player.Functions.AddMoney('bank', 500)
```
!> **Important** - Just like getting the `PlayerData` server side, we need to get the player first as shown above. We specify the source of the player which is the "player id" of a player. This will allow us to trigger functions on the user we passed in.

## Player.Functions.SetJob

**Usage -** Sets a player's job and returns a boolean if was successful or not.

**Parameters -**

|  job   ||  grade   |
| :----:    || :----:    |
| string    || string    |

**Returns -**  *Boolean*

```lua
local newJob = Player.Functions.SetJob('police', '0')
if newJob then
    -- Do something
end
```

## Player.Functions.SetJobDuty

**Usage -** Sets a player's job and returns a boolean if was successful or not.

**Parameters -**

|  onDuty   |
| :----:    |
| boolean    |

**Returns -**  *Nothing*

```lua
local newJob = Player.Functions.SetJobDuty(true)
```

## Player.Functions.UpdatePlayerData

**Usage -** Update the entire `PlayerData`.

**Parameters -**

|  dontUpdateChat   |
| :----:    |
| boolean    |

**Returns -**  *Nothing*

```lua
Player.Functions.UpdatePlayerData(true)
```

## Player.Functions.SetMetaData

**Usage -** Update a metadata based on arguments given.

**Parameters -**

|  meta   ||  val   |
| :----:    || :----:    |
| string    || any    |

**Returns -**  *Nothing*

```lua
Player.Functions.SetMetaData('armor', '0')
```

## Player.Functions.SetGang

**Usage -** Sets a player's gang and returns a boolean if was successful or not.

**Parameters -**

|  gang   ||  grade   |
| :----:    || :----:    |
| string    || string    |

**Returns -**  *Boolean*

```lua
local newGang = Player.Functions.SetGang('lostmc', '0')
if newGang then
    -- Do something
end
```

## Player.Functions.AddJobReputation

**Usage -** Updates the reputation of a player's job.

**Parameters -**

|  amount   |
| :----:    |
| number    |

**Returns -**  *Nothing*

```lua
Player.Functions.AddJobReputation(5)
```

## Player.Functions.AddMoney

**Usage -** Add money to the user's current money account.

**Parameters -**

|  moneyType      ||  amount      ||  reason      |
| :----:    || :----:    || :----:    |
| string    || number    || string    |

**Returns -**  *Boolean*

```lua
local addedMoney = Player.Functions.AddMoney('bank', 1500, 'New money cause cool!')
if addedMoney then
    -- Do something
end
```

## Player.Functions.RemoveMoney

**Usage -** Remove money to the user's current money account.

**Parameters -**

|  moneyType      ||  amount      ||  reason      |
| :----:    || :----:    || :----:    |
| string    || number    || string    |

**Returns -**  *Boolean*

```lua
local addedMoney = Player.Functions.RemoveMoney('bank', 1500, 'Bye money cause cool!')
if addedMoney then
    -- Do something
end
```

## Player.Functions.SetMoney

**Usage -** Sets money to the user's current money account. Does not add money, instead sets it to the passed amount.

**Parameters -**

|  moneyType      ||  amount      ||  reason      |
| :----:    || :----:    || :----:    |
| string    || number    || string    |

**Returns -**  *Boolean*

```lua
local newMoney = Player.Functions.SetMoney('bank', 1500, 'Set money cause cool!')
if newMoney then
    -- Do something
end
```

## Player.Functions.GetMoney

**Usage -** Returns the passed money type amount. If type is not passed, returns false.

**Parameters -**

|  moneytype   |
| :----:    |
| number    |

**Returns -**  *Number*

```lua
local money = Player.Functions.GetMoney('bank')
if money then
    -- Do something
end
```

## Player.Functions.AddItem

**Usage -** Adds an item to the player's inventory. If slot is passed, item will be deleted from slot passed if exists. If info is passed, information about the item will be updated.

**Parameters -**

|  item   ||  amount   ||  slot   ||  info   |
| :----:    || :----:    || :----:    || :----:    |
| string    || number    || number    || string    |

**Returns -**  *Boolean*

```lua
local newItem = Player.Functions.AddItem('phone', 1)
if newItem then
    -- Do something
end
```

## Player.Functions.RemoveItem

**Usage -** Removes a person's item by item name and passed count.

**Parameters -**

|  item   ||  amount   ||  slot |
| :----:    || :----:    || :----:    |
| string    || number    || number    |

**Returns -**  *Boolean*

```lua
local removedItem = Player.Functions.RemoveItem('phone', 1)
if removedItem then
    -- Do something
end
```

## Player.Functions.SetInventory

**Usage -** Sets a player's inventory based on passed items.

**Parameters -**

|  items   ||  dontUpdateChat   |
| :----:    || :----:    |
| table    || boolean    |

**Returns -**  *Nothing*

```lua
Player.Functions.SetInventory(items, true)
```

## Player.Functions.ClearInventory

**Usage -** Clears a player's inventory by setting items to an empty table.

**Parameters -** *Nothing*

**Returns -**  *Nothing*

```lua
Player.Functions.ClearInventory()
```

## Player.Functions.GetItemByName

**Usage -** Returns if a player has the passed item name.

**Parameters -**

|  item   |
| :----:    |
| string    |

**Returns -**  *Table/Nil*

```lua
local item = Player.Functions.GetItemByName('phone')
if item then
    -- Do something
end
```

## Player.Functions.GetItemsByName

**Usage -** Gets all the items by passed item name. Returns all unlike `GetItemByName` which returns the first one.

**Parameters -**

|  item   |
| :----:    |
| string    |

**Returns -**  *Table*

```lua
local items = Player.Functions.GetItemsByName('phone')
if items and #items > 0 then
    -- Do something
end
```

## Player.Functions.SetCreditCard

**Usage -** Updates a player's character credit card to passed argument.

**Parameters -**

|  cardNumber   |
| :----:    |
| string    |

**Returns -**  *Nothing*

```lua
Player.Functions.SetCreditCard(creditCardNumber)
```

## Player.Functions.GetCardSlot

**Usage -** Returns a player's credit card slot based on number and type.

**Parameters -**

|  cardNumber   ||  cardType   |
| :----:    || :----:    |
| string    || string    |

**Returns -**  *Table/Nil*

```lua
local cardSlot = Player.Functions.GetCardSlot(creditCardNumber, creditCardType)
if cardSlot then
    -- Do something
end
```

## Player.Functions.GetItemBySlot

**Usage -** Gets an item by the passed slot number.

**Parameters -**

|  slot   |
| :----:    |
| number    |

**Returns -**  *Table/Nil*

```lua
local item = Player.Functions.GetItemBySlot(1)
if item then
    -- Do something
end
```

## Player.Functions.Save

**Usage -** Saves a player to the database.

**Parameters -** *Nothing*

**Returns -**  *Nothing*

```lua
Player.Functions.Save()
```