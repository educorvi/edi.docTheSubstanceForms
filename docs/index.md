# Technische Dokumentation von edi.substanceforms

Autor: Seppo Walther [seppo.walther@educorvi.de](mailto:seppo.walther@educorvi.de)

IHK-Prüflingsnummer: 158 22139

Das hier dokumentierte Softwareprojekt wurde im Rahmen meiner Projektarbeit für die Abschlussprüfung 
zum Fachinformatiker für Anwendungsentwicklung bei der IHK Nürnberg für Mittelfranken erstellt. Bei
meinem Antrag auf Genehmigung der Projektarbeit habe ich angekündigt eine Technische Dokumentation
einzureichen. Dieser Antrag wurde von der IHK genehmigt. Ich versichere hiermit, die Arbeit allein 
erstellt zu haben und das Dokument sowohl meiner Ausbilderin als auch dem Geschäftsführer meines 
Ausbildungsbetriebes zur Durchsicht und Freigabe vorgelegt zu haben. In dieser technischen Dokumentation
werden keine Geschäftsgeheimnisse preisgegeben und keine datenschutzrechtlichen Daten oder
Informationen erhalten. Die in diesem Dokument enthaltene Anforderungsanalyse wurde auf ausdrücklichen
Kundenwunsch in das Dokument aufgenommen.

Fürth, 07.12.2021 Seppo Walther

Das Dokument wurde von uns gesehen und für die Übermittlung an die IHK Nürnberg für Mittelfranken
freigegeben.

Fürth, 07.12.2021 Anke Lampe (Ausbilderin)

Fürth, 07.12.2021 Lars Walther (Geschäftsführer)

Die Software befindet sich hier: [edi.substanceforms](https://github.com/educorvi/edi.substanceforms).

Für die Dokumentation wurde ein eigenes Softwarepackage auf Basis von [MKDocs](https://www.mkdocs.org/)
entwickelt. Die Dokumentation befindet sich hier: [edi.docTheSubstanceForms](https://github.com/educorvi/edi.docTheSubstanceForms/)


## Zusammenfassung

Mit dem Add-On edi.substanceforms für das freie Web-Content-Management-System [Plone](https://www.plone.org)
wird die Online-Datenbank **Emissionsarme Produkte** der Berufsgenossenschaft Energie Textil Elektro und 
Medienerzeugnisse (BG ETEM) realisiert.

Mit Hilfe dieser Online-Datenbank können Unternehmerinnen und Unternehmer, Arbeitsschützer und Verantwortliche
in den Betrieben der Branche Druck und Papierverarbeitung Chemikalienprodukte finden deren Einsatz in der
Produktionsumgebung mit möglichst geringen Gesundheitsgefahren für die damit in Kontakt stehenden Beschäftigten
verbunden ist.

Die Entwicklung des Plone-Add-Ons war Gegenstand der Projektarbeit von Seppo Walther im Rahmen der Ausbildung
zum Fachinformatiker für Anwendungsentwicklung und wird dem Prüfungsausschuss der IHK Nürnberg für Mittelfranken
zur Bewertung vorgelegt.

Auch wenn es unwahrscheinlich erscheint, dass die hier entwickelte Software 1:1 in anderen Umgebungen oder
für vergleichbare Anwendungsfälle eingesetzt werden kann, so liefert das Projekt doch verschiedene Hinweise und
Softwarebestandteile für vergleichbare Projekte. In Abstimmung mit dem Kunden und dem Ausbildungsbetrieb wurde
deshalb entschieden, das Projekt als Open Source Software auf der Plattfom [Github](https://github.com) zu 
veröffentlichen.

## Technische Voraussetzugen für den Einsatz von edi.substanceforms

Folgende Komponenten und Produkte sind Voraussetzung für die Anwendung von edi.substanceforms

- Lauffähige Datenbank auf Basis von PostgreSQL
- Installation von Python >= 3.8
- Lauffähige Installation (Buildout) des Web CMS Plone in der Version >= 5.2.4

*[IHK]: Industrie und Handelskammer
*[BG ETEM]: Berufsgenossenschaft Energie Textil Elektro Medienerzeugnisse
*[CMS]: Content Management System
