# Spielerhandbuch - Wunderland MUD Client

Willkommen zum Spielerhandbuch für den Wunderland MUD Client. Dieses Dokument dient als Leitfaden für die Nutzung der App und wird kontinuierlich erweitert.

## Hauptfunktionen der App

Hier findest du eine Übersicht der zentralen Funktionen, die dir das Überleben und Erkunden im Wunderland erleichtern:

### 1. Intelligenter Automapper
Der Automapper erkennt deine Bewegungen im MUD und zeichnet automatisch eine Karte deiner Umgebung.
*   **Echtzeit-Tracking:** Deine Position wird basierend auf den Raumbeschreibungen und Ausgängen verfolgt.
*   **Labyrinth-Modus:** Ein spezieller Modus für Gebiete mit identischen Raumbeschreibungen, um auch dort den Weg nicht zu verlieren.
*   **Teleport-Erkennung:** Erkennt automatische Bewegungen oder Sprünge (z.B. durch Portale) anhand von Raum-Fingerabdrücken.
*   **Graph-Ansicht:** Eine interaktive 2D-Karte, die Räume, Verbindungen und unentdeckte Ausgänge visualisiert.

#### Bedienung des Automappers
Der Automapper ist das Herzstück der Navigation. Er bietet verschiedene Interaktionsmöglichkeiten:

*   **Verschieben & Zoomen:** Du kannst die Karte mit einem Finger verschieben und mit zwei Fingern zoomen (Pinch-to-Zoom).
*   **Zentrieren:** Ein Klick auf das Fadenkreuz-Icon zentriert die Karte sofort auf deine aktuelle Position.
*   **Ebenen-Wechsel:** Nutze die Plus- und Minus-Icons in der Toolbar, um manuell zwischen verschiedenen Stockwerken (Z-Ebenen) zu wechseln.
*   **Labyrinth-Modus umschalten:** Aktiviere den Labyrinth-Modus über das entsprechende Icon in der Toolbar, wenn du dich in Gebieten mit identischen Raumbeschreibungen befindest. In diesem Modus erzeugt jeder Schritt einen neuen, eindeutigen Raum, um die Orientierung zu wahren.
*   **Raum-Bearbeiten (Long Press):** Tippe lange auf einen Raum, um technische Details einzusehen. In diesem Menü wird unter "Notizen" die vom Parser erkannte Raumbeschreibung gespeichert.
*   **Autopilot:** Tippe kurz auf einen beliebigen bekannten Raum, um die automatische Wegfindung (Pathfinder) zu starten. Der Client führt dich dann Schritt für Schritt dorthin.

#### Legende der Karten-Symbole

| Icon / Farbe | Bedeutung |
| :--- | :--- |
| **Grüner Raum** | Deine aktuelle Position im MUD. |
| **Dunkelgrauer Raum** | Ein normaler, bereits entdeckter Raum. |
| **Magenta Raute** | Ein Raum, der im Labyrinth-Modus erstellt wurde. |
| **Schwarzer Raum (gestrichelt)** | Ein dunkler Raum (Lichtquelle erforderlich). |
| **Roter Raum** | In diesem Raum befinden sich NPCs (Gegner oder friedliche Wesen). |
| **Gelber Raum** | In diesem Raum liegen Gegenstände am Boden. |
| **Rot/Gelb geteilt** | Der Raum enthält sowohl NPCs als auch Gegenstände. |
| **Cyan Sägeblatt / Wirbel** | Ein Portal oder eine Inter-Map-Verbindung zu einem anderen Gebiet. |
| **Kleine Pfeile (oben/unten)** | Markiert Ausgänge, die die Ebene wechseln (hoch/runter). |
| **Kurze Linienstummel** | Markiert unentdeckte Ausgänge in deiner aktuellen Umgebung. |
| **Pulsierads Path** | Die aktive Route des Autopiloten. |

### 2. Floating Menu (Werkzeugleiste)
Das Floating Menu ist dein zentraler Zugriffspunkt für Schnelleinstellungen und Werkzeuge. Es kann frei auf dem Bildschirm verschoben werden (Drag & Drop) und klappt bei einem einfachen Tippen auf den blau-lila umrandeten Hauptbutton aus.

#### Funktionen im Floating Menu:

