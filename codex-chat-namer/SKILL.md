---
name: codex-chat-namer
description: Pflegt den Titel eines Codex-Chats anhand seines prägenden Hauptthemas. In normalen Codex-Chats verwenden, sobald ein belastbares Ziel erkennbar wird, und bei einem klaren, dauerhaften Themenwechsel erneut abgleichen; auch für ausdrücklich gewünschte Titel und Umbenennungen.
---

# Codex Chat Namer

Benenne den aktuellen Chat nach seinem prägenden Hauptthema, damit der Nutzer ihn später wiederfindet. Gewichte den bisherigen Gesprächsverlauf und die darin geleistete Arbeit; die jüngste Nachricht allein bestimmt den Titel nicht.

## Automatischer Abgleich

Prüfe nach einer Nutzernachricht, ob ein belastbares Hauptziel erkennbar ist:

- Hat der Chat noch keinen von dir passend gesetzten Titel, setze ihn, sobald Ergebnis, Problem oder Vorhaben konkret genug ist.
- Benenne den Chat erneut, wenn der Nutzer das Hauptziel ausdrücklich verwirft oder ersetzt, ein unabhängiges Vorhaben über mehrere Gesprächsschritte zum neuen Schwerpunkt wird oder eine zunächst vage Aufgabe so konkretisiert wird, dass der bisherige Titel irreführend geworden ist. Je stärker das bisherige Thema den Chat geprägt hat, desto klarer muss der Wechsel sein.
- Behalte den Titel bei Rückfragen, Rückblicken, Learnings, nächsten Schritten zum bisherigen Vorhaben und kurzen Themenabstechern bei. Auch ein abgeschlossenes Ziel bleibt für die Wiederauffindbarkeit relevant. Eine einzelne neue Frage oder „Wie machen wir weiter?“ belegt noch keinen dauerhaften Themenwechsel.
- Behalte den Titel ebenfalls bei, wenn sich nur Lösungsweg, Zwischenschritt, Status, technische Einzelheit oder Formulierung ändert. Vermeide Umbenennungen zwischen bloßen Synonymen.
- Ist unklar, ob ein Abstecher oder ein dauerhafter Wechsel vorliegt, behalte den bestehenden passenden Titel bei. Bei einem tatsächlichen Wechsel wähle einen Titel, der weiterhin prägenden Projekt- oder Ticketkontext erhält, soweit er zum neuen Schwerpunkt gehört.
- Warte ab, solange noch kein stabiles Ziel erkennbar ist. Frage nicht allein wegen des Titels nach.

Rufe für den aktuellen Chat `set_thread_title` mit dem gewählten Titel auf und lasse `threadId` weg. Führe diese Pflege ohne Rückfrage und möglichst unaufdringlich aus; mache sie nicht zum Hauptinhalt der Antwort. Wenn das Werkzeug fehlt, überspringe die automatische Umbenennung ohne die eigentliche Aufgabe zu stören.

## Titel bilden

- Verwende die Sprache des Nutzers beziehungsweise die vorherrschende Sprache des Chats.
- Formuliere möglichst 3 bis 7 Wörter und bleibe unter 60 Zeichen.
- Nenne das konkrete Ergebnis, Artefakt oder Problem. Übernimm wichtige Projekt-, Produkt- und Eigennamen aus dem Chat.
- Formuliere so, dass der Titel in einer Liste ähnlicher Chats unterscheidbar bleibt.
- Vermeide generische Titel wie „Hilfe“, „Frage“, „Neuer Chat“, „Projekt bearbeiten“ oder „Problem lösen“.
- Verwende keine Emojis, Anführungszeichen, abschließenden Satzzeichen oder Datumsangaben, sofern sie nicht ausdrücklich gewünscht beziehungsweise fachlich entscheidend sind.
- Erfinde keine Details, die im Chat nicht belegt sind.

## Explizite Titelwünsche

Wenn der Nutzer ausdrücklich um die Umbenennung bittet, nenne nach erfolgreicher Aktion den exakten neuen Titel. Wenn er nur Vorschläge verlangt, liefere 3 bis 5 deutlich unterschiedliche Titel und ändere den Chat nicht.

Wenn der Nutzer einen anderen Chat eindeutig bezeichnet, ermittle dessen ID mit den Codex-Thread-Werkzeugen und rufe anschließend `set_thread_title` für genau diese ID auf. Benenne keinen anderen Chat um, solange das Ziel nicht eindeutig ist.
