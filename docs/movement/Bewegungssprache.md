# Einführung

Die Integration einer spezialisierten Bewegungssprache in das Pepper Framework stellt einen innovativen Ansatz in der Robotik dar. Dieser Ansatz ist von entscheidender Bedeutung, um die Interaktion mit humanoiden Robotern wie Pepper nicht nur effizienter, sondern auch intuitiver und benutzerfreundlicher zu gestalten. Die Entwicklung einer solchen Sprache erfordert ein tiefes Verständnis sowohl der technischen Möglichkeiten als auch der Grenzen von Pepper sowie der Bedürfnisse der Benutzer.
## 1. Standard-Programmiersprachen und ihre Grenzen 

### G-Code

Struktur und Anwendung: G-Code ist eine der ältesten und am weitesten verbreiteten Programmiersprachen zur Steuerung von Maschinen. Ursprünglich für die CNC-Programmierung konzipiert, bietet G-Code eine Reihe von Befehlen zur Steuerung von Bewegungen entlang von Koordinatenachsen. Ein typisches Beispiel zeigt die direkte Ansteuerung der Achsen:

    G00 X0 Y0 Z0  ; Schnelle Bewegung zur Startposition
    G01 X50      ; Bewege in X-Richtung um 50 Einheiten
    G01 Y25      ; Bewege in Y-Richtung um 25 Einheiten
    G02 X50 Y25 I0 J-25 ; Kreisbogen
    G01 Z-10     ; Senke Werkzeug um 10 Einheiten
    G00 Z0       ; Hebe Werkzeug

Einschränkungen: Obwohl G-Code in der Maschinensteuerung effektiv ist, stößt er bei der Anwendung auf humanoide Roboter wie Pepper an seine Grenzen. Die Sprache ist nicht intuitiv und erfordert ein tiefes technisches Verständnis. Zudem ist sie für die komplexen, dynamischen Bewegungen, die in der humanoiden Robotik erforderlich sind, weniger geeignet.

### ROS, Rapid, KRL

Merkmale: Diese Programmiersprachen bieten fortschrittlichere Funktionen als G-Code, insbesondere im Hinblick auf die Integration von Sensordaten und die Koordination komplexer Bewegungsabläufe.

Herausforderungen: Trotz ihrer Fortschritte bleiben auch diese Sprachen in Bezug auf Benutzerfreundlichkeit und spezifische Anpassung an einzelne Robotermodelle hinter den Anforderungen zurück. Insbesondere die Notwendigkeit, spezielle Treiber und Schnittstellen für jeden Roboter zu entwickeln, kann den Entwicklungsprozess verlangsamen und komplizieren.

## 2. Entwicklung einer eigenen Sprache (DSL)
### Vorteile einer DSL

Die Schaffung einer eigenen domänenspezifischen Sprache (DSL) für das Pepper Framework bietet mehrere Vorteile:

Menschenlesbarkeit und Zugänglichkeit: Eine DSL kann so gestaltet werden, dass sie intuitiv und verständlich ist. Dies erleichtert die Programmierung, insbesondere für Entwickler ohne tiefgehende Erfahrung in der Robotik.

Effizienz in der Entwicklung: Durch die Fokussierung auf spezifische Anforderungen humanoider Roboter ermöglicht eine DSL eine schnellere und präzisere Entwicklung von Bewegungsabläufen.

Erhöhte Wartbarkeit: Eine gut strukturierte DSL ist leichter zu warten und zu aktualisieren, was für die Langlebigkeit des Frameworks entscheidend ist.

Abstraktion von Hardware-Details: Entwickler können sich auf die Logik und das Design der Bewegungsabläufe konzentrieren, ohne sich in die technischen Einzelheiten der Roboterhardware vertiefen zu müssen.

Portabilität und Anpassbarkeit: Eine gut entworfene DSL ermöglicht es, Anweisungen für verschiedene Robotermodelle zu generieren und anzupassen, indem man nur den DSL-Interpreter verändert.

### Beispiel einer DSL für Pepper

Ein praktisches Beispiel einer DSL könnte die folgende Struktur haben, die menschenähnliche Befehle für alltägliche Bewegungen des Roboters verwendet:

    BEGIN_SEQUENCE
      SET POSTURE STANDING
      MOVE FORWARD 3_STEPS
      MOVE BACKWARD 2_STEPS
      LIFT LEFT_ARM 45_DEGREES
      LIFT RIGHT_ARM 45_DEGREES
      GRASP LEFT_HAND
      RELEASE LEFT_HAND
      TURN HEAD LEFT 30_DEGREES
      TURN HEAD RIGHT 30_DEGREES
      SAY "Hello, World!"
    END_SEQUENCE

