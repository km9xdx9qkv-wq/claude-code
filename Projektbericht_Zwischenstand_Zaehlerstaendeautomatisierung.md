# Projektbericht

## Zwischenstand zur Zählerständeautomatisierung

**Projekt:** Zählerstände automatisieren mit Numbers und Apple Kurzbefehlen

**Dokumenttyp:** Zwischenbericht mit Projektstand, Erkenntnissen, Ergebnissen und nächstem Umsetzungspfad

| | |
|---|---|
| **Stand** | 19.04.2026 |
| **Projektstatus** | Grundstruktur fachlich definiert; erste Vorlagendatei vorhanden; finale Numbers-native Umsetzung noch offen |
| **Aktueller Kernscope** | Stromzähler Waschmaschine Keller, Stromzähler 1. OG, Gaszähler 1. OG |
| **Zielsystem** | Apple Numbers als Datenbasis, Apple Kurzbefehle für schnelle Erfassung, einfache Plausibilitätsprüfung als Basis |

Dieser Bericht bündelt den bisherigen Projektstand, die festgelegten Strukturentscheidungen, die Bewertung der vorhandenen Vorlagendatei sowie die priorisierten nächsten Schritte. Er dient als belastbare Arbeitsgrundlage für die weitere Umsetzung in Apple Numbers und Apple Kurzbefehlen.

**Systemlogik des Zielaufbaus:**

```
Eingabe (iPhone / Kurzbefehl) → Numbers Messdaten → Plausibilitätsprüfung → Auswertung / Übersicht
```

Die Erfassung startet auf dem iPhone, die Daten landen in Numbers, werden dort geprüft und anschließend für Auswertung und Übersicht genutzt.

---

## 1. Executive Summary

Das Projekt hat eine klare fachliche Richtung: Apple Numbers ist als zentrale Datenbasis gesetzt, während Apple Kurzbefehle später die schnelle Eingabe vereinfachen sollen. Damit ist die Systemlogik sauber: zuerst stabile Tabellenstruktur, danach Automatisierung.

Für die erste lauffähige Version wurde der Scope bewusst klein gehalten. Im Fokus stehen drei Zähler: Stromzähler Waschmaschine Keller, Stromzähler 1. OG und Gaszähler 1. OG. Dieser reduzierte Start ist sinnvoll, weil damit Struktur, Formeln, Plausibilitätslogik und Eingabeworkflow belastbar getestet werden können, bevor weitere Zähler hinzukommen.

Es existiert bereits ein erster Dateistand als Arbeitsvorlage: `zahlerstand_template_v2.xlsx`. Die Datei enthält mit Zählerprofil, Messdaten und Gesamtübersicht bereits die richtige Grundidee. Gleichzeitig zeigt die Analyse, dass die Datei noch eher ein Prototyp ist und für eine endgültige Numbers-Version gezielt überarbeitet werden muss.

## 2. Projektziel und feste Leitplanken

- Ziel ist ein dauerhaft nutzbares, alltagstaugliches System zur Erfassung und Auswertung von Strom- und Gaszählerständen.
- Die Eingabe eines neuen Zählerstands soll im Alltag in weniger als zehn Sekunden möglich sein.
- Numbers bildet die führende Datenquelle; Kurzbefehle unterstützen die Erfassung, dürfen die Struktur aber nicht verkomplizieren.
- Die Struktur muss später Monatsverbräuche, Jahresvergleiche, Diagramme, Kostenberechnung, Erinnerungen und Prognosen aufnehmen können.
- Plausibilitätsprüfungen sollen früh eingebaut werden: steigende Zählerstände, korrekte zeitliche Reihenfolge, Einheitenkonsistenz und einfache Ausreißererkennung.

## 3. Festgelegte Systemarchitektur

Der bisherige Projektkonsens spricht klar für eine wiederverwendbare Vorlage pro Zähler. Dieses Muster ist fachlich sauber, in Numbers gut beherrschbar und später leicht auf weitere Zähler skalierbar.

