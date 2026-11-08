# Quiz-Generator

Eine Lern-App im Browser: Du fügst einen Lerntext ein (oder lädst eine PDF), und Claude erstellt daraus ein Quiz. Danach übst du die Fragen direkt in der App – mit Wiederholungssystem und Statistik.

## Funktionen

- **Quiz aus Text oder PDF** – Text einfügen, Textdatei oder PDF laden (auch per Ziehen und Ablegen), bei PDFs einen Seitenbereich wählen
- **Einstellbar** – 5, 10 oder 20 Fragen; Schwierigkeit leicht, mittel oder schwer
- **Vier Fragetypen** – Multiple Choice, Richtig/Falsch, offene Fragen oder gemischt
- **Offene Fragen** – Claude bewertet deine Antwort mit 0–3 Punkten und gibt Feedback
- **Wiederholen nach dem Leitner-System** – falsche Fragen kommen wieder, bis du sie sicher kannst (5 Stufen)
- **Ordnung** – Quizze nach Fach und Kapitel sortiert, mit Suche
- **Statistik** – Trefferquote pro Fach und Kapitel, die 10 häufigsten Fehler
- **Kostenkontrolle** – Schätzung vor dem Senden, Verbrauch pro Anfrage, Summe pro Tag und gesamt
- **Backup** – alle Daten als JSON-Datei exportieren und wieder importieren
- **Hell- und Dunkelmodus**

## Technik

- Eine einzige Datei: `index.html` (HTML, CSS und JavaScript, ohne Framework, ohne Server)
- Die Fragen erstellt die **Claude-API** von Anthropic (Modell `claude-haiku-5-5`)
- PDFs werden mit **pdf.js** direkt im Browser gelesen – nur der Text geht an Claude, nicht die Datei
- Alle Daten (Quizze, Fortschritt, Statistik, API-Schlüssel) liegen nur im **Speicher deines Browsers** (localStorage). Es gibt keine Datenbank und kein Konto.

## Benutzung

1. App öffnen: online über GitHub Pages oder `index.html` lokal im Browser
2. Einen eigenen **Claude-API-Schlüssel** besorgen: in der [Claude Console](https://console.anthropic.com/) anmelden, Guthaben aufladen und unter „API Keys“ einen Schlüssel erstellen (beginnt mit `sk-ant-`)
3. In der App „Einstellungen“ öffnen, den Schlüssel einfügen und „Schlüssel speichern“ klicken
4. Lerntext einfügen oder PDF laden, Fach/Kapitel, Anzahl, Schwierigkeit und Fragetyp wählen
5. „Quiz erstellen“ klicken und üben

**Zum Schlüssel:** Er wird nur in deinem Browser gespeichert und ausschließlich an `api.anthropic.com` gesendet. Er steht nicht im Code und wird nicht exportiert. Gib deinen Schlüssel niemandem weiter und nutze die App nur auf eigenen Geräten.

## Kosten

Die App selbst ist kostenlos. Jede Anfrage an Claude wird aber über **deinen eigenen API-Schlüssel** abgerechnet.

- Preise für `claude-haiku-5-5`: 0,10 $ pro 1 Million Eingabe-Tokens und 0,50 $ pro 1 Million Ausgabe-Tokens (1 Token ≈ 4 Zeichen)
- Ein Quiz mit 10 Fragen aus einem normalen Kapitel kostet meist **weniger als 1 Cent**
- Achtung: Ab 100.000 Eingabe-Tokens (ca. 400.000 Zeichen) gilt für die ganze Anfrage der **5-fache Preis**. Die App warnt vorher und fragt nach.
- Das Bewerten einer offenen Antwort ist eine eigene, sehr kleine Anfrage

Die Kostenanzeige in der App ist eine Schätzung. Den genauen Verbrauch siehst du in der Claude Console. Tipp: Dort kannst du ein monatliches Ausgabenlimit festlegen.
