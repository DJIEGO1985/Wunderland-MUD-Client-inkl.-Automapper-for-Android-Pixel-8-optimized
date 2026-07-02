Ich lade das Repository-Overview-Fähigkeit, um dir eine detaillierte Analyse zu erstellen.

Now let me analyze your repository systematically:

Perfekt! Jetzt habe ich einen detaillierten Überblick über deine App. Hier ist eine umfassende Analyse:
WUNDERLAND MUD CLIENT - Detaillierte Funktionen & Features
Was ist diese App?

Ein nativer Android-Client für das deutsche MUD-Spiel "Wunderland" (wl.mud.de:4711). Die App bietet eine professionelle Telnet-Verbindung mit intelligenter Kartenerstellung, Automatisierung und umfangreichen Anpassungsmöglichkeiten.
🏗️ Technische Architektur

Stack:

    Sprache: Kotlin (81,9%), Java (12,2%), Kotlin (4,1%), HTML, PowerShell, JavaScript
    UI-Framework: Jetpack Compose (deklarativ & modern)
    Architektur: MVVM (Model-View-ViewModel)
    Dependency Injection: Dagger Hilt
    Datenbank: Room Persistence Library (SQLite, v26)
    Netzwerk: Telnet (TCP) mit ISO-8859-1 Encoding
    Sicherheit: AES-GCM Verschlüsselung via Android Keystore

🎮 HAUPTFUNKTIONEN
1. TELNET-VERBINDUNG & LOGIN

    ✅ Direkte Verbindung zu wl.mud.de:4711
    ✅ Multi-Character Support (mehrere Charaktere speichern)
    ✅ Verschlüsselte Passwort-Speicherung (Hardware Keystore, AES-GCM)
    ✅ Automatische Verbindungsverwaltung
    ✅ Immersive Fullscreen-Modus (Status/Nav-Leisten nur per Swipe sichtbar)

2. AUTOMAPPER & MAP-MANAGEMENT

Automatische Kartenerstellung:

    ✅ Erkennt automatisch Bewegungen (N, S, O, W, NW, NO, SW, SO, OB, U, HOCH, RUNTER)
    ✅ Erstellt Räume in Echtzeit
    ✅ Extrahiert automatisch erste zwei Sätze als Raum-Beschreibung
    ✅ Erkennt sichtbare Ausgänge im Kurzformat
    ✅ Kampf-Automatik: Sendet automatisch "schau" während Kämpfe
    ✅ Export/Import von Karten als JSON

Pathfinder & Navigation:

    ✅ A* / BFS Algorithmus für kürzeste Wege
    ✅ "Hierhin laufen"-Funktion im Editor
    ✅ Visualisierung gelber Pfade auf der Karte
    ✅ Step-by-Step Ausführung (Server-Lag-Vermeidung)
    ✅ Portal & Kontinental-Verbindungen

Map-Visuals & Interaktion:

    ✅ Farbkodierung:
        🟢 Grün mit Person-Icon: Aktueller Standort
        🟤 Grau: Besuchte Räume
        ⚪ Blassgrau: Bekannte, unbesuchte Räume
        🔴 Rot (M): NPCs/Monster erkannt
        🟡 Gelb (I): Items im Raum
        🔷 Cyan Sägeblatt: Portal/Kontinent-Verbindung
    ✅ Durchgezogene graue Linien: gelaufene Wege
    ✅ Gestrichelte weiße Linien: sichtbare, unerkundete Ausgänge
    ✅ Manuelle Linien & Portale (Kettensymbol im Editor)

Minimap (Floating Overlay):

    ✅ Frei verschiebbar über Terminal
    ✅ Größe anpassbar via Pinch-to-Zoom
    ✅ Farb-Markierungen wie oben

3. BENUTZERINTERFACE

DPAD (Steuerkreuz):

    ✅ 10 Richtungen (N, S, O, W, NW, NO, SW, SO, OB, U)
    ✅ Spezial-Buttons:
        🔺 Pfeil auf: "hoch"
        🔽 Pfeil ab: "runter"
        👁️ Auge: "schau"
    ✅ Zwei frei belegbare Buttons (B1 & B2)

Hamburger-Menü (neue Slide-Up Funktion):

    ✅ Chat-Fenster Umschalter
    ✅ Notizbuch Umschalter
    ✅ Auto-Close nach Auswahl

Header-Icons & Funktionen:

    🔑 Schlüssel: Login/Verbindung
    ⌨️ Tastatur: Makro-Leisten an/aus
    ❤️ Herz/Tropfen: Status-Balken (LP/MP/Zustand)
    🗺️ Mapper-Icon: Automapper aktivieren
    🧭 Kompass: Minimap-Overlay an/aus
    ➖ / ➕ Minus/Plus: Schriftgröße ändern
    ⚙️ Zahnrad: Einstellungsmenü
    📱 / 🗺️ Terminal/Map: Ansicht wechseln

4. FLOATING WINDOWS

