# Bestandteile der Applikation (Module und Klassen)

Alle entwickelten Bestandteile des Projekts befinden sich im Plone-Add-On 
**edi.substanceforms**. Dieses Add-on beinhaltet beinhaltet Artikeltypen 
Content-Types (Artikeltypen), mit denen in Plone die Inhalte der Seiten gepflegt werden,
sowie alle benötigten Formulare und Ansichten (Forms und Views), für das Management
der Chemikalienprodukte mit dem CMS Plone. Die Bestandteile der Applikation werden
in den folgenden Abschnitten detaillierter beschrieben.

TODO:MrBob

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