*   **💬 Chat-Umschalter:** Öffnet oder schließt das separate Chat-Fenster für Gilden- und öffentliche Rufe.
*   **🗺️ Minimap-Umschalter:** Blendet eine kompakte Mini-Karte ein oder aus, die deine unmittelbare Umgebung zeigt.
*   **📓 Notizbuch:** Öffnet das globale Notizbuch. Hier kannst du persönliche Notizen, Erinnerungen und Quest-Informationen unabhängig von einzelnen Räumen speichern.
*   **⚡ Trigger-Master:** 
    *   *Einfacher Klick:* Schaltet alle aktiven Trigger global ein oder aus (roter Rand = deaktiviert).
    *   *Langer Klick:* Öffnet ein Menü zur gezielten Aktivierung/Deaktivierung einzelner Trigger.
*   **⏳ Timer-Master:** 
    *   *Einfacher Klick:* Schaltet alle Timer global ein oder aus.
    *   *Langer Klick:* Erlaubt die Auswahl und Steuerung spezifischer Timer (z.B. für Buffs oder Abklingzeiten).
*   **🖱️ Klickbarer Text:**
    *   *Einfacher Klick:* Schaltet die Interaktion mit Wörtern im Terminal global an oder aus (roter Rand = deaktiviert).
*   **ℹ️ Silent Poller:** 
    *   *Einfacher Klick:* Aktiviert/Deaktiviert das stumme Abfragen deines Status (LP/MP).
    *   *Langer Klick:* Hier kannst du das Intervall (1s, 3s, 5s, 10s) für die Status-Updates einstellen.

### 3. Semantischer Textparser
Der Parser liest den Textstrom des Servers und bereitet ihn logisch auf.
*   **NPC- & Item-Erkennung:** Erkennt automatisch NPCs und Gegenstände im Raum und hebt diese hervor.
*   **Status-Extraktion:** Extrahiert Lebenspunkte (LP) und Magiepunkte (MP) direkt aus dem Text oder dem Info-Schild.
*   **Kampflog-Filter:** Filtert störende Kampf-Meldungen im Mapper-Kontext aus, um die Übersicht zu behalten.

### 4. Fortschrittlicher Pathfinder
Plane deine Reisen effizient durch das Wunderland. Der Pathfinder nutzt komplexe Algorithmen, um dich sicher und schnell an dein Ziel zu bringen.

#### Funktionsweise des Pathfinder
*   **A*-Optimierung:** Der Pathfinder nutzt den A*-Algorithmus mit einer Manhattan-Heuristik. Das bedeutet, er berechnet nicht nur die kürzeste Distanz, sondern berücksichtigt auch die geografische Anordnung der Räume auf der Karte.
*   **Inter-Map-Navigation:** Der Pathfinder kann Wege über verschiedene Gebietskarten hinweg berechnen, sofern diese durch Portale oder Übergänge miteinander verknüpft sind. Bei einem Kartenwechsel wird eine "Straf-Gewichtung" einberechnet, um unnötiges Karten-Hopping zu vermeiden.
*   **Sicherheits-Timeout:** Um die App flüssig zu halten, bricht die Suche automatisch nach 3 Sekunden ab, falls kein Pfad gefunden werden kann (z.B. bei extrem komplexen oder unzusammenhängenden Graphen).

#### Autopilot-Steuerung
Sobald ein Pfad gefunden wurde, übernimmt der Autopilot die Ausführung:
*   **Schritt-für-Schritt:** Der Client sendet das nächste Kommando erst, wenn die Ankunft im Zielraum vom Parser bestätigt wurde. Dies verhindert Desynchronisation bei Lags.
*   **Unterstützte Kommandos:** Neben Standard-Richtungen (n, s, o, w, etc.) werden auch spezielle Übergänge (hoch, runter) und manuelle Verknüpfungen (z.B. "betrete portal") unterstützt.
*   **Manuelle Unterbrechung:** Ein Klick auf den pulsierenden Pfad oder die Stop-Schaltfläche beendet den Autopiloten sofort.

#### Gewichtung der Wege (Intelligente Wegwahl)
Nicht jeder Weg ist gleich gut. Der Pathfinder bewertet Verbindungen nach folgenden Kriterien (niedriger ist besser):

