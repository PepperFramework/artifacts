3.11.2023

# Backend Research:
Asp.Net Core
Python

Vorteile:
- C#
- Haslinger Support
- Minimales Vorwissen unserer Seits

Nachteile
- Langsamer als Quarkus

Wie haben wir die Komponenten geplant?

[Komponentendiagramm](./componentDiagram.puml)

Der Nutzer hat 2 verschiedene Möglichkeiten mit unserem System zu
interagieren:

1. Datenerhebungstool
Das Datenerhebungstool soll eine simple Nutzeroberfläche für den Besitzer des Systems darstellen, in der er Fragen vordefinieren oder
bewerten kann. Zusätzlich wird es wahrscheinlich möglich sein, verschiedenste Statistiken anzusehen.

1. Pepper
Der Pepper selbst wird die Fragen von Nutzern beantworten, welche
diese dann an dem Bildschirm bewerten können.

Zusammen kommt das ganze dann in unserem Backend. Hier werden Fragen, Antworten und Feedback in einer Datenbank gespeichert. In einem vom Admin definierbarem Zyklus, wird in unserem AI Trainingstool basierend auf diesen Informationen ein neues, verbessertes AI Model erstellt. Dieses wird dann in unsere Backend geladen. Wenn jetzt eine neue Frage gestellt wird, sendet der Pepper die Daten an den Server, welcher die Antwort als Text zurrück schickt. 