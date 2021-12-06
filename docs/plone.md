# Installation und Konfiguration im CMS Plone

Das Package **edi.substanceforms** wird auf der Plattform GitHub gehostet.

Um edi.substanceforms im Web-Content-Management-System Plone zu installieren, wird das Package zunächst via 
git clone in das Sourcen-Verzeichns (src) der Buildout-Installation heruntergeladen und für die Installation 
in der Datei **buildout.cfg** eingetragen. Die Installation erfolgt dann im Rahmen des Buildout-Prozesses

```
{buildout-home}$ cd src
{buildout-home}/src$ git clone https://github.com/educorvi/edi.substanceforms.git
```

Einträge in der Datei buildout.cfg der Plone-Installation:

```
    eggs:
         ...
         edi.substanceforms

    develop:
         ...
         src/edi.substanceforms
```

Durchführung eines neuen Buildouts im Wurzelverzeichnis der Plone-Installation:

```
{buildout-home}$ ./bin buildout
```

Anschließend kann der Plone-Client hochgefahren werden, dies geschieht mit dem Befehl:

```
{buildout-home}$ ./bin/{instance} start
```

Danach muss das Package in den Plone-Einstellungen installiert werden.

--> Einstellungen ({url}/@@plone_control_panel) --> edi.substanceforms --> **Installieren**

Das Package wurde nun erfolgreich installiert und ist einsatzbereit.

Nun kann mit dem Hinzufügen einer Datenbank begonnnen werden.
