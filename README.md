# minecraft-minimap-pack
Resourcepack für Minecraft  Server 

# Minecraft Server NMinimap & Custom Resource Pack Setup

Diese Dokumentation beschreibt die Konfiguration und Einrichtung der **NMinimap** auf unserem Ubuntu Paper Minecraft-Server inklusive des automatischen Ressource-Pack-Downloads und der erweiterten Mob-Marker.

---

## 🛠️ Technische Eckdaten & Kernkomponenten
- **Server-Plattform:** Ubuntu Server (Micro-PC) mit Paper (Java 25, Version 26.2)
- **Kern-Plugins:** 
  - `NMinimap` (v1.0.9)
  - `packetevents` (v2.13.0)
  - `AnvilORM` (v1.0.2)
- **Ressourcen-Verteilung:** Automatischer Direct-Download über ein zentrales GitHub-Repository per `server.properties`.

---

## 📂 Struktur des Markers-Ordners (`plugins/NMinimap/markers/`)
Alle Custom-Icons für Spieler, Mobs und Tiere werden als `.png`-Dateien im Ordner `markers/` hinterlegt und über die `config.yml` angebunden.

### Wichtigste Marker:
- **Spieler:** `player.png` (eigener Marker), `player_small.png` (Mitspieler)
- **Standard-Mobs:** Zombie, Skeleton, Spider, Creeper, etc.
- **Tiere & Spezial-Mobs:** Axolotl, Biene, Delphin, Dorfbewohner, Dromedar, EisenGolem, EnderDrache, Enderman, Fledermaus, Fuchs, Hund/Wolf, Katze, Kuh, Lama, Lohe, Pferd, Schwein, Slime, Warden und viele mehr.

---

## ⚙️ Konfiguration & Workflow bei Änderungen

Falls neue Icons hinzugefügt oder bestehende Marker angepasst werden, gilt folgender Ablauf:

1. **Icons ablegen:** 
   Neue `.png`-Dateien in den Ordner `/home/minecraft-server/Paper-Server/plugins/NMinimap/markers/` kopieren.
2. **`config.yml` anpassen:**
   - Unter `markers.mob-markers` den Entity-Typen mit dem Dateinamen verknüpfen.
   - Unter `markers.sizes` die Anzeigegröße definieren (Standard meist `height: 4`, `width: 5`, `keep-upright: true`).
3. **Server neu starten / Pack generieren:**
   - Server starten oder in der Konsole `/mm reload` ausführen.
   - NMinimap generiert die aktualisierte Ressource-Pack-Datei lokal unter `plugins/NMinimap/built-pack.zip`.
4. **GitHub aktualisieren:**
   - Die neu generierte `built-pack.zip` in das GitHub-Repository hochladen, damit der direkte Download-Link für Clients immer auf dem neuesten Stand ist.

---

## 🌐 Server-Properties (`server.properties`)
Der automatische Download des Ressource-Packs ist wie folgt konfiguriert:
```properties
require-resource-pack=true
resource-pack=[https://raw.githubusercontent.com/DEIN-GITHUB-NAME/Resource-Pack/main/built-pack.zip](https://raw.githubusercontent.com/DEIN-GITHUB-NAME/Resource-Pack/main/built-pack.zip)
resource-pack-prompt="Wird für das Musik Plugin benötigt, kein drama ist Versprochen"

