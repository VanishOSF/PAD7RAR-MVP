NYRIUM CONTENT TOOLS 1.0.1 - QUICK START

PREPARE
Open Nyrium-Content-Tools.exe, add MP3/WAV/GIF files and click Build.
Select your CS2 root (containing game and content) with Workshop Tools installed.
GIFs resize automatically. Set Premium and SteamID/permission access as needed.

STEP 1 - SERVER
Stop the server. Merge 1-SERVER/game into /home/container/game.
Preserve settings and player data. The PAD7RAR-MVP plugin must already be installed.

STEP 2 - WORKSHOP
2-WORKSHOP contains the complete addon: sounds, volume events, panel and GIFs.
Publish it or update your existing addon with all generated resources.
START-HERE.txt identifies the addon already prepared in your CS2 installation.
Check the directory selected by Workshop Tools and complete Publish/Update.
Set its Workshop ID in mm_extra_addons, preserving other required IDs.
Start the server. Players receive the resources through Workshop.

No manual installation in each player's game is required.
Copying files locally does not publish an update to Steam.

KEEP ON YOUR PC
3-PROJECT/nyrium-project.json: load this next time before adding more content.
Keep all entries and original media in place for every rebuild.
4-SUPPORT: logs and technical details for troubleshooting, not installation.
Do not upload projects or logs to Git/Workshop.

REQUIREMENTS
Windows, .NET Framework 4.5+, Windows PowerShell and CS2 Workshop Tools.
GIF duration 0.1-15 seconds; 50 frames at 256x256, preserving aspect ratio.
Utility source remains private; engine and templates are embedded in the EXE.
https://github.com/VanishOSF/PAD7RAR-MVP
https://discord.gg/FmGBPWTkDP