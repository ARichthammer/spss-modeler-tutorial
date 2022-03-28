
#  Modeler Flow Tutorial


In diesem Tutorial werden TMS Daten (Traffic Measurement System Data) aus Finnland exploriert, aufbereitet und analysiert. Mittels einer Zeitreihenanalyse wird zudem eine Progose des Verkehrsaufkommen an einer ausgewählten RoadStation vorgenommen. Eine nähere Beschreibung der Daten findet sich unter: https://www.digitraffic.fi/en/road-traffic/lam/

Ziel des Tutorials: Erste Schritte und Vertrautwerden mit Modeler Flows innerhalb von Watson Studio


___________


___Ausgangssituation___: In Watson Studio wurde bereits ein Analyse-Projekt erstellt und man befindet sich in eben diesem Projekt.

___________


### 1. Modeler Flow öffnen
Klicke auf den blauen Button: __Add to project__ (oben rechts) und wähle dann __Modeler Flow__ aus

![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/01.png)


### 2. Vergebe einen Namen für die Analyse und klicke auf __Create__

![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/02.png)


Die GUI von Modeler Flow öffnet sich.

 
  

### 3. Datenquelle anbinden
Unter dem Reiter __Import__ findet sich der Knoten __Data Asset__.
Diesen Knoten mit Drag and Drop in den leeren Canvas ziehen und dann mit einem Doppelklick öffnen.

![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/03.png)

Es öffnet sich der Dateneditor.
Unter dem Reiter __Data asset__ den gewünschten Datensatz auswählen und auf den blauen __Select__-Button drücken.

![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/04.png)




### 3. Daten explorieren
Mit der rechten Maustaste auf den runden Datenasset-Knoten und dann auf __Preview__ klicken. Es öffnet sich eine Vorschau auf die Daten.
![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/05.png)

Unter dem Reiter __Graphs__ den __Charts__ Knoten in den Canvas ziehen. Mit der Maustaste über den __Data Asset__-Quellknoten gleiten, bis ein blaues Dreieck erscheint. Das Dreieck anklicken und mittels Drag and Drop zum __Charts__-Knoten ziehen.

![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/06-1.png)

Es entsteht ein Pfeil der beide Knoten miteinander verbindet und die Richtung des Datenflusses visualisiert.

![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/06-2.png)



Doppelklick auf den __Charts__-Knoten. Rechts öffnet sich ein Fenster und hier auf den blauen Button __Launch Chart Builder__ klicken
![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/07.png)

Es öffnet sich die Visualisierungs-Engine.
Eine oder mehrere Variable auswählen und auf __Visualize Data__ klicken. Die Chart-Engine wählt automatisch eine passende Grafik aus.
![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/08.png)

Im Chart Builder stehen 34 Visualsierungsmöglichkeiten zur Verfügung, mit denen man die Daten schnell und intutiv explorieren kann.
Besonders interessant für die später folgende Zeitreihe-Analyse ist der __Timeplot__.

![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/09.png)

Neben einer Zeitreihen-Zerlegung (Decomposition) werden im __Timeplot__-Chart auch noch wichtige statistische Tests angezeigt – wie zum Beispiel der ADF-Test zum Test der Stationärität einer Zeitreihe und ACF/ PACF-Plots für die Autokorrelation der Lag-Variablen.
_P.S: Im Screenshot sind die Sensorwerte für alle IDs dargestellt, was inhaltlich wenig Sinn macht. Die Grafik dient nur zur Veranschaulichung. Für eine sinnvolle Visualisierung müsste man zuerst auf einzelne IDs selektieren (siehe 4.1)_.

Mit dem Button __Return to flow__ (oben rechts) kommt man wieder zurück zum Modeler Flow.

