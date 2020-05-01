# Betriebssysteme

## Grundlagen

### Prinzipieller Aufbau eines Rechnensystems

- Anwendersoftware
- Compiler, Datenbanken, Dienstprogramme
- Betriebssystem
- Maschinensprache
- Mikroarchitektur/Gerätetreiber/Hardware-Software Interface (HSI)
- Physische Geräte

### Systemsoftware

- Betriebssystem und seine Hilfsprogramme
- Unterteilung in:
	- Systemsprogramme/Betriebssystem (Steuerprogramme, Übersetzer, Dienstprogramme, ...)
	- Anwendersoftware (eigene Programme, Bibliotheken, Softwarepakete, ...)

### Betriebssystem als erweiterte Maschine

- Betriebssystem macht die Nutzung eines Computers möglich
- Betriebssystem = Software $\neq$ Betriebssystem
- OS dient als erweiterte Maschine (Abstraktion der Hardware) und Ressourcenmanager
	- Abstraktion der konkreten Instruktionssatzarchitektur, Eigenschaften Zentraler Hardware, Ein-/Ausgabeschnittstellen und Peripheriegeräte
- Anwendersicht:
	- Reale Maschine = Zentraleinheit + Hardware
	- Abstrakte Maschine = Reale Maschine + OS
	- Benutzermaschine = Abstrakte Maschine + Anwendungen

**Das Betriebssystem ist eine virtuelle Maschine, die von der Hardware abstrahiert**

### Betriebssystem als Ressourcenmanager

- aktive Ressourcen (Prozessor [Tastatur, Monitor, Netwerk]) verarbeiten passive Ressourcen (Hauptspeicher [Platte, Bänder, CD])
- Alle Ressourcen eines Computersystems (CPU, RAM, Festspeicher) = Betriebsmittel
- Betriebsmitteln = abstrakte Ressource -> verfügt über ID, Adressbereich, Wertebereich und Funktion
- Klassen von Betriebsmitteln:
	- Entziehbarkeit: entziehbar (z.B. Prozessor) oder nicht (z.B. Dateideskriptor)
	- Zuteilbarkeit: gleichzeitig (z.B. Speicher) oder exklusiv (z.B. Prozessor)
	- Wiederverwendbarkeit: einmalig nutzbar (z.B. Interrupt) oder mehrfach (z.B. CPU, Speicher)
	- Hardware/Software: physikalisches/logisches Betriebsmittel

### Das Betriebssystem in der Definition

**DIN 44300:** __Die Programme__ eines digitalen Rechnersystems __, die zusammen__ mit den Eigenschaften dieser Rechenanlage die Basis der möglichen Betriebsarten des digitalen Rechnersystems bilden und die insbesondere __die Abwicklung von Programmen steuern und überwachen__

### Betriebssystem als Schalen-/Schichtenmodell

**Schichtenmodell**
- Benutzer -> Programm -> Betriebssystem -> Hardware
- Jeder der Schichten wird durch eine Menge an Operationen definiert, die sie bereitstellt (Schnittstelle)

**Schalenmodell**
- HW-spezifische Funktionen auf der untersten Ebene -> aufbauende, elementare Betriebssystemfunktionen -> Schichten für Kommunikation/Dateisysteme/...

| Vorteile | Nachteile |
|----------|-----------|
| - Reduzierte Komplexität (nur Betrachtung der Schnittstellen) | - erhöhte Komplexität der vertikalen Kommunikation (nur durch einzelne Schichten möglich)|
| - Austausch einzelner Schichten durch definierte Schnittstellen möglich (Gesamtsystem bleibt erhalten)| - Effizienz-, Reibungsverluste und lange Pfade |

### Aufgaben eines Betriebssystems

- Verstecken technischer Details/Automatisierung von Vorgängen
	- Abstraktion der HW
	- Definition von Konzepten (Prozess, Datei, Speicher, ...)
	- Vereinfachung der Nutzung (HW), Vermeidung von Fehlern
- Steuern von Abläufen/ Kontrollieren von Ressourcennutzung
	- Blockaden von Prozessen verhindern, CPU-Leistung zuweisen
	- effiziente, zuverlässige, sichere Verwaltung
