# DeluxeChat
## About
DeluxeChat allows you to create endless customizable chat formats that add "hover tooltips" and also suggest/execute command on click to your chat!

This plugin should be compatible with most chat spam/chat utility plugins but it will override your chat format to be displayed through the formats defined in the DeluxeChat config.yml. (This will override any essentials chat formats/chat channel plugins to display the DeluxeChat format)  
DeluxeChat is made to handle all aspects of how your chat formatting looks.

## Chatformat and priority
Chat formats are loaded from the config.yml and are tied to permission nodes.  
To give a player/group a specific/custom chat format, you will need to give the player/group the permission `chatformat.<yourFormatIdentifier>`.

If a player has multiple chat format permissions available, the chat format priority will determine what format should be active for the player/group.  
You can assign the priority of each chat format!

## TownyChat
DeluxeChat is also fully compatible with Towny. It will work alongside TownyChat so you can manage your chat channels within TownyChat and allow DeluxeChat to handle your chat formatting. If you would like To use TownyChat integration, there is only one requirement. In your Towny channels.yml you must add a new option to every channel - hooked: true​

```yaml
    general:
        commands: [g]
        type: GLOBAL
        channeltag: '&f[g]'
        messagecolour: '&f'
        permission: 'towny.chat.general'
        craftIRCTag: 'admin'
        range: '-1'
        hooked: true
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
All formats require a special permission node for the format to be applied to a player/group: 
```
chatformat.<formatidentifier>
```  
The <formatIdentifier> is the key for the format section which you want to apply to the player​

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
​
## Configuration
All of your chat formats are loaded from the config.yml

To create a custom chat format just copy the default chat format section from the `formats:` section and paste it below default!  
You can find an example-config [here](https://github.com/help-chat/DeluxeChat/tree/master/configs/config.yml)!

​## Placeholders
DeluxeChat 1.12.0 or higher uses any placeholder provided by [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/).  
You must have PlaceholderAPI installed on your server for DeluxeChat 1.12+ to work.

Information on pre 1.12.0 placeholders below  
[click for DeluxeChat pre 1.12.0 placeholders](https://www.spigotmc.org/wiki/deluxechat-placeholders/)

[Maximvdw](http://www.spigotmc.org/resources/authors/maximvdw.6687/) was kind enough to share all of his placeholders with his plugin MVdWPlaceholderAPI and they are available to use if you have purchased any of his plugins that have placeholders included in them.

You must have one of the following plugins installed and the plugin [MVdWPlaceholderAPI](https://www.spigotmc.org/resources/mvdwplaceholderapi.11182/) installed to use his placeholders:

[Tab](http://www.spigotmc.org/resources/tab.1448/)
[ActionBar](http://www.spigotmc.org/resources/actionbar.1458/)
[TitleMotdAdvanced](http://www.spigotmc.org/resources/titlemotdadvanced.1629/)
[FeatherBoard](http://www.spigotmc.org/resources/featherboard.2691/)
[AnimatedNames](http://www.spigotmc.org/resources/animatednames.2175/)
[DynamicSigns](http://www.spigotmc.org/resources/dynamicsigns.3566/)

To enable his placeholders, make sure you meet the requirements above, and simple enable the hook by setting:  
```yaml
hooks:
  mvdw_placeholderapi: true
```
After this is done, you can begin using his placeholders with the following placeholder format:
```yaml
%mvdw_<placeholder without brackets>%
```

**Example**:​
```yaml
    prefix_tooltip:
    - 'Maxims placeholders from MVdWPlaceholderAPI:'
    - 'name: %mvdw_player%'
    - 'Plugin count: %mvdw_pluginscount%'
    - 'Ram: %mvdw_usedram% / %mvdw_freeram%'
```
[Click here for Maxims 2000+ placeholders](http://www.spigotmc.org/wiki/mvdw-placeholders/)

## Hooking into DeluxeChat
If you are a developer and want to add placeholders to DeluxeChat, you can too!  
Click [here](https://github.com/extendedclip/DeluxeChatPlaceholderAPI/blob/master/src/me/clip/placeholdertest/PlaceholderTestPlugin.java) for examples on how to do that.

If you don't have DeluxeChat, but still want to add placeholders for people who use your plugin, you can use this API-package:  
[DeluxeChat placeholder API](https://github.com/extendedclip/DeluxeChatPlaceholderAPI/tree/master/src/me/clip/deluxechat/placeholders)

## Known issues/Bugs
The latest version of DeluxeChat is compatible with Bukkit/Spigot 1.9/1.10/1.11/1.12  
for older version support check the version history tab. those old versions are available but no longer supported.

If you want support for any problems, bugs, or features, it is expected that you are running the latest version of DeluxeChat on a 1.9 or higher server!

This plugin modifies chat completely to send tooltip messages and allow clickable chat format parts! There may be some incompatibility issues with other chat related plugins...

If you are using a plugin such as Factions, make sure all Factions chat config options are set to false or it will override DeluxeChat and you won't see your DeluxeChat formats when talking in chat!
​
## Legal Notice:
This plugin utilizes the Fanciful library by Max Kreminski.
Fanciful is licensed under MIT, the Fanciful license can be found
[Here​](https://github.com/mkremins/fanciful/blob/master/LICENSE)

## Links
<a href="https://discord.gg/FtArYRQ" target="_blank"><img src="https://discordapp.com/api/guilds/164280494874165248/embed.png" alt="Discord"></a>  
[SpigotMC](https://www.spigotmc.org/resources/deluxechat.1277/)