EXKURS: Weitere Möglichkeit der Datenexploration:
1. __Data Audit Knoten__ (unter Reiter: __Outputs__): liefert statistische Kennzahlen (Mean, Median, Varianz, Schiefe), fehlende Werte, Ausreißer.
(Vorgehen: Knoten die in Oberfläche ziehen, mit Quellknoten verbinden, rechte Maustaste & __Run__, rechts unter Outputs & Models den Data Audit Button anklicken)
2. __Entscheidungsbäume__: Hierbei handelt es sich um komplexere Verfahren, die es jedoch ermöglichen unbekannte Muster und Struktueren in den Daten zu explorieren. Beipiele: __CHAID__ oder __C$RT__ (unter dem Reiter __Modeling__)



### 4. Daten aubereiten

#### 4.1 Selektion ID

Zunächst selektieren wir die Datensätze für das stündliche Verkehrsaufkommen (ID 5054 oder alternativ ID 5055 oder beide).
Hierfür ziehen wir einen __Select__-Knoten aus dem Reiter __Record Operations__ in die Modeler-Oberfläche und verbinden den Knoten mit dem Quellknoten.

![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/10.png)

Danach Doppelklick auf den Select-Knoten. Es öffnet sich rechts das Settings-Fenster. Im grau markierten Eingabebereich tippen wir folgende Formel ein: ___id = 5054___: und drücken auf den __Save__-Button.

![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/11.png)

Mit einer Vorschau auf den Select-Knoten (rechte Maustaste => Preview) kann man überprüfen, ob die Selektion funktioniert hat.

Komplexere Datenselektierungsoperationen können mit dem sog. _Expression Builder_ ausfgeführt werden. Hierzu klickt man auf das Taschenrechnersymbol (blau eingerahmt) im Select-Settings-Knoten.


#### 4.1 Selektion Roadstation-ID

Im nächsten Schritt selektieren wir eine Roadstation-ID, für die wir im Anschluss ein Forecasting-Model des Verkehrsaufkommens berechnen werden.
Hierzu ziehen wir einen weiteren Select-Knoten in den Modeler Stream (Reiter __Record Operations__) und verbinden diesen mit dem vorher benutzen ID-Select Knoten. Dann: Doppelklick auf den neuen Select-Knoten und Eingabe folgender Formel: ___roadStationId = 23140___. Plus: __Save__. 

Um die Operation zu überprüfen, ziehen wir dieses Mal einen __Table__-Knoten unter dem Reiter __Outputs__ in die Oberfläche und führen die Tabelle aus (rechte Maustaste und __Run__). Im Output-Fenster, das rechts aufpoppt, klickt man auf die Tabelle, wodurch diese sich öffnet.

![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/12.png)

Damit haben wir einen aufbereiteten Datensatz für die Modellierung einer Zeitreihe.

![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/13.png)

Mehr Infos zur Daenaufbereitung unter folgendem Link: 
Record Operations: https://dataplatform.cloud.ibm.com/docs/content/wsd/nodes/_nodes_record_operations.html

Field Operations: https://dataplatform.cloud.ibm.com/docs/content/wsd/nodes/_nodes_field_operations.html


### 4. Modellierung

Vor der eigentlichen Modelierung ziehen wir noch einen sog __Type__-Knoten aus dem Reiter __Field Operations__ in den Canvas und öffnen diesen mit einem Doppelklick. Im Type-Knoten klicken wir auf den blauen Button __Read values__. Damit wird der Modeler-Stream "instanziert". Das heißt, dass die Datenwerte eingelesen und das Skalenniveau und der Datentyp bestimmt werden. Danach drücken wir den blauen __Save__-Button.

![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/14.png)

_P.S: 80% aller Fehlermeldungen im Modeler lassen sich lösen, indem man einen Type-Knoten in den Canvas zieht und den Modeler Stream neu instanziert._


Jetzt können wir mit der __Modellierung__ endlich beginnen!

