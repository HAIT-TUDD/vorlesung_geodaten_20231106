<img data-src="myImage.png" height="420" width="200" /># Datenkuration

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

<img data-src="https://geo.libretexts.org/@api/deki/files/7407/4f157f6b392921b128e220ee56d2eb72.jpg?revision=1&size=bestfit&width=325&height=178)" height="420" width="200" /><img data-src="myImage.png" height="220" width="200" />

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

<img src="https://upload.wikimedia.org/wikipedia/commons/b/b7/The_use_of_a_raster_data_structure_to_summarize_a_point_pattern.gif" height="400">

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
*winkelgetreu*

   - Universale transversale Mercator Projektion (UTM) -> Dezimale Koordinaten
   
----

*winkelgetreu*

   - Gauß-Krüger Schnittzylinder (u.a. Deutsche Landesvermessung bis 2000er Jahre)

----

*flächengetreu*

   - Petersen Projektion (u.a. von UN-genutzt)
   
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



## Historische Geodaten

* **Historische Karten**  
* **Gazetteer**


# Digitalisierung & digitales Surrogat

----

> Spricht nun ein/e MuseumsmitarbeiterIn von einem digitalen Objekt, dann hat er/ sie wahrscheinlich das Wort »digital« aus fremden Zusammenhängen genommen und
ihn mit seinem Begriff von Objekt gepaart.

Rohde-Enslin 2020, 26

----

> ***Digital object***: Any type of electronic file. Within the context of digital repositories, most often used to describe audio, video, images, or text-based documents. 

