---
layout: post
title: "Catchbook German"
---
## Einleitung
Hallo! Mein Name ist Ronald Hrovat und ich habe kürzlich einen 10-monatigen Java-Programmierkurs bei everyone codes abgeschlossen. Um unsere neu erworbenen Fähigkeiten in Java und Spring Boot zu üben, hatten wir 6 Wochen Zeit, um an einem kleinen Projekt unserer Wahl zu arbeiten. Als begeisterter Angler beschloss ich mein Projekt übers angeln zu erstellen. In dem Projekt werden alle Fänge aufgezeichnet. Die Fischarten, Köder, Ort, Zeit und Datum.


## Planung und Projektstrucktur!
Für die Umsetzung meines Projektes habe ich mich folgende Klassen entschieden:
 * FischType (Raub oder Friedfisch)
 * FischSpezies (Fischarten)
 * Köder (Mit welchem Köder der Fisch gefangen wurde)
 * Platz (An welchem Teich/See/Fluß der Fisch gefangen wurde)
 * Fang (Alle gefangenen Fische)


## Datenbank
Als Datenbank wird PostgreSQL verwendet.
Die 

Table Fish_type:            

| id | Right columns |      
| --- |---------------|      
|  1 | NON_PREDATOR  |      
|  2 | PREDATOR      |      
                            
                            

Table species:

| fish_type_id | id | name    |
| ------------ | --- | ------- |
| 1            | 1  | Karpf   |
| 1            | 2  | Schleie |
| 2            | 3  | Hecht   |
| 2            | 4  | Zander  |









<!-- ![alternativtext](\pbl-blog\image\klassen.png) -->