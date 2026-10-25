# 05 – Vergleich möglicher Business-Continuity-Strategien

**Status:** Konzeptionelle Kosten-Nutzen-Gegenüberstellung; alle Preis-/Leistungsdaten fiktiv.

## Varianten

| Kriterium | Option A: Verbesserung primärer Betrieb | Option B: unabhängige Ersatzüberwachung |
|---|---|---|
| Investition einmalig | 5.000 EUR | 35.000 EUR |
| Betriebskosten jährlich | 1.000 EUR | 12.000 EUR |
| Summe über 3 Jahre (ohne Diskontierung) | **8.000 EUR** | **71.000 EUR** |
| Mehrkosten B gegen A / 3 Jahre | – | **63.000 EUR** |
| Hauptwirkung | Reduzierung der Ausfallhäufigkeit | Verkürzung der Dauer bei Gesamtausfall möglich |
| Aussage zur Wiederanlaufzeit | Im Szenario im Mittel weiterhin 4 Stunden | Anbieterangabe: technischer Umschaltvorgang 15 Minuten |
| Einhaltung der RTO 30 min | **Nicht nachgewiesen**; 4-h-Mittelwert genügt nicht | **Nicht nachgewiesen**; Detektion, Alarmierung, Prüfung fehlen |
| Erfüllung des SLA | Nicht nachgewiesen | Nicht nachgewiesen |

**Vorsicht:** Eine durchschnittliche Reparaturdauer von vier Stunden beweist nicht, dass nie innerhalb von 30 Minuten fortgeführt werden könnte, aber sie ist kein tragfähiger Nachweis zur Erfüllung des Zielwertes. Die Anbieterangabe von 15 Minuten ist ebenfalls kein vollständiger RTA-Messwert. Die erforderliche Wiederanlaufzeit gilt **ab Ausfall**, weshalb die Erkennungs-, Entscheidungs-, Umschalt- und Prüfzeiten zusammen betrachtet werden müssen.

## Vergleich mit erwarteten Schäden

- Drei hypothetische Kündigungen: 72.000 EUR wegfallender **Umsatz über 12 Monate**, nicht Gewinn und keine automatische Schadensprognose.
- Mögliche einmalige Servicegutschriften: bis zu 4.000 EUR im konstruierten Gesamtkundenszenario.
- Ohne Ausfallhäufigkeit, tatsächliche Schadenswahrscheinlichkeit, Marge, Betriebskosten-Nebeneffekte und belastbare technische Tests lässt sich **kein sauberer ROI** bestimmen.

## Vorläufige Empfehlung

**Option B als bevorzugter Kandidat zur weiteren Prüfung**, weil sie einen unabhängigen Notbetrieb grundsätzlich ermöglichen kann. **Keine Investitionsfreigabe.** Option A kann ergänzend die Ausfallhäufigkeit senken, ersetzt eine notwendige Wiederanlaufstrategie aber nicht automatisch.

Vor Freigabe zu prüfen:

1. Gemessene Wiederanlaufzeit mit Fehlererkennung, Alarmierung, Berechtigungsprüfung und Funktionsabnahme.
2. Keine gemeinsamen kritischen Abhängigkeiten / keine Übernahme kompromittierter Konfigurationen.
3. Notbetriebsniveau und mögliche Einschränkungen sind mit Kundenverträgen vereinbar.
4. Angemessenheit von Kosten, Schäden und verbleibenden Risiken; mögliche dritte, kostengünstigere Lösung.
5. Organisatorische Tragfähigkeit (Personal, Rufbereitschaft, Verfahren und Übungsintervalle).
