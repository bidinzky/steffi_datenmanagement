---
title: Datenmanagement
description: View the slide with "Slide Mode".
---

## LV-Ziele

**Aufgaben des Datenmanagements**
* Verschiedenen Datenbankarchitekturen und Funktionsprinzipien.
* Entity-Relationship(ER)-Modelle und von relationalen Datenmodelle und deren Sprachelemente.
* Erstellung eines ER-Modells auf der Basis eines Teilausschnitts der
unternehmerischen Realität ein dementsprechendes ER-Modell erstellen.
* Überführung in ein relationales Datenmodell und Implementation mit SQL-Befehlen.
* Normalisierung ein gegebenes relationales Datenmodell bis zur 3. Stufe.
* Datenaustauschformate inklusive deren Notations- und Speicherform sowie deren
Einsatzbereich und Datenübertragungsprotokolle in verteilten Systemen.
* Beschreibung von Softwarekompenenten und -architekturen
sowie deren Einsatzbereich sowie Funktionalität erläutern.

---

# Datenbanken

Referenz: UTB3_Datenanken_02_Ueberblick

---

## Grundlegende Begriffe

1. Datenbank (DB): geordnete, selbstbeschreibende Sammlung von Daten, die in Beziehung stehen.
2. Datenbanksystem (DBS): DB + Datenbank Managemensystem (DBMS) + Kommunikationsschnittstelle.



| Tabelle | Relationale Datenbank| Entity-RelationshipModell (ERM)  | Unified  Modeling Language (UML) |
| -------- | -------- | -------- | ---- |
| Wertebereich (Domäne, Domain)   | --""--  |  --""--    | --""-- |
| Kopfzeile | Relationstyp Relationsformat Relationsschema | Entitätstyp | Klasse | 
| Spaltenüberschrift | Attribut | Attribut | Attribut |
| Inhalt | Relation | Entitätsmenge | Objektmenge Instanzmenge |
| -- | Fremdschlüsselbeziehung | Beziehung | ASsoziation |
| Zeile | Tuple | Entität | Objekt, Instanz |
| Zeile | Attributswert | Attributswert | Attributswert |


---

## "Arten" von Datenbanken

1. relationale DB: Daten liegt in Tabellen
    * Pro: schnell
    * Contra: komplexe Objektstrukturen nicht intuitiv darstellbar (z.B. Eltern-Kind, Student-Jahrgang, ...)
3. objektorienteierte DB: Daten in form von Objekten
    * Pro: Objektsturkturen intuitiv darstelbar 
    * Contra: langsam
3. objketrelationale DBMS: verbindung der Vorteile von relationalen und objektorientierten DBs

---

## Anforderungen einer Datenbank

1. Persistenz: Daten langfristig speichern
2. CRUD (Create, Read, Update, Delete): meist mit Schwerpunkt auf Read
3. Verwaltung des Datenschemas (Kontext/Relationen) der Daten

---

## Datenbankdesign

1. Konzeptionelle Modelle => Logische Struktur => Entity-Relationship-Modell => Welche Daten will ich darstellen/speichern.
2. Implemantative Modelle => Speicherstruktur => relationales Datenbankmodell => Wie will ich die Daten darstellen/speichern.

Beide Modelle sind meistens Notwendig und Sinnvoll!

---

# Datenbankentwurf 

*Referenz: UTB3Datenanken03Entwurf*

Datenbankentwurf ist ein Teil der Wirklichkeit, welche für die betriebliche Informationsverbarbeitung wichitg ist, zu beschreiben:
> A database represents some aspect of the real world, sometimes
> called the miniworld or the universe of discourse (UoD).

---

### Früher

siehe ANSI SPARC

### Heute (semantische Modellierung)

