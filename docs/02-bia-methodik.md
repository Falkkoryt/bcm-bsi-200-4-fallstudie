# 02 – BIA-Methodik und Bewertungsannahmen

**Status:** Übungsmethodik, noch nicht mit realer Unternehmensleitung abgestimmt.

## Zweck

Die BIA untersucht die **zeitabhängigen Folgen des Ausfalls eines Geschäftsprozesses**, zunächst weitgehend unabhängig von der Ausfallursache. Anders als eine Risikoanalyse trifft sie keine unbelegten Aussagen darüber, wie wahrscheinlich ein Cyberangriff während eines Monitoring-Ausfalls ist.

Betrachtete Schadensbereiche:

1. Betriebliche Leistungserbringung und Auswirkungen auf Kunden.
2. Verträge, Gesetze und sonstige Verpflichtungen.
3. Finanzielle Folgekosten.
4. Reputation und Kundenbindung.

Die Geschäftsführung der fiktiven Organisation gibt für die Übung folgende vierstufige Skala vor:

| Stufe | Bedeutung |
|---|---|
| 1 | Geringe Auswirkungen |
| 2 | Spürbare, beherrschbare Auswirkungen |
| 3 | Schwerwiegende, **nicht mehr tolerierbare** Auswirkungen |
| 4 | Außerordentlich schwere Auswirkungen |

Diese Skala und die Untragbarkeit ab Stufe 3 sind **erfundene Bewertungsannahmen**, keine vorgeschriebenen BSI-Klassifizierungen. Zusätzlich gilt für die **isolierte Reputationsbetrachtung** als vereinfachter Schwellenwert: Glaubhaft drohender Verlust von mindestens 10 % der 20 Managed-Security-Kunden (= 2 Kunden) gilt als untragbar.

## Vorgehen

1. Prozessumfang und Szenario definieren.
2. Zeitpunkte festlegen und Folgen je Schadensbereich **mit Begründung** bewerten.
3. Ersten betrachteten Zeitpunkt des Untragbarkeitsniveaus und Datenlücken erfassen; Zwischenwerte **nicht linear interpolieren**.
4. Prozessabhängigkeiten und notwendiges Notbetriebsniveau aufnehmen.
5. MTPD auf Prozessebene herleiten; RTO für Prozess/benötigte Ressourcen mit geeignetem Puffer und inklusive Detektion/Alarmierung ableiten; RPO für informationsbasierte Ressourcen bestimmen.
6. Hypothesen, Freigaben und technische Soll-Ist-Nachweise getrennt dokumentieren.

## Grenzen

- Kundenreaktionen aus Szenarien sind **keine empirisch erhobenen Daten**.
- Eine Vertragsverletzung ist nicht automatisch ein untragbarer Unternehmensschaden, bleibt aber unabhängig davon vertragsrechtlich relevant.
- Mehrfache Ausfälle können kumulative Schäden verursachen. Die wiederholten Ausfälle werden separat modelliert; ein einzelner MTPD-Wert bildet das nicht vollständig ab.
- Zielwerte dürfen nicht als gemessene Wiederanlauffähigkeit dargestellt werden.

Quelle und Begriffserläuterungen: [08 – Quellen](08-quellen-und-begriffe.md).
