# Installation und Konfiguration im CMS Plone

Das Package **edi.substanceforms** wird auf der Plattform GitHub gehostet.
Um es im Web-Content-Management-System Plone zu installieren, wird es zunächst via git clone installiert und anschließend im Plone-Buildout in der Datei **buildout.cfg** entsprechend eingetragen.
Nun wird ein Buildout durchgeführt, indem in der Wurzel von Plone der Befehl ./bin/buildout ausgeführt wird.

Anschließend kann der Plone-Client hochgefahren werden, dies geschieht mit ./bin/client start .

Nun muss das Package in den Plone-Einstellungen installiert werden.
Im CMS unter Einstellungen ist der Punkt Erweiterungen zu finden, neben dem Packagenamen **edi.substanceforms** wird auf **Installieren** geklickt.

Das Package wurde nun erfolgreich installiert und ist einsatzbereit.

Nun kann mit dem Hinzufügen einer Datenbank begonnnen werden.
