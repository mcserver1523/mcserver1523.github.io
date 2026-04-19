# MCServer1523 Homepage

Statische Homepage fuer einen Minecraft-Server, optimiert fuer GitHub Pages.

Die Seite besteht komplett aus `HTML`, `CSS` und `JavaScript` in einer einzigen Datei und nutzt:

- `Tailwind CSS` per CDN
- `Lucide Icons` per CDN
- lokale Speicherung fuer Theme, aktive Seite und Sidebar-Reihenfolge
- Live-Status ueber die `mcstatus.io` API

## Funktionen

- Sidebar im ChessHub-Stil
- Seiten fuer `Home`, `Map`, `Regeln` und `Modpack`
- Einstellungen als Popup
- Mobile Navigation
- Live-Anzeige fuer:
  - Serverstatus
  - Online-Spieler
  - MOTD
  - Server-Icon
- Fallback auf `assets/pack.png`, wenn der Server offline ist
- Modpack-Download ueber `assets/modpack.mrpack`
- Mod-Liste aus einem Modrinth-`.mrpack`, falls vorhanden

## Projektstruktur

```text
.
├── index.html
├── README.md
└── assets
    ├── modpack.mrpack
    └── pack.png
```

## Deployment mit GitHub Pages

Da die Seite rein statisch ist, reicht es aus, das Repository auf GitHub hochzuladen und GitHub Pages fuer den Branch mit `index.html` zu aktivieren.

Typischer Ablauf:

1. Repository auf GitHub pushen
2. In GitHub unter `Settings -> Pages` den Branch auswaehlen
3. Root-Verzeichnis deployen

## Lokal testen

Die Seite kann direkt im Browser geoeffnet werden. Fuer realistischeres Verhalten mit Fetch/Assets ist ein lokaler Webserver besser, zum Beispiel:

```bash
python3 -m http.server 8000
```

Dann:

```text
http://localhost:8000
```

## Wichtige Anpassungen

Die wichtigsten Konstanten stehen in `index.html`:

- Server-IP: `SERVER_IP`
- Server-Port: `SERVER_PORT`
- Pack-Icon: `PACK_ICON`
- Modpack-Datei: `MODPACK_URL`

Aktuell verwendet die Seite:

- Server: `mcserver1523.duckdns.org`
- Port: `25565`

## Hinweise

- Ein echter roher TCP-Portscan ist in einer normalen GitHub-Pages-Seite im Browser nicht moeglich.
- Der Serverstatus wird deshalb ueber `https://api.mcstatus.io/v2/status/java/...` geladen.
- Wenn `assets/modpack.mrpack` kein echtes Modrinth-Pack ist, zeigt die Modpack-Seite einen Fallback-Hinweis.
