NYRIUM CONTENT TOOLS 1.0.2

1. Run Nyrium-Content-Tools.exe on Windows with CS2 Workshop Tools.
2. Select the CS2 root directory containing game and content.
3. Add MP3/WAV/GIF files, set names and access, then Build.
4. Follow START-HERE.txt in the generated output.

1-SERVER/game/csgo -> merge into the server's game/csgo while stopped.
2-WORKSHOP -> publish/update through CS2 Workshop Tools.
3-PROJECT -> keep locally with the original media files.
4-SUPPORT -> diagnostic logs only; do not install.

Install the plugin DLL separately first.
Complete English installation guide: ../../docs/PRESENTATION-EN.md

Load the saved project for later edits and retain all desired entries.
The generated catalog replaces the previous custom catalog.
A new local build addon does not require a new Steam Workshop item.
Preserve ElitePanel assets when updating a shared addon.

1.0.2 updates sound-bank generation. Rebuild and republish existing
custom music to apply the audio fix; updating the DLL alone cannot do it.
Workshop publication and hosted deployment are not automated.
