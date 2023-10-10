**Pepper Besprechung**

- QISDK (Pepper SDK) für Code Samples, Prinzipien, Getting Started etc.
- Discord Link → Fabo
- Ubuntu verwenden
- Plugin NICHT mehr im Marketplace (anderer download link als zip auf webstite)
  - Settings  → Install Plugin from Disk
- Einführung unter Principles
- Gruber Leitner Tutorial
- Eigene Dokumentation zu unseren Fragen? (Stackoverflow schauen, Fragen / Repos!)
- Skeletprojekt → Fabo (verwenden wir das?, jetpack compose Oder xml?)
- für ui emulator, für bewegungen animator (in pepper sdk integriert, sonst als xml)
- Kotlin grundkurs?
- OnPepper funktion (callback fkt) greift auf onpepper property zu (wenn true run und sonst weiter), für emulator das animaition oder so nicht crasht
- Test Projekt (mit Buttons, zb: Say Hello → onclick = pepper macht das)
- Github

**What are we doing?**

- Andere Gruppen finden, zusammenfassen was die machen und dieses Jahr noch vor haben
- Unsere „Lücke“ (Chatbot funktion mit reden und so) erläutern
- Lehrern zeigen

- **Was kann der Pepper?**
  - Bewegen (nicht benutzen)
  - Sprechen (ohne zuhören)
  - Zuhören (geht nicht)
  - Spiele Spielen (Tablet)
  - Touch

- **Wer macht alles Pepper?**
- 5ahif – Seniorenzentrum (Bewegungassisten, Menüplan)
  - Geplannt: Mitmachspiel Builder
  - Umgesetzt: Tanzen, Spiele spielen
  - Wär gut: Zuhören, Gesichtserkennung und Reden (AI generierte antworten) könnnen
- 5chif – Blutspendeassistent
  - Geplannt: Begrüßung, Quiz, etc.
  - Wär gut: Herumfahren
- 4chif – wir
- 4ahif – Tadeof
  - Geplannt: Tanzkoreografie, Feedback, Minispiele (nach tadeof: Seniorenzentrum weiter)
  - Umgesetzt: /
  - Wär gut: Mit Sprache Feedback
- 3ahif – Kein Pepper




- **Unser Plan:**
  - Problem:
  - Es gibt für den Pepper noch keine (gute) Libary, welche ein ordentliche Spracherkennung, Verarbeitung und Ausgabe ermöglicht. Zusätzlich wäre es noch eine Idee die Fragen mithilfe von Gesichtserkennung zu spezifisieren. Wir wollen für jeden usecase ein AI model, anhand von vordefinierten Fragen erstellen, welches dann durch unser schon definiertes Layering System lernt:

`		`3 Layers sorted trough AI:

`		`1. Already known answer

`		`2. Other Source (ChatGPT, Google Maps, etc.)

`		`3. Connection to human (via chat?)

`		`The AI learns from layer 2 and 3.


`		`Zusätzliche Domäne für Fragen storage


2 Schritte:

- 1. Framework input output domain sprache
  - Jonas
  - Paul
- 2. Einfache API für Bewegungen mit UI
  - Fabian
  - Leon
- 3. Full Stack
  - Felix
