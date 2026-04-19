# MCServer1523 Homepage

Statische Homepage für einen Minecraft-Server, optimiert für GitHub Pages.

Die Seite besteht komplett aus `HTML`, `CSS` und `JavaScript` in einer einzigen Datei und nutzt:

- `Tailwind CSS` per CDN
- `Lucide Icons` per CDN
- lokale Speicherung für Theme, aktive Seite und Sidebar-Reihenfolge
- Live-Status über die `mcstatus.io` API

## Funktionen

- Sidebar im ChessHub-Stil
- Seiten für `Home`, `Map`, `Regeln` und `Modpack`
- Einstellungen als Popup
- Mobile Navigation
- Live-Anzeige für:
  - Serverstatus
  - Online-Spieler
  - MOTD
  - Server-Icon
- Fallback auf `assets/pack.png`, wenn der Server offline ist
- Modpack-Download über `assets/modpack.mrpack`
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

Da die Seite rein statisch ist, reicht es aus, das Repository auf GitHub hochzuladen und GitHub Pages für den Branch mit `index.html` zu aktivieren.

Typischer Ablauf:

1. Repository auf GitHub pushen
2. In GitHub unter `Settings -> Pages` den Branch auswählen
3. Root-Verzeichnis deployen

## Lokal testen

Die Seite kann direkt im Browser geöffnet werden. Für realistischeres Verhalten mit Fetch/Assets ist ein lokaler Webserver besser, zum Beispiel:

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

- Ein echter roher TCP-Portscan ist in einer normalen GitHub-Pages-Seite im Browser nicht möglich.
- Der Serverstatus wird deshalb über `https://api.mcstatus.io/v2/status/java/...` geladen.
- Wenn `assets/modpack.mrpack` kein echtes Modrinth-Pack ist, zeigt die Modpack-Seite einen Fallback-Hinweis.
