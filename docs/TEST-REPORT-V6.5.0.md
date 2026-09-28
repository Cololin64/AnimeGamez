# Testbericht V6.5.0

Datum: 2. August 2026

## Automatisch bestanden

- HTML beginnt mit `<!doctype html>` und endet vollständig mit `</html>`.
- Genau ein `<script>`-Block vorhanden.
- Gesamter JavaScript-Block ohne Syntaxfehler kompiliert.
- Nur eine aktive Definition von `startGame` und `renderAppNav` vorhanden.
- Hauptmenü rendert Banner, sieben Modi und Sprachwahl.
- Sprachwechsel Deutsch → Englisch aktualisiert Dokument und Einrichtungsseite.
- Zufallsmix enthält keinen direkten Aufruf von `startGame`.
- Favoriten aus alter ID-Liste werden aus Statistikdaten vollständig migriert.
- Favoritenseite zeigt die migrierten Figuren und den Turnierknopf.
- Favoriten-Turnier mit zwei Figuren startet bis zum Spielbildschirm.
- Manuell gespeicherter Offline-Pool wird im Offline-Modus ohne Netzwerk gelesen.
- Anime vs Anime startet mit zwei Teams vollständig aus Offline-Daten.
- Anime-vs-Anime-Turnier mit drei Teams endet mit Champion-Seite.
- Dublettenregel: gleicher Name in zwei Staffeln derselben Familie wird entfernt.
- Dublettenregel: gleicher Name in einer anderen Anime-Familie bleibt erhalten.
- Alle vier lokalen Medienpfade existieren.

## Bewusst nicht als echter Browsertest ausgegeben

Der eingebaute Browser blockierte das Öffnen der lokalen `file://`-Datei aufgrund seiner Sicherheitsrichtlinie. Die Sperre wurde nicht umgangen. Deshalb wurden DOM-/Logiktests lokal ohne Netzwerk ausgeführt; eine visuelle Kontrolle in einem normalen PC- und Mobilbrowser bleibt erforderlich.

## Manuell auf dem PC prüfen

- 360 × 800, 390 × 844, 768 × 1024 und 1280 × 800
- Bannerzuschnitt im Hochformat
- mobile Höhe der Duellkarten und Erreichbarkeit der unteren Aktionen
- echter AniList-/Jikan-Abruf inklusive 504/Timeout
- Offline-Speichern nach erfolgreichem Online-Abruf
- Export und anschließender Import eines Offline-Pakets
- World-Cup-Durchlauf mit sofort sichtbarem erstem Duell der nächsten Runde
- Bildfehler durch testweise ungültige URL und lokaler No-Image-Fallback

