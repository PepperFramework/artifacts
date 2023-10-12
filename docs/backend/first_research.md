10.10.2023

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

- Question Answering AI
- Speech-to-Text AI
- External AIs (ChatGPT, DeepL, ...)

### Wie werden wir AI nutzten?
#### Layering System

Wir wollen drei Layers machen für die Fragen beantwortungen:

1. Fragen die sich unsere AI zutraut (Known questions)
2. Fragen die man mit Hilfe von externen Sourcen (Google Maps, ChatGPT, ...) beantworten kann
3. Wenn Layer 1 und 2 nicht funktioniert haben, dann soll es möglich sein einen Live Chat mit einer phyisichen Person zu starten

## Backend Research

Wie haben wir die Komponenten geplant?

[Komponentendiagramm](./componentDiagram.puml)
