# Bestandteile der Applikation (Module und Klassen)

Alle entwickelten Bestandteile des Projekts befinden sich im Plone-Add-On 
**edi.substanceforms**. Dieses Add-On beinhaltet beinhaltet Content-Types (Artikeltypen), 
mit denen in Plone die Inhalte gepflegt werden, sowie alle benötigten Formulare und Ansichten 
(Forms und Views), für das Management der Chemikalienprodukte mit dem CMS Plone. Die Bestandteile 
der Applikation werden in den folgenden Abschnitten detaillierter beschrieben.

Für die Erstellung der Plone-Inhaltstypen (Content-Types, Viewklassen, Viewtemplates...) kommt der 
Generator [mr.bob](https://pypi.org/project/mr.bob) zum Einsatz. Dieser ermöglicht den Fokus auf 
die essentielle Programmierung und Anpassung der Inhaltstypen durch massive Zeitersparnisse gegenüber 
einer vollständigen manuellen Programmierung.

## Artikeltypen für die Pflege von Inhalten

Die Content-Types haben für die Autoren und Redakteure eine besondere Bedeutung.
Mit deren Hilfe werden in der Struktur der Plone-Site Inhalte angelegt um diese
für Benutzerinnen und Benutzer zu präsentieren.

Daneben können in den Content-Types Daten gespeichert werden, die für die Steuerung
der Anwendung benötigt werden. Das Package edi.substanceforms beinhaltet folgende
Content-Types:

### Datenbank

Die Datenbank **Emissionsarme Produkte** kann mit diesem Artikeltyp an beliebiger
Stelle in der Inhaltsstruktur der Website eingebunden werden. Die Autoren und Redakteure
können mit entsprechenden Feldern die Datenbank beschreiben und für die Benutzerinnen
und Benutzer präsentieren. Außerdem stellt die Datenbank die technische Verbindung
zur physikalischen Datenbank her. D.h. es werden mit diesem Artikeltyp alle notwendigen
Parameter für die Verbindung zur Datenbank gespeichert.

Aus der Sicht des Web-CMS-Plone stellt die Datenbank einen Ordnertyp dar in dem Objekte
vom Content-Type Tabelle gespeichert werden.

### Tabelle

Der Content-Typ Tabelle stellt die technische Verbindung zu den Tabellen der physikalischen
Datenbank her. Bereits beim Anlegen des Content-Types in Plone wird der Autor und Redakteur
gefragt, welche der Tabellen der Datenbank angezeigt werden soll. Mit dem Content-Typ Tabelle
wird die Absicht verfolgt, im Context einer Tabelle die darin gespeicherten Datensätze
anzuzeigen als wären sie selbst als Objekte im CMS Plone gespeichert.

Aus der Sicht des Web-CMS Plone stellt die Datenbank ebenfalls einen Ordnertyp dar, in dem
Dateiobjekte (Bilder, PDF-Dateien) gespeichert werden, die für die Präsentation der Datensätze,
also z.B. Hersteller, Chemikalienprodukte benötigt werden. Für die Speicherung dieser Objekte
wird ganz bewusst die objektorientierte Datenbank genutzt. In den Datensätzen werden Referenzen
zu den Dateiobjekten gehalten.

## Formulare

Formulare werden nach dem CRUD-Begriff (**CR**eate, **U**pdate, **D**elete)  für folgende 
Anwendungsfälle benötigt:

- **Hinzufügen** von Datensätzen in die Datenbank (create)
- **Aktualisierung** von Datensätzen in der Datenbank (update)

Das **Löschen** von Datensätzen wird mit einem funktionalen View realisiert.

Ausserdem wird ein Formular für die Suche von Datensätzen in der Datenbank benötigt.

## Views

### Einzelansicht für die Datenbank

In der Einzelansicht der Datenbank (datenbank_view.pt) werden die vorher ebenfalls zum CMS hinzugefügte 
Tabellen aufgelistet. Die Tabellen sind die Kind-Elemente einer Datenbank oder mit anderen Worten: die
Inhalte des Ordners Datenbank. Eine Tabelle repräsentiert ihrerseits Hersteller oder Chemikalienprodukte.

### Einzelansicht für die Tabelle

Die Einzelansicht für die Tabelle (tabelle_view.pt) dient dem Listing aller Datensätze in der Tabelle und 
enthält entsprechende Suchparameter, nach denen die Trefferliste bei Bedarf gefiltert werden kann. So ist 
beispielsweise die Anzeige aller Gefahrstoffgemische möglich, die vorher als Sonderreiniger definiert wurden.

### Einzelansicht für Hersteller und Gefahrstoffprodukte

Für jede Art der Gefahrstoffprodukte gibt es eine individuelle Ansicht (Viewtemplate). In diesem Viewtemplate 
wird eine HTML-Tabelle generiert, in der die entsprechenden Eigenschaften des Produktes zur Anzeige gebracht werden.

Beispiel:

| Merkmal             | Eigenschaft       |
|---------------------|-------------------|
| Flammpunkt          | > 70 Grad Celsius |
| Hautschutzkategorie | wasserlöslich     |
| Inhaltsstoffe       | Aceton > 2% < 10% |


 Außerdem erfolgt hier die Darstellung der gespeicherten Bilder. Folgende Viewtemplates sind vorhanden:

- substance_view.pt
- substance_mixture_view.pt
- spray_powder_view.pt
- manufacturer_view.pt

Viele in der Datenbank gespeicherten Werte sind Schlüsselwerte, die nicht ohne Übersetzung lesbar sind. 
Daher erfolgt in der Viewklasse single_view.py, welche allen Einzelansichten zugrunde liegt (Prinzip Vererbung), 
die Schlüssel-/Wert-Zuweisung bzw. die Übersetzung von Werten für die Benutzer.

## Funktionale Views

Ein funktionaler View zeichnet sich dadurch aus, entweder kein eigenes Template zu besitzen, oder eines 
das auf die Bestätigung einer Aktion beschränkt ist. Zu den funktionalen Views gehören:

- single_view
- selector_view
- delete_view

So besitzt bespielsweise der Delete View ein Template zur Bestätigung des Löschens des Artikels per 
Auswahl einer Checkbox, während in den single-view alle Methoden der Einzelansichten ausgelagert wurden.

*[Add-On]: Funktionale Erweiterung einer Software, hier: des Web-CMS Plone
*[CMS]: Content Management System
