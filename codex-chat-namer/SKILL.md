---
name: codex-chat-namer
description: Pflegt den Titel eines Codex-Chats automatisch anhand seines aktuellen Hauptziels. In normalen Codex-Chats verwenden, sobald ein belastbares Ziel erkennbar wird, und erneut prüfen, wenn der Nutzer das Hauptziel ersetzt, präzisiert oder zu einem anderen Vorhaben wechselt; auch für ausdrücklich gewünschte Titel und Umbenennungen.
---

# Codex Chat Namer

Halte den Titel des aktuellen Chats synchron mit dem tatsächlichen Hauptziel. Berücksichtige den relevanten Verlauf und priorisiere die jüngste noch aktive Aufgabe.

## Automatischer Abgleich

Prüfe nach einer Nutzernachricht, ob ein belastbares Hauptziel erkennbar ist:

- Hat der Chat noch keinen von dir passend gesetzten Titel, setze ihn, sobald Ergebnis, Problem oder Vorhaben konkret genug ist.
- Benenne den Chat erneut, wenn der Nutzer das bisherige Hauptziel verwirft oder ersetzt, zu einem unabhängigen Vorhaben wechselt oder eine zunächst vage Aufgabe so konkretisiert, dass der bisherige Titel irreführend geworden ist.
- Behalte den Titel bei, wenn sich nur Lösungsweg, Zwischenschritt, Status, technische Einzelheit oder Formulierung ändert. Vermeide Umbenennungen zwischen bloßen Synonymen.
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
