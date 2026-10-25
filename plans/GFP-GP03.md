# Geschäftsfortführungsplan (GFP) – GP-03 Sicherheitsüberwachung

**Version:** 0.3 | **Status: NICHT FREIGEGEBENER KONZEPTENTWURF** | **Stand:** 25.10.2026

> **Nicht als operative Notfallanweisung verwenden.** Unternehmen, Systeme, Verantwortlichkeiten und Abläufe sind fiktiv; Kontaktwege, Zugriffsdaten, Schaltmaßnahmen und Wirksamkeit sind nicht verifiziert. Der Plan beschreibt die **Fortführung des Geschäftsprozesses**. Technischer Wiederanlauf siehe [WAP-Konzept](WAP-GP03-Konzept.md).

## 1. Geltungsbereich

- Prozess: **GP-03 Sicherheitsüberwachung und Bereitschaft** für 20 Managed-Security-Kunden.
- Prozessverantwortung (Rolle): Leitung Security Operations.
- Notfallkoordination (Rolle): autorisierte Notfallleitung / BCM-Verantwortliche.
- Technische Wiederanlaufverantwortung (Rolle): IT-Bereitschaft.
- Sicherheitsvorfälle (Rolle): Incident-Response-Leitung.
- Kundenkommunikation (Rolle): Service Management / Kundenbetreuung.

**Rollen sind Modellrollen.** Konkrete Namen, Rufnummern, Stellvertretungen und Befugnisse müssten in einer geschützten, ausfallsicher verfügbaren Kontaktliste ergänzt werden.

## 2. Wiederanlaufanforderungen (nicht freigegeben)

| Vorgabe | Wert | Status |
|---|---|---|
| MTPD | 4 h | Konservative Hypothese, nicht abschließend aus BIA abgeleitet |
| RTO | 30 min ab **Ausfall** des Prozesses/der Ressource | Planungsziel; erforderliche Nachweise offen |
| RPO | 0 min für erforderliche Sicherheitslogs | Ambitioniertes, ressourcenbezogen zu prüfendes Soll |
| SLA | 60 min ungeplante Nichtverfügbarkeit kumuliert/Monat | Fiktiver Vertrag |
| Kundeninformation | Bei Unterbrechung >30 min | Fiktiver Vertrag |

**Zeitmessung:** Ausfallereignis `T0`, Detektion, Alarmierung, Notfallausrufung, Freigabe, technischer Umschaltzeitpunkt und geprüfte Notbetriebsaufnahme sind **separat** zu protokollieren. Die RTO darf nicht erst ab Notfallausrufung gerechnet werden.

## 3. Mindestleistungsniveau – vorgeschlagen

- Alle 20 Kundenumgebungen müssen weiterhin relevante Sicherheitsdaten bereitstellen können.
- Kritische sicherheitsrelevante Ereignisse sollen erkannt, an eine autorisierte Stelle alarmiert und bearbeitet werden können.
- Logdaten anderer Prioritäten sollen, soweit datenschutz- und sicherheitsgerecht, vollständig, manipulationsgeschützt gepuffert und nachträglich analysiert werden.
- Die Bewertung von Ereignissen geringerer Priorität darf **nur** reduziert werden, soweit dabei keine unvertretbaren Korrelations-/Erkennungslücken entstehen und Verträge dies zulassen.
- Ziel: Höchstens 8 h stark eingeschränkte Analyse; anschließend erweiterte Auswertung. **Keine nachgewiesene maximal tolerierbare Notbetriebsdauer.**

**Nicht behaupten:** Dass der reduzierte Notbetrieb das 24/7-SLA sicher erfüllt. Umfang und Tauglichkeit der Ersatzleistung sind offen.

## 4. Alarmierung und Auslösung

**Mögliche Auslöser:** Ausfall zentraler Logverarbeitung, Ausbleiben von System-Health-Checks, Ausfall der Alarmzustellung oder Ausfall zentraler Identitäts- und Monitoring-Dienste.

