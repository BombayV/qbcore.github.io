# QBCore Server Cfg
- It is highly recommended to use the [txAdmin recipe](https://raw.githubusercontent.com/qbcore-framework/txAdminRecipe/main/qbcore.yaml). It already runs inside txAdmin so it's not needed to do it manually.

```cfg
## You CAN edit the following:
endpoint_add_tcp "0.0.0.0:30120"
endpoint_add_udp "0.0.0.0:30120"
sv_maxclients 10
set steam_webApiKey "none"
sets tags "default, deployer, qbcore, qb-core"

## You MAY edit the following:
sv_licenseKey "LICENSE_KEY_HERE"
sv_hostname "QBCore Server!"
sets sv_projectName "[QBCore] Server Name"
sets sv_projectDesc "Very cool QBCore testing server!"
sets locale "en-US"
load_server_icon myLogo.png
set mysql_connection_string "mysql://user:password@host/database?charset=utf8mb4&dateStrings=true"

# Voice config
setr voice_useNativeAudio true
setr voice_useSendingRangeOnly true
setr voice_defaultCycle "GRAVE"
setr voice_defaultVolume 0.3
setr voice_enableRadioAnim 1
setr voice_syncData 1

# These resources will start by default.
ensure mapmanager
ensure chat
ensure spawnmanager
ensure sessionmanager
ensure basic-gamemode
ensure hardcap
ensure baseevents

# QBCore & Extra stuff
# As mentioned before, it is easier to download and install QBCore from txAdmin. If you decide to go this route, you might experience problems with the loading order
ensure qb-core
ensure [qb]
ensure [standalone]
ensure [voice]
ensure hospital_map

# Add system admins
add_ace group.admin command allow # allow all commands
add_ace group.admin command.quit deny # but don't allow quit
add_principal identifier.fivem:XXXXXXX group.admin # Your identifier
```