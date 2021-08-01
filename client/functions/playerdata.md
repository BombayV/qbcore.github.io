# PlayerData

In order to retrieve player data client sided. You will need the following to call the values you desire.
```lua
local Player = QBCore.Functions.GetPlayerData()
local citizenid = Player.citizenid
```
!> **Important** - Since the client is already the source, we don't need to specify for the variable `Player`. We also won't need to add `PlayerData` after `Player` unlike obtaining PlayerData server sided.

## Basic Info
All the following is for obtaining a players basic data.

### Citizen Id
*Returns player's citizen id*
```lua
local Player = QBCore.Functions.GetPlayerData()
local citizenid = Player.citizenid
print(citizenid)
```
### Steam
*Returns player's citizen id*
```lua
local Player = QBCore.Functions.GetPlayerData()
local steam = Player.steam
print(steam)
```
### License

### Name

### Cid

### Position 

### Cash

### Bank

## Character Info

### Firstname

### Lastname

### Birthdate

### Gender

### Nationality

### Phone Number

### Account

## Metadata Info

### Hunger

### Thirst

### Stress

### Armor

### Death State

### Stand State

### Handcuffed State

### Jail State

### Tracker

### Status

### Phone

### Fitbit

### Commandbinds

### Bloodtype

### Dealer Rep

### Crafting Rep

### Attachment Crafting Rep

### Job Rep

### Current Apartment

### Callsign

### Fingerprint

### Wallet Id

### Criminal Record

### Licenses

### Inside Data

### Phone Data Apps

## Jobs Info

### Job

### Job Name

### Job Label

### Job Payment

### Job Duty Status

### Gang

### Gang Name

### Gang Label