| Baustein | Inhalt | Bewertung |
|---|---|---|
| Zählerprofil | Stammdaten des einzelnen Zählers: Name, Typ, Einheit, Nummer, Standort, Messintervall, Startwert, Startdatum, Kommentar sowie kleine Auswertung | Fachlich richtig und als Deckblatt sinnvoll |
| Messdaten | Laufende Erfassung mit Datum, Uhrzeit, Zählerstand, Einheit, Differenzen, Zeitabständen, Monats- und Jahreslogik | Kern des Systems; muss Numbers-sicher aufgebaut werden |
| Gesamtübersicht | Verdichtete Sicht über mehrere Zähler hinweg, möglichst automatisch aus den Zählerblättern | Sinnvoll, aber bewusst einfach halten |
| Kurzbefehl-Eingabe | Zählertyp wählen, Wert eingeben, Zeitstempel setzen, speichern, optional bestätigen | Erst nach stabiler Tabellenbasis umsetzen |

Die Reihenfolge der Automatisierung ist bereits sinnvoll priorisiert:

```
1 Struktur → 2 Eingabe → 3 Kurzbefehle → 4 Erinnerungen → 5 Diagramme → 6 Prognosen
```

## 4. Aktueller Scope der ersten Version

Für die erste belastbare Version ist der Umfang absichtlich begrenzt. Dadurch werden Komplexität und Fehlerrisiken reduziert.

| Zähler | Typ | Einheit | Status | Hinweis |
|---|---|---|---|---|
| Stromzähler Waschmaschine Keller | Strom | kWh | Im Scope | Wichtiger Testzähler mit vorhandenen Messwerten |
| Stromzähler 1. OG | Strom | kWh | Im Scope | Soll als Haupt-/Wohnungszähler sauber abgebildet werden |
| Gaszähler 1. OG | Gas | m³ | Im Scope | Eigenhaushalt; wichtiger Kernzähler |
| Weitere Gaszähler (EG, 2. OG, Keller) | Gas | m³ | Später | Bereits als Erweiterung denkbar, aber nicht Teil der ersten Kernversion |

## 5. Datenstandard und Plausibilitätslogik

Der Datenstandard ist inzwischen klar definiert und sollte als unveränderliche Basis beibehalten werden.

| Feld | Bedeutung | Regel |
|---|---|---|
| Zählertyp | Art des Zählers | Strom oder Gas |
| Datum | Messdatum | Pflichtfeld |
| Uhrzeit | Zeitpunkt der Messung | Optional, aber sinnvoll |
| Zählerstand | Abgelesener Wert | Pflichtfeld; numerisch |
| Einheit | Messgröße | Strom = kWh, Gas = m³ |

Geplante Basisprüfungen: steigende Zählerstände, richtige zeitliche Reihenfolge, Einheitenkonsistenz und einfache Prüfung auf unrealistisch hohe Differenzen.

## 6. Bereits vorhandene reale Testdaten

Für die spätere Validierung der Tabellenlogik liegen bereits echte Messwerte vor. Diese Daten sind wertvoll, weil damit Formeln, Differenzen und Plausibilitätsregeln realitätsnah geprüft werden können.

| Zähler | Einheit | Bekannte Messpunkte | Bewertung |
|---|---|---|---|
| Stromzähler Waschmaschine Keller | kWh | 36.968,9 am 07.06.2025; 37.091,1 am 06.03.2026; 37.092,6 am 08.03.2026 | Gut für Differenz- und Verlaufstests |
| Stromzähler 1. OG / Hauptstromzähler | kWh | 815 am 06.11.2025; 1.045 am 22.12.2025; 1.422 am 17.03.2026 | Gut für Standard-Stromlogik |
| Gaszähler 1. OG | m³ | 23,361 am 06.03.2026; 24,034 am 17.03.2026 (korrigierte Ablesung) | Gut für Gaslogik und Korrekturfall |

## 7. Analyse der vorhandenen Datei `zahlerstand_template_v2.xlsx`

Die vorhandene Arbeitsdatei wurde technisch geprüft. Ergebnis: Die Struktur geht in die richtige Richtung, ist aber noch keine finale Numbers-Vorlage.

| Blatt | Ist-Zustand | Stärke | Lücke |
|---|---|---|---|
| Zählerprofil | Feld/Wert-Aufbau mit Stammdaten und ersten Auswertungsformeln | Richtige Trennung von Stammdaten und Messwerten | Foto-/Layoutbereich fehlt; finale Numbers-Optik noch offen |
| Messdaten | Spalten für Zählertyp, Datum, Uhrzeit, Zählerstand, Einheit, Differenzen, Tage, Monat, Jahr, Status | Sehr gute fachliche Basis | Nur als erste Zeile vorbereitet; noch keine robuste Eingabezone |
| Gesamtübersicht | Nur Kopfzeile vorhanden | Gedanke einer übergeordneten Sicht ist gesetzt | Noch nicht funktional verbunden |

