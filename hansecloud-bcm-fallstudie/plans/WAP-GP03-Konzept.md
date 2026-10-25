# Wiederanlaufplan (WAP) – Konzept einer unabhängigen Ersatzüberwachung

**Version:** 0.3 | **Status:** TECHNISCHER KONZEPTENTWURF – nicht installations- oder einsatzbereit

Der WAP beschreibt die Bereitstellung der benötigten **IT-Ressource**, damit GP-03 auf dem vereinbarten Notbetriebsniveau arbeiten kann. Operative Prozessmaßnahmen siehe [GFP GP-03](GFP-GP03.md).

## Voraussetzungen (nicht als bereits implementiert ansehen)

1. Unabhängige Ersatzmonitoring-Instanz mit getesteter Konfiguration, ausreichender Kapazität und funktionierenden Alarmwegen.
2. Separat geschützter Konfigurations- und Integritätsnachweis sowie dokumentierter Bereitstellungspfad.
3. Fehlertolerante, persistente Log-Puffer und definierte Nachübertragung.
4. Autorisierte reguläre beziehungsweise unabhängige privilegierte Notfallkonten mit geübter Nutzung.
5. Sicherheitsfachliche Freigaberegel bei Anzeichen kompromittierter Identitäten oder manipulierten Konfigurationen.
6. Mindestens zwei unterwiesene Personen und erreichbare Bereitschaft.
7. Schriftlich definierte Testereignisse, Abnahmekriterien und Rückfallverfahren.

## Konzeptionelle Tätigkeiten

| Nr. | Aktion | Rolle | Nachweis |
|---|---|---|---|
| W1 | Ausfallzeitpunkt T0 und Symptome erfassen | Bereitschaft/SOC | Zeitstempel im Lageprotokoll |
| W2 | Incident-Response-Verdacht klären, Risiken der Ersatzlösung prüfen | Security / IR | Sicherheitsfreigabe bzw. Sperrentscheidung |
| W3 | Unabhängigen administrativen Zugang nach Notfallverfahren herstellen | Berechtigte IT-Bereitschaft | Zugriffsprotokoll, Autorisierung |
| W4 | Prüfen, ob Referenzkonfiguration unverändert und vertrauenswürdig ist | IT / Security | Signatur/Hash aus separater Vertrauenskette |
| W5 | Ersatzlösung aktivieren; keine ungeprüften Regeln oder Credentials übernehmen | IT-Bereitschaft | Systemstatus/Änderungsprotokoll |
| W6 | Logeingang und Alarmierung aller erforderlichen Kundenumgebungen überprüfen | SOC | Testfall- und Kundenabdeckung |
| W7 | Notbetrieb bestätigen; Einschränkungen und Restarbeiten dokumentieren | Prozessverantwortung | Zeitstempel, Abnahmeprotokoll |
| W8 | Logrückstand kontrolliert und priorisiert nachverarbeiten | SOC / IT | Vollständigkeits- und Leistungskennzahlen |
| W9 | Geregelte Rückschaltung auf bereinigte Primärumgebung | IT / IR | Rückschalt- und Sicherheitsfreigabe |

**Keine produktiv einsetzbaren CLI-Befehle:** Die Zielplattform und ihre sichere Implementierung wurden bisher nicht festgelegt. Ein ausführbarer WAP benötigt systemspezifische, getestete Schrittfolgen.

## Zeitziele korrekt messen

- RTO-Planungswert = **30 min ab Ausfall (T0)** bis zur geprüften Verfügbarkeit einer geeigneten BC-Lösung.
- Zeiten für Erkennen, Melden, Lagebewertung, Freigabe, Aktivieren und Funktionstest **alle erfassen**.
- Die fiktive monatliche SLA-Toleranz wird separat ab tatsächlicher Dienstunterbrechung kumuliert.
- Herstellerangaben über reine Umschaltzeiten reichen nicht als vollständiger RTA-Nachweis.

## Teststatus

Alle oben genannten Schritte sind **konzipiert, nicht technisch durchgeführt**. Testanforderungen stehen in [GP03-Testplan](../tests/GP03-testplan.md).
