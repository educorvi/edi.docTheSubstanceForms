# Dokumentation des Projekts edi.substanceforms

Autor: Seppo Walther [seppo.walther@educorvi.de](mailto:seppo.walther@educorvi.de)

IHK-Prüflingsnummer: 158 22139

Das hier dokumentierte Softwareprojekt wurde im Rahmen meiner Projektarbeit für die Abschlussprüfung 
zum Fachinformatiker für Anwendungsentwicklung bei der IHK Nürnberg für Mittelfranken erstellt. Bei
meinem Antrag auf Genehmigung der Projektarbeit habe ich angekündigt eine Technische Dokumentation
für dieses Open Source Softwareprojekt einzureichen. Dieser Antrag wurde von der IHK genehmigt. 
Ich versichere hiermit, die Arbeit allein erstellt zu haben und das Dokument sowohl meiner Ausbilderin als auch dem Geschäftsführer meines Ausbildungsbetriebes zur Durchsicht und Freigabe vorgelegt zu haben. 
In dieser technischen Dokumentation werden keine Geschäftsgeheimnisse preisgegeben und keine datenschutzrechtlichen Daten oder Informationen erhalten. 
Die Gliederung meiner Dokumentation und die inhaltliche sowie die äußere Form als Online-Dokumentation mit
speziellem PDF-Export wurde im Projektverlauf des agilen Entwicklungsprojektes sowohl mit dem Ausbildungsbetrieb, als auch mit dem Kunden als Anwender der Software abgestimmt und entspricht deren Anforderungen.

Fürth, 08.12.2021 Seppo Walther

Das Dokument wurde von uns gesehen und für die Übermittlung an die IHK Nürnberg für Mittelfranken
freigegeben.

Fürth, 08.12.2021 Anke Lampe (Ausbilderin)

Fürth, 08.12.2021 Lars Walther (Geschäftsführer)

Die Software befindet sich hier: [edi.substanceforms](https://github.com/educorvi/edi.substanceforms).

Für die Dokumentation wurde ein eigenes Softwarepackage auf Basis von [MKDocs](https://www.mkdocs.org/)
entwickelt. Die Dokumentation befindet sich hier: [edi.docTheSubstanceForms](https://github.com/educorvi/edi.docTheSubstanceForms/)


## Zusammenfassung (Management Summary)

Mit dem Add-On edi.substanceforms für das freie Web-Content-Management-System [Plone](https://www.plone.org)
wird die Online-Datenbank **Emissionsarme Produkte** der Berufsgenossenschaft Energie Textil Elektro und 
Medienerzeugnisse (BG ETEM) realisiert.

Mit Hilfe dieser Online-Datenbank können Unternehmerinnen und Unternehmer, Arbeitsschützer und Verantwortliche
in den Betrieben der Branche Druck und Papierverarbeitung Chemikalienprodukte finden, deren Einsatz in der
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

### Fazit 

Im abschließenden Projektgespräch mit dem Ausbildungsbetrieb und dem Kunden am 02.12.2021 wurde festgestellt, 
dass die entwickelte Software den Kundenanforderungen entspricht und außerdem Potenzial für die
Weiterentwicklung bietet. Für den aktuellen Softwarestand wird ein Branch mit der Version 1.0b1 gebildet und
mit Hilfe von GitHub ein Release erstellt. Unmittelbar danach wird die Weiterentwicklung der Software anhand 
neuer Kundenanforderungen fortgesetzt. Dazu zählt beispielsweise die Integration der Gefahrstoffdatenbank
GESTIS der Deutschen gesetzlichen Unfallversicherung (DGUV).

*[IHK]: Industrie und Handelskammer
*[BG ETEM]: Berufsgenossenschaft Energie Textil Elektro Medienerzeugnisse
*[CMS]: Content Management System
