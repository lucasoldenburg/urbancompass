# Projektdokumentation Urban Compass

<img src="https://github.com/lucasoldenburg/urbancompass/blob/main/bilder%20doku/Logo.png" width=150>

(Hinweis: die Dokumentation befindet sich noch in Arbeit)

TODOs:

-   Inhaltsverzeichnis (als letztes)
-   Bilder in Ordner bilder doku laden
-   Bilder Referenzieren in Markdown referenzieren
-   Links einfügen
-   Logo?

## Projektziel

Die Ziele dieses Projekts lassen sich in zwei Unterziele unterteilen, die im Folgenden beschrieben werden.

### Proof of Concept Grüne-Welle-Assistent mit ESP32

Im Rahmen des „Leetzenflow“-Projekts entwickelte das Institut für Verkehrswissenschaften der WWU Münster im Auftrag der Stadt Münster einen prototypischen Grüne-Welle-Assistenten. Dieser unterstützt Fahrradfahrende dabei, die eigene Geschwindigkeit anzupassen, um grüne Ampelphasen optimal zu nutzen und somit an weniger Ampeln anhalten zu müssen. Ziel dieses Projekts ist die Erarbeitung eines Proof of Concept (PoC), das belegt, dass der Grüne-Welle-Assistent ebenso mit abweichender Hardware unter Verwendung eines ESP32 als Mirkocontroller umgesetzt werden kann.

### Urban Compass

Das zweite Projektziel besteht darin, die im Rahmen des PoC entwickelte Hardwarelösung als Grundlage zu verwenden, um eine andere Anzeige als den Ampelstatus auf den LEDs als „Urban Compass“ zu realisieren. Konkret handelt es sich dabei um Infotainment-Inhalte, die auf den LEDs angezeigt werden können. Diese Inhalte sollen dabei das Potenzial haben, Fahrradfahrende bei der Navigation durch die Stadt zu unterstützen und darüber hinaus eine positive psychologische Wirkung auf das Fahrerlebnis zu erzeugen. Die Inhalte werden im Rahmen des Projekts in einem fachlichen Konzept entwickelt und prototypisch als Anzeige auf den LEDs umgesetzt.

## Hardware

Die folgende Tabelle zeigt alle im Projekt verwendeten Hardwarekomponenten inklusive Shopping-Links und Kostenaufstellung.

| **Komponente**         | **Produktname**                                         | **Hersteller**           | **Link**                                                                                                                                                             | **Preis**          |
|------------------------|---------------------------------------------------------|--------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------|
| LED 1                  | 64x32 RGB LED MATRIX – 5MM Pitch                        | Adafruit Industries LLC  | https://www.digikey.de/de/products/detail/adafruit-industries-llc/2277/7035035                                                                                       | 59,99 €            |
| LED 2                  | 32x32 RGB LED MATRIX – 5MM Pitch                        | Adafruit Industries LLC  | https://www.digikey.de/de/products/detail/adafruit-industries-llc/2026/7035028?s=N4IgTCBcDaIIwFYwA4C0Y6NQOQCIgF0BfIA                                                 | 41,98 €            |
| Microcontroller        | ESP32WROOM32E                                           | Espressif Systems        | https://www.digikey.de/de/products/detail/espressif-systems/ESP32-DEVKITC-32E/12091810                                                                               | 12,00 €            |
| Jumper-Kabel           | Jumper Wire Kabel 40 STK. je 20 cm F2F Female to Female | AZ-Delivery              | https://www.kaufland.de/product/342455919/?utm_source=shopping&utm_medium=non-paid&utm_campaign=pricecomparison&sid=42345840                                         | 3,99 € (40 Stück)  |
| Netzteil               | AC-Adapter (Output: 5V, 3A)                             | Leicke                   | https://www.otto.de/p/leicke-ull-netzteil-15w-5v-3a-netzteil-besonders-leicht-kurzschluss-ueberspannungs-und-ueberhitzungsschutz-S0C1G0DZ/\#variationId=S0C1G0DZBSMT | 8,99 €             |
| Netzteil-Adapter       | -                                                       | -                        | -                                                                                                                                                                    | -                  |
| Micro-USB-Kabel        | Micro-USB-Kabel                                         | Liour                    | https://amzn.to/3qPDoVF                                                                                                                                              | 4,99 €             |
| Stromkabel LED         | HUB75-Power Cable                                       | Adafruit Industries LLC  | Im Lieferumfang der LED-Matrix enthalten                                                                                                                             | -                  |
| HUB75-Verbindungskabel | HUB75-Data Cable                                        | Adafruit Industries LLC  | Im Lieferumfang der LED-Matrix enthalten                                                                                                                             | -                  |
| DC-Buchse              | DC Buchse Stecker 5,5 x 2,1mm                           | LitaElek                 | https://www.amazon.de/dp/B019HAC6V4/                                                                                                                                 | 6,49 €  (5 Paar)   |
| -                      | -                                                       | -                        | -                                                                                                                                                                    | Summe: ???         |

