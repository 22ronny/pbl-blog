---
layout: post
title: "Catchbook German"
---
## Einleitung
Hallo! Mein Name ist Ronald Hrovat und ich habe kürzlich einen 10-monatigen Java-Programmierkurs bei everyone Codes abgeschlossen. Um unsere neu erworbenen Fähigkeiten in Java und Spring Boot zu üben, hatten wir 6 Wochen Zeit, um an einem kleinen Projekt unserer Wahl zu arbeiten. Als begeisterter Angler beschloss ich, mein Projekt übers Angeln zu erstellen. In dem Projekt werden alle Fänge aufgezeichnet. Die Fischarten, Köder, Ort, Zeit und Datum.


## Planung und Projektstruktur!
Für die Umsetzung meines Projektes habe ich mich folgende Klassen entschieden:
 * FischType (Raub oder Friedfisch)
 * FischSpezies (Fischarten)
 * Köder (Mit welchem Köder der Fisch gefangen wurde)
 * Platz (An welchem Teich/See/Fluß der Fisch gefangen wurde)
 * Fang (Alle gefangenen Fische)


## Datenbank
Verwendet wird PostgreSQL.  
Die Datenbank befindet sich in einem LXC auf meinem Server, verbunden über VPN.
Der LXC wurde erstellt mit Proxmox. Zu Testzwecken wurde die Datenbank auch in einem Dockercontainer erstellt.
Dafür habe ich Portainer verwendet.  
In der Datenbank befinden sich 5 Folgende Table:



Table Fish_type:            

| id | fish_type |      
| --- |---------------|      
| *1* | *NON_PREDATOR* |      
| *2* | *PREDATOR* |      
                            
                            
Table species:

| fish_type_id | id | name |
| ------- | --- | ------- |
| *1* | *1*  | *Karpf*   |
| *1* | *2*  | *Schleie* |
| *2* | *3*  | *Hecht*   |
| *2* | *4*  | *Zander*  |


Table bait:

| fish_type_id | id | bait |
| -----| --- | -----|
| *1* | *1* | *Erdbeere* |
| *1* | *2* | *Vanille* |
| *2* | *3* | *Wobbler* |
| *1* | *4* | *Pink Tuna* |


Table place:

| id | place |
| --- | --- |
| *1* | *Klein Meiseldorf* |
| *2* | *Geras* |
| *3* | *Klein Finnland* |


Table catch:

| lenght | weight | bait_id | catch_time | id | place_id | species_id |
| ------ | ------ | ------- | ---------- | --- | ------- | ---------- |
| *null* | *8.3* | *1* | *2022-11-19 15:50:00* | *1* | *1* | *1* |
| *null* | *6.5* | *2* | *2022-11-19 16:40:00* | *2* | *1* | *1* |
| *85* | *null* | *3* | *2022-11-19 18:30:00* | *3* | *1* | *3* |



## Funktion
Der Benutzer kann seine Liste Köder, Plätze und Fischart selbst erweitern und ändern.
Sobald man diese individuell angepasst hat kann man seine Fänge eintragen.

![alternativtext](\pbl-blog\image\klassen.png)
