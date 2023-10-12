12.10.2023

# First Research
## Tech Stack
### Database:
Postgresql

Vorteile:
- Gratis
- Schnell

Nachteile:
- Ressourcen schwerer als SQLite

### Backend:
Asp.Net Core
Python

Vorteile:
- C#
- Haslinger Support
- Minimales Vorwissen unserer Seits

Nachteile
- Langsamer als Quarkus

## AI Research
### Wofür brauchen wir AI?

- Welche Antwort brauchen wir wann?
- Welche Antwort ist am besten?
- Was hat der User gesagt?
  
###

- Question Answering AI
- Speech-to-Text AI
- External AIs (ChatGPT, DeepL, ...)

### Wie werden wir AI nutzten?
#### Question Answering AI (Layering System)

Wir wollen drei Layers machen für die Fragen beantwortungen:

1. Fragen die sich unsere AI zutraut (Known questions)
2. Fragen die man mit Hilfe von externen Sourcen (Google Maps, ChatGPT, ...) beantworten kann
3. Wenn Layer 1 und 2 nicht funktioniert haben, dann soll es möglich sein einen Live Chat mit einer phyisichen Person zu starten

#### External AI

Hugging Face: Get Speech emotion AI
OpenAI: https://platform.openai.com/overview


## Backend Research

Wie haben wir die Komponenten geplant?

[Komponentendiagramm](./componentDiagram.puml)

Der Nutzer hat 2 verschiedene Möglichkeiten mit unserem System zu
interagieren:

1. Datenerhebungstool
Das Datenerhebungstool soll eine simple Nutzeroberfläche für den Besitzer des Systems darstellen, in der er Fragen vordefinieren oder
bewerten kann. Zusätzlich wird es wahrscheinlich möglich sein, verschiedenste Statistiken anzusehen.

2. Pepper
Der Pepper selbst wird die Fragen von Nutzern beantworten, welche
diese dann an dem Bildschirm bewerten können.

Zusammen kommt das ganze dann in unserem Backend. Hier werden Fragen, Antworten und Feedback in einer Datenbank gespeichert. In einem vom Admin definierbarem Zyklus, wird in unserem AI Trainingstool basierend auf diesen Informationen ein neues, verbessertes AI Model erstellt. Dieses wird dann in unsere Backend geladen. Wenn jetzt eine neue Frage gestellt wird, sendet der Pepper die Daten an den Server, welcher die Antwort als Text zurrück schickt. 