Hierzu ziehen wir hinter dem Type-Knoten einen __Time Series__-Knoten im Reiter __Modeling__ in die Oberfläche und öffnen diesen mit einem Doppelklick.
Im Knoten setzen wir ein Häcken bei __Use custom field roles__, damit wir selbst die relevanten Zielvariablen auswählen können. Dann klicken wir auf den blauen Button __Add columns +__  und setzen ein Häcken bei der Variable ___sensorValue___, welche inhaltlich das stündliche Verkehrsaufkommen beschreibt. Unsere Auswahl bestätigen wir unten mit __Ok__. Damit haben wir unsere Zielvariable bestimmt. Unter __Candidate Inputs__ könnte man noch externe Faktoren in die Zeitreihenanalyse einfließe lassen.

![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/15.png)


Danach scrollen wir in den Einstellungen weiter nach unten zum Reiter __Observations and Time Intervall__, wo wir die für die Analyse relevante Zeitvariable und das Zeitintervall definieren müssen. 
In unserem Fall sind das:
- Time/Date Field: Variable __"timestamp"__
- Time Interval: __"Hours per day"__


![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/16.png)



Weiter unten im Reiter Build Options kann man die gewünschten Zeitreihenalgorithmen konfigurieren.
Wir belassen es bei den Standard-Einstellungen, bei denen der sog. __Expert Modeler__ benutzt wird, der alle Zeitreihenverfahren (ARIMA sowie Verfahren des exponentiellen Glättens) durchrechnet und das am besten performende Model automatisiert auswählt.

![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/17.png)


Weiter unten im Reiter __Model Options__ nehmen wir die letzte Konfiguration vor. Wir definieren, wie lange das Modell in die Zukunft prognostizieren soll. Dafür setzen wir ein Häkchen beim Punkt _Extend records into the future_ und legen darunter die Anzahl der Stunden fest – in meinem Fall wähle ich drei Stunden.


![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/18.png)

Wir speichern unsere Einstellungen, indem wir unten den blauen __Save__-Button drücken.

Jetzt führen wir das Zeitreihenmodell aus. Rechte Maustaste auf den Time Series Knoten und __Run__.

Es erscheint ein fünfeckiges, brauner Modellknoten, den wir mit rechter Maustaste und __View Model__ öffnen können
![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/19.png)

Es öffnet sich die Modellübersicht

![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/20.png)

#### 5. Evaluation
Der Modellübersicht können wir entnemen, dass in der vorliegenden Zeitreihe das ARIMA das beste Zeitreihenverfahren ist.
Wenn man auf den blau markierten Hyperlink __sensorValue__ klickt, dann bekommt man noch viele weitere Modellgüteparameter

Um die Zeitreihe und die Vorhersage des ARIMA Models zu visualsieren, ziehen wir unter dem Reiter __Graphs__ den __Time plot__-Outputknoten in den Kanvas und öffnen diesen

Wir markieren den Punkt __Selected Time Series models__ und klicken auf den blauen __Add columns__-Button. Dann setzen wir ein Häkchen bei der $TS-Variable. Hierbei handelt es sich um die Variable mit den vorhergesagten Werten.

![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/21.png)

Danach speichern wir unsere Einstellungen (__Save__) und führen den Time plot-Knoten aus (rechte Maustaste & __Run__).

Im Timeplot stehen die roten Punkte für die wirklichen historischen Datenpunkte (in meinem Fall 13). Die Linie beschreibt das ARIMA-Modell inklusive den drei vorhergesagten Werten. Der blaue Korridor visualisiert das Konfidenzintervall – also: wie sicher sich das Modell in Bezug auf seine Verhersage ist. Je breiter, desto unsicherer.



![ScreenShot](https://raw.github.com/ARichthammer/spss-modeler-tutorial/main/readme_images/22.png)


Zudem: History Knoten, Differenzieren
regression und Verfahren zur Vorhersage von numerischen Variablen (z.B. XGBoost, Random Forrest etc.)


Weiterführende Informationen:
Modeler Flow Knowledge Center: https://dataplatform.cloud.ibm.com/docs/content/wsd/spss-modeler.html
Dort findet er eine Eräuterung der einzelnen Modeler Knoten und noch weiterführende Tutorials
