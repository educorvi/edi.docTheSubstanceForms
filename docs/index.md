# Technische Dokumentation von edi.substanceforms

Die Software und die vollständige Online-Dokumentation finden Sie 
hier: [edi.substanceforms](https://github.com/educorvi/edi.substanceforms).

Autor: Seppo Walther (seppo.walther@educorvi.de)

## Zusammenfassung

Mit dem Add-On edi.substanceforms für das freie Web-Content-Management-System [Plone](https://www.plone.org)
wird die Online-Datenbank **Emissionsarme Produkte** der Berufsgenossenschaft Energie Textil Elektro und 
Medienerzeugnisse (BG ETEM) realisiert.

Mit Hilfe dieser Online-Datenbank können Unternehmerinnen und Unternehmer, Arbeitsschützer und Verantwortliche
in den Betrieben der Branche Druck und Papierverarbeitung Chemikalienprodukte finden deren Einsatz in der
Produktionsumgebung mit möglichst geringen Gesundheitsgefahren für die damit in Kontakt stehenden Beschäftigten
verbunden ist.

Die Entwicklung des Plone-Add-On war Gegenstand der Projektarbeit von Seppo Walther im Rahmen der Ausbildung
zum Fachinformatiker für Anwendungsentwicklung und wurde dem Prüfungsausschuss der IHK Nürnberg für Mittelfranken
zur Bewertung vorgelegt.

Auch wenn es unwahrscheinlich erscheint, dass die hier entwickelte Software 1:1 in anderen Umgebungen oder
für vergleichbare Anwendungsfälle eingesetzt werden kann, so liefert das Projekt doch verschiedene Hinweise und 
Softwarebestandteile für vergleichbare Projekte. Es wurde daher entschieden, das Projekt als Beispiellösung 
auf der Plattfom [Github] zu veröffentlichen.

## Technische Voraussetzugen für den Einsatz von edi.substanceforms

- Lauffähige Datenbank auf Basis von PostgreSQL
- Installation von Python >= 3.8
- Lauffähige Installation (Buildout) des Web CMS Plone in der Version >= 5.2.4

## Installation von edi.substanceforms für das Web-CMS Plone

Git Clone von edi.substanceforms in das "src" Verzeichnis der Plone-Installation

    git clone https://github.com/educorvi/edi.substanceforms.git
 
Einträge in der Datei buildout.cfg der Plone-Installation:

    eggs:
         ...
         edi.substanceforms

    develop:
         ...
         src/edi.substanceforms

Durchführung eines neuen Buildouts im Wurzelverzeichnis der Plone-Installation:

    ./bin buildout

Installation des neuen Produkts im Plone Controlpanel
