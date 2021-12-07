# Automatische Testverfahren

Die Entwicklung von edi.substanceforms wurde im grundsätzlichen Ansatz testgetrieben durchgeführt.
Wie im Kapitel "Bestandteile" beschrieben, wurden die Inhaltstypen **Datenbank** und **Tabelle** sowie 
alle Ansichten (Views) und Formulare (Forms) zunächst mit dem Generator mr.bob generiert.

Im Zuge der Generierung werden bereits Templates für funktionale Tests im Package angelegt. Ausserdem
werden in der Datei setup.py des Packages die Abhängigkeiten zur Durchführung automatisierter Tests
vermerkt. Um die automatisierten Tests ausführen zu können müssen diese Abhängigkeiten zunächst installiert
werden. Dazu muss folgende Änderung in der buildout.cfg vorgenommen werden:


```

eggs = 
    ...
    edi.substanceforms [test]
```

Danach muss der Buildout mit dem Befehlt ./bin/buildout im Wurzelverzeichnis der Installation erneut
durchgeführt werden.
 
## Scope der Funktionstests

Funktionstests im Web-CMS Plone verfügen über eine echte (objektorientierte) Datenbank und eine 
Komponentenarchitektur. Darüber hinaus kann mit Python-Code ein Browser simuliert werden. Wenn mit dem 
Python-Browser auf eine Seite zugegriffen wird, ist die komplette Transaktionsmaschinerie von Plone im Einsatz. 
Damit dies funktioniert, verpackt die Testschicht die Datenbank in einen Demospeicher, der einen regulären 
Speicher kapselt. Wird von den Tests etwas in die Datenbank geschrieben, speichert der Demostorage es in 
temporären Feldern des Arbeitsspeichers. Nach jedem Test wird der Demostorage gelöscht. Damit sollten die 
funktionalen Tests fast so schnell ablaufen wie Integrationstests oder gar Unit-Tests und das trotz des
zusätzliche Overheads, der durch das Durchlaufen der Plone-Transaktionsmaschine aufgebaut wird.

Zu beachten ist dabei, dass der simulierte Browser reinen Python-Code darstellt. Javascript-Code kann somit
im Rahmen der funktionalen Tests nicht getestet werden.

Ebenso wurden die Datenbank-Transaktionen zur relationalen Datenbank auf Basis von PostgreSQL nicht in die
Funktionstests einbezogen. Die tatsächliche Kundenkonfiguration wird erheblich von einer Test- oder
Entwicklungskonfiguration abweichen. Die generische Implementierung der notwendigen technischen Voraussetzungen 
für die Installation und Konfiguration der Testumgebung ist nicht möglich.

Die in edi.substanceforms implementierten Funktionstests umfassen die folgenden Themen:

- fehlerfreie Installation des AddOns im Content-Management-System Plone
- Anlegen der Inhaltstypen Datenbank und Tabelle
- Assoziation der View- und Formklassen zu den Inhaltstypen

## Test-Verzeichnis im Package

Alle für die Ausführung der Funktionstests mittels Testroboter ((plone.app.testrobot)[https://pypi.org/project/plone.app.robotframework/]) notwendigen Konfigurationsdateien sowie die Dateien mit den Funktionstests befinden sich 
im Verzeichnis **../src/edi/substanceforms/tests/..**:

```

...src/edi/substanceforms/tests$ ls -la
total 132
drwxrwxr-x 4 plone_buildout plone_buildout 4096 Dec  4 13:03 .
drwxrwxr-x 9 plone_buildout plone_buildout 4096 Dec  4 12:28 ..
-rw-rw-r-- 1 plone_buildout plone_buildout    0 Nov 25 10:50 __init__.py
drwxrwxr-x 2 plone_buildout plone_buildout 4096 Dec  4 10:45 __pycache__
drwxrwxr-x 2 plone_buildout plone_buildout 4096 Nov 25 10:50 robot
-rw-rw-r-- 1 plone_buildout plone_buildout 3042 Nov 25 10:50 test_ct_datenbank.py
...
-rw-rw-r-- 1 plone_buildout plone_buildout 1564 Dec  4 11:33 test_view_update_mixture-form.py
-rw-rw-r-- 1 plone_buildout plone_buildout 1539 Dec  4 11:33 test_view_update_powder_form.py
-rw-rw-r-- 1 plone_buildout plone_buildout 1570 Dec  4 11:33 test_view_update_substance-form.py
-rw-rw-r-- 1 plone_buildout plone_buildout 1518 Dec  4 11:33 test_view_update_view.py

```

## Ausführung der Tests

Die Tests für edi.substanceforms können aus dem Buildout-Verzeichnis heraus mit dem folgenden
Befehl ausgeführt werden:

```
$ ./bin/test edi.substanceforms

...
  Ran 65 tests with 0 failures, 0 errors, 0 skipped in 3.067 seconds.
Tearing down left over layers:
  Tear down edi.substanceforms.testing.EdiSubstanceformsLayer:IntegrationTesting in 0.000 seconds.
  Tear down edi.substanceforms.testing.EdiSubstanceformsLayer in 0.004 seconds.
  Tear down plone.app.contenttypes.testing.PloneAppContenttypes in 0.020 seconds.
  Tear down plone.app.event.testing.PAEventLayer in 0.004 seconds.
  Tear down plone.app.testing.layers.PloneFixture in 0.028 seconds.
  Tear down plone.testing.zope.Startup in 0.003 seconds.
  Tear down plone.testing.zca.LayerCleanup in 0.001 seconds.
```

