PAD7RAR-MVP
Version 0.3.3
By pad7rar

GitHub:  https://github.com/VanishOSF/PAD7RAR-MVP
Discord: https://discord.gg/FmGBPWTkDP

======================================================================
ROMÂNĂ
======================================================================

DESCRIERE
Sistem MVP pentru Counter-Strike 2, cu panou nativ interactiv, selecție de
melodii și GIF-uri, acces Premium/SteamID și limbă individuală.

FUNCȚII
- !mvp deschide panoul; Bibliotecă și Premium.
- Selectare separată a melodiei și animației GIF.
- Volum: 0 / 5 / 10 / 25 / 50 / 100%.
- Preview audio: oprește melodia precedentă înainte de următoarea.
- Banner MVP și animații, plus 9 limbi: EN, RO, RU, DE, HU, ES, PT, SR, MK.
- Limba și GIF-ul se salvează local după SteamID, fără DB.
- Volumul se aplică imediat; persistența sa folosește Clientprefs.
- Catalog custom pentru melodii și GIF-uri, fără recompilarea pluginului.

STRUCTURĂ
server/     DLL, dependențe de încărcare și resursele pluginului.
workshop/   Resursele compilate pentru jucători: panou, GIF, sunete.
tools/      Nyrium Content Tools pentru pregătirea MP3/WAV/GIF.
examples/   Configurație exemplu, fără SteamID-ul proprietarului.
docs/       Instalare, verificări și pregătire Git.
README.txt  Acest ghid bilingv.

CERINȚE
Server CS2 cu Metamod și CounterStrikeSharp, API minimum 375.
Această versiune a fost compilată pentru .NET 10 și CSS API 1.0.375.
MultiAddonManager pentru distribuirea resurselor prin Workshop.
ClientprefsApi.dll este inclus în shared/ClientprefsApi.
Pluginul Clientprefs se instalează separat pentru salvarea volumului.
Pentru utilitarul de conținut: Windows, PowerShell și CS2 Workshop Tools.

INSTALARE NOUĂ
1. Oprește serverul.
2. Copiază CONȚINUTUL server/game/csgo peste game/csgo pe server.
3. Copiază examples/config.toml în:
   game/csgo/addons/counterstrikesharp/configs/plugins/PAD7RAR-MVP/config.toml
4. Exemplul include ban/dedesc publice și cloxy cu @pad7rar/premium.
   Editează accesul pentru serverul tău.
5. Publică addonul din workshop/ sau actualizează addonul existent și
   adaugă ID-ul Workshop în configurația MultiAddonManager.
6. Pornește serverul și testează !mvp.

ACTUALIZARE
Păstrează configurațiile, dependențele deja funcționale și datele existente.
Nu înlocui configurația de producție cu exemplul.
config.json, dacă există, are prioritate față de config.toml.
Folderul tehnic și DLL-ul rămân PAD7RAR-MVP; numele afișat este PAD7RAR-MVP.
Nu șterge data/ sau datele Clientprefs. După copiere, repornește serverul.

RESURSE
nyrium.json este lângă DLL, nu în folderul nyrium/.
nyrium/ din plugin este copia resurselor, nu un mecanism de descărcare.
Jucătorii au nevoie de addonul Workshop; în joc calea rămâne panorama/.
SoundEventFiles folosește "soundevents/pad7rar_mvp.vsndevts", fără _c.
Publicarea Workshop și configurarea ID-ului nu sunt automate.

COMENZI
!mvp           Deschide panoul.
!mvpclose      Închide panoul.
!mvpvol        Meniul de volum.
!mvplang ro    Limba individuală (en/ro/ru/de/hu/es/pt/sr/mk).
!mvpbanner     Testează bannerul selecției curente.
!mvppanel și !mvpchat nu mai deschid panoul.

CONȚINUT NOU
Vezi tools/Nyrium-Content-Tools/CUM-ADAUGI-CONTINUT.txt.
Cumpărătorul deschide Nyrium-Content-Tools.exe, adaugă MP3/WAV/GIF, alege
accesul și apasă Generează. GIF-urile sunt redimensionate automat.
Instalează catalogul GENERAT împreună cu resursele pentru server/client.
Poate salva/încărca proiectul pentru actualizări. Sursele pluginului și ale
aplicației rămân private; motorul și șabloanele sunt incluse în executabil.
Numele conținutului introdus de proprietar nu se traduc automat.

