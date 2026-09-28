# Anime Gamez – lokale Bearbeitung mit Codex

## Ziel

Anime Gamez ist eine mobile-first Einzeldatei-Webapp. PC-Tests sind wichtig, die Oberfläche wird aber zuerst für Smartphones entworfen. Die aktuelle Basis ist `anime-gamez-v6.5.0.html`.

## Mobile-first Regeln

- Zuerst bei 360–390 px Breite gestalten, danach Tablet und Desktop erweitern.
- Touch-Ziele mindestens 44 × 44 px.
- Primäre Aktionen unten oder im leicht erreichbaren Bereich platzieren.
- `100dvh` und `env(safe-area-inset-*)` für moderne Mobilgeräte berücksichtigen.
- Zwei Duellkarten müssen auch auf schmalen Geräten vergleichbar bleiben.
- Der Anime-Pool muss einklappbar bleiben; Zufallsauswahlen dürfen verborgen getestet werden.
- Horizontale Bereiche wie der World-Cup-Turnierbaum müssen scrollbar sein, ohne die ganze Seite zu verbreitern.
- Keine wichtige Information ausschließlich über Hover anzeigen.

## Projektstruktur

| Bereich | Aufgabe |
| --- | --- |
| `anime-gamez-v6.5.0.html` | komplette App: HTML, CSS und JavaScript |
| `assets/anime-gamez-logo.png` | bestehendes App-Logo |
| `assets/home-banner-v1.png` | generiertes Hauptmenü-Banner |
| `assets/app-background-v1.png` | generierter App-Hintergrund |
| `assets/no-image-placeholder.svg` | temporärer lokaler Bild-Fallback |
| `AGENTS.md` | verbindliche Kurzregeln für Codex |
| `docs/GENERATED-MEDIA.md` | Herkunft und Prompts generierter Medien |

## Sichere Änderungsbereiche

Gut abgrenzbar sind:

- V6.5-CSS direkt vor `</style>`
- Übersetzungen in `I18N`
- `renderSetupV65`, `renderModeOptionsV65`, `renderFavoritesV65` und `renderStatsV65`
- Offline-Funktionen rund um `offlinePoolKey` und `downloadSelectedOffline`
- Anime-vs-Anime-Funktionen rund um `createAnimeVsSession`
- neue Medien unter `assets/`

Mit besonderer Vorsicht ändern:

- `startGame`: verbindet Quellen, Filter, Dublettenlogik und alle Modi
- World-Cup-Logik und Live-Turnierbaum
- Import-/Exportformate und bestehende `localStorage`-Schlüssel
- Netzwerklogik für AniList und Jikan
- Favoritenmigration: alte ID-Listen müssen weiter lesbar bleiben

## Daten- und Offline-Regeln

- Online: frische Daten → normaler Cache → älterer Cache → manuelle Offline-Bibliothek.
- Offline-Modus: ausschließlich manuell gespeicherte Bibliothek verwenden.
- Das Offline-Paket enthält Anime- und Charakterinformationen. Bilder können weiterhin von externen Quellen stammen; bei Ausfall greift der lokale Platzhalter.
- Manuelles Offline-Speichern muss Fortschritt und Teilfehler anzeigen.
- Keine unbegrenzten Wiederholungen bei HTTP 429/5xx oder Timeout.

## Favoriten

- Favoriten bestehen aus ID plus vollständigem Datensatz (`favoriteCharacterData`).
- Alte Favoriten-IDs werden über Statistik oder aktuelle Spielsitzung migriert.
- Ein Favoriten-Turnier braucht mindestens zwei zum Geschlechtsfilter passende Figuren.
- Entfernen eines Favoriten löscht ID und gespeicherten Datensatz.

## Charakter-Dubletten und Staffeln

- Stabile Quell-ID bevorzugen.
- Gleiche Namen niemals global als dieselbe Figur behandeln.
- Namensvergleich nur zusätzlich innerhalb einer ähnlich normalisierten Anime-/Staffel-Familie einsetzen.
- Dadurch kann eine wiederkehrende Hauptfigur aus mehreren Staffeln nur einmal erscheinen, während gleichnamige Figuren anderer Werke erhalten bleiben.
- Die manuelle Pool-Auswahl je Anime bleibt unabhängig davon verfügbar.

