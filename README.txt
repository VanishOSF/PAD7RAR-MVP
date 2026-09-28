PAD7RAR-MVP - INSTALARE SI CONTINUT PERSONALIZAT
Ghid pentru pluginul 0.3.6 si Nyrium Content Tools 1.0.2

============================================================
1. CE AJUNGE UNDE?
============================================================

SERVER: pluginul DLL, dependentele, configuratia, catalogul si
copia resurselor generate pentru server.

WORKSHOP: interfata Panorama, imagini/GIF-uri convertite, sunete
compilate si banca de evenimente audio. NU DLL, parole, configuratii,
proiecte private sau datele jucatorilor.

PC-UL TAU: Nyrium, proiectul salvat si fisierele originale MP3/WAV/GIF.
Jucatorii NU instaleaza manual aceste fisiere: descarca addonul Workshop.

IMPORTANT: copierea pe server NU publica pe Workshop.
Publicarea pe Workshop NU instaleaza DLL-ul sau catalogul pe server.

============================================================
2. INSTALAREA INITIALA A PLUGINULUI
============================================================

Cerintele serverului: Metamod, CounterStrikeSharp compatibil cu
pluginul .NET 10 / CSS API 1.0.375 si MultiAddonManager compatibil.
Nu inlocui automat componente deja functionale cu versiuni mai vechi.

Opreste serverul inainte de a inlocui fisierele pluginului.

In acest repository, pachetul server este in server/game/csgo:
copiaza CONTINUTUL acestuia peste game/csgo de pe server.
Combina folderele. Nu crea game/csgo/game/csgo.

Destinatiile finale sunt:

Plugin si dependentele lui:
/home/container/game/csgo/addons/counterstrikesharp/plugins/PAD7RAR-MVP/

Biblioteca partajata ClientprefsApi.dll:
/home/container/game/csgo/addons/counterstrikesharp/shared/ClientprefsApi/

Configuratie:
/home/container/game/csgo/addons/counterstrikesharp/configs/plugins/PAD7RAR-MVP/

La prima instalare, foloseste configuratia exemplu a pachetului.
La actualizare, NU o copia peste configuratia existenta.
Pastreaza si banner.json, nyrium.json, volume-events.json personalizat,
cataloagele custom si datele existente; nu le inlocui cu exemplele.
config.json are prioritate fata de config.toml daca exista ambele.
Comanda de consola css_mvpconfig_status arata configuratia folosita.

ClientprefsApi.dll nu este acelasi lucru cu pluginul Clientprefs.
In 0.3.6 volumul are si salvare locala; Clientprefs poate fi folosit
pentru integrarea existenta. Pastreaza dependentele livrate cu pluginul.

Nu incarca simultan o copie veche MVP-Anthem si PAD7RAR-MVP.
Nu sterge configuratiile, data/ sau datele existente Clientprefs.

============================================================
3. CUM ADAUGI MELODII SI GIF-URI
============================================================

Pe PC trebuie sa ai CS2 Workshop Tools instalat.

1. Deschide tools/Nyrium-Content-Tools/Nyrium-Content-Tools.exe (1.0.2).
2. Alege folderul principal Counter-Strike Global Offensive,
   cel care contine directoarele game si content.
3. Adauga melodiile MP3/WAV si animatiile GIF in aplicatie.
4. Alege numele, accesul public/Premium si restrictiile dorite.
5. Alege un folder de rezultat nou si apasa Genereaza.
6. Asteapta confirmarea succesului. Nu instala un rezultat incomplet.

Nu urca direct MP3/GIF in folderul DLL-ului asteptand sa functioneze.
Nyrium le converteste in resurse CS2 si genereaza catalogul necesar.

Pentru actualizari, incarca proiectul salvat si pastreaza toate
melodiile/GIF-urile pe care vrei sa le ai in continuare.
Pastreaza si fisierele originale: proiectul contine caile catre ele,
nu reprezinta o copie completa a acestora.

============================================================
4. CE FACI CU REZULTATUL NYRIUM
============================================================

1-SERVER
  Contine numai partea generata pentru server, nu instalatorul DLL.
  Pluginul PAD7RAR-MVP trebuie instalat separat, conform pasului 2.

  Sursa:       1-SERVER/game/csgo/
  Destinatie:  /home/container/game/csgo/

  Copiaza continutul pastrand structura si combinand folderele.
  Nu copia folderul 1-SERVER ca atare in plugins.

  Catalogul generat ajunge la:
  game/csgo/addons/counterstrikesharp/plugins/PAD7RAR-MVP/content/nyrium-custom.json

  Resursele generate ajung si la:
  game/csgo/panorama/
  game/csgo/sounds/nyrium/
  game/csgo/soundevents/nyrium_custom.vsndevts_c

  Copia nyrium/ din plugin NU descarca resursele pe client.
  Nu muta manual fisierele din structura generata.

2-WORKSHOP
  Contine addonul compilat pentru publicare.
  START-HERE.txt din rezultat arata numele addonului si calea exacta
  deja pregatita in instalarea locala CS2:
  <CS2>/game/csgo_addons/<numele_addonului>/

3-PROJECT
  Pastreaza nyrium-project.json pe PC pentru modificari ulterioare.
  Nu il urca pe server sau Workshop.

