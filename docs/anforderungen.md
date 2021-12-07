#Anforderungsanalyse

Die Anforderungsanalye ist für die technische Dokumentation vor allem vor dem Hintergrund 
des Verständnisses für die technischen Zusammenhänge der realisierten Softwarelösung von Bedeutung. 
Dieses Kapitel ist deshalb als Gegenüberstellung der Kundenanforderungen mit den im Projekt entwickelten 
Artefakten zu verstehen.

##Bedienbarkeit über das Web-CMS Plone

Die folgenden Anforderungen werden durch die im Projekt entwickelten 
Nutzerformulare und Einzelansichten erfüllt:

- Formulare zum Anlegen von Herstellern und Chemikalienprodukten durch die Autoren 
  und Redakteure mit integrierter Plausibilitätsprüfung und Speicherung im RDBMS
- Einzelansichten für Hersteller und Chemikalienprodukte und Auflistung von deren 
  Eigenschaften für den redaktionellen Prozess
- Möglichkeit zur Löschung von einzelnen Datenbankobjekten aus den Einzelansichten
- Formulare zur Aktualisierung von Herstellern und Chemikalienprodukten 
- Suche nach Produkten und Herstellern im Rahmen des redaktionellen Prozesses (keine 
  Endbenutzersuche)

Außerdem waren die folgenden Punkte zu berücksichtigen und wurden 
entsprechend umgesetzt:

- Nutzung der Benutzerverwaltung des Web-CMS Plone und des Rechte- und Rollenkonzeptes 
  von Plone
- Entwicklung der CMS-Artikeltypen "Datenbank" und "Tabelle". Die Inhaltstypen erlauben
  den Autoren und Redakteuren den freien Aufbau einer Navigationsstruktur innerhalb des CMS,
  stellen die technische Verbindung zu den Datenbankobjekten her und erlauben die Nutzung
  des Berechtigungskonzeptes von Plone bis auf die Ebene der Datenbanktabellen.
- Entwicklung von Methoden zur expliziten Prüfung der Rollen von Benutzern im Kontext der
  Formulare mit denen einzelne Datensätze bearbeitet werden können:
  - **userCanEdit**, prüft das Schreibrecht von Benutzern
  - **userCanReview**, prüft das Recht von Benutzern zur Veröffentlichung

Für die Artikeltypen Datenbank und Tabelle verwenden wir einen eigenen Workflow, der die
Berechtigungen für die Status wie folgt definiert:

- **privat:** Lese- und Schreibrechte für die CMS-Rollen Owner und Manager
- **Entwurf:** Lese- und Schreibrechte für die CMS-Rollen Editor und Manger, Leserecht für
  Reviewer
- **zur Veröffentlichung eingereicht:** Lese- und Schreibrechte für die CMS-Rollen Reviewer
  und Manager, Leserecht für Editor
- **Veröffentlicht:** Lese- und Schreibrechte für die CMS-Rollen Reviewer und Manager,
  Leserecht für Anonymous

##Responsive Webdesign

Auch hier ist das CMS Plone hilfreich. Plone selbst unterstützt von Haus aus Responsive 
Webdesign. Das Webdesign des Kunden verwendet außerdem Bootstrap als CSS- und Javascript-
Basis. Dementsprechend wurde für die Realisierung aller HTML-Templates im Projekt der 
HTML-Markup des [Bootstrap Frameworks in der Version 4.6](https://getbootstrap.com/docs/4.6/getting-started/introduction/) 
verwendet.

Bootstrap teilt jeden Bildschirm in ein Raster aus 12 Spalten ein und ordnet den Endgeräten
je nach Größe des tatsächlichen physikalische Bildschirms eine von 4 Bildschirmgrößen: 

- xs (extra-small), 
- sm (small), 
- md (medium) und 
- lg (large) 

zu. 

In den Templates des Plone-Add-Ons wird definiert, welche Template-Elemente bei welcher 
Bildschirmgröße wie viele Spalten einnehmen sollen. So lässt sich beispielsweise an einem
Arbeitsplatzcomputer ein Bild neben einer Tabelle anzeigen, während es am Smartphone 
nicht möglich ist und deshalb automatisch (responsive) unter der Tabelle angezeigt wird.

##Barrierefreiheit gemäß BITV 2.0 (WCAG 2.1 Level AA)

Bei korrekter Verwendung des HTML-Markups von Bootstrap ist die Barrierefreiheit aus
technischer Sicht gewährleistet. Ausserdem wird in den Formularen zum Upload und zum Update
der Bilder zu Herstellern und Chemikalienprodukten sichergestellt, dass Texte für Titel,
und Bildbeschreibung angegeben werden können. Die Bilder selbst werden als Artikel im CMS
Plone gespeichert. In den Einzelansichten für Hersteller und Chemikalienprodukte werden die
Titel- und Beschreibungstexte in den \<img> Tags verwendet:

- title = Titel des Bildes
- alt = Kurzbeschreibung des Bildes (außerdem Verwendung in der Bildunterschrift)
 
##Integrität der gespeicherten Daten

Die Integrität der gespeicherten Daten wird durch Datentypisierung und fachliche 
Plausibilitätsprüfungen sichergestellt. Somit wird jeder von den Autoren und Redakteuren
eingetragene Wert sowohl im Hinblick auf das Datenformat als auch im Hinblick auf die
fachliche Richtigkeit hin geprüft. 

##Gefahrstoffgemisch hinzufügen

Eine Besonderheit bildet das Gefahrstoffgemisch. Während sonst stets das Produkt der Datenbanktabelle entspricht (beispielsweise wird ein Hersteller in der Hersteller-Datenbanktabelle angelegt), so fasst die Datenbanktabelle Gefahrstoffgemisch die Produkte Etikettenwaschmittel, Waschmittel für UV-Druck, Heatsetwaschmittel, Sonderreiniger und Offsetdruck-Reinigungsmittel zusammen. Daher muss hier darauf geachtet werden, dass in der Datenbank eben solcher Mixturtyp vermerkt wird und die Einzelansichten auf diese Datenbanktabelle entsprechend dynamisch gebildet werden. Informationen über das Prozedere des Anlegens eines Gefahrstoffgemisches sind Anhang 2 zu entnehmen.

##Bildbehandlung
Für einige Produkte (wie beispielsweise das Gefahrstoffgemisch) soll es möglich sein, ein entsprechendes Produktbild zu hinterlegen. Das hierfür angewendendete Verfahren bzw. der Umgang mit diesem Bild sind in Anhang 5 mit Hilfe eiens Sequenzdiagramms veranschaulicht.