#### Interpreter: 
Der Kern der DSL liegt in ihrem Interpreter. Dieser übersetzt die hochgradig abstrahierten Befehle in spezifische Steuerbefehle, die für Pepper geeignet sind. Zum Beispiel wird der Befehl MOVE FORWARD 3_STEPS in eine Serie von Anweisungen übersetzt, die die Bewegung der Beine, die Balance und die Ausrichtung des Roboters koordinieren.

#### Fall 1: Eingeschränkte Gelenksteuerung

##### Herausforderung: 
Wenn es nicht möglich ist, die Gelenke von Pepper individuell anzusteuern, muss dies durch vordefinierte Bewegungsabläufe ausgeglichen werden.

##### Lösungsansatz: 
In diesem Szenario konzentriert man sich auf eine Auswahl grundlegender Bewegungen, die dennoch ein hohes Maß an Ausdrucksfähigkeit ermöglichen. Beispielsweise könnte die DSL Befehle wie "Hebe linken Arm auf 45 Grad" oder "Drehe Kopf um 30 Grad nach rechts" enthalten.

#### Fall 2: Individuelle Gelenksteuerung


##### Möglichkeit:
Bei der Fähigkeit zur individuellen Gelenksteuerung eröffnen sich erweiterte Möglichkeiten für die Bewegungssprache.

##### 2.1 Anpassung an aktuelle Positionen: 
Hier könnte die DSL so konzipiert sein, dass sie die aktuelle Position jedes Gelenks berücksichtigt und entsprechend feinabgestimmte Bewegungen ermöglicht.

#### Erweiterung und Anpassung der DSL

Die Anpassungsfähigkeit der DSL ist entscheidend für ihre langfristige Nützlichkeit und Relevanz. Hierbei können folgende Aspekte berücksichtigt werden:

Einbindung neuer Technologien: Die DSL sollte so gestaltet sein, dass sie leicht um neue Technologien und Funktionen erweitert werden kann, zum Beispiel um verbesserte Sensoren oder fortschrittlichere Bewegungssteuerung.
Anpassung an verschiedene Robotermodelle: Die Sprache sollte so flexibel sein, dass sie nicht nur für Pepper, sondern auch für andere humanoide Roboter anpassbar ist. Dies erfordert eine sorgfältige Planung in Bezug auf die Abstraktionsebenen und die modulare Struktur des Interpreters.
Benutzerfeedback und Iteration: Die Entwicklung der DSL sollte ein iterativer Prozess sein, der Benutzerfeedback einbezieht, um die Sprache kontinuierlich zu verbessern und an die Bedürfnisse der Anwender anzupassen.

#### Fazit und Ausblick

Die Entwicklung einer Bewegungssprache für das Pepper Framework bietet ein enormes Potenzial zur Verbesserung der Interaktion und Steuerung humanoider Roboter. Durch die Schaffung einer benutzerfreundlichen, anpassbaren und effizienten DSL eröffnen sich neue Möglichkeiten für dieses Projekt in verschiedenen Bereichen, von der Pflege bis zur Bildung.

Diese Sprache ist nicht nur ein Werkzeug für die technische Steuerung von Robotern, sondern auch ein Medium, das die Grenze zwischen Mensch und Maschine überbrückt. Mit einer intuitiven und ausdrucksstarken Bewegungssprache können Roboter wie Pepper zu wertvollen und interaktiven Partnern in vielen Aspekten des täglichen Lebens werden, ohne ein Hinderniss für Personen ohne technischen Hintergrund zu sein.


## TaskDSL4Pepper und StateDSL4Pepper

researched and found some interesting links:

    https://books.google.at/books?id=IGjKEAAAQBAJ&pg=PA21&lpg=PA21&dq=TaskDSL4Pepper&source=bl&ots=AksIkblKu_&sig=ACfU3U0M1eWEWnjoR8RRkuf-zumq3RQ1bQ&hl=de&sa=X&ved=2ahUKEwjBx67_msOCAxU3_rsIHZyrBJQQ6AF6BAgJEAM#v=onepage&q=TaskDSL4Pepper&f=false

Es handelt sich bei TaskDSL4Pepper um ein Projekt der Universität Rostock. Man findet beinahe nur Wisseneschaftliche Papers, welche meist etwas kosten. Die Relevanz dieser DSL ist angesicht an unser Projekt eher nicht gegeben, da es auf Therapie Umgebungen und UseCases angepasst ist.

Bei TaskDSL4Pepper und StateDSL4Pepper handelt es sich um eine DSL welche auf die Anforderung von Schlaganfall Therapien angepasst ist. Die Umsetzung des Projektes, führte laut Professor Forbig, Leiter des Informatik Instituts der Universität Rostock, zu einigen wie er beschreibt schwierigen Problemen, welche sich wie bei uns Äußerten und 6 Monate zur behebung und der ersten funktionierenden Umgebung benötigte. Noch dazu kommt dass das Projekt in wenigen Bereichen mit unserem sich ähnelt, da sie auf die gezielte Therapie angepasst ist und nicht auf das Beantworten von Fragen angepasst ist.
