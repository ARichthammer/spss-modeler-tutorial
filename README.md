
#  SPSS Modeler Tutorial


Ziel des Tutorials => Forecasting Model


### 1. Modeler Flow öffnen
Klicke auf den blauen Button: “Add to project” (oben rechts) und dann „Modeler Flow“ auswählen

![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/01.png)


### 2. Namen vergeben und auf „Create“ klicken

![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/02.png)


Die GUI von Modeler Flow öffnet sich.

 
  

### 3. Datenquelle anbinden
Unter dem Reiter „Import“ findet sich der Knoten „Data Asset“.
Diesen Knoten mit Drag and Drop in den leeren Canvas ziehen und dann mit einem Doppelklick öffnen.

![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/03.png)

 s öffnet sich der Dateneditor.
Unter dem Reiter "Data asset" den gewünschten Datensatz auswählen und auf den blauen "Select"-Button drücken.

![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/04.png)




### 3. Daten explorieren
Mit der rechten Maustaste auf den runden Datenasset-Knoten und dann auf Preview klicken. Es öffnet sich eine Vorschau auf die Daten.
![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/05.png)

Unter dem Reiter "Graphs" den "Charts" Knoten in den Canvas ziehen. Mit der Maustaste über den "Data Asset"-Quellknoten gleiten, bis ein blaues Dreieck erscheint. Das Dreieck anklicken und mittels Drag and Drop zum "Charts" Knoten ziehen. Es entsteht ein Pfeil der beide Knoten miteinander verbindet und die Richtung des Datenflusses visualisiert.

![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/06.png)

Rechte Maustaste auf den "Charts"-Knoten und auf "Open" klicken. Rechts öffnet sich Fenster und hier auf den blauen Button "Launch Chart Builder" klicken
![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/07.png)

Es öffnet sich die Visualisierungs-Engine.
Eine oder mehrere Variable auswählen und auf "Visualize Data" klicken. Die Chartengine wählt automatisch eine passende Grafik aus.
![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/08.png)

Im Chart Builder stehen 34 Visualsierungsmöglichkeiten zur Verfügung, mit denen man die Daten schnell und intutiv explorieren kann.
Besonders interessant für die später folgende Zeitreihe-Analyse ist der "Timeplot".

![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/09.png)

Neben einer Zeritreihenzerlegung (Decomposition) werden links auch noch der wichtige ADF-Test (bzgl. Stationärität) und der ACF/ PACF-Plot ausgegeben. (P.S: Im Screenshot sind die Sensorwerte für alle IDs dargestellt, was inhaltlich wenig Sinn macht, da man hier vorher noch auf einzelne ID selektieren müsste. Screenshot dient nur zur Veranschaulichung)

Mit dem Button "Return to flow" (oben rechts) kommt man wieder zurück zum Modeler Flow.

Weitere Möglichkeit der Datenexploration:
_Data Audit Knoten_ (unter Reiter: Outputs): statistische Kennzahlen, Verteilung, fehlende Werte, Ausreißer
(Vorgehen: Knoten in Oberfläche ziehen, mit Quellknoten verbinden, rechte Maustaste & RUN, rechts unter Outputs & Models den Data Audit Knopf anklicken)

#### 4. Daten aubereiten

#####4.1 Selektion ID

Zunächst selektieren wir die Datensätze für das stündliche Verkehrsaufkommen (ID = 5054  bzw. 5055).
Hierfür ziehen wir einen _Select_-Knoten aus dem Reiter _Record Operations_ in die Modeler-Oberfläche und verbinden den Knoten mit dem Quellknoten.

![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/10.png)

Danach Doppelklick auf den _Select_-Knoten öffnet sich rechts das Einstellungsfenster. Im grau markierten Eingabebereich tippen wir folgende Formel ein: ___id = 5054__: und drücken auf den _Save_-Button.

![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/11.png)

Mit einer Vorschau auf den Selcet-Knoten (rechte Maustaste => Preview) kann man überprüfen, ob die Selektion funktioniert hat.

Komplexere Datenselektierungsoperationen können mit dem sog. Expression Builder ausfegührt werden. Hierzu klickt man auf das Taschenrechnersymbol (blau eingerahmt) im geöffneten Select-Knoten.

#####4.1 Selektion Roadstation-ID

Im nächsten Schritt selektieren wir eine Roadstation-ID, für die wir im Anschluss ein Forecasting-Model des Verkehrsaufkommens bauen werden.
Hierzu ziehen wir einen weiteren Select-Knoten in den Modeler Stream und verbinden diesen mit dem vorher benutzen ID-Select Knoten. dann: Doppelklick auf den neuen Selectknoten und Eingabe folgender Formel: ___roadStationId = 23140___. Plus Save. 

Um die Operation zu überprüfen, ziehen wir dieses Mal einen _Table_-Knoten – unter dem Reiter _Outputs_ – in die Oberfläche und führen die Tabelle aus (rechte Maustaste und _Run_). Im Output-Fenster, das rechts aufpoppt, klickt man auf die Tabelle an, wodurch sich diese öffnet.

![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/12.png)


id = 5054

roadStationId = 23140
#### 5. Modellieren





#### 5. Evaluation



Weiterführende Informationen:
Modeler Flow Knowledge Center: https://dataplatform.cloud.ibm.com/docs/content/wsd/spss-modeler.html
Dort findet er eine Eräuterung der einzelnen Modeler Knoten und noch weiterführende Tutorials
