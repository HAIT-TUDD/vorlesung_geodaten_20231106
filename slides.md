# Titel

|  |  |
|:---|---|
| date | 28-10-2023 |
| author | Anne Klammt |
| license | cc by-s.a 4.0 |

---

## https://hait-tudd.github.io/vorlesung_geodaten_20231106

---


|  |  Thema |
|---|---|
| 1 | HAIT und Beispiele raumbezogener Forschung |
| 2 | Datenmodelle und -formate |
| 3 | Historische geographische Karten |
| 4 | Gazetteer und Semantic Web |
| 5 | Take aways |

----

### HAIT

• Hannah-Arendt-Institut für Totalitarismusforschung e.V. an der TU Dresden

• "...vergleichenden Analyse von Diktaturen .... Besonderes Augenmerk liegt dabei auf den Strukturen des Nationalsozialismus und des Kommunismus sowie den Voraussetzungen und Folgen beider Weltanschauungsdiktaturen"

• 1993 gegründet und vom Land Sachsen finanziert

----

Beispiele von raumbezogenen histor. Informationen in der  Forschung des

**Regimedatensatz**

----

**Geflüchtete jüdische Akademikerinnen und Künstlerinnen 1918&ndash;1945**

----

**Ortsgruppen der NSDAP in Dresden** als SpinOff der [Erschließung der NS-Tageszeitung "Der Freiheitskampf"](https://hait.tu-dresden.de/ext/forschung/der-freiheitskampf.asp)

Link: Digitallabor / [Ortsgruppen der NSDAP](https://digilab-hait.de/freiheitskampf/vis/hait/dresden/ortsgruppen.html)

----

### Was ist allen drei Beispielen gemeinsam?

---

Datenmodelle 

|  Koordinaten | Matrix  |
|---|---|
| Vektordaten *(Punkte, Linien, Polygone)* | Rasterdaten *(Matrix gleichförmiger Zellen (z.B. Pixel))* |

---

#### Vektordaten

![[Libre Texts Geosciences. 4.2: Vector Data Models](https://geo.libretexts.org/Bookshelves/Geography_(Physical)/Essentials_of_Geographic_Information_Systems_(Campbell_and_Shin)/04%3A_Data_Models_for_GIS)](https://geo.libretexts.org/@api/deki/files/7402/5e0adb92da29fb258470bfeb5265cc55.jpg?revision=1&size=bestfit&width=385&height=356)


---

#### Typische Verwendung von Vektordaten

- thematische Karten
- disparat verteilte punktuelle Werte (Reisestationen, Wahllokale)
- topologische Karten (Streckenpläne, Straßennetze)

----

- Punkte weisen mind. ein Tupel auf (Hoch- und Rechtswert) und können dann theoretisch unbegrenzt weitere Attribute aufweisen (Höhe, Datierung, Label, Bevölkerungszahl ....)
- Linien weisen mind. Anfangs- und Endpunkt auf, können zudem gerichtet sein und wiederum Attribute zugewiesen bekommen
- Polygone weisen mindestens drei Punkte auf und können wiederum mit weiteren Attributen belegt werden 

----

#### Rasterdaten

![[Libre Texts Geosciences. 4.1: Raster Data Models, Fig. 4.1](https://geo.libretexts.org/Bookshelves/Geography_(Physical)/Essentials_of_Geographic_Information_Systems_(Campbell_and_Shin)/04%3A_Data_Models_for_GIS/4.01%3A_Raster_Data_Models) ](https://geo.libretexts.org/@api/deki/files/7407/4f157f6b392921b128e220ee56d2eb72.jpg?revision=1&size=bestfit&width=325&height=178)


----

####  Typische Verwendung von Rasterdaten

- Basemaps (Hintergrundkarten)
- Relief etc. (kontinuierliche Verteilung)
- Geodaten aus der Fernerkundung (Luftbilder, Satellitenbilder ...)

----

#### Von Raster zu Vektor

- Konturlinien (z.B. Höhenlinien; Areale)
- Ableitung von Mindest- und Höchstwerten
- ...

![[Libre Texts Geosciences. 4.1: Raster Data Models, Fig. 4.3](https://geo.libretexts.org/Bookshelves/Geography_(Physical)/Essentials_of_Geographic_Information_Systems_(Campbell_and_Shin)/04%3A_Data_Models_for_GIS/4.01%3A_Raster_Data_Models)](https://geo.libretexts.org/@api/deki/files/7403/00422de47b6d09c35c398db0ed103ea7.jpg?revision=1&size=bestfit&width=457&height=246)

----

#### Von Vektor zu Raster

- räumliche Interpolationen (Heatmaps)

<img src="https://upload.wikimedia.org/wikipedia/commons/b/b7/The_use_of_a_raster_data_structure_to_summarize_a_point_pattern.gif" height="200">

[The use of a raster data structure to summarize a point pattern](https://en.wikipedia.org/wiki/Raster_graphics#Image_storage)

----

### Datenmodelle


----

#### Datenformate für Vektordaten

- Textfiles: txt, csv, tsv ...
- JSON: GeoJson
- XML: GML, KML (Google) 
- ESRI: Shapefile (shp)

- Geodatabases (ESRI), PostGIS etc.

----

#### Datenformate für Rasterdaten

- TIFF: GeoTIFF
- JPG: GeoJPG
- Textfiles: txt
- zahlreiche proprietäre Formate (Fernerkundung)

----

#### *Pakete* mit beiden Formaten

* GeoPackage **gpkg** - offener, nicht proprietärer Standard
  - beruht auf einer SQLite Datenbank, die z.B. gemeinsame Metadaten und Verknüpfungen vorhält
  - vom Open Geospatial Consortium definiert

---

## 2 Historische geographische Karten



----

### Historische geographische Karten

**Coordinate-Reference-Systems // Koordinatenbezugssystem**

|_Projektion

|_Ellipsoid und Geoid
	- Bezugspunkt

----

#### Projektion

Kurz: In 2D soll ein kugelförmiges Objekt dargestellt werden. Dazu wird es mit einem Netz von Längen- und Breitengraden überzogen, und anschließend ein Teilbereich oder das gesamt Netz in eine plane / 2D Ansicht überführt.
Gebräuchliche Lösungen:

----

<table><tr><td>an den Längen getreu</td><td> Universale transversale Mercator Projektion (UTM)<br>https://upload.wikimedia.org/wikipedia/commons/f/f0/MercNormSph.png</td><td><img src="https://upload.wikimedia.org/wikipedia/commons/f/f0/MercNormSph.png" height="150"></td></tr>
<tr><td>flächengetreu</td><td> Petersen Projektion (u.a. von UN-genutzt)</td><td><img src="https://upload.wikimedia.org/wikipedia/commons/3/34/Gall%E2%80%93Peters_projection_SW.jpg" height="150"></td></tr></table>


----

#### Weiterlesen

* Beate Weninger, Die Peters-Projektion &ndash; die einzige ""Alternative"?. Blog: Die bemerkenswerte Karte. Deutsche Gesellschaft für Kartographie e.V. 4. Februar 2015. [https://web.archive.org/web/20160403060948/http://bk.dgfk.net/2015/02/04/die-peters-projektion/](https://web.archive.org/web/20160403060948/http://bk.dgfk.net/2015/02/04/die-peters-projektion/)

----

#### Ellipsoid / Geoid

|vertikaler Schnitt | horizontaler Schnitt |
|---|----|
|<img src="https://upload.wikimedia.org/wikipedia/commons/7/78/Geoundnsrp.png" alt="Geoundnsrp.png" height="381" >| <img src="https://upload.wikimedia.org/wikipedia/commons/4/41/Geoundaequrp.png" alt="Geoundaequrp.png" height="381">|
| [https://de.wikipedia.org/wiki/Geoid#/media/Datei:Geoundnsrp.png](https://de.wikipedia.org/wiki/Geoid#/media/Datei:Geoundnsrp.png)  | [https://de.wikipedia.org/wiki/Geoid#/media/Datei:Geoundaequrp.png](https://de.wikipedia.org/wiki/Geoid#/media/Datei:Geoundaequrp.png)|
| schwarz: (Rotations)Ellipsoid <br>Geometrisches Erdmodell | rot: Geoid <br> Physikalisches Erdmodell|


----

**Ellipsoid / Geoid**

* Prä-Satellitenzeitlich!: Verschiedene Modelle (Ellipsoide) der Erde (Geoid)
* 1841 Bessel Ellipsoid (Anwendung u.a. Deutschland, westl. Europa)
* 1930 Krassowski (Anwendung ehemalige Sowjetunion, DDR)
* ab 1990er Jahre in DE Umstellung auf GRS-80 Ellipsoid (= WGS84 / World Geodetic System 1984) und UTM

----

#### Standard

**EPSG**-Codes für Bezugssysteme (Koordinatensysteme, Geoide, Transformationen)
* wird vom [Open Geospatial Consortium](LINK) betreut
* Eigene Beschäftigung:

| EPSG Code | Ellipsoid | Region |
|---|---|---|
| GK4 Bessel |  Sachsen |
| GK 4 | Krassowski |

---

#### Anwendung EPSG

Ausschnitt aus KML und GeoJSON

----

**Georeferenzieren**

* Umrechnung von einzelnen Punkten
* mit Software zum Georeferenzieren (z.B. QGIS)
* Einhängen in Leaflet.js (IIIF)
* Georeferenzieren online

----




----

### Mitnehmen

* Es gibt Vektordaten (Darstellung diskreter Werte) und Rasterdaten (Darstellung kontinuierlicher Werte)
* Geographische Koordinaten sind nur im Kontext ihres Bezugssystems interpretierbar
* vor 1990er Jahre zahlreiche verschiedene Bezugssysteme im Gebrauch - Verwendung historisch geographischer Daten nicht völlig trivial

---- 

### Selbsttest 

Welche Koordinaten bekommen Sie in der Wikipedia angezeigt ?

* WGS 84 / Pseudo-Mercator ?
* WGS 84 / Geographische Koordinaten?

---

## Historischer Lagebezug ohne geographische Koordinaten

<img src="https://upload.wikimedia.org/wikipedia/commons/e/e9/Part_of_Tabula_Peutingeriana.jpg" alt= "Tabula Peutingeria" height="500">

[Tabula Peutingeria, Wikicommons](https://commons.wikimedia.org/wiki/File:Part_of_Tabula_Peutingeriana.jpg)

----

* Bevölkerungsgröße ehemaliger Sowjetrepubliken
* Fluchtrouten 
* Adressdaten von NSDAP-Organisationen

----

#### Geogazetteer

* Verzeichnisse von Adressen, Orten, Regierungseinheiten 
* mit Koordinaten (Mittelpunktskoordinate oder Polygone)
* mit Hierarchie und Ontologie (Kontinent - Staat - Bundesland  - Landeshauptstadt)

----

#### Historische Gazetteer

* Getty Thesaurus of Geonames
* Geonames
* HOV
* Herder Institut

----

#### Maschinenlesbare Gazetteer

Publikation von Gazetteer mit persistenten Adressen

* Disambiguierung (Audorf in Sachsen (HOV-Link))
* Historische Zustände (Karl-Marx Stadt)
* Mehrsprachige Bezeichnungen (Jerusalem; Ankara)

----

#### Gazetteer in Semantic Web Technologien


* Verknüpfung mit weiteren Ressourcen über den Ortsbezug -> Deutsches Archäologisches Institut Dresden . Hygiene Museum Literatur Fundort Datenformat!
* same_as, um mehr als ein Gazetteer zu nutzen

----

#### World Historical Gazetteer

* Formatentwicklung um Daten auszutauschen (JSON)

----

#### Georeferenzieren ohne Geographischen Lagebezug?

* Recogito 
* Exportformate; Vorgehensweise

Drei Aufgaben:


----

#### zum Mitnehmen

* Ortsverzeichnisse, die persistente IDs anbieten, sparen Zeit und verbessern die Datenqualität
* Texte, Tabellen und nicht geographische Karten können einen Geografischen Raumbezug erhalten
* Gazetteer werden von verschiedenen Institutionen angeboten; die Nutzung der fachlich spezifischen ist eine Aufgabe der adäquaten Passung


---

### Geovisualisierung

---

## Historische Geodaten

* **Historische Karten**  
* **Gazetteer**





----


----

#### Wikidata 

* Kein kontrolliertes Vokabular, sondern eine kollaborative Datensammlung.
* Wird von Google zur Verbesserung der Suche genutzt (*kleiner Kasten rechts*)
* Zentraler Datenknoten im *'Semantic-Web'*

----



----

#### Getty AAT

* gehört wie ULAN zu den Werkzeugen des Getty Research Institutes
* wird seit den 1970ern entwickelt und wird Mitte der 1990er Jahren als Online-Ressource angeboten
* mittlerweile inhaltlich betreut durch ein internationales Konsortium zur Pflege und Entstehung verschiedener Übersetzungen (darunter deutsch und chinesisch)
* ca. 55.000 beschrieben Begriffe (Konzepte)

----

#### PACTOLS

* Französisches Normvokabular zur Beschreibung von Begriffen der Archäologie )
* gegliedert in 6 Bereiche: (*Peuples, Anthroponymes, Chronologie, Toponymes, Oeuvres, Lieux, Sujets*)
*  ca. 50.000 beschriebene Begriffe (Konzepte)

Webseite: [PACTOLS](https://www.frantiq.fr/pactols/le-thesaurus/)

----