![](https://i.imgur.com/j6kj4uL.png)

### Unterschiede


Das **Was** ist abstahiert und aus Managementsicht entscheidened.
Das **Wie** besser Experten zu überlassen ist.

Bei ANSI SPARC ist dies nicht gut getrennt --> in der semantischen Modellierung gut getrennt (Was: ER-Modell, Wie: relationales Schema).

--> das sematische Modell erleichtert Kommunikation zwischen Management und IT (für Laien lesbar und für IT eindeutig)

---

## Gutes vs Schlechtes Datenbankkonzept

Bei einem guten Datenbankkonzept geht es nicht um Entities, Tabellen, etc. sondern um reale Objekte, Informationen, Zusammenhänge, etc.
**Nicht zu technisch Denken!** und auch inhaltich abklären welche Daten zu erfassen sind.
#### User werden kreativ wenn sie:
    1. Daten nich angeben können obwohl sie wollen (Extrainformationen)
    2. Daten nicht erforderlich sind (zuviel Information notwendig)
    3. Daten fehlerhaft, doppel sind (unsinnige Informationen)

---
## Wie erstellt man ein sematisches Modell?

Entity-Relationship-Modelle nicht standardisiert --> zum Teil in gleicher Firma unterschiedliche "Dialekte"
--> Unified Modeling Language (UML) Diagramme als stndardisierte Lösung
*    Klassendiagramme
*    Objektdiagramme

---

## sematische Modellierung vorgehen

1. Daten auf klar idenifizierbare und unterscheidbare **Objekte** (sowohl der realität als auch des Denkens) durchsuchen --> Entities/Objekte
2. Untersuchung der **Beziehungen** zwischen diesen Objekten --> Relationship/Association 
    * Kann eine Zahl sein z.B. ein Kurs hat mindestens 5 und maximal 12 Teilneihmer (Kardinalität)
    * aber auch ob eine Beziehung vorhanden ist z.B. ein Student kann muss aber keinen Abschluss haben (Optionalität)
3. Untersuchung der **Eigenschaften** dieser Objeken
    * **identifizierende** Eigenschaften vs sonsitige Eigenschaften
    * Art der Eigenschaft (Typ --> z.B. Text, Zahl)
    * Wertebereich der Eigenschaft (z.B. Noten nur zwischen 1-5)
    

---

## sematische Modellierung vorgehen 2

* zwei Betrachtungsebenen
    * einzelne Objekte (Exemplar)
    * Gruppe von Objekten (Typen, Klassen)
* Entity Typen sind eine Sammlung von Entties mit den selben Attributen
* Alle Entities eines Types haben zwar die gleichen Attribute aber besitzen ihre eigene Werte (z.B. Alter)

---

## sematische Modellierung vorgehen 3

![](https://i.imgur.com/Jn4B4Zy.png)

---

## sematische Modellierung vorgehen 4

![](https://i.imgur.com/2SirHIQ.png)

---

## ER-Modellierung

* Entity Typen werden zu Tabellen
* Entities werden zu Zeilen (bzw. deren Werte werden zeilenweise eingetragen)

---

## ER-Modellierung 2

![](https://i.imgur.com/4m8bGPs.png)

---
## ER-Modellierung 3

1. ![](https://i.imgur.com/hx1qKRJ.png) sind Entities (Objekte)
2. ![](https://i.imgur.com/fV17i4W.png) sind Relationen (Beziehungstypen)
3. ![](https://i.imgur.com/xkSLVd3.png) sind Attribute (Eigenschaften)
4. ![](https://i.imgur.com/r6Ez9G7.png =60%x100%) sind Kardinalitäten (Beziehungen)
5. ![](https://i.imgur.com/44LFzox.png =60%x100%) Generalisierung / Spezialisierung 

---

## ER-Modellierung 4 / Kardinalitäten

1. Chen: Wieviele Objekte sind einem Objekt höchstens zugeordnet
![](https://i.imgur.com/HLHY5Qz.png)
Eine Bestellung entöhlt viele (n) Bestellposten.<br>
Ein Bestellposten ist einer Bestellung zugeordnet.
    1. 1:1 => Ein Objekt is einem anderem zugeordnet
    2. 1:n => Mehrere Objekte sind einem Objekt zugeordnet
    4. n:1 => Ein Objekt ist mehreren Objekten zugeordnet
    5. n:m => Mehrere Objekte sind mehreren Objeketen zugeordnet
2.  Schlageter-Stucky: Mit wieviel Objeketen  steht ein Objekt in Beziehung
![](https://i.imgur.com/rFVURs2.png)
Ähnlich wie Chen nur Leserichtung "umgedreht"<br>
Erlaubt Auflösung von komplexeren Beziehungen
    | Kürzel | Bedeutung | Beispiel |
    | -------- | -------- | -------- |
    | k     | k-mal     | 5     |
    | [n,m] | mindesten n, maximal m | [2,6] |
    | * | 0 oder mehr | 8 |
    | + | 1 oder mehr | 1 |
    | c | 0 oder 1 | 0 |

3. ISO: Mit wie vielen OBjekten steht ein Objekt minmal und maximal in Beziehung
![](https://i.imgur.com/4ja8ziE.png)
4. Modified-Chen (MC): wie Chen nur mit extras :smiley:
    1. c => 0 oder 1
    2. m => mulitple

    Der unterschied ist, dass 1 in MC bedeutet mindestens 1<br>
    | Chen | Modified-Chen |
    | --- | --- |
    | 1:1 | c:c |
    | 1:N | c:mc|
    | 1:N + total participation| 1:mc|
    | M:N | mc:mc|
    | total part. + 1:1 | c:1|
    | total part. + 1:1 + total part.| 1:1|
    |total part. 1:N + total part. | 1:m|
    |total part. + M:N | mc:m |
    |total part. + M:N + total part.| m:m|
5. Chen mit Min-Max Kennzeichnung (für Vorlesung)
Mischung aus Chen und ISO + '0' für keins oder mehrere und '1' für eins oder mehr
 ![](https://i.imgur.com/aqs5FSh.png)
Eine Bestellung enthält mehrere Bestellposten (1:n) und ein Bestellposten ist in einer Bestellung enthalten (1:1). Eine Bestellung enthält mindestens 1 Bestellposten und ein Bestellposten ohne Bestellung gibt es auch nicht!
![](https://i.imgur.com/63zFqOW.png)
Ein Student kann Bücher ausleihen muss aber nicht (0:n) und ein Buch kann von einem Studenten ausgeliehen sein muss aber nicht (0:1).
6. Crow's Foot / Martin Notation: grafische Darstellung einer Notation
![](https://i.imgur.com/d7WtM2S.png =50%x)


---

## Unified Modeling Language (UML)

Standardisierte Diagramme um Kommunikation zu vereinfachen.
![](https://i.imgur.com/HHG9Hr3.png)

---

# Datenbankschema

Beschreibt die Struktur und Art der Daten einer Datenbank.

1. Welche Tabellen gibt?
2. Für jede Tabelle: Welche Spalten gibt es?
3. Für jede Spalte:
    4. Welcher Datentyp?
    5. Nullable?
    6. Defaultwert?
    7. Constraints (Einschrenkung des Wertebereichs)
5. Primärschlüssel?
6. Fremdschlüssel?
7. Indizes?

---

## Architektur eines DBMS

![](https://i.imgur.com/F6DyINy.png)

---

## Architektur eines DBMS - Einschichtig

* Alles auf einem PC (z.B. SqlLite)
* Im Unternhemensumfeld oft nicht sinnvoll (z.B. wegen Wartung, Skalierbarkeit, ...)
![](https://i.imgur.com/rUuGJNc.png)

---
## Architektur eines DBMS - Zweischichtig

Unterscheidung zwischen Intelegentem Server oder Client
### Intelligenter Client

![](https://i.imgur.com/sBPRAWL.png)

* Daten müssen nur einmal Übertragen werden, Bearbeitung kann selbständig erfolgen
* Client benötigt entsprechende Resourcen (Rechenleistung) um komplexe Verbeitungen durchzuführen


### Intelligenter Server

![](https://i.imgur.com/0eqXnVr.png)

* Clients benötigen nicht viel Rechenleistungs selbst für komplexe Verarbeitungen
* Server muss basierend auf den Usern Skaliert sein (oft Engpass)

### Hybride Lösung

Server und Client teilen sich die Verarbeitung basierend auf den Anforderungen <br> so können rechenintensive Auswertungen z.B. Täglich in der Nacht auf dem Server durchgeführt und dann gecached dem Client übergeben werden <br> kleiner Auswertungen aber direkt vom Client beim Verwenden erstellt werden+

---

## Architektur eines DBMS - n-schichtig

Auftrennung der Layer zum teil mit extra Redundanz.
![](https://i.imgur.com/ecCyfE1.png)
