# Lebensversicherungsmathematik in Python

Barwerte, Nettoprämien, Deckungskapital und Sensitivitätsanalysen einer Risikolebensversicherung und einer aufgeschobenen Rentenversicherung, einschließlich Vergleich mit der Destatis-Sterbetafel.

## Ziel
Ich wollte die Grundlogik der Lebensversicherungsmathematik verstehen und in Python sauber umsetzen: von der Sterbetafel über Barwerte und Prämien nach dem Äquivalenzprinzip bis zum Deckungskapital.

## Inhalt
1. Sterbetafel (Gompertz-Makeham): mu, qx, px, lx, dx, Lebenserwartung
2. Barwerte: Erlebensfall, Todesfall, temporäre und lebenslange Leibrente
3. Prämien der Risikolebensversicherung (x = 40, n = 20, S = 100.000 EUR)
4. Prämien der aufgeschobenen Rentenversicherung (x = 35, n = 32, R = 12.000 EUR pro Jahr)
5. Prospektives Deckungskapital mit Rekursionsprobe
6. Sensitivitätsanalyse: Rechnungszins und Sterblichkeit
7. Datenbereinigung und Einbindung der Destatis-Sterbetafel 2023/25 (männlich)

## Ausgewählte Ergebnisse
| Größe | Übungsmodell | Destatis männlich 2023/25 |
|---|---|---|
| Lebenserwartung bei Geburt | 80,28 Jahre | 78,82 Jahre |
| Jahresprämie Risikoversicherung | 353,99 EUR | 336,90 EUR (−4,8 %) |
| Jahresprämie Rentenversicherung | 4.931,68 EUR | 4.318,04 EUR (−12,4 %) |

Sensitivität (Übungsmodell): Bei einem Rechnungszins von 3 % statt 1 % sinkt die Prämie der Risikoversicherung um 6,7 %, die der Rentenversicherung um 43,0 %. Eine um 15 % höhere Sterblichkeit erhöht die Risikoprämie um 14,9 % und senkt die Rentenprämie um 7,1 %.

## Qualitätssicherung
- Identität der gemischten Versicherung: Differenz ca. 2e-16
- Direkte Summenkontrolle der aufgeschobenen Rente: Differenz ca. 2e-15
- Rekursionsformel des Deckungskapitals: größte Abweichung ca. 1e-12
- Datenprüfung der Destatis-Tafel: keine fehlenden Werte, Alter lückenlos, 0 ≤ qx ≤ 1, lx fallend; berechnetes lx weicht um höchstens 0,5 vom veröffentlichten ab

## Annahmen und Grenzen
- Das Übungsmodell ist keine echte Sterbetafel. Die Destatis-Tafel gilt nur für Männer und endet bei Alter 100 (darüber: qx +10 % pro Jahr, eigene Annahme).
- Nettoprämien ohne Kosten, Zillmerung und Überschussbeteiligung
- Rechnungszins konstant 1 %, jährliche Zahlweise, kein Storno
- Rentenversicherung ohne Todesfallleistung in der Aufschubzeit

## Technik
Python, numpy, pandas, matplotlib, Jupyter Notebook

## Nutzung
Notebook und CSV-Datei im selben Ordner in Jupyter öffnen und alle Zellen von oben nach unten ausführen.

## Datenquelle
Statistisches Bundesamt (Destatis), GENESIS-Online, Tabelle 12621-0001, Periodensterbetafel 2023/25, männlich. Datenlizenz Deutschland – Namensnennung – Version 2.0 (dl-de/by-2-0), https://www.govdata.de/dl-de/by-2-0. Die Daten wurden bereinigt und weiterverarbeitet.

## Autorin
Yasmin Al Madani, M.Sc. Mathematik (Schwerpunkt Stochastik), Duisburg
LinkedIn: https://www.linkedin.com/in/ynalmadani/
17.11.2026