## World-Cup-Turnierbaum

- Bereits feststehende Duelle der nächsten Runde sofort anzeigen.
- Sieger in Baumreihenfolge in die nächste Runde übertragen.
- Gewinner und abgeschlossene Äste golden markieren.
- Aktuelles Match mit rotem Punkt markieren.
- Baum während Gruppenphase und Tiebreak sichtbar lassen.
- Mobil horizontal scrollbar; Champion bleibt mittig.
- Speichern, Fortsetzen und Rückgängig nicht ohne Migration ändern.

## Test-Checkliste

### Struktur

- [ ] genau ein ausführbarer `<script>`-Block
- [ ] JavaScript-Syntax ohne Fehler
- [ ] `<!doctype html>`, `</body>` und `</html>` vorhanden
- [ ] alle lokalen Medienpfade existieren

### Einrichtung

- [ ] Zufallsmix lädt nur den Pool
- [ ] Pool lässt sich ein- und ausklappen
- [ ] Modusoptionen erscheinen erst nach Moduswahl
- [ ] Geschlecht und Runden/Teilnehmer stehen im jeweiligen Modusbereich
- [ ] Tournament bietet Normal und Favoriten
- [ ] Anime vs Anime bietet Teamgröße 5/10/15/20

### Daten

- [ ] manuelles Offline-Speichern zeigt Fortschritt
- [ ] Offline-Modus verwendet keine fehlenden Online-Daten
- [ ] Offline-Paket lässt sich exportieren und importieren
- [ ] 504/Timeout endet kontrolliert
- [ ] No-Image-Fallback greift bei defekter URL

### Spiel

- [ ] Smash or Pass
- [ ] Kiss Marry Kill
- [ ] Blind Ranking
- [ ] Character VS
- [ ] Tournament normal
- [ ] Tournament aus Favoriten
- [ ] Weltmeisterschaft inklusive nächster feststehender Begegnung
- [ ] Anime vs Anime mit ungerader und gerader Teamzahl

### Ansichten

- [ ] 360 × 800
- [ ] 390 × 844
- [ ] 768 × 1024
- [ ] 1280 × 800
- [ ] keine unbeabsichtigte Seitenbreite
- [ ] Duellaktionen mobil erreichbar
- [ ] Statistik gut lesbar und logisch geordnet

## Versionskonvention

Format: `anime-gamez-vMAJOR.MINOR.PATCH-kurzname.html`

- `MAJOR`: inkompatible Daten- oder Architekturänderung
- `MINOR`: neuer Modus oder größerer UI-/Funktionsblock
- `PATCH`: Fehlerbehebung ohne grundlegenden neuen Ablauf

Beispiele:

- `anime-gamez-v6.5.1-favorites-fix.html`
- `anime-gamez-v6.6.0-account-prep.html`
- `anime-gamez-v7.0.0-database-accounts.html`

## Beispiel-Prompts für Codex

```text
Arbeite in Anime-Gamez und lies zuerst AGENTS.md sowie den lokalen Guide.
Erstelle eine neue Patch-Version. Behebe den Fehler, dass Favoriten nach einem
Neustart fehlen. Bewahre alte localStorage-Daten und teste die Migration.
```

```text
Überarbeite den mobilen World-Cup-Turnierbaum bei 360 px Breite. Ändere keine
Turnierlogik. Prüfe, dass das erste bekannte Duell der nächsten Runde sofort
erscheint und der Baum horizontal scrollbar bleibt.
```

```text
Erweitere Anime vs Anime um eine Best-of-3-Variante. Die Modusoption soll erst
nach der Moduswahl erscheinen. Teams dürfen weiterhin höchstens 20 eindeutige
Charaktere enthalten. Lege eine neue Minor-Version an.
```

```text
Ersetze den temporären No-Image-Fallback durch die gelieferten Medien. Bewahre
die Fehlerbehandlung für kaputte externe Bild-URLs und optimiere die Dateien
für mobile Ladezeiten.
```

## Definition of Done

Eine Änderung ist fertig, wenn sie in einer neuen Version gespeichert, statisch geprüft, in den relevanten Ansichten getestet und mit klarer Trennung zwischen automatischen Prüfungen und manuellem Browsertest dokumentiert wurde.

