# Komponentendiagramm:

![alt text](image.png)
### Plantuml code:
@startuml
skinparam componentStyle rectangle

package "Hotel" {
[User]
}

package "System" {

    [AI API GPT] --> [Backend] : provides responce
    [Backend] --> [SLM] : sends prompt
    [Backend] --> [Good Looking Face (frontend)] : sends responce
    [Good Looking Face (frontend)] --> [Backend] : sends user input
    [Good Looking Face (frontend)] --> [TTS] : uses
    [TTS] --> [Good Looking Face (frontend)] : data
    [TTS] ..> [User] : provides spoken feedback
    [SLM] --> [AI API GPT] : sends prompts with aditional info
    [STT] --> [Good Looking Face (frontend)] : sends input
}

package "Hotel" {
[User] ..> [STT] : speaks with
[User] ..> [Good Looking Face (frontend)] : looks at
}

@enduml
### Erklärung:

#### System-Komponenten:

  + **AI API GPT:**
    Diese Komponente steht für ein fortschrittliches KI-Modell, das in der Lage ist, komplexe Textverarbeitungsaufgaben auszuführen.
Es liefert Antworten auf Eingaben, die es erhält, und sendet diese Antworten an das Backend.
Backend:

  + **Backend:**
    Das Backend fungiert als zentrale Komponente, die die Eingaben vom Frontend (Good Looking Face) verarbeitet und diese Anfragen weiterleitet.
Es empfängt Anfragen vom Good Looking Face, sendet diese an das SLM zur weiteren Bearbeitung und gibt die fertige Antwort an das Good Looking Face zurück.
Zudem nimmt das Backend die Antwort von AI API GPT entgegen und nutzt SLM, um die Informationen für spezifische Anfragen zu verfeinern.
SLM (Small Language Model):

  + **SLM:**
    Das SLM ist ein kleineres Sprachmodell, das vom Backend angesprochen wird.
Es verfeinert und ergänzt die Anfragen an die AI API GPT, indem es zusätzliche Informationen liefert, um die Qualität der Antworten zu verbessern.
Es sendet diese angereicherten Anfragen dann zurück an die AI API GPT.
  + **Good Looking Face (Frontend):**
    Dies ist die Benutzeroberfläche, mit der der User interagiert.
Es empfängt Benutzereingaben vom STT und leitet diese an das Backend weiter.
Sobald eine Antwort vom Backend erhalten wird, kann diese Antwort in Textform dem TTS übergeben werden, um sie in Sprache umzuwandeln.
Damit bietet die Benutzeroberfläche eine benutzerfreundliche Darstellung der KI-Funktionalitäten und eine Sprachinteraktion.
  + **TTS (Text-to-Speech):**
  TTS konvertiert Textantworten in gesprochene Sprache.
Es wird vom Face aufgerufen, wenn eine Sprachausgabe der Antworten benötigt wird, und liefert Feedback an das Frontend zurück.
#### Hotel-Komponenten:


  + **User:**
    Die User-Komponente repräsentiert den Benutzer des Systems.
Der Benutzer interagiert mit dem Good Looking Frontend, indem er spracheingaben tätigt, die dann weiterverarbeitet werden.