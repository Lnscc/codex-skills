---
name: obsidian-memory
description: Nutzt und pflegt den persönlichen Obsidian-Vault als dauerhaftes Arbeitsgedächtnis für Projektkontext, Entscheidungen, Arbeitspräferenzen und Inhalte zur späteren Weiterarbeit. Verwenden, wenn eine Aufgabe diesen Kontext benötigt oder nach substanzieller Arbeit neue dauerhafte Erkenntnisse oder weiterverwendbare Inhalte festzuhalten sind.
---

# Obsidian-Arbeitsgedächtnis

Der persönliche Vault liegt unter `C:\Users\linus\Documents\Obsidian\mind palace`.
Arbeite direkt mit den Markdown-Dateien; ein Obsidian-Plugin ist nicht erforderlich.

## Kontext gezielt lesen

- Beginne bei `00 Codex/Start.md`. Lies bei Projektarbeit `00 Codex/Aktueller Stand.md` und folge nur den für die Aufgabe relevanten Links.
- Suche bei Bedarf mit `rg` gezielt nach Projekt, Thema oder Entscheidung, statt den gesamten Vault zu laden.
- Für technische Ist-Zustände sind aktueller Repository-Code und aktuelle Repository-Dokumentation maßgeblicher als Obsidian-Zusammenfassungen. Behandle frühere Notizen als Kontext, nicht als Nachweis aktueller Umsetzung.

## Dauerhafte Erkenntnisse und Arbeitsinhalte pflegen

Prüfe nach jeder substanziellen Aufgabe, ob neue Informationen in späteren Chats nützlich bleiben: bestätigte Entscheidungen, Korrekturen, Arbeitspräferenzen, wesentlicher Projektfortschritt, wichtige Einschränkungen sowie offene Schleifen und nächste Schritte. Speichere solche Erkenntnisse ohne zusätzliche Aufforderung.

Prüfe dabei auch, ob im Gespräch Inhalte entstanden sind, die für spätere Weiterarbeit erhalten bleiben sollten. Speichere diese ohne zusätzliche Aufforderung, auch wenn sie noch vorläufig sind oder keine Entscheidung getroffen wurde. Unterscheide klar zwischen Vorschlägen, bestätigten Aussagen und Entscheidungen des Nutzers.

- Lies vor einer Änderung die Zielnotiz. Aktualisiere eine passende bestehende Notiz, wenn Ziel und Einordnung klar sind. Nutze `00 Codex/Inbox.md` nur, solange die Zuordnung unklar ist; lege nicht für jede Aufgabe eine neue Notiz an.
- Sobald ein neues Projekt mit dauerhaftem Kontext eindeutig erkennbar ist, lege automatisch `<Projektname>/Beschreibung.md` im Vault an. Prüfe zuvor auf einen bestehenden Ordner oder abweichenden Projektnamen, um Duplikate zu vermeiden. Halte Zweck, bekannten Projektpfad, aktuellen Gesamtstand und offene nächste Schritte knapp fest und verlinke die Beschreibung in `00 Codex/Start.md` sowie `00 Codex/Aktueller Stand.md`. Überführe bereits zugeordnete Inbox-Inhalte in die passende Projektnotiz und entferne die übernommenen Inhalte aus der Inbox. Dafür ist keine zusätzliche Aufforderung nötig; ein eigener Code-Projektordner ersetzt die Ablage im Vault nicht.
- Halte jede Information möglichst an einer Stelle fest. Ergänze oder korrigiere vorhandene Aussagen, statt widersprüchliche oder doppelte Einträge anzuhängen. Erhalte weiterhin relevante Begründungen früherer Entscheidungen.
- Wähle Ablageort und Umfang nach dem Inhalt, nicht nach der gerade geöffneten Notiz. Projektbeschreibungen bleiben ein knapper Einstieg mit Zweck, aktuellem Gesamtstand und Links. Eigenständige Themen zur späteren Weiterarbeit erhalten bei entsprechendem Umfang eine eigene Themennotiz, die im passenden Einstieg verlinkt wird; allgemeine Arbeitspräferenzen projektübergreifend ablegen. Kleine Ergänzungen benötigen keine eigene Datei.
- Lege ohne zusätzliche Aufforderung passende Unterordner an, wenn sie zusammengehörige Themen oder Arbeitsinhalte sinnvoll bündeln. Nutze vorhandene Ordner und halte die Hierarchie so flach wie sinnvoll; eine einzelne kurze Notiz braucht keinen eigenen Ordner. Verlinke die Notizen im passenden Einstieg. Verschiebe bestehende Notizen nur bei ausdrücklichem Auftrag und passe dabei betroffene Wikilinks an.
- Technische Implementierungsdetails, Test- und Laufprotokolle, Commit-Nachweise und Ticketverläufe gehören in Repository-Dokumentation beziehungsweise Linear. Verweise im Vault auf diese Quellen, statt sie zu kopieren; halte dort nur die für spätere Arbeit relevante Aussage fest. Diese Einordnung allein beauftragt keine Änderungen in externen Systemen.
- Führe bei Statusänderungen die betroffene Zusammenfassung auf den aktuellen Stand zusammen. Ersetze überholte Aussagen und erledigte offene Punkte, statt spätere Abschlussabschnitte anzuhängen. Projektbeschreibungen und Statusnotizen sind keine chronologischen Tätigkeitsprotokolle.
- Aktualisiere bei wesentlichem Projektfortschritt auch `00 Codex/Aktueller Stand.md`: knapp zusammenfassen und auf die ausführliche Projektnotiz verweisen.
- Formuliere bestätigte Ergebnisse und verbleibende offene Punkte klar getrennt. Gib bei zeitabhängigen Statusaussagen ein Datum an, wenn es für die spätere Einordnung nötig ist.
- Halte unbestätigte Annahmen nicht als Tatsachen fest. Vorläufige Arbeitsinhalte dürfen mit klar erkennbarem Status gespeichert werden.
- Speichere keine flüchtigen Gesprächsdetails, Geheimnisse oder Informationen, die sich zuverlässig und leicht aus dem aktuellen Code ableiten lassen. Ohne neue dauerhafte Erkenntnisse oder Inhalte zur späteren Weiterarbeit ist kein Eintrag nötig.

## Änderungen abschließen

- Erhalte Obsidian-Wikilinks, Frontmatter und die vorhandene Struktur. Beschränke Änderungen auf die betroffenen Abschnitte.
- Lies die geänderten Abschnitte zur Kontrolle erneut und prüfe neu gesetzte lokale Wikilinks auf ein vorhandenes Ziel.
- Committe oder pushe den Vault nur auf ausdrücklichen Wunsch.
- Erwähne in der Abschlussantwort knapp, was und wo im Vault festgehalten wurde. Falls ein erforderlicher Schreibzugriff blockiert ist, benenne den ausstehenden Eintrag, statt eine Speicherung zu behaupten.
