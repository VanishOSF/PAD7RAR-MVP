# Installation Guide

**PAD7RAR-MVP 0.3.6 / Nyrium Content Tools 1.0.2**

[Home](../README.md) · [Romanian guide](../README.txt)

## Two Destinations, One Installation

- **Server:** plugin DLL, dependencies, settings, catalog and server assets.
- **Workshop:** compiled Panorama UI, textures, sound files and sound-event bank.
- **Your PC only:** Nyrium, saved projects and original MP3/WAV/GIF files.

Uploading files to the server does not publish them to Steam.
Workshop publication does not install the server plugin.
Never upload DLLs, credentials, private projects or player data to Workshop.

## Requirements

Use compatible Metamod, CounterStrikeSharp and MultiAddonManager builds.
This plugin targets .NET 10 and CSS API 1.0.375; do not downgrade a working server blindly.
Custom content preparation requires Windows and CS2 Workshop Tools.

ClientprefsApi.dll is included as a shared dependency. It is not the Clientprefs plugin.
Volume, language and GIF preferences have local persistence; Clientprefs integration is optional.

## 1. Prepare the Workshop Addon

The standard compiled addon is in:
`workshop/game/csgo_addons/pad7rar_mvp/`

Copy it to:
`<CS2>/game/csgo_addons/pad7rar_mvp/`

Create `<CS2>/content/csgo_addons/pad7rar_mvp/` if it is missing.
Select the addon in CS2 Workshop Tools and publish it, or update your existing item.
It is a resource addon, not a playable map. It includes compiled assets, not editable plugin source.

For a shared ElitePanel + MVP item, merge these assets with the existing addon and preserve the
other plugin's files. Do not replace the shared addon with MVP assets alone.
Avoid mounting conflicting versions of the same MVP resources.

Wait for successful publication and note the numeric Workshop ID.

## 2. Install the Server Plugin

Stop the server. Merge the **contents** of `server/game/csgo/` into the server's `game/csgo/`.
Do not create `game/csgo/game/csgo/`.

| Files | Final server location |
| --- | --- |
| Plugin DLL, deps.json and plugin dependencies | `game/csgo/addons/counterstrikesharp/plugins/PAD7RAR-MVP/` |
| ClientprefsApi.dll | `game/csgo/addons/counterstrikesharp/shared/ClientprefsApi/` |
| Panorama assets | `game/csgo/panorama/` |
| Compiled sounds | `game/csgo/sounds/` |
| Sound-event bank | `game/csgo/soundevents/` |

For Pterodactyl, paths usually begin with `/home/container/`.

**New installations only:** copy `examples/config.toml` into
`game/csgo/addons/counterstrikesharp/configs/plugins/PAD7RAR-MVP/config.toml`.
The example includes two public songs and one requiring `@pad7rar/premium`.
Adjust access for your server. If both exist, `config.json` takes precedence over `config.toml`.
Use `css_mvpconfig_status` in the console to inspect the active configuration path.

**Updates:** preserve your configs, banner.json, nyrium.json, customized volume-events.json,
custom catalogs and player data. Copy required dependencies and deps.json first, then the DLL.
Do not load an old MVP-Anthem installation alongside PAD7RAR-MVP.

## 3. Configure Downloads and Test

Edit `game/csgo/cfg/multiaddonmanager/multiaddonmanager.cfg`.
Set `mm_extra_addons` to include the published ID, preserving other required IDs.
An update to the same item does not require changing its ID.

Start the server and verify plugin loading and addon download/mounting.
Reconnect a client, allow Workshop downloads, and test `!mvp`, audio preview, GIF selection,
`!mvpbanner`, and playback at an actual round end.
Do not use manually installed client assets to mask Workshop delivery problems.

[MultiAddonManager documentation](https://github.com/Source2ZE/MultiAddonManager)

## 4. Add Your Own Music and GIFs

Open `tools/Nyrium-Content-Tools/Nyrium-Content-Tools.exe`.
Select the CS2 root directory, add MP3/WAV/GIF files, configure access and click Build.

| Output | Action |
| --- | --- |
| `1-SERVER/game/csgo/` | Merge into server `game/csgo/` while stopped; plugin installation is required separately. |
| `2-WORKSHOP/` | Publish/update the compiled addon using Workshop Tools. |
| `3-PROJECT/nyrium-project.json` | Keep on your PC with the original media for future builds. |
| `4-SUPPORT/` | Diagnostic logs only. |

The generated `START-HERE.txt` identifies the exact addon and local directory.
The custom catalog belongs in `plugins/PAD7RAR-MVP/content/nyrium-custom.json`.
`nyrium.json` stays next to the DLL; it is a separate panel setting.

Load the saved project for later edits and retain every entry you want to keep.
Rebuilding replaces the generated custom catalog, not just individual new entries.
A new local build addon does not mean you must create a new Workshop item.
Keep ElitePanel resources if sharing the same item.

Publish the new Workshop assets, stop the server, install matching generated server files,
then restart. Do not hot-reload sound-bank changes.

## What Requires Workshop Publication?

| Change | Server | Workshop |
| --- | --- | --- |
| DLL-only fix | Upload DLL/deps as needed and restart | No |
| Catalog names/access only, unchanged resource references | Update catalog and restart | No |
| New/modified songs, GIFs, images, UI or sound bank | Install matching assets/catalog and restart | Yes |

Nyrium 1.0.2 changes audio-bank generation.
Existing custom music must be rebuilt and republished to receive that fix.
The new DLL does not modify an old custom sound bank.

## Troubleshooting

- **Plugin command missing:** check plugin loading and server-console errors.
- **Missing catalog entry:** check the generated catalog and permissions.
- **Visible song but no audio:** check volume, sound bank and downloaded Workshop version.
- **Old or missing UI/GIF:** compare the published addon, configured ID and client download.
- **Download appears stuck:** fully restart CS2, check Steam downloads and capture console errors if it persists.
- **Crash:** retain the exact log and version; do not delete data or randomly replace all dependencies.

Do not share passwords, Steam server tokens or database credentials in diagnostic logs.
Premium restricts selection through the plugin, not access to downloaded Workshop files.

## Verification and Scope

The owner confirmed server startup after the 0.3.6 fix. Compilation and automated checks passed.
Workshop publication and clean-client downloading are separate checks, not implied by a Git push.

This repository contains compiled distribution files, not private C# source or player data.