| Verbindungstyp | Gewicht | Beschreibung |
| :--- | :--- | :--- |
| **Normal / Auto** | 1.0 | Standardwege und automatisch erkannte Richtungen. |
| **Tür** | 1.1 | Wege, die durch Türen führen. |
| **Treppe** | 1.2 | Vertikale Verbindungen über Stockwerke. |
| **Versteckt** | 1.3 | Geheimgänge oder versteckte Ausgänge. |
| **Portal** | 2.0 | Magische Übergänge oder Teleporter. |
| **Falle** | 10.0 | Gefährliche Wege (werden nach Möglichkeit umgangen). |
| **Fallback** | 20.0 | Nur theoretisch mögliche Wege basierend auf Raumaustritten (höchste Priorität für Vermeidung). |

### 5. Terminal & Integriertes Chat-System
Ein moderner Zugriff auf das klassische MUD-Erlebnis.

#### Interaktion im Terminal
Das Terminal bietet mehr als nur Textausgabe. Es unterstützt moderne Touch-Interaktionen:

*   **Klickbarer Text (Smart Actions):**
    *   Du kannst auf fast jedes Wort im Terminal tippen.
    *   Der Client führt daraufhin eine konfigurierbare Aktion aus (Standard: `untersuche <wort>`).
    *   In den Einstellungen kann das Präfix für diese Klick-Aktionen angepasst oder die Funktion ganz deaktiviert werden.
*   **Text kopieren:**
    *   Um Text aus dem Terminal zu kopieren, muss der "Klickbare Text" in der Toolbar (Icon mit dem Finger-Zeiger) kurzzeitig deaktiviert werden.
    *   Anschließend kannst du Text durch langes Drücken markieren und in die Zwischenablage kopieren.
*   **Zoom:**
    *   Du kannst den Text im Terminal mit zwei Fingern (Pinch-to-Zoom) vergrößern oder verkleinern.
*   **Leere Eingabe (Enter-Signal):**
    *   Wenn du auf den Senden-Button (Papierflieger) tippst oder "Enter" drückst, ohne Text eingegeben zu haben, sendet der Client ein leeres Signal an das MUD.
    *   Dies ist besonders nützlich, um Texte weiterzublättern (z.B. bei `--mehr--`) oder Standard-Prompts schnell zu bestätigen.

#### Das Chat-System im Wunderland
Die Kommunikation im Wunderland erfolgt über verschiedene "Ebenen" (Chat-Kanäle). Der Client trennt diese Meldungen automatisch vom restlichen Textfluss und zeigt sie im Chat-Fenster an.

*   **Syntax:** Befehle beginnen mit `-` (Minus) oder `ebene `.
*   **Wichtige Steuerbefehle:**
    *   `-ebene+`: Betrete eine Ebene (z.B. `-allgemein+`).
    *   `-ebene-`: Verlasse eine Ebene.
    *   `-ebene text`: Sende eine Nachricht an eine Ebene.
    *   `-!`: Liste alle betretenen Ebenen auf.
    *   `-?`: Liste alle Lauscher auf einer Ebene auf.
    *   `-_`: Temporäres Stummschalten/Reaktivieren von Ebenen.
*   **Emotes:** Nutze `-ebene:text` für Emotes oder `-ebene;text` für Genitiv-Emotes.
*   **Historie:** Mit `-ebene*` kannst du die letzten Nachrichten einer Ebene abrufen (z.B. `-allgemein*20`).

### 6. Tastatur-Unterstützung (Hotkeys)
Für Spieler mit einer externen Tastatur bietet der Client umfangreiche Möglichkeiten zur Steuerung über Kurzbefehle.

*   **Vordefinierte System-Hotkeys:**
    *   **F1:** Mapper an/aus umschalten.
    *   **F2:** Minimap ein/ausblenden.
    *   **F3:** Globales Notizbuch öffnen/schließen.
    *   **F4:** Karte ein/ausblenden.
    *   **F5:** Quick-Buttons (Makros) ein/ausblenden.
    *   **F6:** Status-Leiste ein/ausblenden.
    *   **F7:** Alle Timer pausieren/fortsetzen.
*   **Benutzerdefinierte Mappings:**
    In den Einstellungen können beliebige Tasten (auch in Kombination mit STRG, ALT oder SHIFT) mit MUD-Kommandos belegt werden. Zusätzlich stehen spezielle System-Aktionen zur Verfügung:
    *   **Automatisierung toggeln:** Trigger-Master, Timer-Master und Silent Poller.
    *   **UI toggeln:** Mapper, Minimap, Notizbuch, Makro-Leisten und Status-Leiste.
    *   **Interaktion:** Klickbarer Text an/aus.
    Dies ermöglicht blitzschnelle Reaktionen im Kampf oder bei der Navigation.

