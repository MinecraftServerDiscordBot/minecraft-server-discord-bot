# Overview
Do you want a Discord Bot to start your Minecraft server? This program will help you do just that!

## Features
This script starts your Minecraft server and shuts it down too! It also shuts down the server when it's inactive. 

## Commands
### There are 6 commands that can be used by anyone: 
1. `/start` will start the Minecraft server if it's not already running. 
2. `/stop` will shut down the Minecraft server if no players are online.  
3. `/info` will give you the server information. 
4. `/ipcheck` will check the server address given in `$info`. The bot will try to update the server address on its own if the address doesn't work. 
5. `/say <message>` will send a message in the Minecraft server if it's running. The message will appear as `{username#0000} <message>`. Note that this is only one-way and that Minecraft to Discord chat integration hasn't been implemented yet. 
6. `/help` can be used to get information on these commands on Discord.
### These commands can be used only by the user(s) set in `server-op`: 
1. `/cmd` will execute a Minecraft command. For example, `/cmd time set 0`. The bot will respond with the output, in this case `Rcon: Set the time to 0`. 
2. `/ipset` will take a new server address and check it. If it's valid, the bot will start using that address moving forward (will be reset if the bot restarts). 

## Installation
Follow these steps: 
### Setting up the Discord bot
#### Do this part ONLY IF you are setting this up for the first time! If you set your bot up previously but are using slash commands on it for the first time, please redo the steps carefully. 
Go to [the Discord Developer site](https://discord.com/developers/), and create a new application. Now go to the "Bot" section and build a bot. 
Head over to the "OAuth2" section, and under it, the "URL Generator" section. Under "Scopes", check `bot` and `applications.commands`.
Under "Bot Permissions", select the permissions "Send Messages", "Read Message History". At the very bottom, there will be a "Generated URL".
Copy it and paste it in your browser. This will allow you to invite your bot to your server. 

### Setting up the Minecraft server
If you haven't already, set up your Minecraft server on your machine as normal. Now go to your `server.properties` file. 
Change the following values:
- `enable-rcon=true`
- `rcon.password=<password>`, where <password> is the password you wish to use for Rcon. 

### Setting up the Bot variables
Open the file named `bot.env`. 
1. Paste your Discord bot token next to `bot-token`. 
2. Paste the server address that other players would use to connect next to `server-address`. 
3. Paste the server start script next to `start-script`. (For example, `start-script=java -Xmx2G -Xms512M -jar server.jar`)
4. Paste the user ID of the account that shall be allowed to execute commands through Rcon next to `server-op`. If you want multiple users, separate each one with `,`. For example: `server-op=123,456,243,632`. Do not use spaces. 

### Important notes
- Minecraft connects to port 25565 by default. If you forward any port other than 25565, your address would look something like `xxx.xxx.xxx.xxx:port` since the port must also be specified for Minecraft. This CAN be set in `bot.env`, in which case the program pings the server on `port`. However, if you use port 25565, you may leave the address as `xxx.xxx.xxx.xxx` and the program will use port 25565 automatically. 