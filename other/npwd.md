# NPWD
Here you will find all the information related to the newly released phone called [NPWD](https://github.com/project-error/npwd/releases). If you want further documentation about the phone, it is recommened that you go [HERE](https://projecterror.dev/docs/npwd/start/installation).

## Dependencies
Below are a list of dependencies, outside of the standard installation, for *NPWD* to work with *QBCore*
- [qb-core](https://github.com/qbcore-framework/qb-core)
- [qb-npwd](https://github.com/project-error/qb-npwd)
    - Required for the resource to work with the framework.
    - Uses the `newPlayer` export.

### Configuration
You will need to adjust the `config.json` file to match the example below. This is required for `qb-npwd` to function correctly. This is located within the root of your `npwd` folder. See [here](https://github.com/project-error/npwd/blob/master/config.json).

```json
  "general": {
    "useResourceIntegration": true,
    "toggleKey": "f1",
    "toggleCommand": "phone"
  },
  "database": {
    "useIdentifierPrefix": false,
    "playerTable": "players",
    "identifierColumn": "citizenid",
    "identifierType": "license",
    "profileQueries": true,
    "phoneNumberColumn": "phone_number"
  },
```

### Final Notes
Be sure your `server.cfg` resembled the example found within the [installation](../start/installation#example-final-config) page. As a reminder, `qb-npwd` will not support any non official versions of [QB-Core](https://github.com/qbcore-framework/qb-core).

## Errors

### Event playerJoining was not safe for net

You need to update your artifacts to a version beyond `3622`. Don’t know your artifact version? Type `version` into your console.

Click [here](https://runtime.fivem.net/artifacts/fivem/build_server_windows/master/?) to download the latest.

### No such export isPhoneVisible

You downloaded the source code and didn’t build.

Please download from the [release tab](https://github.com/project-error/npwd/releases) and **be sure** you download the `npwd.zip` as this is the built version.

If you want to modify the source code please see the [documentation page](dev/DevelopmentBootstrap.md) for building.

### No such export: newPlayer in resource npwd

This export is only available when the `useResourceIntegration` is set to true. See [here](https://github.com/project-error/npwd/blob/fc2a905f0fd85db797b716053b8f0d4398b8bd61/config.json#L8).

### Cannont read properties of undefined (reading 'phone_number')
The error would look like [this](https://i.imgur.com/IIM0vEd.png)

This is usually caused by:
- You did not configure the `config.json` properly.
    - Please follow the configuration [documentation](start/installation#basic-configuration) again.
- You do not have a users table where you store player's identifiers.
    - As of v1.04, *NPWD* doesn't generate one.
    - You will need to install [pe-core](https://github.com/project-error/pe-core).
- You do not have a `phone_number` column.
    - See the [sql file](https://github.com/project-error/npwd/blob/13335e98d55ea7a082bf08c7c17f24866658a2d1/import.sql#L3) for an example query.

### Failed to upload photo, Column 'image' cannot be null
Ensure you installed the correct version of [screenshot-basic](https://github.com/project-error/screenshot-basic) and have followed the documentation for generating an *imgur* [token](start/installation#setting-up-camera-functionality). If you have done so, then imgur may be blocked in your country. We're working on alternatives for this issue.