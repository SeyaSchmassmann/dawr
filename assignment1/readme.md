# Quellen

Für die Erstellung der drei Ranglisten wurden folgende Quellen verwendet:

- [Wikipedia](https://de.wikipedia.org/wiki/Gemeinden_des_Kantons_Waadt)
- [BFS](https://www.atlas.bfs.admin.ch/maps/13/de/17825_9164_8282_8281/27598.html) ([CSV-Datei](https://www.atlas.bfs.admin.ch/core/projects/13/xshared/csv/27598_131.csv))
- [OpenData Waadt*](https://mstrpub.vd.ch/MicroStrategy/servlet/mstrWeb)

*) Für die Daten von OpenData Waadt wurde nebst dem Link auch noch den Pfad zur Navigation auf der Website angegeben. Dies, da sich der Link während dem Projekt geändert hat und somit die Datenquelle nicht mehr verfügbar war. Die Website verlangt teilweise ein Login, dies kann aber teilweise mittels Page-Refresh umgangen werden. Die Daten wurden im Ordner "raw" abgelegt. Die Datenquelle ist wie folgt zu finden:
 * [010 Population (Statpop + RCPERS) > Shared Reports > Etat et structure de la population>Population : communes, districts, régions > Population dès 2017 > 1. Population résidante permanente par origine, district et commune, Vaud, 2017-2023](https://mstrpub.vd.ch/MicroStrategy/servlet/mstrWeb?evt=4001&src=mstrWeb.4001&visMode=0&reportViewMode=1&reportID=AD31782944D27F7B77AD84ABDD760583&Server=SLV8107P&Project=010%20Population%20(Statpop%20%2B%20RCPERS)&Port=0&share=1&uid=public&pwd=5WyKl359I9mQ)
 * [010 Population (Statpop + RCPERS) >Shared Reports > Etat et structure de la population>Population : communes, districts, régions > Population dès 2017 > 6. Population résidante permanente par classe d'âges quinquennale, sexe, origine, district et commune, Vaud, 2017-2023](https://mstrpub.vd.ch/MicroStrategy/servlet/mstrWeb?evt=4001&src=mstrWeb.4001&visMode=0&reportViewMode=1&reportID=4865E36445DC2352A5533EBB94F3FBF4&Server=SLV8107P&Project=010%20Population%20(Statpop%20%2B%20RCPERS)&Port=0&share=1&uid=public&pwd=5WyKl359I9mQ)

# Ranglisten

Die Jupyter-Notebooks sind nach den Ranglisten strukturiert. Jedes Notebook lädt die Daten von der Quelle und bereitet sie auf. Anschliessend werden die Ranglisten erstellt und die Resultate ausgegeben. Zusätzlich werden die Ranglisten auch noch als csv-Dateien im Ordner "rankings" abgelegt. Diese Struktur wurde gewählt, da die einzelnen Ranglisten überwiegend auf unterschiedlichen Datenquellen basieren und somit die Datenverarbeitung und -aufbereitung zwischen den Ranglisten unterschiedlich ist.

Die einzelnen Kriterien der Ranglisten wurden normalisiert, sodass sich die Werte zwischen 0 und 100 bewegen.

## Rangliste 1

Quelle: Wikipedia, siehe [`1_ranking.ipynb`](/assignment1/1_ranking.ipynb)

Die Rangliste wurde aufgrund der Gemeindeauflistung auf Wikipedia erstellt. Die Rangliste besitzt folgende Kriterien:

1. Anzahl Bindestriche im Gemeindenamen\
   Besitzt die Gemeinde genau einen Bindestrich, erhält sie 100 Punkte, ansonsten 0 Punkte.
2. Grünanteil im Gemeindewappen\
   Wie viel Prozent des Gemeindewappens ist grün? Die Prozentzahl wird als Punkte vergeben.
3. Bezirkswechsel der Gemeinde\
   Wenn die Gemeinde bis 2007 im gleichen Bezirk wie ab 2008 war, so enthält sie 100 Punkte, ansonsten 0 Punkte.

## Rangliste 2

Quelle OpenData Vaud, siehe [`2_ranking.ipynb`](/assignment1/2_ranking.ipynb)

Die Rangliste wurde aufgrund der Daten von OpenData Vaud erstellt. Die Rangliste besitzt folgende Kriterien:

1. Anteil Personen in arbeitstätigem Alter\
   Wie viel Prozent der arbeitstätigen Personen sind zwischen 15 und 64 Jahre alt? Die Prozentzahl wird als Punkte vergeben.
2. Verteilung der Altersklassen\
   Gibt es bei der Bevölkerung grosse Abweichungen bei den Altersklassen? Eine Altersklasse enthält jeweils 5 Jahre. Es wird die Abweichung von jeder Altersklasse zur Gleichverteilung berechnet und das Quadrat der Abweichung aufsummiert. Je grösser die Abeichung, desto mehr Punkte erhält die Gemeinde.
3. Zuwachs der Bevölkerung\
   Die Differenz zwischen der Bevölkerung von 2022 und 2017 wird als Punkte vergeben.

## Rangliste 3: BFS / Wikipedia

Quelle BFS und Wikipedia, siehe [`3_ranking.ipynb`](/assignment1/3_ranking.ipynb)

Die Rangliste wurde aufgrund der Daten von BFS und Wikipedia erstellt. Die Rangliste besitzt folgende Kriterien:

1. Fläche der Gemeinde\
   Die Fläche der Gemeinde wird quadriert und dieser Wert wird als Punkte vergeben.
2. Steuerbares Einkommen\
   Das steuerbare Einkommen wird als Punkte vergeben. Dabei werden die steuerbare Einkommen, welche grösser als 60'000 CHF sind, doppelt gezählt (also steuerbares Einkommen zählt doppelt als Punktzahl).
3. Anzahl Wörter im Gemeindenamen\
   Die Anzahl Wörter im Gemeindenamen (Gemeindenamen, separiert nach Leerzeichen) wird als Punkte vergeben. Gemeinden, welche eine gerade Anzahl Wörter im Namen haben, erhalten die doppelte Anzahl Punkte (also Anzahl Wörter zählt doppelt als Punktzahl).

# Resultate

Die Resultate der Ranglisten sind in den erstellten csv-Dateien im Ordner "rankings" abgelegt. Die Resultate sind in gekürzter Form auch in den Jupyter-Notebooks ersichtlich.
(Total 300 Gemeinden)

## Rangliste 1

- 1. Lavey-Morcles (92.4 Punkte)
- 261. Le Chenit (0 Punkte)  
- 296. Mauraz (0 Punkte)

## Rangliste 2
- 1. Mauraz (81.5 Punkte)
- 262. Lavey-Morcles (19.1 Punkte)
- 297. Le Chenit (9.2 Punkte)

## Rangliste 3

- 1. Le Chenit (72.7 Punkte)
- 286. Lavey-Morcles (1.6 Punkte)
- 300. Mauraz (0.0 Punkte)
