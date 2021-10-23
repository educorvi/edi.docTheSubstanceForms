#Technische Dokumentation des Plone-Add-Ons edi.substanceforms

Autor: Seppo Walther (seppo.walther@educorvi.de)

Die Dokumentation wurde mit dem Softwaretool [MKDocs](https://www.mkdocs.org/) erstellt.

Um diese Dokumentation zumammen mit dem Tool MKDocs und weiteren benötigen Softwarekomponenten lokal 
zu installieren gehen Sie wie folgt vor:

Python-Installation (Ubuntu)

    ~/$ sudo apt-get install build-essential python-dev libjpeg-dev libxslt-dev supervisor
    ~/$ sudo apt-get install libpython3-dev
    ~/$ sudo apt-get install python3-pip python3-venv

Installation der Dokumentation für den lokalen Betrieb

    ~/$ python3 -m venv dokumentation 
    ~/$ cd dokumentation
    ~/dokumentation$ git clone https://github.com/educorvi/edi.docTheSubstanceForms.git 
    ~/dokumentation$ source bin/activate
    ~/dokumentation$ cd edi.docTheSubstanceForms
    ~/dokumentation$ pip install -r requirements.txt

Start des lokalen MKDcos Servers

    ~/dokumentation$ mkdocs build
    ~/dokumentation$ mkdocs serve