1. **Erkennen / dokumentieren:** Ausfallbeginn und betroffene Kunden/Funktionen erfassen; kritische Ausfälle über einen vom Hauptmonitoring unabhängigen Weg melden.
2. **Eskalieren:** IT-Bereitschaft, Security Operations, Notfallleitung informieren; etwaigen Sicherheitsverdacht unverzüglich an Incident Response weitergeben.
3. **Lage einschätzen:** Handelt es sich um eine behebbare Störung, einen Notfall oder einen Hinweis auf Kompromittierung? Sofortmaßnahmen, Risiken und Zeitbudget festhalten.
4. **Notfall ausrufen:** Nur durch die autorisierte Rolle gemäß vorher vereinbartem Eskalationsverfahren; die Ausrufung setzt **nicht** den RTO-Zeitgeber auf null.
5. **Geschäftsfortführung vorbereiten:** Ersatzlösung gemäß WAP ausfallsicher aktivieren, sofern sie vertrauenswürdig ist. Ein unsicherer Umschaltvorgang ist zu unterlassen und zu eskalieren.

## 5. Entscheidung vor Umschaltung

| Frage | Erwartete Prüfung / Vorgehen |
|---|---|
| Ist die Ersatzumgebung von der Störung unabhängig? | Gemeinsame Netz-, IAM-, Storage-, Provider- oder Management-Abhängigkeiten prüfen |
| Gibt es Hinweise auf Angreiferzugang / manipulierte Konfigurationen? | IR-Team einschalten; keine ungeprüfte Primärkonfiguration übernehmen |
| Ist eine vertrauenswürdige Referenzkonfiguration vorhanden? | Authentizität und Integrität gegen unabhängig geschützte Referenz prüfen |
| Ist der administrative Zugang zuverlässig und berechtigt? | Regelzugang oder dokumentierter Notfallzugang nach definierten Kriterien |
| Kann der erforderliche Logempfang und die Alarmierung funktionieren? | Sichere technische Prüfung; erst nach bestandener Abnahme Notbetrieb bestätigen |

**Wenn keine sichere Umschaltung möglich ist:** Notfallleitung / IR-Leitung entscheiden über alternative Eindämmung, teilweisen Notbetrieb oder begründete Verzögerung. Erwartete Zielverletzung, Risiken und weitere Maßnahmen dokumentieren.

## 6. Notbetrieb organisieren

- Security Operations überwacht verfügbare Alarme und eskaliert kritische Vorfälle.
- IT-Bereitschaft stellt die technische Ersatzressource bereit und überwacht ihre Stabilität.
- Incident Response untersucht parallel erkennbare Angriffsanzeichen; notwendige Eindämmung geht unsicherem Wiederanlauf vor.
- Kundenmanagement prüft Zeitpunkt und Umfang einer nach SLA erforderlichen Nachricht; da die SLA-Uhr ab tatsächlicher Unterbrechung läuft, nicht die Meldung bis zur vollständigen Wiederherstellung aufschieben.
- Alle Einschränkungen, nicht verarbeiteten Logbestände und Personal-/Kapazitätsgrenzen in einem Lageprotokoll erfassen.
- Neue kritische Ereignisse bevorzugt zeitnah bearbeiten; ältere Ereignisse parallel **risikobasiert** aufarbeiten.

## 7. Rückkehr zum Normalbetrieb

Nur nach technischer und sicherheitsfachlicher Freigabe: Primärumgebung bereinigen/prüfen, Konfigurationen vertrauenswürdig bereitstellen, Logbestände abgleichen, Alarmketten testen, kontrolliert zurückschalten. Fehleranalyse, Incident-Review, SLA-Meldungen und Lessons Learned dokumentieren.

## 8. Abnahme und offene Punkte

- [ ] Zuständigkeiten und Vertretungen freigegeben
- [ ] SLA-Gleichwertigkeit des Notbetriebs geklärt
- [ ] RTO inkl. Detektion, Freigabe, Umschaltung und Funktionsprüfung in Test nachgewiesen
- [ ] RPO/RPA je relevanter Informationsressource geprüft
- [ ] Notfallzugänge unter kontrollierten Bedingungen getestet
- [ ] Ersatz-Konfiguration aus unabhängiger vertrauenswürdiger Quelle validiert
- [ ] Logverarbeitung und Alarmierung sämtlicher erforderlichen Kundendaten getestet
- [ ] Nachlauf-/Rückschaltungsverfahren getestet

**Genehmigung / praktische Tests:** Keine durchgeführt.
