# M300-Services

## Gitbash

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

### Git-Befehle

*  git clone git@github.com:<Ihr Name>/my_M300.git
*  git status                       Geänderte Datei(en) werden rot aufgelistet
*  git add -A                      Fügt alle Dateien zum "Upload" hinzu
*  git status                      Der Status ist nun grün > Dateien sind Upload-bereit (Optional) 
*  git commit -m "Mein Kommentar"  Upload wird "commited" > Kommentar zu Dokumentationszwecken ist dafür notwendig
*  git status                      Dateien werden nun als "zum Pushen bereit" angezeigt
*  git push                        Upload bzw. Push wird durchgeführt

## Vagrant

Die wichtigsten Vagrant Befehle:

* vagrant init:       Initialisiert im aktuellen Verzeichnis eine Vagrant-Umgebung und erstellt, falls nicht vorhanden, ein Vagrantfile
* vagrant up:         Erzeugt und Konfiguriert eine neue Virtuelle Maschine, basierend auf dem Vagrantfile
* vagrant ssh:        Baut eine SSH-Verbindung zur gewünschten VM auf
* vagrant status:     Zeigt den aktuellen Status der VM an
* vagrant port:       Zeigt die Weitergeleiteten Ports der VM an
* vagrant halt:       Stoppt die laufende Virtuelle Maschine
* vagrant destroy:    Stoppt die Virtuelle Maschine und zerstört sie.

Wenn man also eine Vagrant VM erstellen will geht man wie folgt vor.

1. Ordner für die VM erstellen
2. wenn man sich in diesem Ordner befindet muss ein Vagrantfile erzeugtwerden z.B. mit dem Befehl 
```
vagrant init ubuntu/xenial64  
```
nun wurde in dem Verzwichniss ein Vagrant file erstellt. Vagrant Files sind in in 5 Abschnitte unterteile:
| File Abschnitt| Bedeutung |
| --- | --- |
| config.vm.box | Betriebssystem |
| Config.vm.network | Sämtliche Netzwerkeinstellungen (IP-Adrese usw.) |
| Config.vm.provider | Provider (z.B. VirtualBox) |
| Config.vm.synced_folder | wie man auf bestimmte DAteien der VM vom HOst aus zugreifen will |
|  Config.vm.provision | automatisiert aufsetzen / Befehlsreihenfolge |

3. Nun kann man die VM starten und eine ssh Verbindung herstellen um mit der VM zu arbeiten
```
$ vagrant up
$ vagrant vagrant ssh
```

## Systemsicherheit
Um die IT Sicherheit sicherzustellen wird eine Firewall und ein reverseproxy erstellt.

### 1. Schritt
Wir bearbeiten das Vagrantfile. Um einiges zu vereinfachen und damit wir nicht für alles andere editoren verwenden, öffnen wir das File in Visual Studio Code.

### 2. Schritt
im Abschnitt provision Abschnitt müssen folgende Zeilen eingetragen werden.
![Bild zu ufw Rules](https://github.com/petritajdari/M300-Services/blob/master/Images/ufw_rules.PNG "Bild zu ufw Rules")