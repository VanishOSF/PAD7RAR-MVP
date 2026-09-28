PAD7RAR-MVP 0.3.9 / NYRIUM CONTENT TOOLS 1.0.6
INSTALARE

1. PLUGINUL (o singura data)
Server: Metamod, CounterStrikeSharp compatibil (.NET 10 / API 1.0.375)
si MultiAddonManager. Nu retrograda componente functionale.
Opreste serverul. Copiaza server/game/csgo/addons/ in:
  /home/container/game/csgo/addons/
Dependentele si .deps.json se urca inainte de PAD7RAR-MVP.dll.
ClientprefsApi.dll ramane in addons/counterstrikesharp/shared/ClientprefsApi/.

Doar la prima instalare, copiaza examples/config.toml in:
  game/csgo/addons/counterstrikesharp/configs/plugins/PAD7RAR-MVP/config.toml
La update pastreaza config, banner.json, nyrium.json, volume-events.json
personalizat, content/ si data/. config.json are prioritate fata de TOML.
css_mvpconfig_status arata configuratia activa.
Nu incarca simultan MVP-Anthem si PAD7RAR-MVP.

2. GENEREAZA
Pe PC ai nevoie de CS2 Workshop Tools. Inchide CS2 si Workshop Tools.
Deschide tools/Nyrium-Content-Tools/Nyrium-Content-Tools.exe.
Alege radacina CS2 (game si content), adauga MP3/WAV/GIF, nume si acces.
Apasa Genereaza si asteapta confirmarea succesului.
Nyrium reutilizeaza <CS2>/game/csgo_addons/nyrium_global/.
Pastreaza resursele altor pluginuri; nu instaleaza automat ElitePanel.
GIF-urile umplu cadrul prin decupare centrata; marginile pot fi taiate.

3. PUBLICA SI INSTALEAZA CATALOGUL
In Workshop Tools publica/Re-Upload addonul nyrium_global la acelasi item.
Noteaza ID-ul. Nu publica DLL-uri, proiecte, parole sau datele jucatorilor.
Din rezultatul Nyrium urci doar nyrium-custom.json in:
  /home/container/game/csgo/addons/counterstrikesharp/plugins/PAD7RAR-MVP/content/
nyrium-project.json si originalele MP3/WAV/GIF raman pe PC.
Proiectul contine caile originalelor, nu copii ale lor.
.logs/ contine diagnosticul local si nu se instaleaza.

Nu copiezi separat sounds/soundevents/panorama pe server.
Resursele compilate raman necesare in Workshop.

4. WORKSHOP PE SERVER
Adauga ID-ul la mm_extra_addons in:
  game/csgo/cfg/multiaddonmanager/multiaddonmanager.cfg
Pastreaza alte ID-uri necesare. Nu folosi doar mm_client_extra_addons:
serverul trebuie sa monteze aceleasi resurse ca jucatorii.
Ordine: genereaza -> publica -> opreste serverul -> actualizeaza pluginul
daca este necesar -> urca catalogul -> porneste si verifica montarea.
Daca descarcarea se termina dupa incarcarea hartii, reincarca harta
pentru precache. Pentru banci audio schimbate prefera restart complet.
Testeaza !mvp, preview, GIF si finalul unei runde.
Nu sterge foldere audio comune; elimina doar duplicate MVP identificate
dupa verificarea montarii Workshop.

5. ACTUALIZARI
Incarca proiectul salvat si pastreaza TOATE intrarile dorite.
Catalogul nou inlocuieste catalogul custom anterior.
Melodiile demonstrative din config si GIF-urile standard raman pana
sunt dezactivate separat; catalogul custom nu le elimina automat.
Doar nume/Premium/restrictii: editeaza catalogul si reporneste serverul.
Pastreaza modificarile si in proiect pentru urmatoarea generare.
Audio/GIF/UI schimbat: regenerare + Re-Upload.
Doar DLL schimbat: update server, fara Re-Upload.

workshop/game/csgo_addons/pad7rar_mvp/ contine addonul standard optional.
Nu copia CSS-ul standard peste cel generat pentru GIF-uri custom.
Nu monta versiuni conflictuale ale acelorasi resurse.

6. CORECTII
GiveRandomMVP = true: random la fiecare MVP castigat pentru jucatorii
fara selectie manuala, respectand accesul. !mvprandom revine la random.
Volumul se salveaza dupa SteamID in data/volume-selections.json.
Nu sterge data/ la actualizare.
86 teste lifecycle trecute local pentru pluginul 0.3.9.
Bancile custom vechi necesita regenerare pentru corectia audio.
Nyrium 1.0.6 corecteaza incadrarea GIF la urmatoarea generare.
Publicarea Git nu publica Workshop si nu instaleaza serverul.
