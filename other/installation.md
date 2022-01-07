# QBCore Installation
Here you'll find all the ways to install QBCore into your server.

?> **Before continuing** - If your doing this without [txAdmin](https://txadm.in/), make sure you already have a basic server installed. This includes [artifacts](https://runtime.fivem.net/artifacts/fivem/build_server_windows/master/) and the default [cfx-server-data](https://github.com/citizenfx/cfx-server-data). You will also need a database like MySQl, HeidiSQL, or XAMPP. Check out [database info]() for more information about this.

## Using txAdmin
**NEW METHOD**
1) We are now in popular templates. Click on Popular Templates and select the QBCore one.
2) Follow the steps given by txAdmin. You will need a key from keymaster and have a database connection established. We recommend adding your Steam API Key too.
3) Wait for everything to download and you'll have your new QBCore server ready to go!

**OLD METHOD**
1) Open the txAdmin interface. It will prompt you with a login and then it will proceed to make you pick to create a server. You will choose **Remote URL Template**.
![](https://c.file.glass/cecj6.png)
2) It will prompt you with select template input. You will add the following

```input
https://raw.githubusercontent.com/qbcore-framework/txAdminRecipe/main/qbcore.yaml
```
![](https://c.file.glass/6e30e.png)
3) Press save and we recommend txAdmin choose the place to save data.
4) After the recipe finishes installing, press start server if it has not yet started. Once it has started, let it run through the basic resources such as yarn and webpack which need to build up. Once they have builded up, restart the server from the txAdmin interface and there you go, your **first QBCore server**.

## Manual Installation
1) Go into your resources folder for your server.
2) Download the dependecies, core resources which you can find in [here](./other/servercfg?id=qbcore-server-cfg), and other resources you plan to use.
3) Add them in your resources folder.
4) Ensure them in your server cfg by adding the following for every resource or by adding with the folder structure.
```cfg
ensure [folderName] # Similar to globbing
ensure resourceName # Singular resource
```
5) In your `server.cfg` add the following. Remember to replace it with your own data.
```cfg
set mysql_connection_string "mysql://user:password@host/database?charset=utf8mb4&dateStrings=true"
```