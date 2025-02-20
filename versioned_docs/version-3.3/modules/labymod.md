---
id: labymod
title: LabyMod Module
sidebar_label: LabyMod
---

## What does the "LabyMod module"?
- It shows to your LabyMod friends whenever someone plays on your server:  
![CloudNet-LabyMod-Module-Example.png](img/CloudNet-LabyMod-Module-Example.png)
- It adds support for your Discord friends to join/spectate through your rich presence

## Where can I get it?
The module is located in the extras folder in the [CloudNet.zip](https://github.com/CloudNetService/CloudNet-v3/releases/latest/download/CloudNet.zip),
you just have to put it into your modules folder and restart CloudNet. It will be automatically installed on your proxies.

## Configuration
### enabled
Enables (or disables) the LabyMod Module (`true`/`false`)

<br></br>

### displayRPG
#### enabled
Enables (or disabled) the custom rich presence (`true`/`false`)
:::tip
If you disable the custom rich presence, LabyMod will show the default one:
```
DOMAIN
Ingame
```
:::

#### displayType
Configures what should be replaced by the `%display%` variable in the format
[Here](#displaytypes) you can find the available DisplayTypes

#### format
Sets the message shown in the rich presence.  
`%display%` will be replaced by the value of the chosen `displayType`

<br></br>

### discordJoinMatch
Here you can configure the "Ask to join" button in the Discord rich presence.

#### enabled
Enables (or disables) the button totally (`true`/`false`)

#### excludedGroups
Here you can disable the "Ask to join" button for specific groups.  
Example:
```json
      "excludedGroups": [
        "Lobby",
        "Replay"
      ]
```

<br></br>

### discordSpectateEnabled
Enables (or disables) the "Spectate" button in the Discord rich presence (`true`/`false`)

### excludedSpectateGroups
Disables the "Spectate" button for specific groups.  
Example:
```json
    "excludedSpectateGroups": [
      "Lobby",
      "Community"
    ]
```
:::tip Info
This option is ignored when `discordSpectateEnabled` is set to `false`
:::

<br></br>

### gameModeSwitchMessages
In this section you can configure the gamemode swith message:  
![CloudNet-LabyMod-Module-Example.png](img/CloudNet-LabyMod-Module-Example.png)

#### enabled
Enables (or disables) the gamemode switch message (`true`/`false`)

#### displayType
Configures what should be replaced by the `%display%` variable in the format  
[Here](#displaytypes) you can find the available DisplayTypes

#### format
Sets the message shown in LabyMod.  
`%display%` will be replaced by the value of the chosen `displayType`

<br></br>

### loginDomain
This is the domain on which players will be connected when they click the ["Ask to join"](#discordjoinmatch) or
["Spectate"](#discordspectateenabled) Button in Discord.  
After that they will be sent automatically to the specific server by the module.

<br></br>

## DisplayTypes
The following DisplayTypes are available:
- `SERVICE` - the name of the service (e.g. `Lobby-1`)
- `TASK` - the name of the task (e.g. `Lobby`)
- `FIRST_GROUP` - the name of the first group of the service
- `LAST_GROUP` - the name of the last group of the service

## Sample Configuration
```json
{
  "config": {
    "enabled": true,
    "discordRPC": {
      "enabled": true,
      "displayType": "SERVICE",
      "format": "Playing on %display%"
    },
    "discordJoinMatch": {
      "enabled": true,
      "excludedGroups": []
    },
    "discordSpectateEnabled": true,
    "excludedSpectateGroups": [
      "Lobby"
    ],
    "gameModeSwitchMessages": {
      "enabled": true,
      "displayType": "SERVICE",
      "format": "§bCloud§fNet §8➢ §e%display%"
    },
    "loginDomain": "mc.example.com"
  }
}
```