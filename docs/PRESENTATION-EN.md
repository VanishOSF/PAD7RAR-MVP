# Installation Guide

**PAD7RAR-MVP 0.4.0 / Nyrium Content Tools 1.0.7**

## Update 0.4.0

- Personalized panel title displaying each viewer's player name.
- Fixed CustomHud rejection caused by an unsupported title attribute.
- One built-in applause variant; previous monochrome/sepia choices display the original. Custom GIFs are preserved.
- Random MVP selects free songs when no valid fixed selection is available, including while database preferences are pending. Temporary choices never overwrite saved selections.
- Panel and Random MVP confirmed working in game by the server administrator; 103 local regression checks passed.
- Update the DLL and deps file, then re-upload the compiled Workshop resources to your existing item. Preserve configuration, custom catalogs and player data.
- Content Tools remains at 1.0.7 and is unchanged by this release.

[Home](../README.md) | [Romanian guide](../README.txt)

## Install Once
Use compatible Metamod, CounterStrikeSharp (.NET 10 / API 1.0.375) and MultiAddonManager.
Stop the server. Merge `server/game/csgo/addons/` into `/home/container/game/csgo/addons/`.
Upload dependencies and deps.json first, then PAD7RAR-MVP.dll.
Keep ClientprefsApi.dll in `addons/counterstrikesharp/shared/ClientprefsApi/`.
For new installations only, copy `examples/config.toml` into
`game/csgo/addons/counterstrikesharp/configs/plugins/PAD7RAR-MVP/config.toml`.
Preserve configs, banner.json, nyrium.json, custom volume-events.json, catalogs and data on updates.
config.json takes precedence over TOML. Do not load MVP-Anthem alongside this plugin.

## Generate, Publish, Configure
1. Close CS2 and Workshop Tools. Open Nyrium on Windows.
2. Select the CS2 root, add MP3/WAV/GIF files and configure names/access.
3. Generate and wait for success. Nyrium reuses `nyrium_global`.
4. Publish/update that addon in Workshop Tools, keeping the same Workshop item.
5. Upload only `nyrium-custom.json` to `game/csgo/addons/counterstrikesharp/plugins/PAD7RAR-MVP/content/`.
6. Add the Workshop ID to `mm_extra_addons` in `game/csgo/cfg/multiaddonmanager/multiaddonmanager.cfg`.
7. Restart and verify server mounting, client downloads, preview, GIF and round-end playback.

Do not use only `mm_client_extra_addons`: the server must mount resources too.
If downloads finish after map loading, reload the map for precache.
[MultiAddonManager documentation](https://github.com/Source2ZE/MultiAddonManager)

No separate sounds/soundevents/Panorama server upload is needed.
Those compiled assets remain necessary inside Workshop.
Never delete shared server folders wholesale during migration.

## Project and Updates
Keep `nyrium-project.json`, originals and `.logs/` on your PC.
The project stores paths, not copies of media.
Keep ALL desired entries when rebuilding: the new catalog replaces the old custom catalog.
Configured demo songs and built-in GIFs are not automatically removed.
Nyrium preserves other plugins' resources but does not install ElitePanel.

The optional standard addon is in `workshop/game/csgo_addons/pad7rar_mvp/`.
Do not overwrite generated custom-GIF CSS with standard CSS or mount conflicting resources.

- DLL update: server only, no Workshop re-upload.
- Names/access/Premium: edit the catalog and restart; keep the project in sync.
- Audio/GIF/UI: regenerate and re-upload.
- Old custom banks must be regenerated to receive the audio fix.
- Nyrium 1.0.6 center-crops GIFs without added letterboxing; edges may be cropped.

With `GiveRandomMVP = true`, players without manual choices receive a random accessible
song at each MVP award. `!mvprandom` clears the fixed choice.
Volume persists by SteamID in `data/volume-selections.json`; preserve data on updates.
86 lifecycle tests passed locally. Git publication does not install the server or publish Workshop.
No private plugin C# source, credentials or player data are included.