## Zusätzlich wurde im Rahmen des Projekts folgendes Werkzeug verwendet:

-   3D-Drucker für die Case (Anycubic Mega X Drucker)**  
    **(<https://de.anycubic.com/products/mega-x?_pos=14&_sid=d5e44558a&_ss=r)>)
-   Messer (Case)
-   Pfeile (Case)
-   Bohrer (Case)
-   Seitenschneider für das zuschneiden der Kabel
-   Lötkolben
-   Schrumpfschlauch

Die genaue Beschreibung der Zusammensetzung der Komponenten findet sich in Kapitel Elektronik-Bauteile.

## Fachkonzeption

### Grüne-Welle-Assistent

Siehe Leezenflow

Eine ausführlich Fachkonzeption befindet sich in der Projektdokumentation

### Urban Compass – Konzeptskizzen

[Bilder]

Eine ausführlich Fachkonzeption befindet sich in der Projektdokumentation

## Projektvorgehen

### Hardwareentwicklung – Elektronik-Bauteile

#### 1. Verbindung ESP mit LED 32x32

-   über Jumper-Kabel
-   Probleme/Herausforderungen:
    -   Jumper-Kabel physisch schwierig einzustecken (ggf. schlechte Qualität)
    -   Mapping-Beschriftung auf LED leicht anders als in Doku (<https://github.com/mrfaptastic/ESP32-HUB75-MatrixPanel-I2S-DMA>): Nummerierung beginnend mit „0“ statt mit „1“

[Bilder]

#### 2. Verbindung ESP mit Laptop über Micro-USB-Kabel

-   Allgemeine Verbindungsherstellung & Test ESP mit LED 32x32
-   Test der LED 32x32 mit „Simple Test Shapes“ (<https://github.com/mrfaptastic/ESP32-HUB75-MatrixPanel-I2S-DMA/tree/master/examples/1_SimpleTestShapes>) à fehlerfrei
-   Noch ohne Netzteil, Stromversorgung LED nur über ESP à LED-Anzeige zu schwach

[Bilder]

#### 3. Test Stromversorgung: ESP mit LED 32x32

-   Verbindung: ESP à LED 32x32
-   Verbindung Stromkabel des LED 32x32 über Hohlstecker Buchse zu 5V-Netzteil
-   Verbindung ESP über Micro-USB-Kabel an Laptop
-   Anzeige-Test ok, aber: Floating-Ground-Problem aufgetreten à Flackern des LED 32x32

[Bilder]

#### 4. Test Stromversorgung: ESP mit LED 32x32 + LED 64x32

-   Verbindung: ESP à LED 32x32 à LED 64x32
-   Verbindung der Stromkabel der LED 64x32 & LED 32x32 über Hohlstecker Buchse zu 5V-Netzteil
-   Verbindung ESP über Micro-USB-Kabel an Laptop
-   Test ok, aber: Floating-Ground-Problem aufgetreten à Flackern des LED 64x32

[Bilder]

#### 5. Test Anzeige: ESP mit LED 32x32 + LED 64x32

-   Verbindung: ESP à LED 32x32 à LED 64x32
-   HUB75-Verbindungskabel für Verbindung LED 32x32 zu LED 64x32
-   Test beider LEDs zusammengeschaltet, erneut nach „Simple Test Shapes“ (<https://github.com/mrfaptastic/ESP32-HUB75-MatrixPanel-I2S-DMA/tree/master/examples/1_SimpleTestShapes>) à fehlerhafte Anzeige

    [Bilder]

#### 6. Test Anzeige: ESP mit LED 32x32

-   Verbindung ESP à LED 32x32
-   Test mit Bouncing Squares (<https://github.com/mrfaptastic/ESP32-HUB75-MatrixPanel-I2S-DMA/tree/master/examples/BouncingSquares>) à fehlerhafte Anzeige

#### 7. Test Anzeige: ESP mit LED 64x32

-   Verbindung: ESP à LED 64x32
-   Test mit „Bouncing Squares“ (<https://github.com/mrfaptastic/ESP32-HUB75-MatrixPanel-I2S-DMA/tree/master/examples/BouncingSquares>) à in Ordnung, fehlerfreie Anzeige

[Bilder]

#### 8. Test Anzeige: ESP mit LED 64x32 + LED 32x32

-   Änderung LED-Reihenfolge
-   Verbindung: ESP à LED 64x32 à LED 32x32
-   HUB75-Verbindungskabel für Verbindung LED 64x32 zu LED 32x32
-   Test mit „Bouncing Squares“ (<https://github.com/mrfaptastic/ESP32-HUB75-MatrixPanel-I2S-DMA/tree/master/examples/BouncingSquares>) à keine verbundene Anzeige auf LEDs, jeweils nur einzeln
-   Anzeige auf LED 64x32 fehlerfrei wie zuvor
-   Anzeige auf LED 32x32 fehlerhaft: erkannt als LED 64x32, deshalb nur halbe Anzeige, sonst korrekte Anzeige

[Bilder]

#### 9. Test Anzeige: ESP mit LED 64x32 + LED 32x32 ohne separaten Ground

-   Verbindung: ESP à LED 64x32 à LED 32x32
-   Wesentliche Änderungen zu Schritt 8:
    -   Entfernung der Ground-Verbindung zwischen ESP und LED 64x32
    -   Verwendung eines anderen Netzteils mit wirklicher 5V-Spannung (zuvor leicht über 5V)
-   Test mit „Bouncing Squares“ (<https://github.com/mrfaptastic/ESP32-HUB75-MatrixPanel-I2S-DMA/tree/master/examples/BouncingSquares>) à Anzeige fehlerfrei & über beide Panels
-   Test mit „Aurora Demo“ (<https://github.com/mrfaptastic/ESP32-HUB75-MatrixPanel-I2S-DMA/blob/master/examples/AuroraDemo/AuroraDemo.ino>) à Anzeige fehlerfrei & über beide Panels
-   Finale Komponenten-Konstellation
-   Schaltplan: siehe letztes Bild

[Bilder]

### Hardwareentwicklung – 3D-Druck Gehäuse

Im Rahmen des Projekts wurde mithilfe eines 3D-Druckers ein Gehäuse konzipiert und gedruckt. Dieses dient dazu, die zwei LEDs als hauptsächliche Komponenten statisch zu verbinden und ihnen Stabilität zu verleihen. Zusätzlich wurde an der Vorderseite eine Halterung gedruckt, in die eine Plexiglasscheibe für weiteren Schutz der LEDs eingesetzt werden kann. Die einzelnen Arbeitsschritte umfassten dabei folgendes:

1.  Maße nehmen und Suche nach Druckvorlagen

    Zunächst wurden die Maße der Halterungen der LED-Matrizen genommen. Da in diesem Projekt beide Matrizen zusammengebaut werden müssen, erschwerte dies die Suche nach einer passenden Druckvorlage. Letztendlich wurden einzelne Vorlagen für die Modellierung des Gehäuses in Betracht gezogen, jedoch wichen die Maße der gewählten Gehäuse zu weit von unseren Matrizen ab.

2.  Konzeption einer eigenen Lösung (UseCase-spezifisch)

    Da keine passende Druckvorlage gefunden wurde, konzipierten wir eine eigene Lösung, welche für unseren Nutzen zugeschnitten wurde. Wichtig war dabei die Möglichkeit der Justierung der beiden Matrizen in einem Rahmen, sowie die Anbringung einer Frontscheibe zum Schutz der LEDs.

3.  Modellierung der Einzelteile

    Die Einzelteile wurden mit der Website <https://www.tinkercad.com/> modelliert. Da der Rahmen für die LEDs größer ist, als die Platte des 3D-Druckers, muss dieser in zwei Teile geteilt werden. Gleiches gilt für die Halterung der Plexiglasscheibe.

4.  Druckeinstellungen anpassen

    Damit der Druck eine ausreichende Qualität hat, müssen unterschiedliche Druckeinstellungen angepasst werden.

5.  Testdruck durchführen: 7-mal bis gewünschtes Ergebnis erreicht

    Um die Druckeinstellungen zu verproben wurden Testdrucke durchgeführt. Diese Testdrucke dauerten aufgrund der relativ großen Rahmengröße zwischen 3 und 15 Stunden. Nach einigen Iterationen standen die optimalen Druckeinstellungen für jedes Einzelteil fest.

6.  Finale Drucke

    Anschließend wurden die finalen Drucke für den Rahmen, als auch für die Plexiglashalterung druchgeführt.

7.  Beschaffung Plexiglasscheibe

    Die Plexiglasscheibe wurde nach der Fertigstellung des Drucks im Baumarkt für die Rahmengröße zugeschnitten, sodass diese bestmöglich in die Halterung hineinpasst.

8.  Zusammenbau der Einzelteile

    Im Anschluss wurden die Einzelteile zusammengesetzt und die Hardware wurde erneut für Bohrung der Löcher im Rahmen vermessen, damit diese fest montiert werden kann.

9.  Einsetzen der Hardwarekomponenten

    Zum Schluss wurde die Hardware in den Rahmen eingesetzt und festgeschraubt. Die Plexiglasscheibe wurde in der entsprechenden Halterung eingeklebt. Diese wurde dann wiederum mithilfe von Magneten auf den Rahmen der LED-Matrizen gesetzt.

## Softwareentwicklung

Dieses Kapitel umfasst eine Beschreibung über die einzelnen Schritte der Softwareentwicklung. Dabei werden die einzelnen Entwicklungsschritte des Grüne Welle Assistenten und des urban compass im Groben erläutert, um ein generelles Verständnis für das gewählte Vorgehen zu vermitteln. Der vollständige Code kann aus der technischen Dokumentation bzw. dem GitHub Repository zum Projekt unter https://github.com/lucasoldenburg/urbancompass entnommen werden.

### Grüne-Welle-Assistent

Im Folgenden werden die Entwicklungsschritte des Grüne Welle Assistenten erläutert.

#### Anzeige Balken

-   Verwendung der Library Adafruit GFX für alle Methoden
-   Matrix einfarbig füllen mit *fill color(),* Farbe grün
-   Spaltenweise überschreiben mit „leeren Pixeln“, um Füllung schrittweise zu entfernen

[Bilder]

-   Matrix erneut einfarbig füllen mit *fill color()*, Farbe rot
-   Spaltenweise überschreiben mit „leeren Pixeln“, um Füllung schrittweise zu entfernen

[Bilder]

#### Anzeige Fahrrad-Symbol

-   Zeichnen eines Fahrrad-Piktogramms mit Pixilart (https://www.pixilart.com/) und speichern als Bitmap
-   Anschließend Konvertierung in HEX-Code für Verwendung in Arduino-Code (<https://github.com/mrfaptastic/ESP32-HUB75-MatrixPanel-I2S-DMA/blob/master/examples/BitmapIcons/bmp2hex.py>)
-   Zeichnen des Fahrrad-Symbols auf LEDs mit drawBitmap()

[Bilder]

### Urban Compass

Folgende Entwicklungsschritte wurden im Rahmen der Softwareentwicklung des urban compass durchgeführt:

-   Prototypisches Zeichnen einer der in Kapitel 3.2 (Fachkonzeption) erstellten Infotainment-Inhalte mit Pixilart (https://www.pixilart.com/) und speichern als Bitmap
-   Anschließend Konvertierung in HEX-Code für Verwendung in Arduino-Code (<https://github.com/mrfaptastic/ESP32-HUB75-MatrixPanel-I2S-DMA/blob/master/examples/BitmapIcons/bmp2hex.py>)
-   Zeichnen der Inhalte mit *drawXbm565()*: Draw-Funktion von <https://github.com/mrfaptastic/ESP32-HUB75-MatrixPanel-I2S-DMA/blob/master/examples/BitmapIcons/BitmapIcons.ino>
-   Ergebnis: fehlerhafte Anzeige (siehe folgende Bilder)

[Bilder]

-   auf *drawBitmap()* Funktion der Adafruit GFX Library gewechselt
-   Änderung:
    -   Umwandlung der Bitmap in HEX (muss nicht mehr gespiegelt/geflipped sein)
    -   Änderung des Aufrufs von Skript (<https://github.com/mrfaptastic/ESP32-HUB75-MatrixPanel-I2S-DMA/blob/master/examples/BitmapIcons/bmp2hex.py>)
-   Bitmaps für alle vier Kategorien der Infotainment-Inhalte erstellt und optimiert (Bezirke, Sehenswürdigkeiten, Uhrzeit, ÖPNV)
-   Code-Anpassung: Iteration durch verschiedene Bitmaps nacheinander à Wechsel der Anzeige
-   Ergebnis: Kategorien Uhrzeit, Sehenswürdigkeiten und Bezirke werden fehlerfrei angezeigt (siehe folgende Bilder)

[Bilder]

-   Erstellung Bitmaps für einzelne Elemente der ÖPNV-Anzeige (farbige Umrandungen, Schrift und Pfeile)
-   Einzelne Bitmaps der farbigen Umrandungen und Linienkennung sowie Pfeile mit *drawBitmap()* in einzelnen Farben übereinander gezeichnet, um mehrfarbiges Bild zusammen zu setzen
-   Ergebnis: auch fehlerfreie Anzeige der Kategorie ÖPNV

[Bilder]

## Projektergebnis

Im Folgenden wird das Projektergebnis als Bildergalerie dargestellt. Beide Projektziele, sowohl die Umsetzung des PoC Grüne-Welle-Assistenten als auch der urban compass, konnten vollständig erreicht werden. Der PoC gilt als erfolgreich umgesetzt, da alle in Kapitel 3.1 definierten Schritte im Rahmen des Abnahmeszenarios fehlerfrei durchgeführt werden können. Auch die Anzeige der Infotainment-Inhalte im Rahmen des „urban compass“ ist vollständig (alle Kategorien und Inhalte) und fehlerfrei (korrekte Anzeige), weshalb auch dieses Ziel als erreicht gilt.

[Bilder]

## Ausblick

In Bezug auf den urban compass wurden im Verlauf der prototypischen Umsetzung bereits einige offene Aspekte und Optimierungspotenziale identifiziert, die im Folgenden aufgeführt werden:

-   Optimierung der Anzeige & Inhalte für den urban compass:
    -   Identifikation weiterer Infotainment-Inhalte sowie Bestimmung der relevantesten Inhalte bzw. Kategorien. Umsetzung ggf. über Befragung von Fahrradfahrenden, Sichtung von Studien und durch den Einsatz interdisziplinärer Teams (z.B. Psychologen, Stadtplaner, Designer, etc.).
    -   Hinzufügen von sprechenden Icons, sodass die angezeigten Informationen von Fahrradfahrenden besser eingeordnet werden können.
    -   Je nach Standort eines urban compass Angabe von Kilometern für die Distanz zu Orten wie Bezirken oder Sehenswürdigkeiten und Angabe von Minuten für nächste Anbindungen des ÖPNV.
    -   Ermittlung der optimalen Anzeigedauer je Kategorie über die durchschnittliche Geschwindigkeit der Fahrradfahrenden.
-   Weitere LED-Anzeige in Außenrichtung der Radbahn: Gegebenenfalls wäre die Umsetzung einer zweiten Anzeige sinnvoll, die in die Außenrichtung der Radbahn zeigt. Auf dieser könnten andere Infotainment-Inhalte angezeigt werden, die zum Beispiel Fußgänger über die Radbahn informieren und zur Nutzung dieser anregen.
-   Solar-Betrieb: Gegebenenfalls könnte der Betrieb der Hardware-Komponenten über Solarzellen und Akkus ermöglicht werden und so die Abhängigkeit zu gesonderter Stromversorgung eliminiert werden.
-   Witterungsfestigkeit: Das 3D-gedruckte Gehäuse könnte erweitert bzw. vervollständigt werden, indem eine Rückwand konzipiert und Dichtungen für die Abweisung von Wasser eingesetzt werden.

Für eine potenzielle Weiterführung des Projekts wird eine genaue Prüfung dieser o.g. Ansätze empfohlen, um den urban compass bzw. den Grüne Welle Assistenten weiter zu optimieren.
