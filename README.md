# Anime Gamez

Mobile-first Party- und Turnierspiel für Anime-Charaktere. Die aktuelle Arbeitsversion ist `anime-gamez-v6.5.0.html` und läuft als eigenständige HTML-Datei. Lokale Medien liegen vollständig unter `assets/`.

## Aktueller Stand V6.5.0

THIS WEBSITE IS MADE WITH AI. THE ANIMES AND CHARACTERS ARE FROM A DATABASE AND NOT MINE
- Einrichtungsablauf: Anime-Pool → Spielmodus → modusspezifische Optionen
- Zufallsmix lädt nur den Anime-Pool und startet kein Spiel
- Anime-Pool kann vollständig ein- und ausgeklappt werden
- manuelle Offline-Bibliothek mit Export und Import
- reparierte Favoritenspeicherung mit vollständigen Charakterdaten
- Tournament wahlweise aus Anime-Pool oder Favoriten
- neuer Modus Anime vs Anime mit bis zu 20 Figuren je Team
- vorsichtige Dublettenentfernung für wiederkehrende Figuren mehrerer Staffeln
- neue mobile Kampfansicht und neu geordnete Statistikseite
- Sprachwahl Deutsch/Englisch in der oberen Leiste
- lokaler No-Image-Fallback
- lokales, generiertes Hauptmenü-Banner und Hintergrundmotiv

## Start

Öffne `anime-gamez-v6.5.0.html` in einem modernen Browser. Für zuverlässigere lokale Tests kann der Ordner mit einem beliebigen statischen Webserver geöffnet werden; die App benötigt keinen Build-Schritt.

## Ordner

```text
Anime-Gamez/
├─ anime-gamez-v6.5.0.html
├─ AGENTS.md
├─ README.md
├─ assets/
│  ├─ anime-gamez-logo.png
│  ├─ app-background-v1.png
│  ├─ home-banner-v1.png
│  └─ no-image-placeholder.svg
└─ docs/
   ├─ ANIME-GAMEZ-CODEX-LOCAL-GUIDE.md
   ├─ GENERATED-MEDIA.md
   └─ TEST-REPORT-V6.5.0.md
```

## Wichtiger Offline-Hinweis

„Auswahl offline speichern“ speichert Anime- und Charakterinformationen dauerhaft im Browser. Bild-URLs werden zum Browser-Cache vorgeladen, können aber je nach Browser und Quelle offline fehlen; dann erscheint der lokale No-Image-Fallback. Später bereitgestellte Medien können in `assets/` ergänzt werden.