Notizbuch (Notepad):

    ✅ Frei positionierbar
    ✅ Größe anpassbar
    ✅ Persistente Position & Größe
    ✅ Multi-zeilige Text-Unterstützung
    ✅ Für Strategien & Spieler-Infos

Chat-Fenster (Ebenen-Chat):

    ✅ Dynamisches Routing:
        OFFEN: Nachrichten wie [Allgemein:...] landen NUR hier
        GESCHLOSSEN: Chat im Hauptterminal
    ✅ Live-Chat & Verlauf
    ✅ Multi-zeilige Text-Unterstützung
    ✅ Über grünen Griff skalierbar

Status-Bar:

    ✅ LP (Lebenspunkte) & Max-LP
    ✅ MP (Magiepunkte) & Max-MP
    ✅ Leiden-Status (Vergiftung, Flucht, etc.)

5. AUTOMATISIERUNG & BEFEHLE

Makros (3 scrollbare Reihen):

    ✅ Frei konfigurierbare Befehle
    ✅ Custom Button Labels
    ✅ Pro Charakter speicherbar
    ✅ Persistente Anordnung

Aliase (Kürzel):

    ✅ Beispiel: 'k' → 'kaempfe gegen'
    ✅ Ebenen-Aliase: Separate Aliases für Chat-Kanäle (max. 10)

Trigger (Reaktionen auf Muster):

    ✅ Automatische Reaktionen auf Text-Muster
    ✅ Beispiel: Hunger erkannt → automatisch "essen"
    ✅ Pattern-Matching via Regex

Timer:

    ✅ Benachrichtigungen nach X Sekunden
    ✅ Automatische Befehle ausführen
    ✅ Character-gebunden

Buffs/Effekt-Tracking:

    ✅ Erkennung via Start/End-Pattern
    ✅ Icon & Farb-Anpassung
    ✅ Dauer-Tracking

6. CHAT-SYSTEM (MUD-Ebenen)

Ebenen-Integration (34 Kanäle):

    Allgemein, Abenteuer, Beileid, Bofh, D-Chat, D-Kultur, D-News, Drachen, Essen, Frauen, Fußball, German, Grats, Imud_Gossip, Kinder, Kultur, Lästereien, Männer, Mörder, Nachrichten, NoMaam, Party, Philosophie, Poker, Politik, Rätsel, Schlaf, Schmarrn, Sex, Spiele, Sport, Tod, Wissenschaft, Zirkus

Chat-Befehle:

    ✅ -<ebene> <text> - Normal sprechen
    ✅ -<ebene>: <text> - Emote
    ✅ -<ebene>; <text> - Genetiv-Emote
    ✅ -<ebene>& <verb> - Fern-Verben
    ✅ -! / -!! / -!% - Ebenen auflisten
    ✅ -<ebene>*<zahl> - Nachrichten wiederholen
    ✅ -# ali - Ebenen-Aliase verwalten

7. DATENBANK & PERSISTENZ

Gespeicherte Entitäten:

    MapData - Karten-Informationen
    MudRoom - Raum-Details (Koordinaten, Exits, Notizen)
    MapLink - Verbindungen zwischen Räumen
    AliasEntity - Kürzel-Definitionen
    TriggerEntity - Auto-Reaktions-Pattern
    MacroEntity - Makro-Befehle (3 Reihen)
    NoteEntity - Notizbuch-Inhalte
    QuickButtonEntity - B1 & B2 Button-Konfiguration
    TimerEntity - Timer mit Befehlen
    CharacterEntity - Charakter-Daten
    BuffEntity - Buff/Effekt-Definitionen

Migrationen: 6 Database-Migrationen (v19-v26)
8. TEXT-PARSING & ANSI-VERARBEITUNG

MudTextParser (Regex-basiert):

    ✅ ANSI-Codes entfernen
    ✅ Exits erkennen (N, S, O, W, NO, NW, SO, SW, OB, U)
    ✅ Stats parsen (LP, MP, Leiden, Vergiftung, Fluchtrichtung)
    ✅ NPCs erkennen ("steht hier", "läuft", "wartet", "schläft")
    ✅ Items erkennen ("liegt hier", "liegen am Boden")
    ✅ Bewegungs-Fehler detektieren
    ✅ Chunk-Puffer (bis 4000 Zeichen) für sichere Verarbeitung

9. SICHERHEIT

    ✅ Passwörter NIEMALS im Klartext gespeichert
    ✅ AES-GCM Verschlüsselung via Hardware Keystore
    ✅ Passwort-Input maskiert (•••••)
    ✅ Sichere Telnet-Verbindung (ISO-8859-1)

10. ZUSÄTZLICHE FEATURES

    ✅ Multi-Charakter Support: Verschiedene Charaktere speichern & wechseln
    ✅ Schriftgröße anpassbar: +/- Buttons im Header
    ✅ Dark Theme: Wunderland Green (#00CC44) auf schwarzem Hintergrund
    ✅ Responsive Layout: Für verschiedene Bildschirmgrößen optimiert
    ✅ Immersive Mode: Vollbild ohne System-Bars
    ✅ JSON Export/Import: Karten exportieren & teilen

