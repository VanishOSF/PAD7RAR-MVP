# PAD7RAR-MVP

**Your round. Your signature.**  
Muzica MVP, portrete animate si panou interactiv pentru Counter-Strike 2.

**Plugin 0.4.0** | **Nyrium Content Tools 1.0.7** | **By pad7rar**

[Instalare pas cu pas](README.txt) · [English guide](docs/PRESENTATION-EN.md) · [Discord](https://discord.gg/FmGBPWTkDP)

![Panoul PAD7RAR-MVP](docs/media/panel-ro.png)

## Incepe aici

Acesta este repository-ul de **distributie**, nu folderul unui server.
Contine pluginul compilat, resursele clientului si utilitarul Windows pentru continut personalizat.

| Vrei sa... | Folosesti |
| --- | --- |
| Instalezi pluginul pe server | [server/game/csgo/](server/game/csgo/) |
| Publici interfata, sunetele si imaginile | [workshop/game/csgo_addons/pad7rar_mvp/](workshop/game/csgo_addons/pad7rar_mvp/) |
| Adaugi MP3/WAV/GIF proprii | [Nyrium Content Tools](tools/Nyrium-Content-Tools/) |
| Configurezi o instalare noua | [examples/config.toml](examples/config.toml) |
| Afli toate caile si ordinea instalarii | [README.txt](README.txt) |

**Server si Workshop sunt doua destinatii diferite. DLL-ul nu se publica in Workshop.**
Copierea pe server nu distribuie singura resursele jucatorilor.

## Instalare in 5 pasi

1. Pregateste un server cu Metamod, CounterStrikeSharp compatibil cu .NET 10 / CSS API 1.0.375 si [MultiAddonManager](https://github.com/Source2ZE/MultiAddonManager).
2. Publica addonul compilat din `workshop/`, sau combina resursele cu addonul tau existent si fa Re-Upload. Pastreaza resursele altor pluginuri din acel addon.
3. Cu serverul oprit, copiaza **continutul** `server/game/csgo/` peste `game/csgo/` de pe server. La actualizare pastreaza setarile si datele.
4. **Doar la prima instalare**, copiaza `examples/config.toml` in `game/csgo/addons/counterstrikesharp/configs/plugins/PAD7RAR-MVP/config.toml`. Configureaza ID-ul publicat in `mm_extra_addons`, in configuratia MultiAddonManager.
5. Porneste serverul, verifica descarcarea/montarea addonului si testeaza `!mvp`, preview-ul, GIF-ul si `!mvpbanner`.

[Ghidul complet](README.txt) explica si publicarea pe acelasi item, continutul custom, actualizarile si depanarea.
Nyrium si Workshop Tools se folosesc pe PC-ul administratorului, nu pe serverul Linux.

## Ce copiezi, exact?

| Din repository | Destinatia pe server |
| --- | --- |
| `server/game/csgo/addons/counterstrikesharp/plugins/PAD7RAR-MVP/` | `game/csgo/addons/counterstrikesharp/plugins/PAD7RAR-MVP/` |
| `server/game/csgo/addons/counterstrikesharp/shared/ClientprefsApi/` | `game/csgo/addons/counterstrikesharp/shared/ClientprefsApi/` |

Resursele Panorama/audio sunt livrate prin Workshop, nu copiate separat pe server.

Pe Pterodactyl, prefixul uzual este `/home/container/`; alte gazduiri pot avea alta radacina.
Combina directoarele, fara sa creezi accidental `game/csgo/game/csgo`.

`nyrium.json` ramane langa DLL. Catalogul custom generat de Nyrium se instaleaza in
`plugins/PAD7RAR-MVP/content/nyrium-custom.json`.
MP3-urile si GIF-urile originale nu se copiaza manual in plugin.

## Continut personalizat

Deschide **Nyrium-Content-Tools.exe**, adauga MP3/WAV/GIF, seteaza accesul si apasa **Genereaza**.
Utilitarul produce:

| Rezultat | Destinatie |
| --- | --- |
| Addonul indicat la final | Deja pregatit in CS2 Workshop Tools; publica sau fa Re-Upload. |
| `nyrium-custom.json` | `game/csgo/addons/counterstrikesharp/plugins/PAD7RAR-MVP/content/nyrium-custom.json` |
| `nyrium-project.json` | Ramane pe PC impreuna cu originalele pentru actualizari. |
| `.logs/` | Diagnostic local, nu se instaleaza. |

Pentru continutul custom nu copiezi separat sounds/soundevents/Panorama.
ID-ul trebuie inclus in `mm_extra_addons`, nu doar `mm_client_extra_addons`,
pentru ca serverul si jucatorii sa monteze acelasi Workshop.

La reconstruire pastreaza toate intrarile dorite in proiect. Catalogul nu se adauga automat peste cel vechi.
Nyrium reutilizeaza addonul local `nyrium_global`; publica actualizarile pe acelasi item Workshop.
Nu monta simultan addonuri care contin versiuni diferite ale acelorasi resurse MVP.

## Functii

- Biblioteca publica si continut Premium, cu acces prin permisiuni sau SteamID.
- Selectie independenta a melodiei si portretului animat.
- Preview audio, volum individual si banner personalizat la MVP.
- Preferinte locale dupa SteamID si integrare optionala Clientprefs.
- Interfata in RO, EN, RU, DE, HU, ES, PT, SR si MK.

Premium controleaza accesul prin plugin, nu confidentialitatea resurselor descarcate.
Nu include procesarea platilor.

![Banner MVP](docs/media/mvp-banner-ro.png)

| Comanda | Rol |
| --- | --- |
| `!mvp` | Deschide panoul. |
| `!mvpclose` | Inchide panoul. |
| `!mvpvol` | Meniu de volum. |
| `!mvplang ro` | Selecteaza limba. |
| `!mvpbanner` | Testeaza bannerul selectiei curente. |
| `css_mvpconfig_status` | Diagnostic pentru calea configuratiei, din consola. |

## Actualizarea 0.4.0

- Titlul panelului afiseaza numele jucatorului, separat pentru fiecare utilizator.
- Corectata validarea CustomHud: eliminat atributul `html` incompatibil din titlu.
- Ramane o singura varianta de aplauze; selectiile vechi monochrome/sepia folosesc originalul. GIF-urile custom sunt pastrate.
- Random MVP foloseste doar melodii free cand nu exista o selectie manuala valida, inclusiv cand preferintele din baza de date intarzie. Alegerea temporara nu suprascrie preferintele salvate.
- Meniul si Random MVP au fost confirmate functional in joc de administrator; 103 verificari automate locale au trecut.
- Necesita actualizarea DLL + `.deps.json` si Re-Upload al resurselor Workshop din acest repository. Pastrati configuratiile, cataloagele si datele jucatorilor.
- Nyrium Content Tools ramane 1.0.7; acest update nu schimba utilitarul.

## Actualizarea 0.3.9

- Elimina crearea anticipata a bannerului la incarcarea hartii; pornirea serverului a fost confirmata de utilizator dupa corectie.
- Pastreaza corectia pentru configuratii fara sectiunea veche `MVPSettings`.
- Salveaza local volumul dupa SteamID, inclusiv intre harti.
- Foloseste aceeasi selectie MVP pentru banner si redarea melodiei.
- Random la fiecare MVP pentru jucatorii fara selectie manuala, cu `GiveRandomMVP = true`.
- Include Nyrium 1.0.6: addon comun reutilizabil si GIF cu decupare centrata, fara benzi de incadrare.
- 86 de teste lifecycle trecute local.

**Pentru melodii custom vechi, corectia audio necesita regenerare cu Nyrium si Re-Upload Workshop.**
Actualizarea DLL-ului nu recompila banca de sunete a clientului.
Doar actualizarea DLL nu necesita Re-Upload.

Verificari locale: compilare si teste automate. Publicarea Workshop si descarcarea pe un client curat
raman operatii separate de publicarea acestui repository.

## Actualizare fara pierderea datelor

Opreste serverul. Instaleaza dependentele necesare si `.deps.json`, apoi DLL-ul si resursele necesare.
Pastreaza configurarile existente (`config.toml/config.json`, `banner.json`, `nyrium.json`),
cataloagele custom, `volume-events.json` personalizat si datele jucatorilor.
Nu copia exemplul peste configuratia de productie. Reporneste dupa instalare.

Acest pachet nu include sursa C# privata, credentiale sau date de jucatori.

[Prezentare video RO](docs/media/PAD7RAR-MVP-RO-music.mp4) · [Video EN](docs/media/PAD7RAR-MVP-EN-music.mp4)

Imaginile si videoclipurile sunt materiale de prezentare, nu dovezi de testare live.