### 7. Bufftracker (Status-Anzeige)
Behalte deine aktiven Zauber, Tränke und Effekte immer im Blick.

*   **Visuelle Leiste:** Aktive Buffs werden in einer speziellen Leiste unterhalb des Terminals angezeigt. Jeder Buff zeigt seine verbleibende Laufzeit grafisch (Cooldown-Radial) und als Text an.
*   **Spezial-Slots (Priorität):** Der Client verfügt über zwei dedizierte Buff-Slots (Slot 1 & 2), die oberhalb der Leiste (meist neben der Status-Anzeige) platziert sind. Diese sind ideal für kritische Buffs oder De-Buffs, die du keine Sekunde aus den Augen lassen darfst.
*   **Automatische Erkennung:** Der Tracker erkennt neue Buffs basierend auf den Server-Meldungen (vorausgesetzt passende Trigger sind konfiguriert).
*   **Farbsignalisierung (Zustand):** Die Umrandung der Buff-Icons ändert ihre Farbe, um den Status des Delays zu signalisieren:
    *   **Grün:** Der Buff ist aktiv und hat noch ausreichend Laufzeit.
    *   **Gelb:** Der Buff läuft in Kürze ab (weniger als 30 Sekunden).
    *   **Rot:** Kritischer Status – der Buff läuft sofort ab (weniger als 10 Sekunden).

#### Buff-Icons suchen & konfigurieren
In den App-Einstellungen unter dem Reiter "Buffs" kannst du jeden Tracker individuell gestalten:
*   **Icon-Suche:** Über die Lupe kannst du online nach passenden Symbolen für deine Zauber suchen.
*   **Lokale Galerie:** Du kannst Icons aus installierten Icon-Packs oder deiner lokalen Galerie wählen.
*   **Platzierung:** Wähle zwischen "Slot 1", "Slot 2" oder der allgemeinen "Leiste".

### 8. Charakterverwaltung
Der Wunderland MUD Client ermöglicht es dir, mehrere Charaktere bequem zu verwalten.

*   **Charakter-Auswahl:** Beim Start der App oder über das Hauptmenü kannst du zwischen deinen gespeicherten Charakteren wählen.
*   **Separate Einstellungen:** Aliase, Trigger, Makros und Tastaturbelegungen werden **charakterspezifisch** gespeichert. So kannst du für deinen Zauberer völlig andere Hilfsmittel konfigurieren als für deinen Krieger.
*   **Schnell-Login:** Deine Zugangsdaten (Benutzername & Passwort) können sicher hinterlegt werden, um den Login-Prozess zu automatisieren.

### 9. Automatisierung & Hilfen
*   **Alias-System:** Erstelle Kurzbefehle für komplexe Kommandofolgen.
*   **Trigger-System:** Reagiere automatisch auf bestimmte Ereignisse im MUD.

### 10. Daten-Backup & Portabilität (Import/Export)
Um deine mühsam erstellten Karten und Skripte zu sichern oder auf andere Geräte zu übertragen, bietet der Client umfangreiche Import- und Exportfunktionen.

#### Karten-Export/Import
In der Kartenverwaltung (Icon links oben in der Mapper-Toolbar) findest du die globalen Schaltflächen für den Datenaustausch:
*   **Export:** Erzeugt eine ZIP-Datei, die alle Räume, Verbindungen und Metadaten deiner aktuellen Karten-Datenbank enthält.
*   **Import:** Erlaubt das Einlesen einer zuvor exportierten ZIP-Datei. Dabei werden vorhandene Karten ergänzt oder aktualisiert.

#### Einstellungen-Export/Import
In den App-Einstellungen (Zahnrad-Icon) kannst du deine gesamte Konfiguration sichern:
*   **Was wird gesichert?** Alle Aliase, Trigger, Makros, Timer, Buff-Konfigurationen (inkl. Zuweisung zu Slot 1 & 2), Tastaturbelegungen und Notizen.
*   **Sicherung:** Über die Export-Schaltfläche wird ein Backup-Paket erstellt.
*   **Wiederherstellung:** Über den Import können diese Einstellungen jederzeit wieder eingespielt werden. Nach dem Import aktualisiert der Client automatisch alle Systeme (z.B. Buff-Tracker), sodass deine Einstellungen sofort aktiv sind.

---