- Dienste für Anwender/Anwendungsprogramme
	- Prozessverwaltung, E/A-Operationen, Interprozesskommunikation
	- Über APIs realisiert
	- Privilegiensystem zum Schutz der Anwendungen untereinander (inkl. OS)

### Arten von Betriebssystemen

**Mainframe-Betriebssysteme**

- Hohe I/O-Bandbreite, Einsatz als Webserver o. Server für B2B-Anwendungen
- Typische Prozessverwaltungsarten: Batchverfahren (sukzessive Abarbeitung), Transaktionsverfahren (Buchungen), Zeitaufeilungsverfahren (Anfragen an DB)


**Sever-Betriebssysteme**

- viele Nutzer über Netzwerk, Verteilung der Ressourcen an Nutzer (z.B. ISPs, Google)
- Typische Vertretter: UNIX, Linux, (Windows Server)

**Multiprozessor-Betriebssysteme**

- Zusammenschalten mehrerer Prozessoren (höhere Kapazität)
- enge Kopplung (gemeinsamer Speicher), lose Kopplung (Kommunikation über Nahrichten) oder Verteilte Systeme (Netzwerk)

**Betriebssysteme für den PC**

- vernünftige Schnittstelle für Benutzer (Office, Internet, ...)

**Echtzeitbetriebssysteme**

- Zeit als wichtigster Parameter für Ressourcenvergabe
- z.B. Überwachung maschineller Fertigung, Audio/Multimedia-Systeme

**Betriebssysteme für eingebettete Systeme**

- kontrollieren andere Geräte
- kleine Größe, Speicher, Verbrauch

**Betriebssysteme für Chipkarten**

- Smart Cards besitzen eigenen Prozessor (nur einzelne Funktionen)
- Applikationen stark unterschiedlich (bei mehreren Ressourcenverwaltung und Schutzmechanismen sehr wichtig)

### Bits und Bytes

- **Bit:** kleinstmögliche Speichereinheit
- **Byte:** 8 Bits
- **Si-Präfixe:** 10er- Potenz als Basis (kb, MB, GB, TB, PB, ... -> $=10^x$ Byte)
- **IEC-Präfixe:** 2er- Potenz als Basis (KiB, MiB, GiB, TiB, PiB, ... -> $=2^x$ Byte)

## Grundlegende Strukturen

### Aufgaben

**Bedienschnittstelle (UI)**

- Betriebssysteme und alle Programme müssen mit Nutzer kommunizieren und nach dessen Wünschen verfahren (CLI/UI)

**Programmierschnittstelle (API)**

- Bereitstellung einfacher Schnittstellen zur HW (Prinzip der virtuellen (abstrakten) Maschine)
- Schutz der HW vor direktem Zugriff (Stabilität)

**Verwalten von Ressourcen**

- quasiparallele Ausführung mehrere Prozesse; Zugang mehrere Benutzer
- sichere Trennung von einzelnen Nutzern oder Prozessen (Adressraum, Rechenzeit, Speicherzugriff, Zuteilung E/A-Geräte)
- keine allgemeine perfekte Strategie
	- Zerlegung der Zugriffe in kurze Zeitscheiben
	- Effiziente Verwaltung von Datenpuffern (langsame Zugriffe)
	- korrekte Zuteilung (z.B. E/A-Geräte)
	- Spooling (für Geräte mit langsamer Verarbeitung)

**Dienste von Betriebssystemen**

- Bereitstellung von Diensten
	- Prozessmanagement
	- Speichermanagement
	- Dateiverwaltung
	- Steuerung und Abstraktion der HW, Geräteverwaltung, E/A-Steuerung
	- Bereitstellung der Benutzeroberfläche
- Kommunikation mit Diensten über APIs

**Privilegiensystem**

- Verhinderung von negativen Auswirkungen auf das OS bei Programmfehlfunktionen (insbesondere bei Multitask/-user Anwendungen/Systemen)
- Ermöglichen unterschiedlicher Betriebsarten
	- **Kern-Modus**: alle Rechte für Betriebssystem-Code
	- **Benutzer-Modus**: eingeschränkte Rechte für Anwendungs-Code

