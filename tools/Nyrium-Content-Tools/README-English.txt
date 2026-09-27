NYRIUM CONTENT TOOLS 1.0.0 - By pad7rar
Windows application for PAD7RAR-MVP 0.3.1 or newer.

1. Install CS2 and CS2 Workshop Tools on your PC.
2. Put MP3/WAV/GIF files in input, then open Nyrium-Content-Tools.exe.
   You can also use Add files or drag files into the list.
3. Select the CS2 root directory containing game and content.
4. Review names and IDs. Set Premium and optionally SteamIDs or permissions
   such as @pad7rar/premium, separated with commas.
   Preview controls whether a song can be previewed in the plugin.
5. Choose an output parent folder and click Build.
6. On success, click Open output and read BUILD-INFO.txt.

AUTOMATIC GIF RESIZING
GIFs become 50 frames at 256x256 pixels, packed in a 2048x2048 atlas and
compiled for CS2. Aspect ratio is preserved; rectangular images may have
black padding. Accepted duration: 0.1-15 seconds. Short square GIFs work best.

OUTPUT
server/plugins/PAD7RAR-MVP -> server game/csgo/addons/counterstrikesharp/plugins/PAD7RAR-MVP
server/game/csgo           -> server game/csgo
client/game/csgo           -> assets for local testing
BUILD-INFO.txt             -> compiled addon path for Workshop Tools
nyrium-project.json       -> reusable project (not a server content catalog)
logs/                     -> compiler logs

Workshop publishing is a separate step. Publish/update your addon and set
its ID in MultiAddonManager. The application does not upload to Steam.
Preserve player data and server settings. Restart after updating assets.

ADDING MORE CONTENT
Load your previous project before adding new files. Keep ALL custom entries
in every build; building only the new item replaces the custom collection.
Save project also works before compilation. Project files reference original
media paths: keep the original files in place. Each build gets a new folder.
Keep your personal projects and media outside the public repository.

REQUIREMENTS
Windows with .NET Framework 4.5+ (included in Windows 10/11), Windows PowerShell,
CS2 and CS2 Workshop Tools. The compiler needs write access to the CS2 addon folders.
Application source and the build script are not shipped as editable files.
The conversion engine and templates are embedded and extracted temporarily
at runtime. Generated addon resources remain available for Workshop use.

GitHub: https://github.com/VanishOSF/PAD7RAR-MVP
Discord: https://discord.gg/FmGBPWTkDP
