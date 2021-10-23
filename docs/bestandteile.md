# Bestandteile der Applikation (Module und Klassen)

Alle entwickelten Bestandteile des Projekts befinden sich im Plone-Add-On 
**edi.substanceforms**. Dieses Add-on beinhaltet beinhaltet Artikeltypen 
Content-Types (Artikeltypen), mit denen in Plone die Inhalte der Seiten gepflegt werden,
sowie alle benötigten Formulare und Ansichten (Forms und Views), für das Management
der Chemikalienprodukte mit dem CMS Plone. Die Bestandteile der Applikation werden
in den folgenden Abschnitten detaillierter beschrieben.

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
wird die Absicht verfolgt im Context einer Tabelle die darin gespeicherten Datensätze
anzuzeigen als wären sie selbst als Objekte im CMS Plone gespeichert.

Aus der Sicht des Web-CMS Plone stellt die Datenbank ebenfalls einen Ordnertyp dar, in dem
Dateiobjekte (Bilder, PDF-Dateien) gespeichert werden, die für die Präsentation der Datensätze,
also z.B. Hersteller, Chemikalienprodukte benötigt werden. Für die Speicherung dieser Objekte
wird ganz bewusst die objektorientierte Datenbank genutzt. In den Datensätzen werden Referenzen
zu den Dateiobjekten gehalten.

## Formulare

Formulare werden nach dem CRUD-Begriff (**CR**eate, **U**pdate, **D**elete)  für folgende 
Anwendungsfälle benötigt:

Hinzufügen von Datensätzen in die Datenbank (create)
Aktualisierung von Datensätzen in der Datenbank (update)

Das Löschen von Datensätzen wird mit einem funktionalen View realisiert.

Ausserdem wird ein Formular für die Suche von Datensätzen in der Datenbank benötigt.

## Views

### Einzelansicht für die Datenbank

Sinn: Listing der Tabellen, die ihrerseits wiederum Hersteller oder Chemikalienprodukte
repräsentieren

### Einzelansicht für die Tabelle

Sinn: Suchforms für die Hersteller oder Chemikalienprodukte und Listing der Treffer

### Einzelansicht für Hersteller und Gefahrstoffprodukte

### Funktionale Views

- Delete View
- ...

## Hier Seppos Inhalte, die noch in die richtige Struktur eingeordnet werden müssen.

Mein Projekt beinhaltet hier die 
Entwicklung aller Einzelansichten und Formulare, wehalb ich auf die 
anderen  Bestandteile des Add-Ons nicht mehr weiter eingehen werden.
Das Projekt beinhaltet nun also die folgende Module:

Viewklassen:
single_view.py

Page-Templates für Einzelansichten:
substance_view.pt
substane_mixture.pt
manufacturer_view.pt
spray_powder_view.pt

Add / Update-Forms:
create_substance_form.py
create_mixture_form.py
create_manufacturer_form.py
create_powder_form.py
create_ingredient_view.py

Page-Template für Add/Update-Forms:
create_view.pt

single_view.py enthält die Klasse SingleView, welche für alle 
Einzelansichten die zugrunde liegende Viewklasse darstellt. Diese Klasse 
enthält zahlreiche Methoden zur Aufbereitung von aus der Datenbank 
geladenen Trefferlisten, die in den unterschiedlichen Einzelansichten 
dann aufgerufen werden. Die Bestandteile dieser und weiterer Klassen 
sind den Klassendiagrammen zu entnehmen.

Die für alle Produkte individuellen Page-Templates dienen zur Anzeige 
von Treffertabellen, die ihre Werte aus der Datenbank entnehmen. Muss 
ein Wert aufbereitet werden (kommt beispielsweise True/False zurück und 
soll nach Ja/Nein umgewandelt werden) wird eine Methode des single_view 
gerufen und der Rohwert übergeben.

Die Add / Updateforms (beispielsweise create_substance_form.py) enhalten 
jeweils zwei Klassen mit den Namen CreateFormView und UpdateFormView, 
welche Methoden enthalten die das Schreiben der Werte in die Datenbank 
übernehmen oder die Belegung mit Standardwerten übernehmen. In diesen 
Klassen wird eine FormClass referenziert, von der wir 2 Stück haben- 
eine CreateForm und eine UpdateForm. In diesen Formklassen werden alle 
Felder definiert die zur Anzeige gebracht werden sollen, beispielsweise 
der Name des Gefahrstoffes. So referenziert also die Klasse 
CreateFormView die Form-Klasse CreateForm, zeigt alle Felder an und 
übernimmt bei Drücken des Speichern-Knopfes das Datenbankhandling. Wird 
die Klasse UpdateForm nun aber instanziert, ist das Verfahren sehr 
ähnlich, jedoch werden hier die Felder die auch schon in der CreateForm 
zu finden sind mit Standardwerten belegt, also die Werte die zu den 
entsprechenden Feldern in der Datenbank gespeichert sind. Bei Druck des 
Speichern-Knopfes wird nun der entsprechende Datenbankeintrag 
aktualisiert, es werden also alle Werte mit den neuen Werten in der Form 
überschrieben.

Das Page-Template für alle Create/Updateforms ist create_view.pt und 
wird dynamisch auf Basis der Formklassen erzeugt.
