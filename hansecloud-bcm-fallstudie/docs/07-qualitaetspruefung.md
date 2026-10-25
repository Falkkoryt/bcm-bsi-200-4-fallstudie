# 07 – Fachliche Qualitätssicherung und Korrekturprotokoll

**Stand:** 25.10.2026 | **Status:** Selbstprüfung einer Lernfallstudie, kein unabhängiges Audit und keine Konformitätsbestätigung.

## Korrekturen und offene Punkte

| ID | Behauptung / Problem aus der Projektentwicklung | Fachliche Behandlung in Version 0.3 |
|---|---|---|
| Q-01 | MTPD von 4 h wurde als fester Wert diskutiert | Nur **konservative Arbeitshypothese**. Im Reputationsszenario unter den getesteten Zeitpunkten 4 h tolerierbar, 5 h erstmals untragbar. Kein exakt bestimmter Prozess-MTPD-Wert. |
| Q-02 | RTO von 30 min wurde mehrfach ab *Notfallausrufung* gerechnet | **Korrigiert:** Nach BSI-Standard 200-4 ab Ausfall des betroffenen Geschäftsprozesses oder der Ressource bis BC-Lösung, inklusive Detektion/Alarmierung. Bei Ausfall 03:00 Uhr Ziel 03:30 Uhr, nicht 03:40 Uhr. |
| Q-03 | RPO 0 min aus später vollständiger Übertragung abgeleitet | **Korrigiert:** 100 % nach 35 min zeigt in der Fallannahme keinen endgültigen Logverlust. Es beweist **nicht** automatisch, dass RPO 0 **zum Wiederanlaufzeitpunkt** erreicht war. |
| Q-04 | Alarmierung innerhalb von 5 min nach Logeingang mit Echtzeit-Monitoring gleichgesetzt | **Getrennt:** Eingang→Alarm und Ereignisentstehung→Alarm messen. Gepufferte Ereignisse können viel älter sein. |
| Q-05 | 24/7-Vertrag als durch „kritische Ereignisse allein“ erfüllt dargestellt | **Offen:** Vertraglicher Überwachungsumfang und Erkennungsketten sind im Detail nicht geprüft. |
| Q-06 | 8 h eingeschränkte Auswertung mit maximalem Alter aller Ereignisse verwechselt | **Getrennt:** 8 h reduzierte Analyse plus ggf. 6,4 h Aufholzeit; später bearbeitete Ereignisse können entsprechend älter sein. |
| Q-07 | 72.000 EUR als gesamter Jahresumsatz interpretiert | **Korrigiert:** 72.000 EUR ist hypothetischer Umsatzverlust bei 3 gekündigten Kunden; die 20 Kunden generieren im Beispiel 480.000 EUR Jahresumsatz. Kein Gewinnwert. |
| Q-08 | SLA = MTPD oder 30-min-Kundeninformation = 30-min-Umschaltfrist | **Getrennt:** SLA 60 min kumuliert/Monat und Informationspflicht >30 min sind Vertragsparameter, nicht identisch mit MTPD oder RTO. |
| Q-09 | 15-min-Umschaltung (Herstellerangabe) als erfüllte RTO interpretiert | **Nicht übernommen:** Fehlende Detektion, Alarmierung, Freigabe, Verifikation und eigene Tests. |
| Q-10 | Option B als freigegebene BC-Lösung betrachtet | **Nicht übernommen:** Bevorzugt nur für weitere Tests; vollständige Kosten-Nutzen-Bewertung offen. |
| Q-11 | Nutzerseitige Einschätzungen als Unternehmensentscheidungen missverstanden | **Klarstellung:** Alle Bewertungen sind vorläufige, fiktive Fallstudienentscheidungen; keine Freigaben durch echte Prozessverantwortliche. |

## Evidenzstatus

| Kategorie | Was liegt vor? | Was liegt nicht vor? |
|---|---|---|
| Unternehmensszenario | Durchgehende fiktive Ausgangsannahmen und Prozesse | Reale Unternehmensdaten |
| BIA | Methodische Schadensbewertung und Szenarien | Vollständige freigegebene BIA |
| BCM/BC-Strategie | Konzeptvergleich und Abhängigkeitsanalyse | Nachgewiesene technische Wirksamkeit / ROI |
| GFP/WAP | Dokumententwürfe mit Rollen, Abnahmekriterien, Sicherheitsmaßnahmen | Freigabe, betriebsfertige Schrittabfolge und Kontaktliste |
| Tabletop | Textbasierte Fall-/Entscheidungsbesprechung | Reales Mehrpersonen-Tabletop bzw. technische Übung |
| RTO/RPO | Zielhypothesen und Berechnungen | RTA/RPA-Messwerte aus einer echten Testumgebung |

## Veröffentlichungsfreigabe

**Als Lern- und Portfolio-Fallstudie veröffentlichbar**, sofern die fiktive Natur klar angegeben bleibt. **Nicht** als „implementiertes BCMS“, „BSI-200-4-konform“, „BCM-Audit durchgeführt“, „RTO eingehalten“, „RPO nachgewiesen“ oder „vollständig getesteter Notfallplan“ darstellen.

## Referenz

Der herangezogene [BSI-Standard 200-4](https://www.bsi.bund.de/SharedDocs/Downloads/DE/BSI/Grundschutz/BSI_Standards/standard_200_4.pdf?__blob=publicationFile&v=8) definiert u. a. MTPD/RTO/RPO und behandelt BIA, BC-Strategien, GFP und WAP. Die Fallstudie überträgt diese Methodik vereinfacht auf fiktive Daten.
