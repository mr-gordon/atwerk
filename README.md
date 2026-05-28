# awork Meldungen (atwerk) — Chrome Extension

Eine hochentwickelte, datenschutzfreundliche Manifest V3 Chrome Extension, die ein dediziertes Offline-Dashboard für awork-Benachrichtigungen und Konversationen bereitstellt. 

Die Extension überwacht das awork-DOM im Hintergrund, fängt neue Benachrichtigungen in Echtzeit ab und speichert sie lokal im Browser. Dadurch gehen Benachrichtigungen nie wieder verloren, selbst wenn das native awork-Dropdown geschlossen wird oder Meldungen dort automatisch verschwinden.

---

## Features

* **Intelligente Filter & Inbox**: Schneller Zugriff auf *Eingang* (Meldungen ohne Ordner), *Ungelesen*, *Gelesen*, *Angepinnt* und den *Papierkorb*.
* **Nahtlose Echtzeit-Suche (Neu!)**: Eine direkt in die Top-Bar integrierte Volltextsuche. Durchsucht in Echtzeit alle Absender, Betreffe und Vorschau-Texte der gesamten Datenbank (inklusive archivierter Ordner und gelöschter Meldungen im Papierkorb).
* **Dynamische Ordnerstruktur**: Eigene Ordner anlegen, umbenennen oder löschen. Meldungen können einfach per Drag & Drop in Ordner sortiert werden.
* **Benutzer-Kategorisierung**: Automatische Auflistung aller aktiven Absender in der Sidebar. Ein Klick filtert alle Meldungen des jeweiligen Teammitglieds.
* **Maus-Kontextmenüs (Rechtsklick)**:
  * **Meldungen**: Schnell als gelesen/ungelesen markieren, anpinnen/entpinnen, in den Papierkorb legen oder eine manuelle awork-URL hinzufügen.
  * **Ordner**: Direkt umbenennen oder löschen (Meldungen werden dabei sicher verwahrt).
  * **Papierkorb**: Schnell leerbar über das eigene Kontextmenü.
  * **Einstellungen**: Tab-Modus öffnen, Export & Import.
* **Sortierungs-Umkehr**: Mit einem Klick in der Top-Bar die chronologische Reihenfolge umdrehen (neueste vs. älteste zuerst).
* **Backup & Datensicherheit**: Exportiere deine gesamte lokale Meldungs-Datenbank und Ordnerstruktur als `.json`-Datei und importiere sie auf anderen Geräten.
* **Multi-Select & Bulk-Aktionen**: Wähle mehrere Meldungen mit gehaltener `Shift`- oder `Ctrl`/`Cmd`-Taste aus, um sie gesammelt als gelesen zu markieren, zu pinnen oder zu löschen.
* **Responsives Popup & Tab-Modus**: Das Popup passt seine Größe automatisch an den Inhalt an, lässt sich aber auch manuell skalieren. Über das Einstellungsmenü kann das Dashboard als vollwertiger Browser-Tab geöffnet werden.

---

## Installation (Entwicklermodus)

Da die Extension als maßgeschneidertes Tool entwickelt wurde, kann sie ganz einfach im Entwicklermodus von Google Chrome (oder anderen Chromium-Browsern wie Brave, Edge oder Opera) installiert werden:

1. Lade dieses Repository als ZIP-Datei herunter und entpacke es (oder clone es direkt via Git).
2. Öffne Google Chrome und navigiere zu `chrome://extensions/`.
3. Aktiviere den **Entwicklermodus** (Schalter oben rechts).
4. Klicke auf **Entpackte Erweiterung laden** (oben links).
5. Wähle den entpackten Ordner aus, der die `manifest.json` enthält.
6. Fertig! Pinne die Extension in deiner Menüleiste für schnellen Zugriff.

---

## Funktionsweise & Technik

* **Manifest V3**: Entwickelt nach den neuesten Richtlinien und Sicherheitsstandards für moderne Chrome-Erweiterungen.
* **DOM Monitoring (MutationObserver)**: Ein ressourcenschonendes Content-Script läuft im Hintergrund auf `*.awork.com` und `*.awork.io`. Es überwacht das DOM und extrahiert neue Meldungen, sobald diese im nativen awork-Benachrichtigungsmenü geladen werden.
* **Nativer Deep-Link Clickback**: Beim Klick auf eine Meldung im Popup öffnet sich entweder direkt das verknüpfte Element in awork oder die Extension steuert das geöffnete awork-Tab via Message Passing an, öffnet dort selbstständig die Benachrichtigungs-Glocke und löst einen nativen Klick auf die Konversation aus, um sie aufzurufen.
* **Lokaler Datenspeicher**: Sämtliche Daten (Meldungen, Ordner, Fenstergrößen) werden ausschließlich lokal in der sicheren Chrome Storage API (`chrome.storage.local`) deines Browsers aufbewahrt. Es werden keinerlei Daten an externe Server übertragen oder getrackt.
