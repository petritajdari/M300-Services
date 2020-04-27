# M300-Services

## GitHub

Da GitHub eine Linuxbasierte Shell ist, sind auch die Befehle wie in einer Linux Shell. Hier sind die für mich wichtigsten Befehle:

* chmod --> Berechtigungen wechseln
* chgroup --> 		Gruppe wechseln
* chown	-->	Owner wechseln

* mkdir	-->	Erstellt ein Verzeichnis
* mkdir/home/X -->	Erstellt ein Verzeichnis unter dem Pfad X
* mkdir –p X --> 		Erstellt ganzer verzeichnisbaum X
* cd --> Wechselt in ein (Unter)Verzeichnis
* cd –L	-->	cd folgt der logischen Verzeichnisstruktur (Standard)
* cd –P	-->	cd folgt der physischen Verzeichnisstruktur

## Vagrant

Die wichtigsten Vagrant Befehle:

* Befehl             Beschreibung
* vagrant init	  -->  Initialisiert im aktuellen Verzeichnis eine Vagrant-Umgebung und erstellt, falls nicht vorhanden, ein Vagrantfile
* vagrant up	      -->  Erzeugt und Konfiguriert eine neue Virtuelle Maschine, basierend auf dem Vagrantfile
* vagrant ssh	  -->  Baut eine SSH-Verbindung zur gewünschten VM auf
* vagrant status	  -->  Zeigt den aktuellen Status der VM an
* vagrant port	  -->  Zeigt die Weitergeleiteten Ports der VM an
* vagrant halt	  -->  Stoppt die laufende Virtuelle Maschine
* vagrant destroy  -->  Stoppt die Virtuelle Maschine und zerstört sie.