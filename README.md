# DeluxeChat
## About
DeluxeChat allows you to create endless customizable chat formats that add "hover tooltips" and also suggest/execute command on click to your chat!

This plugin should be compatible with most chat spam/chat utility plugins but it will override your chat format to be displayed through the formats defined in the DeluxeChat config.yml. (This will override any essentials chat formats/chat channel plugins to display the DeluxeChat format. See the [known issues/bugs part](https://github.com/help-chat/DeluxeChat#known-issuesbugs) for incompatible plugins)  
DeluxeChat is made to handle all aspects of how your chat formatting looks.

## Chatformat and priority
Chat formats are loaded from the config.yml and are tied to permission nodes.  
To give a player/group a chat format, you will need to give the player/group the permission `chatformat.<yourFormatIdentifier>`.

If a player has multiple chat format permissions available, the chat format priority will determine what format should be active for the player/group.  
You can assign the priority of each chat format!  
The priority-system is always lower number = higher priority!

## TownyChat
DeluxeChat is also fully compatible with Towny. It will work alongside TownyChat so you can manage your chat channels within TownyChat and allow DeluxeChat to handle your chat formatting. If you would like To use TownyChat integration, there is only one requirement. In your Towny channels.yml you must add a new option to every channel - hooked: true

```yaml
    general:
        commands: [g]
        type: GLOBAL
        channeltag: '&f[g]'
        messagecolour: '&f'
        permission: 'towny.chat.general'
        craftIRCTag: 'admin'
        range: '-1'
        hooked: true # Add this to your channel in TownyChat
```

## Commands
* `/dchat`  
View plugin version/info  
Permission: `deluxechat.admin`
* `/dchat reload`  
Reload DeluxeChat configuration  
Permission: `deluxechat.admin`
* `/gtoggle`  
Switch from global to local chat if bungee is enabled  
Permission: deluxechat.bungee.toggle
* `/msg <player> <message>`  
Send a player a private message  
Aliases: [message, pm, tell]  
Permission: `deluxechat.pm`
* `/reply <message>`  
Description: reply to a private message  
Aliases: [r]  
Permission: `deluxechat.pm`
* `/socialspy:`  
Spy on private messages  
Aliases: [deluxesocialspy]  
Permission: `deluxechat.socialspy`

## Permissions
If you have bungeecord enabled, players need permission to speak across servers! Give the player the permission `deluxechat.bungee.chat` to allow them to chat across servers!  
See the [BungeeCord-installation](https://github.com/help-chat/DeluxeChat/wiki/Installation#bungeecord) page on the wiki for more information.

**Normal permissions**:
* `chatformat.default`  
Default chat format  
Default: true
* `deluxechat.color`  
Ability to use color codes in chat  
Default: OP
* `deluxechat.formatting`  
Ability to use formatting codes in chat  
Default: OP
* `deluxechat.utf`  
Ability to use special utf characters in chat  
Default: OP
* `deluxechat.admin`  
Ability to use dchat commands  
Default: OP
* `deluxechat.hidden`  
Ability to see hidden tooltip messages  
Default: OP
* `deluxechat.filter.bypass`  
Ability to bypass the chat filter if enabled  
Default: OP
* `deluxechat.url`  
Ability to send clickable links in chat  
Default: OP
* `deluxechat.pm.url`  
Ability to send clickable links in private messages  
Default: OP
* `deluxechat.pm`  
Ability to use /msg and /reply to private message  
Default: OP
* `deluxechat.socialspy`  
Ability to use /socialspy to see private conversations  
Default: OP
* `deluxechat.socialspy.onjoin`  
Will toggle socialspy on for the player when they join the server  
Default: OP

**BugeeCord-related permissions**:
* `deluxechat.bungee.chat`  
Ability to chat globally if bungee is enabled  
Default: OP
* `deluxechat.bungee.toggle`  
Ability to chat globally if bungee is enabled  
Default: OP
* `deluxechat.bungee.override`  
Always send to all players when in global chat even if player is in server only chat  
Default: OP

## Configuration
All of your chat formats are loaded from the config.yml

To create a custom chat format just copy the default chat format section from the `formats:` section and paste it below default!  
You can find an example-config [here](https://github.com/help-chat/DeluxeChat/tree/master/configs/config.yml)!

## Placeholders
DeluxeChat 1.12.0 or higher uses any placeholder provided by [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/).  
You must have PlaceholderAPI installed on your server for DeluxeChat 1.12+ to work.  
A list of available placeholders can be found [here](https://helpch.at/placeholders)

Information on pre 1.12.0 placeholders below  
[click for DeluxeChat pre 1.12.0 placeholders](https://www.spigotmc.org/wiki/deluxechat-placeholders/)

[Maximvdw](http://www.spigotmc.org/resources/authors/maximvdw.6687/) was kind enough to share all of his placeholders with his plugin MVdWPlaceholderAPI and they are available to use if you have purchased any of his plugins that have placeholders included in them.

You must have [MVdWPlaceholderAPI](https://www.spigotmc.org/resources/mvdwplaceholderapi.11182/) and one of his premium-plugins installed to use his placeholders!

To enable his placeholders, make sure you meet the requirements above, and simply enable the hook by setting:  
```yaml
hooks:
  mvdw_placeholderapi: true
```
After this is done, you can begin using his placeholders with the following placeholder format:
```yaml
%mvdw_<placeholder without brackets>%
```
Make sure, that you have downloaded the mvdw-expansion with `/papi ecloud download mvdw`

**Example**:
```yaml
    prefix_tooltip:
    - 'Maxims placeholders from MVdWPlaceholderAPI:'
    - 'name: %mvdw_player%'
    - 'Plugin count: %mvdw_pluginscount%'
    - 'Ram: %mvdw_usedram% / %mvdw_freeram%'
```
[Click here for Maxims 2000+ placeholders](http://www.spigotmc.org/wiki/mvdw-placeholders/)

## Hooking into DeluxeChat
### For DeluxeChat Version 1.12 or above
DeluxeChat uses PlaceholderAPI for its placeholders from this version and onward.  
Check the [hook into PlaceholderAPI](https://github.com/help-chat/PlaceholderAPI/wiki/Hook-into-PlaceholderAPI) page for more info.

## Known issues/Bugs
The latest version of DeluxeChat is compatible with Bukkit/Spigot 1.9 up to 1.13 
for older version support check the version history tab. those old versions are available but no longer supported.

If you want support for any problems, bugs, or features, it is expected that you are running the latest version of DeluxeChat on a 1.9 or higher server!

This plugin modifies chat completely to send tooltip messages and allow clickable chat format parts! There may be some incompatibility issues with other chat related plugins...  
Known plugins, that won't work with DeluxeChat are:
- EssentialsChat

Please contact us on discord (link below) for any other incompatible plugin, that isn't listed here.

If you are using a plugin such as Factions, make sure all Factions chat config options are set to false or it will override DeluxeChat and you won't see your DeluxeChat formats when talking in chat!

## Legal Notice:
This plugin utilizes the Fanciful library by Max Kreminski.
Fanciful is licensed under MIT, the Fanciful license can be found
[Here](https://github.com/mkremins/fanciful/blob/master/LICENSE)

## Links
[![HelpChat Discord](https://discordapp.com/api/guilds/164280494874165248/embed.png)](https://discord.gg/FtArYRQ 'Join the Help Chat!')  
[SpigotMC](https://www.spigotmc.org/resources/deluxechat.1277/)
