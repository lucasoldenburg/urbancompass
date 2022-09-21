# Projektdokumentation Urban Compass

(TODO)

-   Inhaltsverzeichnis (als letztes)
-   Bilder in Ordner bilder doku laden
-   Bilder Referenzieren in Markdown referenzieren
-   Alles auf Projektdoku übertragen
-   Entscheiden, welche Kapitel für technische Doku wirklich relevant
    -   Kapitel Fachkonzeption können mm nach raus oder in einen Satz gepackt werden
-   Links einfügen
-   Logo?

## Einleitung und Hintergrund

Test test

## Projektziel

### Proof of Concept Grüne-Welle-Assistent mit ESP32

Im Rahmen des „Leetzenflow“-Projekts (Link) entwickelte das Institut für Verkehrswissenschaften der WWU Münster im Auftrag der Stadt Münster einen prototypischen Grüne-Welle-Assistenten. Dieser unterstützt Fahrradfahrende dabei, die eigene Geschwindigkeit anzupassen, um grüne Ampelphasen optimal zu nutzen und somit an weniger Ampeln anhalten zu müssen. Ziel dieses Projekts ist die Erarbeitung eines Proof of Concept (PoC), das belegt, dass der Grüne-Welle-Assistent ebenso mit abweichender Hardware unter Verwendung eines ESP32 als Mirkocontroller umgesetzt werden kann.

### Urban Compass

Das zweite Projektziel besteht darin, die im Rahmen des PoC entwickelte Hardwarelösung als Grundlage zu verwenden, um eine andere Anzeige als den Ampelstatus auf den LEDs als „Urban Compass“ zu realisieren. Konkret handelt es sich dabei um Infotainment-Inhalte, die auf den LEDs angezeigt werden können. Diese Inhalte sollen dabei das Potenzial haben, Fahrradfahrende bei der Navigation durch die Stadt zu unterstützen und darüber hinaus eine positive psychologische Wirkung auf das Fahrerlebnis zu erzeugen. Die Inhalte werden im Rahmen des Projekts in einem fachlichen Konzept entwickelt und prototypisch als Anzeige auf den LEDs umgesetzt.

## Hardware

Die folgende Tabelle zeigt alle im Projekt verwendeten Hardwarekomponenten inklusive Shopping-Links und Kostenaufstellung.

| **Komponente**         | **Produktname**                                         | **Hersteller**          | **Link**                                                                                                                                                             | **Preis**         |
|------------------------|---------------------------------------------------------|-------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------|
| LED 1                  | 64x32 RGB LED MATRIX – 5MM Pitch                        | Adafruit Industries LLC | https://www.digikey.de/de/products/detail/adafruit-industries-llc/2277/7035035                                                                                       | 59,99 €           |
| LED 2                  | 32x32 RGB LED MATRIX – 5MM Pitch                        | Adafruit Industries LLC | https://www.digikey.de/de/products/detail/adafruit-industries-llc/2026/7035028?s=N4IgTCBcDaIIwFYwA4C0Y6NQOQCIgF0BfIA                                                 | 41,98 €           |
| Microcontroller        | ESP32WROOM32E                                           | Espressif Systems       | https://www.digikey.de/de/products/detail/espressif-systems/ESP32-DEVKITC-32E/12091810                                                                               | 12,00 €           |
| Jumper-Kabel           | Jumper Wire Kabel 40 STK. je 20 cm F2F Female to Female | AZ-Delivery             | https://www.kaufland.de/product/342455919/?utm_source=shopping&utm_medium=non-paid&utm_campaign=pricecomparison&sid=42345840                                         | 3,99 € (40 Stück) |
| Netzteil               | AC-Adapter (Output: 5V, 3A)                             | Leicke                  | https://www.otto.de/p/leicke-ull-netzteil-15w-5v-3a-netzteil-besonders-leicht-kurzschluss-ueberspannungs-und-ueberhitzungsschutz-S0C1G0DZ/\#variationId=S0C1G0DZBSMT | 8,99 €            |
| Netzteil-Adapter       | Sara fragen                                             | Platzhalter             | Platzhalter                                                                                                                                                          | Platzhalter       |
| Micro-USB-Kabel        | Micro-USB-Kabel                                         | Liour                   | https://amzn.to/3qPDoVF                                                                                                                                              | 4,99 €            |
| Stromkabel LED         | Sara                                                    | Platzhalter             | Platzhalter                                                                                                                                                          | Platzhalter       |
| HUB75-Verbindungskabel | Sara                                                    | Platzhalte              | Platzhalter                                                                                                                                                          | Platzhalter       |
| DC-Buchse              | DC Buchse Stecker 5,5 x 2,1mm                           | LitaElek                | https://www.amazon.de/dp/B019HAC6V4/                                                                                                                                 | 6,49 € (5 Paar)   |
| Platzhalter            | Platzhalter                                             | Platzhalter             | Platzhalter                                                                                                                                                          | Summe: ???        |