4-SUPPORT
  Contine logurile compilarii si informatii de diagnostic.
  Nu se instaleaza pe server sau Workshop. Verifica eventualele date
  private din loguri inainte sa le distribui.

============================================================
5. PUBLICAREA WORKSHOP
============================================================

PACHET STANDARD DIN ACEST REPOSITORY:
Copiaza workshop/game/csgo_addons/pad7rar_mvp in
<CS2>/game/csgo_addons/pad7rar_mvp pe PC.
Creeaza si <CS2>/content/csgo_addons/pad7rar_mvp daca lipseste.
Acest pachet contine resurse deja compilate, nu o harta jucabila.
Selecteaza addonul pad7rar_mvp in Workshop Tools pentru publicare.

PACHET CUSTOM GENERAT CU NYRIUM:
Deschide addonul indicat in START-HERE.txt folosind Workshop Tools.
Verifica directorul selectat pentru impachetare.

PRIMA PUBLICARE:
Publica addonul si noteaza ID-ul numeric al itemului Workshop.

ACTUALIZARE:
Foloseste Re-Upload/Update pentru ACELASI item Workshop.
Fiecare generare Nyrium creeaza un addon local de compilare nou;
acest lucru NU te obliga sa publici un item Steam nou.
Asigura-te ca publici resursele ultimei generari, nu addonul vechi.

DACA AI ELITEPANEL SI MVP IN ACELASI WORKSHOP:
Nyrium genereaza resurse MVP, nu un pachet complet ElitePanel + MVP.
Combina resursele MVP cu addonul comun inainte de Re-Upload.
Pastreaza resursele ElitePanel si cele ale altor pluginuri.
Nu inlocui intregul addon comun cu pachetul MVP si nu sterge foldere
intregi panorama/sounds/soundevents: pot contine resurse comune.

Nu publica DLL-uri, configuratii, parole sau surse private.
Foloseste numai continut pentru care ai dreptul de distribuire.

Publicarea este reusita doar dupa confirmarea Workshop Tools/Steam.
Un build local reusit nu inseamna ca actualizarea a fost publicata.

============================================================
6. ORDINEA RECOMANDATA PENTRU INSTALARE
============================================================

1. Genereaza complet continutul si verifica rezultatul.
2. Pregateste addonul final, pastrand resursele comune daca exista.
3. Publica sau actualizeaza Workshop-ul si asteapta confirmarea.
4. Opreste serverul.
5. Pentru instalare/actualizare DLL, copiaza dependentele necesare
   si fisierul .deps.json, apoi PAD7RAR-MVP.dll. Nu rescrie setarile.
6. Copiaza continutul 1-SERVER/game/csgo peste game/csgo pe server.
7. Configureaza ID-ul Workshop in mm_extra_addons din configuratia
   persistenta game/csgo/cfg/multiaddonmanager/multiaddonmanager.cfg,
   pastrand alte ID-uri
   necesare. La acelasi item deja configurat nu schimbi ID-ul.
8. Porneste serverul si verifica in consola versiunea pluginului,
   lipsa erorilor si descarcarea/montarea addonului de catre server.
9. Reconecteaza clientul si asteapta descarcarea resurselor Workshop.
10. Testeaza !mvp, preview audio, selectarea GIF-ului si !mvpbanner.
    Verifica apoi si redarea la un final real de runda.

Pentru banci audio modificate foloseste restart complet, nu hot reload.
Nu modifica bazele de date pentru a instala sunete sau GIF-uri.

============================================================
7. CE NECESITA RE-UPLOAD?
============================================================

Doar DLL/dependente plugin: server + restart; fara Re-Upload Workshop.
Doar nume/acces in catalog: server + restart; fara Re-Upload daca
resursele si referintele lor raman aceleasi.
Melodii/GIF-uri noi sau schimbate: regenerare, Workshop + server.
Interfata/imagini/banca audio schimbata: Workshop + resurse server.

Pentru corectia sunetului din Nyrium 1.0.2, bancile audio custom vechi
trebuie regenerate si republicate; un DLL nou nu modifica banca veche.

============================================================
8. VERIFICARI RAPIDE DACA NU FUNCTIONEAZA
============================================================

Nu merge !mvp:
Verifica daca pluginul s-a incarcat si ce eroare apare in consola serverului.

Melodia/GIF-ul nu apare in lista:
Verifica instalarea catalogului content/nyrium-custom.json si accesul.

Melodia apare, dar nu se aude:
Verifica volumul, banca audio, resursele si ultima versiune Workshop.
Compara preview-ul cu redarea la final de runda.

Interfata/GIF-ul lipseste sau apare vechi:
Verifica itemul publicat, ID-ul configurat, addonul montat si descarcarea
pe client. Nu masca problema prin fisiere copiate manual la jucatori.

Ramane la descarcare:
Inchide complet CS2 si redeschide-l, apoi verifica descarcarea Steam.
Daca persista, pastreaza mesajele consolei pentru diagnostic.

Nu sterge la intamplare configuratii, date sau tot continutul Workshop.
La nevoie trimite versiunea pluginului, ID-ul Workshop si eroarea exacta,
fara parole, tokenuri Steam sau alte date de acces.

Acest ghid nu executa instalarea si nu confirma publicarea sau
descarcarea vreunui pachet pe serverul/clientul tau.
