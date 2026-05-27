# awork Meldungen (v3.0.0)

**atwerk** ist eine schlanke, performante Google Chrome Extension, die als persistente Bridge für awork-Benachrichtigungen fungiert. Da Benachrichtigungen im nativen System flüchtig sind und nach dem Lesen oft dauerhaft verschwinden, fängt dieses Tool die Daten per DOM-Scraping ab und sichert sie lokal in einem persistenten Speicher.

---

## Key Features

* **Persistenter Notification-Stream:** Sichert wichtige Projektmeldungen lokal, bevor sie in awork ins "Nirvana" gelangen.
* **Erweiterte Sidebar-Navigation:** Dynamische Filterung nach Status (*Eingang, Ungelesen, Gelesen, Pinned*), dedizierten Ordnerstrukturen und einzelnen Benutzern.
* **Umfangreiches Context-Menu-System:** Vollständige Kontrolle per Rechtsklick (z. B. schnelles Pinnen, manuelles Einsortieren in Ordner, Wiederherstellen aus dem Papierkorb).
* **Datenhoheit (Backup & Restore):** Integrierte JSON-Export- und Importfunktion über das Einstellungsmenü für nahtlose Datensicherung.

---

## Architektur & Funktionsweise

Das Tool ist nach aktuellen Manifest V3-Standards aufgebaut und trennt die Logik strikt in drei Ebenen:

1. **Content Script (`content.js`):** Überwacht das native awork-Benachrichtigungszentrum (DOM-Scroll & MutationObserver) und extrahiert Metadaten (Absender, Titel, Nachrichtentext, Zeitstempel), sobald neue Einträge geladen werden.
2. **Background Script (`background.js`):** Nimmt die gescrapten Daten via Message-Passing entgegen und persistiert sie isoliert in der `chrome.storage.local` Datenbank.
3. **Popup-UI (`popup.html` / `popup.js`):** Rendert die zweigeteilte App-Ansicht (Sidebar links, Stream-Ansicht rechts) und steuert das dynamische Filtern sowie die Custom Context Menüs ohne spürbare Latenz.

---

## Installation (Entwicklermodus)

1. Repository klonen oder als ZIP herunterladen.
2. Google Chrome öffnen und zu `chrome://extensions/` navigieren.
3. Den **Entwicklermodus** (oben rechts) aktivieren.
4. Auf **Entpackte Erweiterung laden** klicken und den Projektordner auswählen.

---

## Lizenz
Internes Werkzeug – Nutzung und Weiterentwicklung für produktive Workflows.
