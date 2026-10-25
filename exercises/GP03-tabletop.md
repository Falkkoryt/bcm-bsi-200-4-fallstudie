# Tabletop-Fallstudie GP-03 – Angriffsverdacht beim Monitoring-Ausfall

**Art:** Textbasierte hypothetische Entscheidungsübung (keine reale Übung mit Betriebspersonal, keine technische Simulation)
**Szenarienstand:** 23.–24.10.2026 | **Protokolliert:** 25.10.2026

## Ausgangssituation

03:00 Uhr: Primäres Monitoring und zentrale Identitätsverwaltung fallen aus. 03:10 Uhr: Die Notfallleitung ruft (hypothetisch) den Notfall aus. Ein zuvor unbekannter externer privilegierter Login wird um 02:57 Uhr entdeckt. Später wird im Szenario bestätigt, dass ein Angreifer IAM kompromittiert hat. Die Ersatzumgebung wirkt unabhängig, erhält aber bestimmte Konfigurationsdaten von der möglicherweise manipulierten Primärumgebung.

**RTO-Korrektur:** Bei einem Ziel von **30 Minuten ab Ausfall um 03:00 Uhr** wäre das Ziel **03:30 Uhr**, nicht 03:40 Uhr. Die alte Übungsannahme, die RTO beginne erst um 03:10 Uhr, war fachlich falsch und ist hier korrigiert.

## Diskutierte Entscheidungen

| Moment | Überlegung/Entscheidung | Fachliche Einordnung |
|---|---|---|
| Verdächtiger privilegierter Login | IR-Team sofort alarmieren; sichere Geschäftsfortführung parallel prüfen | Sinnvoll; keine kompromittierte Zugriffsberechtigung übernehmen |
| Ausfall des zentralen IAM | Vorbereiteten, unabhängig authentifizierenden Break-Glass-Zugang unter klaren Regeln prüfen | Nur bei tatsächlich unabhängiger und sicherer Implementierung |
| Verdacht auf manipulierte Primärkonfiguration | Umschaltung anhalten, Dateien vor Nutzung validieren | Sicherheitsfachlich geboten, RTO-Konflikt eskalieren |
| Präventive Verbesserung | Vertrauenswürdige getrennte Referenzkonfiguration bereitstellen | Vermeidet Abhängigkeit von potenziell kompromittierter Quelle |
| Rückkehr zu GP-03 | Alarme, Logempfang und Integrität der Ersatzumgebung prüfen, erst dann freigeben | Notwendige Abnahme, nicht bloß „System an“ |

## Lessons Learned

1. Notbetrieb und Incident Response können parallel erfolgen, **sofern** die Ersatzlösung sicher ist.
2. Technische Redundanz allein reicht nicht, wenn Konfiguration und Zugangsdaten gemeinsam kompromittierbar sind.
3. Break-Glass-Zugänge brauchen unabhängige Authentifizierung, sichere Bereitstellung, Überwachung und personelle Vertretung.
4. Die RTO darf nicht über kompromittierende Schnellmaßnahmen erreicht werden.
5. Zeitmessung muss mit Ausfallbeginn starten; frühere Zeitachse ist zu korrigieren.

## Ergebnis und Grenzen

**Ergebnis:** Potenzielle Schwachstellen identifiziert, Sicherungsmaßnahmen vorgeschlagen und die Zeitmessung fachlich korrigiert.

**Nicht nachgewiesen:** Tatsächliche Umschaltzeit, RTO-Einhaltung, RPO/RPA, echte Kompromittierung, reale Angriffserkennung oder ausfallsicheres IAM-Verfahren.