[Abby Clobridge 2010](https://www.sciencedirect.com/science/article/pii/B9781843345961500018)

----

>Vielleicht wäre in diesem Fall das digitali­sierte Museumsobjekt die genauere Bezeichnung. Aber auch hier sind die Begriffe nicht geklärt : 
>Ab wann ist ein Museumsobjekt digitalisiert (oder digital)?

Rohde-Enslin 2020, 26

----

Schema: Evolution der Digitalisierung von Kunst- und Kulturgut 

| | |
|---|:---|
| * | Digitale Bestandserfassung | 
| ** | Digitale Verwaltung aller Informationen zum Objekt |
| *** | Digitales Surrogate des Objekts mit Beschreibungen des  Objekts und des Surrogats |
| ***\* | Gemeinsame Verwaltung von Daten zum Objekt und dem digitalen Surrogaten |
| ***** | Gemeinsame Verwaltung + Präsentation der Surrogate und Informationen |

----

> ***Digital surrogate***: A digital version of an object, one that is intended to serve as a stand-in for the object itself. Most often used when referring to works of art. Example: a .JPG image of the Mona Lisa.

[Abby Clobridge 2010](https://www.sciencedirect.com/science/article/pii/B9781843345961500018)

----

> How many times have you said, or heard someone else say, “I saw the manuscript online” or “I consulted it online” or “I used it online”? Not pictures of the manuscript or the digitized manuscript but the manuscript? 

Dot Porter 2018

----

![Mona Lisa 2017. Foto: Artnews 2017](https://www.artnews.com/wp-content/uploads/2017/11/Crowd_looking_at_the_Mona_Lisa_at_the_Louvre.jpg)

ArtNews 29.11.2017

----

Nach Dot Porter (2018) können digitale Surrogate das Original und die Erfahrung des Originals nicht ersetzen. 
(s. a. W. Benjamin "Aura" des Kunstwerks)

**Aber !**

----

> ... this gives us something practical to aim for. ...let’s do more with 3D, RTI, and MSI to show us parts of the manuscript we can’t see under regular institutional photography, **let’s do more work using data about the manuscript to organize our flat images in new and interesting ways**, all with a mind towards informing us about that unreproducible ghost.

Dot Porter 2018

----

![PixPlot](https://yale-smithsonian.yale.edu/sites/default/files/images/pixplot-mk-sm.jpg)

---
## Metadaten 

***oder : ***

***... let’s do more work using data about the manuscript to organize our flat images in new and interesting ways...*** 

---

## Sparkling Metadata

1. Beispiel: Facettierung der Bildsuche über Iconclass in der digitalen Sammlung des Städel Museum [Link: Adam und Eva vor dem Sündenfall](https://sammlung.staedelmuseum.de/de/suche?scope=all&q=term(8849:iconclass))

2. Beispiel: Metadaten zum Trainieren von Bilderkennung und -clustering. Yale DH-Lab [Link: Meserve-Kunhardt Collection](https://yale-smithsonian.yale.edu/projects/exploring-meserve-kunhardt-collection)

----

## Metadaten ?

----

> Imagine data as information in any form sitting on shelves, in drawers, or boxes (objects, numbers, files). Metadata provides the labels for those entities and the organizational system in which they are stored.

Johanna Drucker 2021,52

----

Kurz gesagt: Metadaten sind Daten über Daten

----

> For digital ressources, two levels of metadata may be required - information about the original source ( e.g painting or film) and the digital file (who made it, when, in what format, and so on).

Johanna Drucker 2021,52

----

Metadaten beschreiben also einerseits das digitale Surrogat und andererseits das wiedergegebene Objekt.

----

| Thema | Surrogat | Objekt |
| ------ | ------ | ------ |
| Technik    | Rasterimage, Dateiformat TIFF,..    | Öl auf Leinwand, gebrannter Ton... |
| Urheber | Photodienst Museum XY | Michelangelo |
| Größe | 45 MB | 80 x 120 m ; 320 Seiten |
| usw.... | |

Reiche Metadaten beschreiben also das digitale Surrogat und das wiedergegebene Objekt.

----

> Ohne Metadaten zur Struktur sind die Seitenabbildungen oder die Textdateien, aus denen es besteht, so gut wie wertlos. Und ohne technische Metadaten über den Digitalisierungsprozess können Leser nicht sicher sein, wie genau die digitale Version die ursprüngliche Vorlage wiedergibt.

[Deutsches METS Tutorial](https://www.loc.gov/standards/mets/METSOverview.v2_de.html), Version 2, Abruf 2021

----

### Metadaten sind domänenspezifisch

Bücher, Zeitschriften, Manuskripte etc.

* Dublin Core TM [Website https://dublincore.org/](https://dublincore.org/)
* Resource Description and Access (RDA), [RDA Registry https://www.rdaregistry.info/](https://www.rdaregistry.info/)

----

Digitale Bücher, Manuskripte etc. 

* Metadata Encoding & Transmission Standard (METS) [METS - Einführung auf Deutsch](https://www.loc.gov/standards/mets/METSOverview.v2_de.html)

----

### Metadaten beschreiben Inhalte, Strukturen, Rechte

* Deskriptive Metadaten : *Titel, Abstract, Motive, Materialien ...*
* Operationale Metadaten : *Farbprofile, Gliederung der Bestandteile, Namespace ...*
* Administrative Metadaten : *Lizensierung, Urheber ...*

---

### Hands On 

Öffnen Sie: Drottningholm, Schloss, nordwestlicher Flügelbau, Bauaufnahme, Teilaufriss, Kopie nach Carl Hårleman
[https://www.graphikportal.org/document/gpo00319478](https://www.graphikportal.org/document/gpo00319478)

----

#### Fragen

* Wo wird die Druckgrafik aufbewahrt ?
* Wer stellt das digitale Surrogat zur Verfügung ?
* Aus wievielen Teilen besteht das analoge Objekt, aus wievielen das digitale Surrogat?
* Welche Rechte liegen vor ?
* Von welchen Informationseinheiten führen Informationen zu weiteren Informationen ? Nennen Sie einige Beispiele

----

### Technische Metadaten als Teil des Dokuments

> In die Datei einzubetten sind die Bezeichnung von genutztem Scanner, verwendeter Software, Auflösung in ppi, Datum und Uhrzeit des Scanvorgangs.

Deutsches Museum München

Fabienne Huguenin, AKMB-news 2/2019, 9

----

Beispiel: Bilddatenbank Arachne als Teil von i.DAI objects

[Digitales Surrogat Nr. 463541](https://arachne.dainst.org/entity/463541) für Datensatz zu [Objekt 1249171](https://arachne.dainst.org/entity/1249171)  der Marcussäule -> Bildmetadaten

---

## Normdaten, um Informationen zu vernetzen

----

> Hierzu zählen normierte Ansetzungen wie die Gemeinsame Normdatei (GND) für die genaue Identifizierung von Personen, Körperschaften und Schlagworten, und die GeoNames für die exakte Lokalisierung von Orten.

Fabienne Huguenin, AKMB-news 2/2019, 9

----

![Die Damstädter Madonna](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4e/Darmstadtmadonna.jpg/139px-Darmstadtmadonna.jpg)

Gemälde: "Die Darmstädter Madonna von **Hans Holbein dem Jüngeren**" (Öl auf Holz). Renaissance. Sammlung Würth, Schwäbisch-Hall

**Person** : Hans Holbein d. J., deutscher Maler  1497/1498-1543 =  [Getty ULAN 500005259](http://vocab.getty.edu/page/ulan/500005259), [GND 118552953](https://d-nb.info/gnd/118552953), [BnF ID 12030224](https://data.bnf.fr/fr/12030224/hans_holbein/), [VIAF ID 4945401](https://viaf.org/viaf/4945401/)

----

#### Getty ULAN - Union List of Artists names

* Künstler:innen, Sammler:innen, Kurator:innen ...
* Teil der digitalen Forschungsinfrastruktur des Getty Research Institute

mehr Informationen: [http://www.getty.edu/research/tools/vocabularies/ulan/about.html](http://www.getty.edu/research/tools/vocabularies/ulan/about.html)

----

#### GND - Gemeinsame Normdatei

* Gemeinsame Normdatei der Deutschen Nationalbibliothek
* War Sammlung von Personen, Körperschaften, Werke und Themen, um Publikationen zu katalogisieren. Wird zum zentralen Knoten für Normdaten im deutschsprachigen Raum ausgebaut (-> GND4C)
* Nutzung z.B. durch Kunsthistorisches Museum Wien [Beispiel](https://www.khm.at/de/object/fe73f687e5/)

mehr: Barbara K. Fischer 2021 in den AKMB-News 

----

#### VIAF - Virtual International Authority File

* Internationale Normdatei von Bibliotheken Im Verbund des [OCLC](https://www.oclc.org) (Online Computer Library Center)

----

Gemälde: "Die **Darmstädter Madonna** von Hans Holbein dem Jüngeren" (Öl auf Holz). Renaissance. Sammlung Würth, Schwäbisch-Hall

**Werk**: GND [4331511-2](https://portal.dnb.de/opac.htm?method=simpleSearch&cqlMode=true&query=nid%3D4331511-2), VIAF [207937698/](https://viaf.org/viaf/207937698/)

Wikidata [Q455319](https://www.wikidata.org/wiki/Q455319) (*hier auch der Beleg für das gezeigte digitale Surrogat*)

----

#### Wikidata 

* Kein kontrolliertes Vokabular, sondern eine kollaborative Datensammlung.
* Wird von Google zur Verbesserung der Suche genutzt (*kleiner Kasten rechts*)
* Zentraler Datenknoten im *'Semantic-Web'*

----

![Die Damstädter Madonna](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4e/Darmstadtmadonna.jpg/139px-Darmstadtmadonna.jpg)

Gemälde: "Die Darmstädter **Madonna** von Hans Holbein dem Jüngeren" (Öl auf Holz). Renaissance. Sammlung Würth, Schwäbisch-Hall

**Motiv**: Mutter Gottes stehend mit Christus auf dem Arm nahe an ihrer Brust

Iconclass [11F411(+5)](https://test.iconclass.org/11F41(%2B5))

----

#### Iconclass 

* Vokabular ab 1947 von Henri van de Waal zur Beschreibung von Bildmotiven entwickelt
* Wird inzwischen als *Linked Open Data* angeboten und vom niederländischen RKD gepflegt
* u. a. vom Bildarchiv Foto Marburg verwendet

mehr: [Alina Kühnl 2020](https://thearticle.hypotheses.org/9773)

----

**Gemälde**: "Die Darmstädter Madonna von Hans Holbein dem Jüngeren" **(Öl auf Holz)**. Renaissance. Sammlung Würth, Schwäbisch-Hall

**Gemälde** : Getty AAT [300033618](http://vocab.getty.edu/page/aat/300033618), PACTOLS [12471](https://pactols.frantiq.fr/opentheso/?idc=12471&idt=TH_1) 

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

Gemälde: "Die Darmstädter Madonna von Hans Holbein dem Jüngeren" (Öl auf Holz). 1526 n. Chr. **Renaissance**. Sammlung Würth, Schwäbisch-Hall

**Datierung **: Getty AAT [300021140](300021140), BnF Rameau [13318531w](https://catalogue.bnf.fr/ark:/12148/cb13318531w)

----

#### Rameau

* Vokabular zur Sacherschließung (Verschlagwortung) der Bibliotheque national de la France (BnF) und universitärer Bibliotheken
* Beschriebene Begriffe (Konzepte)

Webseite: [BnF Rameau](https://rameau.bnf.fr/)

----

![Sammlung Würth, Wikidata](https://upload.wikimedia.org/wikipedia/commons/thumb/5/5c/Schw%C3%A4bisch_Hall-Kunsthalle_W%C3%BCrth-_Niki_de_Saint_Phalle-04.jpg/110px-Schw%C3%A4bisch_Hall-Kunsthalle_W%C3%BCrth-_Niki_de_Saint_Phalle-04.jpg)

Gemälde: "Die Darmstädter Madonna von Hans Holbein dem Jüngeren" (Öl auf Holz). 1526 n. Chr. Renaissance. Sammlung Würth, **Schwäbisch-Hall**

* Getty TGN [7012708](http://vocab.getty.edu/page/tgn/7012708), geonames [28354581](https://www.geonames.org/2835481/schwaebisch-hall.html), GND [4053684-1](https://d-nb.info/gnd/4053684-1)

----

#### Getty TGN - Thesaurus of geographic Names Online

* Gazetteer (Verzeichnis von Toponymen und ggfs. weiteren geographischen Einheiten) des Getty Research Institute (Entwicklung und Pflege ähnlich ULAN und AAT)
* Als Linked Open Data angeboten

Webseite: [https://www.getty.edu/research/tools/vocabularies/tgn/](https://www.getty.edu/research/tools/vocabularies/tgn/)

----

#### geonames

* Gazetteer, das aus offiziellen US-amerikanischen Gazetteer hervorgegangen ist und inzwischen von einer offenen Community (wie Wiikipedia) weiter betrieben wird. 
* Sehr umfangreiche Informationen, Ortsnamen und geographische Bezeichnungen in vielen Sprachen. Keine systematische Kontrolle.
* Als Linked Open Data angeboten

Webseite: [https://www.geonames.org](https://www.geonames.org)

----

### Hands on

Dauer 10 min. + ~ 10 min. Erfahrungsaustausch

Wählen Sie eines der beiden PDFs (OLAT), markieren Sie darin einige Namen, Geographica und weitere Entitäten und reichern Sie sie an / referenzieren Sie sie auf eines der vorgestellen kontrollierten Vokabulare oder auch auf Wikidata.

----

### Praxis: Daten anreichern ? (A)

* [Openrefine](https://openrefine.org) für **strukturierte Daten insbesondere Tabellen** mit Personennamen, Ortsnamen, Gattungsbegriffen etc., "einfache" Nutzung mit Wikidata, GND, Getty ULAN und AAT

Links : [Einstieg](https://openrefine.org/documentation.html) und [Reconcilation](https://docs.openrefine.org/manual/reconciling), GND mit [lobid-gnd](https://blog.lobid.org/2018/08/27/openrefine.html), Video Openrefine und [Wikidata](https://youtu.be/q8ffvdeyuNQ), Openrefine und [Getty Vocabulars](https://www.getty.edu/research/tools/vocabularies/obtain/openrefine.html)

----

### Praxis: Daten anreichern ? (B)

* [Recogito](https://recogito.pelagios.org/) um unstrukturierte Daten aus Texten (z. B. Katalogtexte) und Bildern (z.B. historische Karten, Fotografien) zu gewinnen.

Link: [10 Minuten Tutorial](https://recogito.pelagios.org/help/tutorial)

----

### Normdaten selbst ansetzen ?

Frage: Und wenn es die Person, das Ereignis, die Objektgruppe nicht gibt oder die Konzepte nicht passend sind ?

Langfristig z.B. [GND4C](https://gnd.network/Webs/gnd/DE/Home/home_node.html)

Kurzfristig z.B. bei Wikidata anlegen. Hinweise dazu im [Community-Portal](https://www.wikidata.org/wiki/Wikidata:Community_portal)

----

### Take away

* Normdaten sind festgelegte Label/Bezeichner für Entitäten (Personen, Orte, Ereignisse, Werke, ...) und Konzepte (Stil, Material, Technik, Objekttyp, Gattung, ...)
* Normdaten können maschinenlesbar und mit einer URI hinterlegt sein (-> Semantic Web)
* Normdaten werden oft von Bibliotheken (DNB, BnF), Museen/Sammlungen (Iconclass), Denkmalbehörden (PACTOLS) und Forschungseinrichtungen (Getty ULAN, AAT) entwickelt und betreut

---

## Ontologien, um Datenbestände zu vernetzen

----

> Ist der Ortsname, den Sie exportieren möchten, ein Name für den Herstellungsort oder den Standort in Ihrer Sammlung? Handelt es sich beim Personennamen um einen Künstler oder ehemaligen Besitzer des Kunstwerks?

arthistoricum.net: Graphik vernetzt zum LIDO Handbuch 

----

### Was ist also was ?

![Mapping](https://www.researchgate.net/profile/Manvi_Siwach/publication/280912167/figure/fig4/AS:669964532985870@1536743400627/Mapping-of-two-Ontologies.png)

A Novel Design of Hidden Web Crawler using Ontology - Scientific Figure on ResearchGate. Available from: https://www.researchgate.net/figure/Mapping-of-two-Ontologies_fig4_280912167 [accessed 24 Jan, 2022]

----

### Ontologien vs. Normdaten ?

> Confused? Don't be. Think of taxonomies as sets of names (What should I call it?), and ontologies as model of knowledge (Where does it belong in the scheme of things).

Johanna Drucker 2021, 59.

----

#### Eselsbrücke 

A sagt: *Hast Du mein Schloss gesehen?*

B sagt: *Sie ist rechts.*

* Welcher Satz wird mit einem Begriff aus der GND oder dem Getty AAT eindeutig? -> Thesaurus, Taxonomie

* Für welchen Satz muss ich Kontextwissen haben?  -> Ontologie

----

> A computational ontology is a system for organizing knowledge that describes and defines relationships among things within a domain.

Jana Millar Usiskin, Christine Walde, Caroline Winter 2020, 184 f.

----

### Sinn von Ontologien ?

Ontologien bestehen aus Klassen und Subklassen, die in definierten Beziehungen zueinander stehen und darüber Eigenschaften teilen.
Regeln klären die Beziehungen und tragen zur Datenqualität bei.

----

#### 1. Beispiel einer fiktiven Ontologie 

Picasso ist eine Instanz (~Verwirklichung) der Klasse *Künstler:in*. 

*Künstler:in* ist eine Subklasse von *Mensch*. 

Ein *Ereignis*, das die Klasse Mensch betrifft, ist die *Geburt*. 

Picasso kann ein *Geburtsdatum* und *Geburtsort* haben. 

----

#### 2. Beispiel

Picasso ist eine Instanz von Künstler:in.

*Schriftsteller:in, Maler:in, Sänger:in, Fotografin:in, Tänzer:in, Keramiker:in*  sind Teil des Konzepts Künstler:in

Picasso kann gleichzeitig zu *Maler:in, Fotograf:in, Keramiker:in* gehören. 

----

### CIDOC CRM

* Ontologie, um Informationen zu Objekten des kulturellen Erbes und sie betreffende Aktivitäten systematisch zu erfassen und zu beschreiben. 

	- *top-level  ontology*, weil sie auf den Grundeinheiten beruht
	- *domain ontology*, weil sie einen klaren fachlichen Fokus hat

----

> * a generic model of recording of “what has happened” in
human scale
>* can generates huge, meaningful networks of knowledge by
a simple abstraction: history as meetings of people, things and
information.

Georg Bruseker, Anais Guillem, The function and use of CIDOC CRM ans its Extensions. Präsentation 2019 [PDF](https://masa.hypotheses.org/files/2019/10/1.-CIDOC-CRM-Intro-5.pdf)

----

#### Physical Man-made Thing oder Physical Object

Definition of the CIDOC Conceptual Reference Model, vers. 7.2, September 2021,  [PDF](https://cidoc-crm.org/Version/version-7.2)

* Definition E18

* Definition E24

[Übersicht als Grafik](https://cidoc-crm.org/sites/default/files/CIDOC-501.PNG)

----

![Faustkeile, Libyen](https://upload.wikimedia.org/wikipedia/commons/thumb/6/62/Gro%C3%9Fe_Faustkeile.JPG/180px-Gro%C3%9Fe_Faustkeile.JPG)

* ein Meteroit ....

* ein Faustkeil ....

* Aber! beide Objekte können im 19. Jahrhundert zusammen ausgestellt worden sein

----

#### Physical Man-made Thing oder Information Object ?

* Definition E24

* Definition E55

----

* ein Gedicht ....

* ein Gemälde ....

* ein Buch ....

----

#### eine Nummer, viele Bedeutungen

* Nummern sind in CIDOC CRM zusammen mit Zeichenketten und Zeitangaben *Primitive values*. Sie können also ganz verschiedene Bedeutungen haben
* Jahreszahl, Gewicht, Anzahl von etwas, ID ....

----

#### Ereignisse im Mittelpunkt

> Ein Schlüsselkonzept des CIDOC CRM ist es, Aussagen über Objekte an Ereignisse seiner Geschichte zu binden. Dieses ereigniszentrierte
Vorgehen ermöglicht es, Eigenschaften von Objekten mit Bezügen zu beteiligten Akteuren oder Ort und Zeit präziser abzubilden. 

LIDO-Handbuch 1: Graphik (2019- ), S. 13 [https://doi.org/10.11588/arthistoricum.382.544](https://doi.org/10.11588/arthistoricum.382.544)

----

> Es unterstützt dadurch das (automatische) Aufdecken von Zusammenhängen zwischen ursprünglich verstreuten Informationen und trägt so zur Kontextualisierung der Objekte bei. Das CIDOC CRM gibt nicht den Inhalt der Dokumentation von Museumsobjekten vor, sondern legt Regeln für die logische Verknüpfung von Informationen fest.

Ebenda

----

#### Eigenschaften im CIDOC CRM

* Die Eigenschaften einer Entität machen den Unterschied aus. Ein Meteroit kann nicht die Eigenschaften von "place" haben, z.B. *P122 borders with*

* ein Gemälde hat keine *P191 had duration (was duration of)*, wohl aber die Ausstellung, auf der es erstmals gezeigt wurde

* eine Person (E21) wird geboren -> *P98 brought into life (was born)*.  Ein Stuhl (E24) wurde hergestellt -> *P108 has produced (was produced by)*

----

### Take away

* Domänen-spezifische Ontologien beschreiben Konzepte und mit ihnen verbundene Eigenschaften in einem bestimmten Wissensgebiet.

* CIDOC CRM ist eine umfassende Ontologie zur Beschreibung von Kunst- und Kulturgut, die von ICOM getragen wird.

* Die Beschäftigung mit CIDOC CRM unterstützt das konzeptionelle Verständnis der eigenen Arbeit mit Daten. 

---

## Umsetzungen von CIDOC CRM

----

### LIDO XML

* LIDO – *Lightweight Information Describing Objects* ist eigentlich ein Standard, um Daten zwischen verschiedenen Datenbanken zu verbinden. z.B. um Daten in der [Deutschen Digitalen Bibliothek](https://www.deutsche-digitale-bibliothek.de/) und damit der [Europeana](https://www.europeana.eu) zusammenzuführen.
* Wird von einer Arbeitsgruppe der ICOM betreut.
* Ist in XML verfasst.

----

> Es funktioniert so, dass jeder Information aus Ihrer Datenbank ein LIDO Element zugewiesen wird, das beschreibt, um welche Art von Information es sich handelt. Ist der Ortsname, den Sie exportieren möchten, ein Name für den Herstellungsort oder den Standort in Ihrer Sammlung? ... Diese Fragen beantwortet das zugewiesene LIDO Element. 

Quelle: [arthistoricum.net](https://www.arthistoricum.net/netzwerke/graphik-vernetzt/lido-handbuch-graphik)

----

#### Aus dem Handbuch zum "Bildinhalt"

Eigene Datenbank: "Porträt  von Martin Luther"

* Schritt 1: Anreichern mit GND für Person Martin Luther
* Schritt 2: Zuweisen des eigenen Datenbankfeldes zum LIDO-Element   

*Subject (subject) → Subject Actor Set (subjectActor) mit → Actor Identifier (actorID) und → Name Actor Set (nameActorSet)*

LIDO-Handbuch, Kapitel "8. Block: Thema Bildinhalte", S. 111-115

----

### Hands On

| Link Bildindex | Link XML-Dokument |
|:---|:---|
| [https://www.bildindex.de/document/obj05091715?part=1](https://www.bildindex.de/document/obj05091715?part=1) |  [https://www.graphikportal.org/lido-examples/Albrecht_Duerer.xml](https://www.graphikportal.org/lido-examples/Albrecht_Duerer.xml) |

* Finden Sie im XML die Angaben zur Datierung, zur Rolle Albrecht Dürers, zum Entstehungsort.

* Was enthalten die *administrative metadata* ?

----

### Linked Art Data Model

* [Linked Art Data Model](https://linked.art/model/) ist ein community-basiertes Format um Daten aus Einrichtungen des kulturellen Erbes (insbes. Museen) auszutauschen
* das Model richtet seinen Blickwinkel auf die Integration der Daten in Applikationen 
* eine Arbeitsgruppe zu Linked Art Data Model ist ICOM zugeordnet
* die Daten werden in JSON-LD abgelegt -> Semantic Web

----

#### Ein Beispiel

The physical thing is classified as being a Painting, and the concept "Painting" is for classifying the type of object.

	{
	 "@context": "https://linked.art/ns/v1/linked-art.json",
	  	"id": "https://linked.art/example/object/20",
	  	 "type": "HumanMadeObject",
		 "_label": "Simple Example Painting",
		 "classified_as": [
           {
             "id": "http://vocab.getty.edu/aat/300033618",
             "type": "Type",
            "_label": "Painting"
          },
    	     {
           "id": "http://vocab.getty.edu/aat/300133025",
           "type": "Type",
           "_label": "Work of Art"
         }
       ]
    }

Gehe zu [JSON-LD playground](http://json-ld.org/playground-dev/#startTab=tab-expanded&copyContext=true&json-ld=https%3A%2F%2Flinked.art%2Fexample%2Fobject%2F21)

----

#### Doing LOUD things

> If our data isn't used, then no value is gained from the resources that were invested in its creation, publication, maintenance and improvement. If we want our data to be used, then it needs to be usable: Linked Open Usable Data.

Webseite [Linked Art Data Model zu LOUD](https://linked.art/loud/), Abruf Januar 2022

----

### Take Away 

* LIDO XML ist ein maschinenlesbares Austauschformat. Es ermöglicht die Integration verschiedener Datenbestände in zentralen Hubs, ohne dass die eigenen Daten umgeschrieben werden müssen. 
* Linked Art Data Model ist ein auf das Semantic Web ausgerichtetes Daten Model, dass die Nutzung der Daten erleichtern soll. 
* CIDOC CRM ist für beide der konzeptionelle Referenzrahmen. Beide beziehen Normdaten/kontrollierte Vokabulare ein (Getty AAT, GND usw.) 

---

## Umsetzung

* Was sind aus Ihrer eigenen Arbeit die wichtigsten Aspekte ? *Usability* der Daten? Datensichtbarkeit ? Datenqualität ?
* Worin sehen Sie die Vorteile einer zentralistischen und worin die Vorteile einer föderalen Vorgehensweise ?

---

Vielen Dank !

Kontakt: aklammt@dfk-paris.org, @archaeoklammt

----

##### Literatur

* Bussche, Ruth von dem. 2019. „Link my data - Normdaten als Dreh- und Angelpunkt für wissenschaftliche Anwendungen“, AKMB news, 25.2: 44–47.

* Clobridge, Abby. 2010. „1 - Introduction“. In Building a Digital Repository Program with Limited Resources, herausgegeben von Abby Clobridge, 3–11. Chandos Information Professional Series. Chandos Publishing. https://doi.org/10.1016/B978-1-84334-596-1.50001-8.

----

* Drucker, Johanna. 2021. The Digital Humanities Coursebook. An Introduction to Digital Methods for Research and Scholarship. London, New York.

* Fischer, Barbara Katharina. 2021. „Das Wenn-Dann-Prozip oder Normdaten brauchen eine Lobby“, AKMB-news: Informationen zu Kunst, Museum und Bibliothek, 27: 20–25.

----

* Huguenin, Fabienne. 2019. „Deutsches Museum digital“, AKMB news, 25.2: 3–11.

* Knaus, Gudrun, Regine Stein, und Angela Kailus. 2019. LIDO-Handbuch für die Erfassung und Publikation von Metadaten zu kulturellen Objekten. Graphik. Bd. 1. Heidelberg: arthistoricum.net.

----

* Lincoln, Matthew D. 2020. „Computer Vision’s Digital Surrogates, and Implications for Collections Management Technology“. Matthew Lincoln, PhD (blog). 21. November 2020. https://matthewlincoln.net/2020/11/21/new-digital-surrogates.html.

* Millar Usiskin, Jana, Christine Walde, und Caroline Winter. 2020. „Ontologies for Digital Humanities“. In Doing More Digital Humanities, 184–98. London, New York.

----

* Porter, Dot. 2018. „The Uncanny Valley and the Ghost in the Machine: A Discussion of Analogies for Thinking about Digitized Medieval Manuscripts“. Dot Porter Digital (blog). 31. Oktober 2018. http://www.dotporterdigital.org/the-uncanny-valley-and-the-ghost-in-the-machine-a-discussion-of-analogies-for-thinking-about-digitized-medieval-manuscripts/.

* Rohde-Enslin, Stefan. 2020. „Das Innere nach außen kehren? Inventarisieren mit Publikationsanspruch“. In Das digitale Objekt – Zwischen Depot und Internet, herausgegeben von Andrea Geipel, Johannes Sauter, und Georg Hohmann, 7:25–38. Deutsches Museum Studies. Deutsches Museum Verlag.

----

* „The Santa Barbara Statement on Collections as Data“. o. J. Always Already Computational - Collections as Data. Zugegriffen 27. Januar 2022. https://collectionsasdata.github.io/statement/.

----

##### Bildbeleg

ArtNews 2017: ArtNews, The Louvre was the ‘Most Instagrammed Museum’ in 2017. published 29.11.2017 https://www.artnews.com/art-news/news/louvre-instagrammed-museum-2017-9392/


M7hvBpAZ4Bm1gjZ3bhuH

