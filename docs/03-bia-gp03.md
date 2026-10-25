# 03 – Business Impact Analyse GP-03: Sicherheitsüberwachung

**Version:** 0.3 | **Status:** Vorläufige Fallstudien-BIA, nicht durch Unternehmensleitung freigegeben | **Stand:** 25.10.2026

## Prozessbeschreibung und Ausfallannahme

GP-03 überwacht 20 Kundenumgebungen, verarbeitet Log- und Sicherheitsereignisse, erkennt kritische Auffälligkeiten und alarmiert den Bereitschaftsdienst. Szenario: Zentraler Monitoring-Dienst ausgefallen; Kundenplattformen laufen zunächst weiter. Die Ursache ist in der BIA nicht festgelegt. Ein Cyberangriff ist möglich, wird aber **nicht automatisch unterstellt**.

## Schadensbereiche

| Bereich | Mögliche Folgen | Bewertungsstand |
|---|---|---|
| Betrieb | Keine automatisierte Erkennung und Bearbeitung bestimmter Ereignisse; Verzögerung von Reaktionen | Zeitkritisch, genaue Schwelle nicht belegt |
| Vertrag | Unterbrechung der 24/7-Leistung; Überschreiten des 60-Min.-Monatsbudgets möglich | SLA-Verstoß ≠ automatisch MTPD |
| Finanzen | Servicegutschriften, Zusatzaufwand, mögliche Folgeschäden | Gewinn-/Liquiditätsdaten fehlen |
| Reputation | Beschwerden, Vertrauensverlust und mögliche Kündigungsandrohungen | Zeitverlauf für ein *fiktives* Einzelausfallszenario untersucht |

## Fiktiver Reputations-Schadensverlauf

Annahme: Die Geschäftsführung betrachtet **mindestens zwei von 20 glaubhaft kündigungsbereiten Kunden** als untragbar (Stufe 3). Die folgenden Werte sind **Szenariowerte, keine echten Kundeninterviews oder Prognosen**.

| Durchgehende Ausfalldauer | Glaubhaft kündigungsbereite Kunden | Anteil | Einordnung zu genau diesem Bewertungszeitpunkt |
|---:|---:|---:|---|
| 1 Stunde | 0 | 0 % | Unter der Reputationsschwelle |
| 2 Stunden | 0 | 0 % | Unter der Reputationsschwelle |
| 4 Stunden | 1 | 5 % | Unter der Reputationsschwelle |
| 5 Stunden | 2 | 10 % | Schwelle **erreicht** |
| 6 Stunden | 3 | 15 % | Schwelle überschritten |

**Ableitung:** Der erste *untersuchte* untragbare Zeitpunkt in diesem Szenario liegt bei 5 h; 4 h ist der letzte untersuchte tolerierbare Zeitpunkt. Der tatsächliche Übergang könnte **nach 4 und spätestens bei 5 Stunden** liegen, wenn sich die Schadensentwicklung in diesem Einzelausfallszenario entsprechend verhält. Nicht interpolieren; Wiederholungsstörungen können frühere Reaktionen auslösen. Bei rechtlichen, betrieblichen oder finanziellen Schäden könnte die **Gesamt-MTPD von GP-03 kürzer** sein.

**Festlegung:** Eine **konservative Planungsgrenze von 4 Stunden** wird bis zur vollständigen BIA verwendet. Sie ist **keine abschließend ermittelte MTPD** und nicht durch die Szenariozahlen allein bestätigt.

## Vertragliche und finanzielle Szenarien

- Managed-Security-Umsatz (nur diese Sparte): `20 × 2.000 EUR × 12 = 480.000 EUR/Jahr` (fiktiver Bruttoumsatz, **nicht gesamter Unternehmensumsatz**).
- Bei überschrittenem SLA-Budget und Gutschrift für alle Kunden: `20 × 2.000 EUR × 0,10 = 4.000 EUR` **potenzielle einmalige Gutschriften** (nicht automatisch fällige Strafzahlung).
- Bei hypothetischer Kündigung von 3 Kunden: `3 × 2.000 EUR × 12 = 72.000 EUR` **potenziell wegfallender Jahresumsatz**, nicht erwiesener Schaden und nicht entgangener Gewinn.
- Zwei Ausfälle zu je 2 h = **240 Minuten kumulierter Ausfall** im Monat und somit 180 Minuten über dem fiktiven SLA-Budget (falls keine anrechenbare Ersatzleistung erbracht wurde).

Die 120 Mitarbeitenden erlauben keine zuverlässige Aussage über Liquidität, Gewinn oder Tragbarkeit einzelner Beträge. Vertragsfolgen und potenzielle Kundenverluste müssen getrennt bewertet werden.

## Vorläufige Sollwerte

| Größe | Entwurf | Notwendiger Nachweis |
|---|---|---|
| MTPD, Prozess GP-03 | 4 h als **Arbeitshypothese** | Vollständige, abgestimmte BIA über alle Schadenskategorien |
| RTO, GP-03 / notwendige Ressourcen | 30 min **ab Prozess-/Ressourcenausfall** | RTA-Messung inkl. Detektion, Alarmierung, Umschaltung, Funktionsprüfung |
| RPO erforderlicher Logdaten | 0 min als anspruchsvolles **Soll** | Ressourcenspezifische Festlegung und RPA-Nachweis |
| Mindestleistungsniveau (MBCO) | Alle 20 Kunden, zeitnahe Erkennung kritischer Ereignisse, relevante Logdaten sichern | Fachliche Freigabe; SLA- und Korrelationsprüfung |
| Stark eingeschränkte Auswertung | maximal 8 h als internes **Ziel** | Nachweis zu Kapazität, Risiken und Vertragspflichten |

**RTO-Definition:** Im herangezogenen BSI-Standard 200-4 ist der Zeitraum vom **Ausfall** des betroffenen Prozesses oder der Ressource bis zum benötigten Wiederanlauf relevant. Nicht erst ab Notfallausrufung zählen! Die organisatorische Alarmierungszeit gehört deshalb in die Gesamtbetrachtung.

**RPO-Definition:** Fachliche Anforderung an den maximal zulässigen Datenrückstand beim Wiederanlauf. Eine vollständige spätere Log-Nachlieferung belegt nicht automatisch RPO 0 **zum Wiederanlaufzeitpunkt**. Die zeitgerechte Angriffserkennung ist eine zusätzliche, getrennte Anforderung.

## Fehlende Informationen zur BIA-Freigabe

1. Fachliche Schadensgrenzen in **allen** Kategorien einschließlich nachvollziehbarer Unternehmens- und Vertragsannahmen.
2. Relevante Kunden-SLA-Details und Akzeptanz von Ersatz-/Teilüberwachung.
3. MTPD-Ableitung über Gesamtprozess und mögliche Mehrfachausfälle.
4. RTO/RPO je benötigter Ressource mit Eigentümer und Wiederanlaufreihenfolge.
5. Belastbare personelle, technische und wirtschaftliche Soll-Ist-Erhebung.

**Nicht abgeschlossen:** Die MTPD- und RPO-Freigabe, GP-01/GP-02-BIA sowie die gesamte Prozesspriorisierung.
