# Aufbau des Software-Packages

## Konzeptbild Aufbau Software-Package
Hierbei handelt es sich um eine vereinfachte Darstellung des Zusammenspiels unterschiedlicher Komponenten des Projekts.
![Blockdiagramm](images/blockdiagramm.001.jpeg "Blockdiagramm")
[Bild öffnen](https://doku.educorvi.de/wissensartikel/abbildungen-emissionsarme-produkte/blockdiagramm-001.jpeg/image_view_fullscreen)

## Aufbau Software-Package
Das Softwarepaket besteht aus mehreren Ebenen, die miteinander kommunizieren und Daten untereinander austauschen können. Im Folgenden wird das obige Bild, und damit unser Package, von unten nach oben beschrieben.

### PostgreSQL

#### Relationales Datenbanksystem PostgreSQL
Ganz unten befindet sich ein relationales Datenbankmanagementsystem (RDBMS), basierend auf PostgreSQL. Da die Einrichtung dieser Datenbank nicht Teil meines Projektes ist werde ich hier nur soweit darauf eingehen zu sagen, dass alle Daten zu Gefahrstoffprodukten hier gespeichert werden. Dafür kommt jeweils eine Tabelle zum Einsatz, die in ihren Spalten alle Eigenschaften der Produkte abbildet.

### Plone

#### Content-Type Datenbank
Der Plone Content-Type Datenbank interagiert direkt mit der zugrunde liegenden PostgreSQL Datenbank. Da im Content-Type Datenbank die Anmeldedaten der Datenbank hinterlegt werden ist es das Modul, welches die Verbindung zur PSQL-Datenbank herstellt und aufrecht erhält.

#### Content-Type Tabelle
Auf dem CT Datenbank sitzt der CT Tabelle. Für jede PostgreSQL-Datenbanktabelle die im CMS abgebildet werden soll wird ein CT Tabelle angelegt. Darin wird neben der referenzierten Datenbanktabelle auch spezifiziert, welche Spalten berücksichtigt werden sollen und es gibt, am Beispiel des Gefahrstoffgemisches die Möglichkeit, nur bestimmte Typen dieser Mixtur anzuzeigen.

#### Einzelansicht Tabelle
Die Standardansicht der Tabelle besitzt die Möglichkeit, alle Elemente der Tabelle anzusehen (= Tuples der Datenbanktabelle).
Diese Standardansicht kann im Programmcode spezialisiert werden, sodass sie in der Lage ist, die Datensätze nach entsprechenden Datensätzen zu filtern. Diese Ansicht bildet eine Trefferliste, bei der der Nutzende auf einen Datensatz zu klicken um in die spezialisierte Einzelansicht des Produktes zu kommen.

#### Einzelansicht Produkt
Für jede Tabelle (beispielsweise Hersteller) gibt es eine Einzelansicht für deren Produkte (beispielsweise hersteller-view). In dieser Einzelansicht werden alle Eigenschaften des Produktes, welche aus der PostgreSQL Datenbank abgerufen werden, visuell aufbereitet und angezeigt. Hierfür stehen der Einzelansicht unterschiedlichste Übersetzungs- und Umwandlungsmethoden der Klasse single_view zur Verfügung, welche von allen Einzelansichten gleichermaßen genutzt werden können.

#### create-view
Der Create-View erlaubt es, einen neuen Datensatz anzulegen. Er wird in der Ansicht der Tabelle über einen Button "Artikel hinzufügen" aufgerufen. Der create-view ist ein Formular und beinhaltet Felder zu allen Attributen die erfasst werden können bzw. müssen. Die eingegebenen Eigenschaften werden nach mehrerer Prüfungen auf Plausibilität der Daten schließlich in die PSQL-Datenbank geschrieben.

#### update-view
Der Update-View wird aus der Einzelansicht der Produktes über einen Button "Artikel bearbeiten" aufgerufen. Der Update-View ist technisch wie optisch nahezu identisch mit dem Create-View, beinhaltet ebenfalls ein Formular mit allen Feldern, jedoch werden hier die Felder bereits vorbelegt mit den vorhandenen Daten. Soll eine Änderung vorgenommen werden, so ändert der Nutzer beispielsweise im Feld "Titel" den Inhalt von "Silux Max Super" zu "Silux Super Max".

#### delete-view
Der Delete-View wird ebenfalls aus der Einzelansicht des Produktes aufgerufen, zum Einsatz kommt ein Button "Artikel löschen". Der Delete-View beinhaltet eine Abfrage, ob man sich sicher seie das Produkt löschen zu wollen. Wird das Kästchen entsprechend angekreuzt so wird der Datensatz aus der Datenbanktablle von PostgreSQL entfernt. 
