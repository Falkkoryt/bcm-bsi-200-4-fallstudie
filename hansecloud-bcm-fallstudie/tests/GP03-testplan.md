# Test- und Nachweiskonzept GP-03

**Status: Noch kein Test durchgeführt.** Sämtliche Zahlen in diesem Dokument sind **Hypothesen oder synthetische Testbeispiele**.

## T-01: Ende-zu-Ende-Wiederanlauf (RTA gegen RTO)

**Ziel:** Bei simuliertem vollständigem Primärausfall alle Stufen ab T0 messen: Detektion, Alarmierung, Lagebewertung/Entscheidung, Ersatzfreigabe, Aktivierung, Prüfung kritischer Eventerkennung und Bestätigung des Notbetriebs. Ziel-RTO: 30 Minuten **ab Ausfall**. Alle Schritte müssen mit Zeitstempeln dokumentiert werden.

**Bestandenkriterium (Vorschlag):** Ersatzlösung zum dokumentierten Endzeitpunkt mit erforderlichem MBCO nachweislich nutzbar, RTA <= RTO. *Ein erreichbares Dashboard allein zählt nicht.* Die Einhaltung eines SLA ist separat zu beurteilen.

## T-02: Logvollständigkeit und RPO/RPA

**Synthetisches Beispiel:** 5.000 Events während einer 30-minütigen Störung, 4.950 beim Wiederanlauf zentral vorhanden, 50 weitere nach fünf Minuten nachgeliefert.

- Prüfen: Exakte Ereigniskennungen/Sequenzen, Quellzeitstempel, lokale Puffer, Transportwarteschlangen, Duplikate und Integritätsmerkmale.
- **Aussage:** Keine dauerhaften Verluste, *wenn* alle 5.000 unverändert erhalten sind. Kein automatischer Beleg für **RPO 0 zum Wiederanlaufzeitpunkt**, falls wesentliche Daten zunächst nicht nutzbar waren.
- **Bestandenkriterium (Vorschlag):** Ressourcenspezifisch definierter RPO-Grenzwert wird zum vereinbarten Messpunkt nachgewiesen; für kritische Ereignisse zusätzlich Erkennungszeit messen.

## T-03: Alarmierung kritischer Ereignisse

Gezielte, ungefährliche Testevents mit bekannten Quellzeitpunkten erzeugen. Vergleichen:

1. Zeitpunkt der Ereignisentstehung.
2. Zeitpunkt der Ankunft im Ersatzsystem.
3. Zeitpunkt der Detektion durch ein Regelwerk.
4. Zeitpunkt der tatsächlichen Alarmzustellung.

**Zielhypothese:** Zumindest im funktionierenden Monitoring sollen kritische Ereignisse beispielsweise **binnen 5 Minuten nach Eingang** alarmiert werden. Das garantiert im vorherigen 30-minütigen Ausfall **keine** 5-Minuten-Ende-zu-Ende-Zeit; ggf. separaten Puffer-/Alarmweg prüfen.

## T-04: Rückstands- und Kapazitätsmodell

Fiktives Lastmodell: 10.000 Events/h, davon 20 % in den ersten acht Stunden analysiert.

- Gesamt: `10.000 × 8 = 80.000` Events.
- In Phase mit reduzierter Analyse bearbeitet: `80.000 × 0,2 = 16.000`.
- Zurückgestellt: `80.000 × 0,8 = 64.000`.
- Bei Gesamtkapazität 20.000/h und 10.000/h neuen Events verbleiben 10.000/h für den Rückstand.
- Ideale Nachverarbeitungsdauer: `64.000 / 10.000 = 6,4 h = 6 h 24 min` **zusätzlich nach der 8-h-Phase**.

**Wichtige Warnung:** Die ältesten Events wären beim letzten Abbau deutlich älter als acht Stunden. Risikobasierte Sortierung verändert die Reihenfolge. Der Test muss sicherstellen, dass neue kritische Events priorisiert und nicht durch Backfill verdrängt werden.

## T-05: Unabhängiger Notfallzugang und vertrauenswürdige Konfiguration

- Unter kontrollierten Bedingungen zentrale IAM-Anbindung als nicht verfügbar simulieren.
- Autorisierten Notfallzugang mit Protokollierung, Alarmierung und Vertretungsregelung testen.
- Manipulierte bzw. nicht verifizierte Primärkonfiguration **nicht** übernehmen; Referenzkonfiguration mit unabhängig geschütztem Integritätsnachweis verwenden.
- Nachweisen, dass der Notbetrieb ohne kompromittierte Primärabhängigkeiten funktioniert.

## T-06: Tabletop-Fortsetzung

Mit mehreren klaren Rollen (SOC, IT-Bereitschaft, IR, BCM, Kundenkommunikation) ein neues, protokolliertes Tabletop durchführen. Beobachtungen, Entscheidungspunkte, Freigaben, offene Risiken und Maßnahmen getrennt erfassen.

## Teststatus-Tabelle

| Test | Ausführung | Gemessene Werte | Ergebnis |
|---|---|---|---|
| T-01 | Nicht durchgeführt | Keine | Offen |
| T-02 | Nicht durchgeführt | Keine; nur Zahlenbeispiel | Offen |
| T-03 | Nicht durchgeführt | Keine | Offen |
| T-04 | Nicht durchgeführt | Keine; nur Modellrechnung | Offen |
| T-05 | Nicht durchgeführt | Keine | Offen |
| T-06 | Nicht durchgeführt | Keine | Offen |
