# Dokumentation des Projekts edi.substanceforms

Autor: Seppo Walther [seppo.walther@educorvi.de](mailto:seppo.walther@educorvi.de)

IHK-Prüflingsnummer: 158 22139

Das hier dokumentierte Softwareprojekt wurde im Rahmen meiner Projektarbeit für die Abschlussprüfung 
zum Fachinformatiker für Anwendungsentwicklung bei der IHK Nürnberg für Mittelfranken erstellt. Bei
meinem Antrag auf Genehmigung der Projektarbeit habe ich angekündigt, eine Technische Dokumentation
für dieses Open Source Softwareprojekt einzureichen. Dieser Antrag wurde von der IHK genehmigt. 
Ich versichere hiermit, die Arbeit allein erstellt zu haben und das Dokument sowohl meiner Ausbilderin als auch dem Geschäftsführer meines Ausbildungsbetriebes zur Durchsicht und Freigabe vorgelegt zu haben. 
In dieser technischen Dokumentation werden keine Geschäftsgeheimnisse preisgegeben und es sind keine datenschutzrechtlich relevanten Daten oder Informationen enthalten. 
Die Gliederung meiner Dokumentation und die inhaltliche sowie die äußere Form als Online-Dokumentation mit
speziellem PDF-Export wurde im Projektverlauf des agilen Entwicklungsprojektes sowohl mit dem Ausbildungsbetrieb, als auch mit dem Kunden als Anwender der Software abgestimmt und entspricht deren Anforderungen.

Fürth, 08.12.2021 Seppo Walther

Das Dokument wurde von uns gesehen und für die Übermittlung an die IHK Nürnberg für Mittelfranken
freigegeben.

Fürth, 08.12.2021 Anke Lampe (Ausbilderin)

Fürth, 08.12.2021 Lars Walther (Geschäftsführer)

Die Software befindet sich hier: [https://github.com/educorvi/edi.substanceforms](https://github.com/educorvi/edi.substanceforms).

Für die Dokumentation wurde ein eigenes Softwarepackage auf Basis von MKDocs (siehe [https://www.mkdocs.org/](https://www.mkdocs.org/))
entwickelt. 

Die Dokumentation befindet sich hier: [https://github.com/educorvi/edi.docTheSubstanceForms/](https://github.com/educorvi/edi.docTheSubstanceForms/)


# Zusammenfassung (Management Summary)

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

Für die Durchführung des Entwicklungsprojekts wurde eine agile Projektorganisation gewählt. Diese Entscheidung
hat sich vor allem unter den besonderen Bedingungen der Corona-Pandemie bewährt. Nach Vorbereitung des
Softwarepackages mit den Generierungs-Werkzeugen von 
"Mr.Bob" (bobtemplates.plone, siehe [https://bobtemplatesplone.readthedocs.io/en/latest/](https://bobtemplatesplone.readthedocs.io/en/latest/)) wurden alle wesentlichen 
Bestandteile des Add-Ons in 3 zweitägigen Sprints entwickelt. Davon fand ein Sprint mit Kundenbeteiligung
in Präsenz am Sitz der educorvi GmbH & Co. KG in Fürth statt. Für die Sprints wurden jeweils Kanban-Boards aufgestellt und 
erfolgreich abgearbeitet.

Auch wenn es unwahrscheinlich erscheint, dass die hier entwickelte Software 1:1 in anderen Umgebungen oder
für vergleichbare Anwendungsfälle eingesetzt werden kann, so liefert das Projekt doch verschiedene Hinweise und
Softwarebestandteile für vergleichbare Projekte. In Abstimmung mit dem Kunden und dem Ausbildungsbetrieb wurde
deshalb entschieden, das Projekt als Open Source Software auf der Plattfom GitHub([https://github.com](https://github.com)) zu 
veröffentlichen.

Für die Dokumentation wurde entschieden, auf [MKDocs](https://www.mkdocs.org/) zu setzen. MKDocs erlaubt die 
Dokumentation mittels Markdown-Dokumenten. Die Dokumentation kann mit dem gleichen Werkzeug wie die Erstellung
des Softwarecodes erfolgen. Außerdem kann die Dokumentation ebenfalls über die Plattform Github versioniert
werden und es können auf diese Weise Reviews durchgeführt werden. MKDocs erlaubt die Online-Veröffentlichung
der Dokumentation über automatisch generierte HTML-Seiten. Mit dem für dieses Projekt angepassten Zusatzmodul
mkdocs-with-pdf ([https://pypi.org/project/mkdocs-with-pdf/](https://pypi.org/project/mkdocs-with-pdf/)) wurde die Dokumentation automatisch und ohne
Zusatzaufwand als PDF-Dokument exportiert.

**Fazit** 

Im abschließenden Projektgespräch mit dem Ausbildungsbetrieb und dem Kunden am 02.12.2021 wurde festgestellt, 
dass die entwickelte Software den Kundenanforderungen entspricht und außerdem Potenzial für die
Weiterentwicklung bietet. Für den aktuellen Softwarestand wird ein Branch mit der Version 1.0b1 gebildet und
mit Hilfe von GitHub ein Release erstellt. Unmittelbar danach wird die Weiterentwicklung der Software anhand 
neuer Kundenanforderungen fortgesetzt. Dazu zählt beispielsweise die Integration der Gefahrstoffdatenbank
GESTIS der Deutschen gesetzlichen Unfallversicherung (DGUV).

*[IHK]: Industrie und Handelskammer
*[BG ETEM]: Berufsgenossenschaft Energie Textil Elektro Medienerzeugnisse
*[CMS]: Content Management System
*[Kanban-Boards]: Die Kanban-Board ist ein visuelles Hilfsmittel für den Überblick über den aktuellen Arbeitsstatus und die Kommunikation im Team
*[Mr.Bob]: Werkzeug zur Generierung von Softwarepackes und weiteren Modulen mittels Schablonen (Templates)
