# Client-Sided Functions and Usage

The following info contains every function in QBCore framework and how to use it. It also contains some basic info on what it does.

?> **Important information** - All the following functions required QBCore object which is called through the import in the fxmanifest. If you don't know yet about importing the QBCore object, we recommend reading the [fxmanifest documentation]()

## QBCore.Functions.GetPlayerData

**Usage -** Perhaps the most used function in the framework. This functions returns the players data of the current source which, since its used client side, is automatically the client or player. It can be used with modifiers on the end starting with a "." (period).

**Parameters -** cb

**Returns -**  *QBCore.PlayerData*

```lua
QBCore.Functions.GetPlayerData = function(cb)
    if cb ~= nil then
        cb(QBCore.PlayerData)
    else
        return QBCore.PlayerData
    end
end
```