
#  SPSS Modeler Tutorial


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





#### 5. Modellieren





#### 5. Evaluation



Weiterführende Informationen:
Modeler Flow Knowledge Center: https://dataplatform.cloud.ibm.com/docs/content/wsd/spss-modeler.html
Dort findet er eine Eräuterung der einzelnen Modeler Knoten und noch weiterführende Tutorials