Zusätzlich wurde folgendes Werkzeug verwendet:

-   3D-Drucker (wir haben einen Anycubic Mega X Drucker benutzt (https://de.anycubic.com/products/mega-x?_pos=14&_sid=d5e44558a&_ss=r))
-   Seitenschneider
-   Lötkolben
-   Schrumpfschlauch

Die genaue Beschreibung der Zusammensetzung der Komponenten findet sich in Kapitel Hardware-Inbetriebnahme

## Fachkonzeption

### Grüne-Welle-Assistent

Der Grüne-Welle-Assistent stellt, wie bereits in Kapitel 1.1 beschrieben ein Produkt dar, das aus dem „Leetzenflow“-Projekt der Stadt Münster heraus entstanden ist. Er soll Fahrradfahrende, die sich einer Kreuzung mit Ampelanlage nähern, mit Informationen bzgl. der aktuellen Ampelphase versorgen. Ziel dessen ist, dass die Fahrradfahrenden ihre Geschwindigkeit auf Basis dieser Information so regulieren können, dass sie an der aufkommenden Ampel nicht anhalten sowie absteigen müssen und so im „flow“ durch die Stadt kommen.

Realisiert wurde der Grüne Welle Assistent durch eine digitale Anzeige (zwei verbundene LEDs) vor einer aufkommenden Straßenkreuzung, die anhand eines Farbverlaufs die verbleibende Dauer der aktuellen Ampelphase darstellt. Dabei wird bei einer grünen Ampelphase ein grüner Balken angezeigt, der mit abnehmender Grün-Phase immer kleiner wird. Wechselt die Ampel auf „Rot“ wechselt analog dazu auch die LED-Anzeige auf einen roten Balken, der mit abnehmender Rot-Phase immer kleiner wird. Zusätzlich während einer Rot-Phase ein statisches und bei einer Grün-Phase ein sich bewegendes Fahrrad-Symbol angezeigt. Dies symbolisiert den Fahrradfahrenden, dass sie sich von der Anzeige angesprochen fühlen sollen und verdeutlicht zudem, ob Fahrradfahrende an der aufkommenden Ampel aktuell anhalten müssen oder fahren können.

[BILD LEEZENFLOW]

Quelle: <https://smartcity.ms/leezenflow/>

Die vollständige fachliche Beschreibung des Projekts kann unter <https://smartcity.ms/leezenflow/> eingesehen werden. Bei dem Projekt handelt es sich zudem über ein Open-Source-Projekt, bei dem alle Vorgehensweisen und Komponenten der Implementierung frei öffentlich verfügbar gemacht wurden. Diese können unter <https://github.com/bCyberGmbH/leezenflow-doku> abgerufen werden. Die drei relevantesten verwendeten Komponenten zur Anzeige des Ampelstatus umfassen dabei:

| **Komponente** | **Produktname**                                 | **Hersteller**          | **Link**                                                                                                                                                                                                                                 |
|----------------|-------------------------------------------------|-------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| LED 1          | 64x32 RGB LED MATRIX – 5MM Pitch                | Adafruit Industries LLC | https://www.digikey.de/de/products/detail/adafruit-industries-llc/2277/7035035                                                                                                                                                           |
| LED 2          | 32x32 RGB LED MATRIX – 5MM Pitch                | Adafruit Industries LLC | https://www.digikey.de/de/products/detail/adafruit-industries-llc/2026/7035028?s=N4IgTCBcDaIIwFYwA4C0Y6NQOQCIgF0BfIA                                                                                                                     |
| Raspberry Pi   | Raspberry 1373331 Pi 3 Modell B+ Mainboard, 1GB | Raspberry               | https://www.amazon.de/Raspberry-1373331-Modell-Mainboard-1GB/dp/B07BFH96M3/ref=as_li_ss_tl?dchild=1&keywords=raspberry+pi+3&qid=1625566866&sr=8-4&th=1&linkCode=sl1&tag=bcyber-21&linkId=62525177043a4efc0c5861fe447f3e6c&language=de_DE |

Ziel dieses Projekts ist die ist die technische Nachstellung des Projekts bzw. der Anzeige des Ampelstatus. Dabei wird anstatt der oben aufgeführten Raspberry Pi Komponente jedoch ein ESP32 als Microcontroller eingesetzt, wobei die gleichen LED-Komponenten verwendet werden (siehe auch Kapitel xx.xx Hardware). Das erste Projektziel beinhaltet also die Entwicklung eines Proof of Concept (PoC), das zeigen soll, dass die Anzeige des Ampelstatus auch unter Verwendung abweichender Hardware (ESP32) möglich ist.

Der ESP32 ist im Gegensatz zum Raspberry Pi deutlich günstiger und verfügt zum Zeitpunkt des Projekts über eine höhere Verfügbarkeit, was die Implementierung des Grüne Welle Assistenten skalierbarer machen würde. Im Vergleich zum Raspberry Pi verfügt der ESP32 jedoch über eine geringere Performanz, weshalb innerhalb des PoC geprüft werden soll, ob eine Umsetzung unter diesem Nachteil trotzdem möglich ist. Eine Verbindung zur Ampelanlage, wie sie im Leetzenflow-Projekt umgesetzt wurde, ist dabei noch nicht vorgesehen.

Für die Umsetzung des PoC innerhalb dieses Projekts wird dabei folgendes Abnahmeszenario definiert:

1.  Genereller Nachweis der Betriebsfähigkeit der verfügbaren Hardware-Komponenten (siehe Kapitel xx).
2.  Konstante Anzeige eines statischen Fahrrad-Symbols auf der LED-Anzeige.
3.  Anzeige eines grünfarbigen Balkens auf der LED-Anzeige, der mit der Zeit in konstanter Geschwindigkeit abnimmt bzw. sich verkleinert und schließlich vollends verschwindet.
4.  Automatischer Wechsel der Anzeige auf einen rotfarbigen Balken, sobald der grünfarbige Balken komplett ausgeblendet ist.
5.  Anzeige des rotfarbigen Balkens auf der LED-Anzeige, der ebenfalls mit der Zeit in konstanter Geschwindigkeit abnimmt bzw. sich verkleinert und schließlich vollends verschwindet.
6.  Erneuter automatischer Wechsel der Anzeige auf einen grünfarbigen Balken, sobald der rotfarbige Balken komplett ausgeblendet ist.

Gelingt es zum Ende des Projekts, das oberhalb beschriebene bzw. geplante Szenario unter Einsatz der in Kapitel X.X aufgeführten Hardware-Komponenten zu realisieren, gilt das PoC als erfolgreich umgesetzt.

### Urban Compass

In diesem Kapitel werden die auf dem Urban Compass anzuzeigenden Inhalte, deren Gestaltung sowie die angestrebte Nutzung des Urban Compass aus Sicht eines Fahrradfahrenden beschrieben.

#### LED-Inhalte

Hauptziel der Anzeige von Infotainment-Inhalten ist in erster Linie, das Fahrerlebnis von Fahrradfahrenden positiv zu beeinflussen, indem auf den LEDs verschiedene Informationen angezeigt werden. Einerseits soll dabei die Navigation durch die Stadt erleichtert werden mit dem Ziel, dass Fahrradfahrende nicht anhalten bzw. nicht vom Fahrrad absteigen müssen, um sich über den weiteren Weg zu informieren. Dies ist insbesondere in Verbindung mit dem Grüne-Welle-Assistenten sinnvoll, der ebenfalls das Ziel verfolgt, Fahrradfahrenden einen guten „Flow“ im Verkehrsfluss zu ermöglichen. Zum anderen sollen die angezeigten Informationen dazu anregen, die Stadt und ihre Sehenswürdigkeiten besser kennen zu lernen und Menschen zur Entschleunigung des Alltags zu bewegen.

Für die Identifikation der anzuzeigenden Informationen wurde ein Brainstorming-Teamworkshop durchgeführt, in dem acht verschiedene Kategorien von Informationen bestimmt wurden, die für die Anzeige auf der LED sinnvoll und geeignet wären:

| **\#** | **Kategorie**         | **Beschreibung / Inhalt**                                                                                                                            | **Nutzen**                                                                                                                                                                                                                                                                          |
|--------|-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1      | Bezirke               | Stadtbezirke wie z.B. „Friedrichshain“, „Kreuzberg“, etc.                                                                                            | Ermöglichung grober Orientierung für Fahrradfahrende, damit diese angenehmer durch die Stadt navigieren können und dabei weniger auf Navigationsdienste / Karten zurückgreifen müssen.                                                                                              |
| 2      | ÖPNV                  | Zentrale Linien des öffentlichen Personennahverkehrs wie z.B. „U5“, „S41/S42“, etc.                                                                  | Ermöglichung grober Orientierung analog zu „1“, zusätzlich Förderung des multimodalen Verkehrsverhaltens von Fahrradfahrenden. Außerdem nützlich für Fahrradfahrende, um bei plötzlich auftretenden schlechten Wetterverhältnissen auf die öffentlichen Verkehrsmittel zu wechseln. |
| 3      | Kieze                 | Bekannte Stadtkieze wie z.B. „Bergmannkiez“, „Wrangelkiez“, etc.                                                                                     | Ermöglichung grober Orientierung analog zu „1“, zusätzlich Ermöglichung der Erkundung des Stadtbildes für Fahrradfahrende.                                                                                                                                                          |
| 4      | Plätze                | Bekannte Stadtplätze wie z.B. „Hermannplatz“, „Moritzplatz“, etc.                                                                                    | Ermöglichung grober Orientierung analog zu „1“, zusätzlich Ermöglichung der Erkundung des Stadtbildes für Fahrradfahrende.                                                                                                                                                          |
| 5      | Sehenswürdigkeiten    | Bekannte Sehenswürdigkeiten wie Gebäude, Denkmale, Brücken, Museen, etc. wie z.B. „Checkpoint Charlie“, „East Side Gallery“, „Jüdisches Museum“ etc. | Ermöglichung grober Orientierung analog zu „1“, zusätzlich Ermöglichung der Erkundung des Stadtbildes für Fahrradfahrende.                                                                                                                                                          |
| 6      | Freizeitmöglichkeiten | Diverse Arten von öffentlichen Freizeiteinrichtungen wie z.B. Schwimmbäder, Kinos, Theater, etc.                                                     | Ermöglichung der Erkundung des Stadtbildes für Fahrradfahrende.                                                                                                                                                                                                                     |
| 7      | Parks & Seen          | Parkanlagen, z.B. „Viktoriapark“, „Görlitzer Park“, „Plötzensee“, etc.                                                                               | Ermöglichung grober Orientierung analog zu „1“, zusätzlich Anregung von Fahrradfahrenden zur vermehrten Nutzung von Grünflächen für die Förderung psychischer Gesundheit.                                                                                                           |
| 8      | Uhrzeit               | Anzeige der aktuellen Uhrzeit.                                                                                                                       | Ermöglichung zeitlicher Orientierung von Fahrradfahrenden, um Navigation ggf. anzupassen oder neue Ziele bzw. Zwischenziele einzuplanen.                                                                                                                                            |

Um die Relevanz der einzelnen Informationskategorien für Fahrradfahrende im Einzelnen zu bewerten und eine finale Auswahl zu treffen, wird an dieser Stelle eine weitere Befragung von Radfahrern im Rahmen eines zukünftigen Umsetzungsprojekts empfohlen. Aus zeitlichen Gründen wird dies in diesem Projekt nicht durchgeführt und stattdessen die drei Kategorien „Bezirke“, „Sehenswürdigkeiten“, „ÖPNV“ und „Uhrzeit“ exemplarisch ausgewählt.

Zusätzlich zu der Anzeige der Elemente (z.B. „Friedrichshain“, „Fernsehturm“, etc.) soll hinter diesen eine Anzeige der Richtung erfolgen, die ein Fahrradfahrender ab der nächsten Kreuzung einschlagen soll, um sich in die Richtung des jeweiligen Elements zu begeben. Für die Richtungsanzeige werden dabei fünf Pfeilarten definiert:

[Pfeile]

Die jeweiligen Kategorien inkl. der Richtungspfeile sollen dabei immer im Wechsel als Dauerschleife angezeigt werden. Dies bedeutet, dass nach der Anzeige einer Kategorie für einige Sekunden die nächste Kategorie auf der LED angezeigt werden soll und dieser Vorgang kontinuierlich wiederholt wird. Die genaue Zeitdauer für die Anzeige einer Kategorie wird dabei in diesem Projekt auf fünf Sekunden festgelegt, da dies für Test- & Demonstrationszwecke einen guten Wert darstellt. Für die Umsetzung sollte nach der Bestimmung der finalen Kategorien eine Anzeigedauer gewählt werden, bei der mit einer durchschnittlichen Fahrgeschwindigkeit von Fahrradfahrenden alle Kategorien während der Fahrt erkannt und wahrgenommen werden können.

Als weitere LED-Inhalte kam im Projektverlauf zudem die Idee auf, passende Icons zu den verschiedenen Kategorien zu definieren und auf der LED-Matrix anzuzeigen. Dies könnte für Fahrradfahrende den Mehrwert schaffen, die angezeigten Informationen schneller und besser einordnen zu können. Aus zeitlichen Gründen wird darauf im Rahmen dieses Projekts bei der Umsetzung verzichtet.

#### Konzeptskizzen

Als Grundlage für die Umsetzung des Urban Compass wurden Konzeptskizzen entwickelt, die sich hinsichtlich der Gestaltung an denen des Reallabor Radbahn orientieren. Die Konzeptskizzen wurden mit PowerPoint und dem Online-Tool Pixilart (https://www.pixilart.com) erstellt. Für die Erstellung der Bilder der in Kapitel X.X konzeptionierten LED-Inhalte wurde Pixilart ausgewählt, weil es sehr einfach und schnell ermöglicht, ein Bild mit der gleichen Auflösung wie die der LED-Matrix zu erstellen. Diese können anschließend in verschiedenen Bildgrößen exportiert werden. Anschließend wurden die erstellten Bilder der LED-Inhalte mit PowerPoint in die Fotos von der Radbahn eingesetzt, um die Konzeptskizzen zu erstellen, die in den folgenden Unterkapiteln dargestellt werden. Darüber hinaus wurden erste Logos entworfen, die zur Bewerbung und Gestaltung des finalen Produkts eingesetzt werden können.

[Bilder der Konzepte + Beschriftung/Beschreibung]

#### Storyboard

Kann raus

## Projektvorgehen

### Hardware-Inbetriebnahme

[Bilder] + Beschriftung

### Grüne-Welle-Assistent

### Urban Compass

### Kastenbau

## Projektergebnis

## Ausblick

In Bezug auf den urban compass wurden im Verlauf der prototypischen Umsetzung bereits einige offene Aspekte und Optimierungspotenziale identifiziert, die im Folgenden aufgeführt werden:

-   Optimierung der Anzeige & Inhalte für diese LED-Matrizen:
    -   Identifikation weiterer Informationskategorien (Vgl. Kapitel X.X) und Bestimmung der relevantesten Kategorien. Umsetzung ggf. über Befragung von Fahrradfahrenden, Sichtung von Studien und durch den Einsatz interdisziplinärer Teams (z.B. Psychologen, Stadtplaner, Designer, etc.).
    -   Hinzufügen von sprechenden Icons, sodass die angezeigten Informationen von Fahrradfahrenden besser eingeordnet werden können.
    -   Je nach Standort eines urban compass Angabe von Kilometern für die Distanz zu Orten wie Bezirken oder Sehenswürdigkeiten und Angabe von Minuten für nächste Anbindungen des ÖPNV.
    -   Ermittlung der optimalen Anzeigedauer je Kategorie über die durchschnittliche Geschwindigkeit der Fahrradfahrenden.
-   Weitere LED-Anzeige in Außenrichtung der Radbahn: Gegebenenfalls wäre die Umsetzung einer zweiten Anzeige sinnvoll, die in die Außenrichtung der Radbahn zeigt. Auf dieser könnten andere Infotainment-Inhalte angezeigt werden, die zum Beispiel Fußgänger über die Radbahn informieren und zur Nutzung dieser anregen.
-   Solar-Betrieb: Gegebenenfalls könnte der Betrieb der Hardware-Komponenten über Solarzellen und Akkus ermöglicht werden und der urban compass so unabhängig von einer gesonderten Stromversorgung gemacht werden.

Für eine potenzielle Weiterführung des Projekts wird eine genaue Prüfung dieser o.g. Ansätze empfohlen, um den urban compass weiter zu optimieren.