STAREA VERIFICĂRILOR
Compilarea DLL, încărcarea locală în .NET, conversia MP3/GIF și testele de
catalog, acces, volum, persistență și traduceri au trecut.
Testul complet de descărcare Workshop pe un client curat rămâne de făcut.
Acest folder nu conține sursa C#, proiecte .csproj/.sln sau datele jucătorilor.

======================================================================
ENGLISH
======================================================================

ABOUT
A Counter-Strike 2 MVP system with an interactive native panel, independent
song/GIF selection, Premium/SteamID permissions and per-player language.

FEATURES
- !mvp opens the Library/Premium panel.
- Independent music and animated portrait selection.
- Volume: 0 / 5 / 10 / 25 / 50 / 100%.
- Starting a new audio preview stops the previous preview.
- MVP banner, animations and EN/RO/RU/DE/HU/ES/PT/SR/MK localization.
- Language and GIF preferences saved locally by SteamID, no DB required.
- Volume applies immediately; persistence uses Clientprefs.
- Custom song/GIF catalogs without rebuilding the plugin.

FOLDERS
server/     Plugin DLL, load dependencies and plugin resources.
workshop/   Compiled client assets: UI, GIF and music.
tools/      Nyrium Content Tools for preparing MP3/WAV/GIF assets.
examples/   Example configuration without the owner's SteamID.
docs/       Installation and Git preparation notes.

REQUIREMENTS
CS2 server with Metamod and CounterStrikeSharp API 375 minimum.
Built for .NET 10 and CSS API 1.0.375.
MultiAddonManager for Workshop asset delivery.
ClientprefsApi.dll is included under shared/ClientprefsApi.
Install the Clientprefs plugin separately for volume persistence.
The content builder requires Windows, PowerShell and CS2 Workshop Tools.

NEW INSTALLATION
1. Stop the server.
2. Merge the CONTENTS of server/game/csgo into the server's game/csgo.
3. Copy examples/config.toml into:
   game/csgo/addons/counterstrikesharp/configs/plugins/PAD7RAR-MVP/config.toml
4. The sample makes ban/dedesc public and cloxy require @pad7rar/premium.
   Customize access for your server.
5. Publish/update the addon from workshop/ and configure its Workshop ID
   in MultiAddonManager.
6. Start the server and test !mvp.

UPGRADING
Preserve existing configuration, working dependencies and player data.
Do not replace production settings with the example.
config.json takes precedence over config.toml when both exist.
Keep the technical folder/DLL name PAD7RAR-MVP. The display name is PAD7RAR-MVP.
Do not delete data/ or Clientprefs data. Restart after installing.

ASSETS AND COMMANDS
nyrium.json belongs next to the DLL. The plugin's nyrium/ directory does
not automatically download to clients. Clients require the Workshop addon;
the actual game resource directory remains panorama/.
SoundEventFiles uses "soundevents/pad7rar_mvp.vsndevts" without _c.
Workshop publishing and Workshop ID configuration are separate manual steps.

!mvp           Open panel.
!mvpclose      Close panel.
!mvpvol        Volume menu.
!mvplang en    Individual language (en/ro/ru/de/hu/es/pt/sr/mk).
!mvpbanner     Preview the equipped MVP banner.
The old !mvppanel and !mvpchat opening commands were removed.

CUSTOM CONTENT
Read tools/Nyrium-Content-Tools/README-English.txt.
Open Nyrium-Content-Tools.exe, add MP3/WAV/GIF, set access and click Build.
GIFs are resized automatically. Install the GENERATED catalog and server/client
resources together. Save/load projects for updates. Application and plugin
source remain private; the engine and templates are embedded in the executable.
Owner-defined content names are not translated automatically.

VALIDATION
Plugin compilation, local .NET loading, MP3/GIF compilation, and automated
catalog/access/audio/persistence/localization checks passed.
An end-to-end Workshop download test with a clean client remains outstanding.
No C# plugin source, .csproj/.sln projects or player data are included here.



UPDATE 0.3.1: vezi / see docs/UPDATE-0.3.1.txt pentru redenumirea instalării existente / for renaming an existing installation.



UPDATE 0.3.2: docs/UPDATE-0.3.2.txt - oprirea muzicii native inainte de MVP / stop native music before custom MVP.