|                                 | Benutzer-Modus      | Kern-Modus      |
|---------------------------------|---------------------|-----------------|
| Ausführbare Maschinenbefehle    | begrenzte Auswahl   | alle            |
| HW-Zugriff                      | Nein (nur durch OS) | Ja, Vollzugriff |
| Zugriff auf System-Code/Dateien | keiner/read-only    | exklusiv        |

- Schnittstelle zwischen Usermode und Kernel = Traps (Einstiegspunkte; vgl. Software-Interrupt)

### Klassifizierung von Betriebssystemen

**Nach Betriebsart**
- Netzwerk-Betriebssysteme
	- Einbindung von Computern in Netze, Teilen von Ressourcen
	- Client-Server-Betrieb oder Peer2Peer-Netze
- Realzeit-Betriebssysteme
	- Verarbeitungszeit als wichtigster Faktor
- Universelle Betriebssysteme
	- erfüllen mehrere der zuvor genannten Kriterien

**Nach Anzahl der gleichzeitig laufenden Programme**

- Einzelprogrammbetrieb (singletasking)
	- Zu jedem Zeitpunkt nur ein Programm ausgeführt, Ausführung mehrerer nacheinander
- Mehrprogrammbetrieb (multitasking)
	- gleichzeitige Ausführung mehrere Programme (mehrere CPUs) oder zeitlich verschachtelt (quasi-parallel)

**Nach Anzahl der gleichzeitigen Nutzer**

- Einzelbenutzerbetrieb (singleuser mode)
- Mehrbenutzerbetrieb (multiuser mode): Ressourcen werden aufgeteilt

**Nach Anzahl der Verwalteten Prozessoren bzw. Rechner**

- Ein-Prozessor-Betriebssystem
	- Von-Neumann-Architektur besitzt meist nur einen Universalprozessor
- Mehr-Prozessor-Betriebssystem
	- jedem Prozessor wird eine Aufgabe zugeteilt (Aufgabenverarbeitung abhängig von Prozessorzahl -> Koordinationsprobleme) oder
	- Aufgaben werden auf alle Prozessoren verteilt (aber sind nicht an die Beendigung einer Aufgabe gebunden -> quasiparallele Verarbeitung mehrerer Aufgaben durch einen Prozessor)
- Die Verteilung des OS auf mehrere Prozessoren ist möglich (verteilte Betriebssysteme)

### Programmausführung und Hardware

#### Grundmodell eines Rechners

- Ausführung von Programmen = Aufgabe von Prozessorhardware + OS
- Basis meister Rechner: Von-Neumann-Architektur

**Steuerwerk**

Laden der Steuerbefehle aus dem Speicher -> Interpretation -> Steuerung der Instruktionsausführung (Steueralgorithmen wie z.B. Rechenoperationen, logische Operationen, ...)

**Rechenwerk**

Laden der Operanden aus dem Speicher -> Verarbeitung (logische/arithmetische Operationen) -> Ablage des Ergebnis im Speicher

**Speicher**

Enthält Maschinenbefehle und Daten in gemeinsamen Adressraum

**Ein-/Ausgabe**

Verbindung von Peripheriegeräten (Tastatur, Monitor, ...) mit Rechenwerk (Schnittstelle zur Umwelt)

#### Von-Neumann-Rechner

- Rechenwerk und Steuerwerk häufig als CPU zusammengefasst
- Verbindung einzelner Komponenten über BUS-System
- Prozessor-Speicher-Anbindung = "Von-Neumann-Flaschenhals" (Daten und Befehle über gemeinsamen BUS)

#### Befehlsausführung

Pipeline:

- Befehl holen (FETCH)
- Befehl dekodieren (DECODE)
- Befehl ausführen (EXECUTE)
- Speicher-/Registerwerte einlesen und zurückschreiben

Durchsatzerhöhung durch "Prefetching" (während Anweisung n ausgeführt wird, wird n+1 dekodiert und n+2 geholt) -> Latenzzeit (5 Takte), Durchsatz (ein Befehl/Takt)