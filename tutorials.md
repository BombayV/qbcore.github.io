# QBCore Tutorials
Here you can find tutorials about everything related to QBCore + some extra ones about FiveM. We will add the most updated ones or the ones with the most useful information.

## Videos

### QBCore Setting Permissions
- *https://www.youtube.com/watch?v=7OzvgL7B7hs*

### QBCore Installation with txAdmin
- *https://www.youtube.com/watch?v=7OzvgL7B7hs*

### QBCore Installation on ZapHosting
- *https://zap-hosting.com/guides/docs/en/fivem_txadmin_setup/*

- *https://youtu.be/dGXEj_06WEw*

- **Remote URL:**

```input
https://raw.githubusercontent.com/qbcore-framework/txAdminRecipe/main/qbcore.yaml
```

## Text

### Script Optimization
1) Always replace `GetPlayerPed(1)1)` with `PlayerPedId()`.

1) Always replace `GetDistanceBetweenCoords` with lua math aka #`(vector3 1) vector3)`

1) Don't create unnecessary threads. If you can take a thread and turn it into a function and call that somewhere else to trigger it, do it.

1) If you are creating a function or an event, make it so that it can be used in many different formats with different variables. Keep it universal basically.

1) If you do have to create a thread that includes a `while` loop, always avoid using `while true do` if possible. If you have to use this then just follow #6 and it won’t impact performance much.

1) Control your thread times by using a variable that changes the wait time retroactively. So you can set the thread wait time to say `1000ms` which check for your if statement every second and if it makes it into the statement you can lower the wait time by just changing the variable value, `Wait(sleep)`.

1) If you have job specific loops, make sure they only apply to players with that job. There's no reason for someone who is not a cop to be running a loop on their machine that does not apply to them

1) Not really optimization related but a surplus amount of security in a code is not a bad thing. Don't be afraid to add in multiple if checks or create random variables to pass through your events

1) Ties into security as well, never do any type of transaction with the player regarding money or items on the client side of a resource

1) Instead of using `table.insert`, use `tableName[#tableName+1] = data`. You can read more about this [here](https://springrts.com/wiki/Lua_Performance).

1) Instead of using `if something ~= nil` use `if something then`. This method checks for nil and/or false at the same time. You can also do `if not something then`.

1) Localize as many functions and variables as possible. Lua can read them faster.

1) Utilize the `onPlayerLoaded`, `onJobUpdate`, `onGangUpdate`, `onPlayerUnloaded` event handlers to set variables in your script like `local PlayerJob = {}` and then in your script you can do `if PlayerJob.name == 'job' then`. This allows you to not have to get the player object all the time.


### Enable Onesync Infinity

- Startup Args:

```cmd
+set onesync on
```

- `server.cfg` file:

```cfg
set onesync on
```

- txAdmin: Go to settings, then onesync, and choose infinity.

### Voice System
1) Set onesync infinity on.
2) Download [**pma-voice**](https://github.com/AvarianKnight/pma-voice/releases/tag/v4.0.0).
3) Add the following code in your `server.cfg` file.
```cfg
# PMA Voice Convars (Onesync Infinity Only) -- https://github.com/AvarianKnight/pma-voice
ensure pma-voice
setr voice_useNativeAudio true
setr voice_useSendingRangeOnly true
setr voice_defaultCycle "N"
setr voice_defaultVolume 0.3
setr voice_enableRadioAnim 1
setr voice_syncData 1
```
4) Download [rp-radio](https://github.com/qbcore-framework/rp-radio) for a better roleplaying experience.