Wesentliche Erkenntnisse aus der Dateiprüfung:

- Die Datei spiegelt bereits den richtigen Denkansatz wider: Profil, Messdaten und verdichtete Übersicht sind sauber getrennt.
- Die Statuslogik in den Messdaten zeigt, dass Plausibilitätsprüfung bereits mitgedacht wurde.
- Die Gesamtübersicht ist noch ein Platzhalter und liefert derzeit keine Ergebnisse.
- Die Datei ist im aktuellen Zustand eher eine XLSX-Arbeitsfassung als eine final saubere Numbers-Vorlage.
- Für Apple Numbers müssen Formeln und Layout gezielt nativ geprüft und gegebenenfalls angepasst werden, statt die XLSX-Datei unverändert zu übernehmen.

## 8. Bisherige Ergebnisse des Projekts

| Ergebnis | Status | Einordnung |
|---|---|---|
| Projektziel und Rolle von Numbers/Kurzbefehle geklärt | Erledigt | Wichtigster Grundsatz steht fest |
| Datenstandard für Messdatensätze definiert | Erledigt | Basis für jede weitere Automation |
| Kernscope der ersten Version auf drei Zähler begrenzt | Erledigt | Reduziert Komplexität |
| Vorlagenidee pro Zählerblatt festgelegt | Erledigt | Skalierbar und nachvollziehbar |
| Erste Arbeitsdatei vorhanden | Teilweise | Gute Basis, aber noch nicht final |
| Automatisierte Eingabe per Kurzbefehle | Offen | Folgeschritt nach finaler Tabellenbasis |
| Gesamtübersicht mit echter Verdichtung | Offen | Konzept vorhanden, Umsetzung fehlt |

## 9. Offene Punkte und Risiken

- Die finale Zielumgebung ist Apple Numbers, die vorhandene Datei ist aber noch eine XLSX-Vorstufe. Daraus ergibt sich Anpassungsbedarf bei Formeln, Layout und Bedienlogik.
- Die gewünschte Bild-/Profilseite des Zählers ist im bisherigen Dateistand fachlich noch nicht abgebildet.
- Noch offen ist die konkrete Methode, wie ein iPhone-Kurzbefehl am stabilsten in die Numbers-Struktur schreibt.
- Die Gesamtübersicht darf nicht zu komplex werden, muss aber trotzdem später mehrere Zähler zusammenführen können.

## 10. Empfohlene nächste Schritte

| Nr. | Schritt | Nutzen |
|---|---|---|
| 1 | Finale Numbers-Vorlage für einen Zähler fertigstellen | Zählerprofil optisch sauber aufbauen, Messdatentabelle nativ für Numbers formulieren, Plausibilitätsstatus vereinfachen. |
| 2 | Vorlage auf drei Startzähler anwenden | Waschmaschine Keller, Strom 1. OG und Gas 1. OG mit echten Daten füllen. |
| 3 | Einfache Gesamtübersicht aufbauen | Nur letzte Messung, letzter Stand, aktueller Monatsverbrauch und Status anzeigen. |
| 4 | Kurzbefehle-Eingabeworkflow definieren | Auswahl des Zählers, Eingabe des Werts, automatischer Zeitstempel, kontrolliertes Speichern. |
| 5 | Erinnerungen und Diagramme ergänzen | Erst nach stabiler Datenpflege; kein Vorziehen dieser Stufe. |

## 11. Fazit

Das Projekt ist fachlich deutlich weiter als eine lose Idee: Zielsystem, Datenstandard, Scope, Strukturprinzip und Plausibilitätslogik stehen bereits. Auch eine erste Arbeitsdatei existiert. Der nächste Hebel ist nun nicht weitere Theorie, sondern die konsequente Überführung dieser Grundlage in eine saubere, Numbers-native Vorlage, die im Alltag wirklich benutzt werden kann.

Damit ist der Zwischenstand insgesamt positiv: Das Fundament ist gelegt, die Komplexität wurde bewusst begrenzt, und es gibt einen klaren Weg zur ersten stabilen Version.
