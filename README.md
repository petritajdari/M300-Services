# M300-Services
Dies ist der Link zu [LB03](#lb03)
# LB02
## Gitbash

Da GitHub eine Linuxbasierte Shell ist, sind auch die Befehle wie in einer Linux Shell. Hier sind die für mich wichtigsten Befehle:

| Befehl | Auswirkung |
| --- | --- |
| chmod | Berechtigungen wechseln |
| chgroup | Gruppe wechseln |
| chown	| Owner wechseln |
| mkdir	| Erstellt ein Verzeichnis |
| mkdir/home/X | Erstellt ein Verzeichnis unter dem Pfad X | 
| mkdir –p X | Erstellt ganzer verzeichnisbaum X | 
| cd | Wechselt in ein (Unter)Verzeichnis |
| cd –L	| cd folgt der logischen Verzeichnisstruktur |
| cd –P	| cd folgt der physischen Verzeichnisstruktur |

### Git-Befehle

```
$  git clone git@github.com:<Ihr Name>/my_M300.git
$  git status                       Geänderte Datei(en) werden rot aufgelistet
$  git add -A                      Fügt alle Dateien zum "Upload" hinzu
$  git status                      Der Status ist nun grün > Dateien sind Upload-bereit (Optional) 
$  git commit -m "Mein Kommentar"  Upload wird "commited" > Kommentar zu Dokumentationszwecken ist dafür notwendig
$  git status                      Dateien werden nun als "zum Pushen bereit" angezeigt
$  git push                        Upload bzw. Push wird durchgeführt
```

## Vagrant

Die wichtigsten Vagrant Befehle:

```
$ vagrant init:       Initialisiert im aktuellen Verzeichnis eine Vagrant-Umgebung und erstellt, falls nicht vorhanden, ein Vagrantfile
$ vagrant up:         Erzeugt und Konfiguriert eine neue Virtuelle Maschine, basierend auf dem Vagrantfile
$ vagrant ssh:        Baut eine SSH-Verbindung zur gewünschten VM auf
$ vagrant status:     Zeigt den aktuellen Status der VM an
$ vagrant port:       Zeigt die Weitergeleiteten Ports der VM an
$ vagrant halt:       Stoppt die laufende Virtuelle Maschine
$ vagrant destroy:    Stoppt die Virtuelle Maschine und zerstört sie.
```

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
### 3. Schritt
Im selben Abschnitt müssen noch folgende Zeilen eingetragen werden, für den reverse Proxy
![Bild zu proxy aktivierung](https://github.com/petritajdari/M300-Services/blob/master/Images/proxy.PNG "Bild zu proxy aktivierung")
### Benutzer und Berechtigungen
Ein sehr wichtiger ASpekt wenn es um die Sicherheit geht, sind die Benutze/ Gruppen und ihre Berechtigungen. Hier ist eine Auflistung mit Befehlen, welche Hilfreich sein könnten.
```
chmod       Berechtigungen wechseln
chgroup     Gruppe wechseln
chown       Owner wechseln
useradd     erstellt einen Benutzer
passwd      ändert das passwort eines Benutzers
groupadd    erstellt eine Benutzergruppe
```

## Wissenszuwachs
Ich habe in diesem Modul sehr viel gelernt. ich habe eine neue Art von Virtualisierung mit Vagrant templates kennengelernt und dazu noch, wie man trotzdem die Sicherheit gewährleisten kann. Abgesehen von der FAchkompetenz, habe ich auch in der Methodenkompetenz viel gelernt. In diesem Modul habe ich das erste mal mit eine Git Repository gearbeitet und so erfahren, welche vorteile das haben kann, sein wissen mit der Community zu teilen den ich selbst habe auch für einige Schwierigkeiten die ich hatte in Git Repositorys von anderen Leuten Hilfe gefunden.

## Reflexion
Ich konnte in der LB02 sehr viel lernen. Zu Beginn jedoch, war praktisch alles neu, die Arbeitsmethodik, die Tools, selbst die Art des dokumentierens. deshalb habe ich mich sehr vor dem Auftrag gescheut und hatte somit einen holprigen start. Ich habe den Fehler gemacht, dass ich einfach der Anleitung gefolgt bin und mir dabei nicht viel gedacht geschweige den Dokumentiert habe. Ich dachte das wäre bloss der Einstieg, um die neue Umgebung kennenzulernen und der Richtige Auftrag käme erst. somit musste ich später alles nachdokumentieren. In Zukunft werde ich von Beginn an dokumentieren, was ich tue, egal ob es dem Auftrag entspricht oder noicht, den alles was ich neu lerne ist hilfreich, wenn es in der Dokumentation steht.

# LB03
Für diese Arbeit habe ich eine Ubuntu VM erstellt. Anhand folgender Anleitung habe ich Docker installiert: https://docs.docker.com/engine/install/ubuntu/

Um die Installation zu testen, kann man folgenden Befehl ausfüren. Anhand der Ausgabe erkennt man ob die Installation erfolgreich war.
```
Docker run hello-world
```
![Docker test](https://github.com/petritajdari/M300-Services/blob/master/Images/Docker_Hello-World.PNG "Bild zu Docker run hello-world")

## Container und Images
Es gibt eine grosse auswahl an Images die man verwenden kann. Images können auch selbst erstellt werden.
Für Testzwecke werde ich einen Apache und einen mysql Container mit folgenden Befehlen erstellen.
```
docker container run -d -p 8081:80 --name MyApache httpd
docker container run -it -p 8082:80 mysql

```
Um die die Funktionalität zu testen, kann man im Browser http://localhost:[port] suchen. wenn die Installation erfolgreich war, sieht man die webserver. Ich habe den Command Line  Browser ELinks verwendet.
![Apache container Test](https://github.com/petritajdari/M300-Services/blob/master/Images/Docker_Apache-test.PNG "Bild zu Apache container Test")

Hier ist eine Auflistung, von Docker Befehlen welche häufig verwendet werden:

| Befehl | Beschreibung |
| --- | --- |
| $docker ps | Alle laufende Container anzeigen |
| $docker container ls -a | Alle Container anzeigen |
| $docker images | Alle Images anzeigen |
| $pull (Imagename) | Image herunterladen |
| $docker image build -t | Image erstellen | 
| $docker container stop [ID] | Container stoppen |
| $docker container exec -it "containername" bash | den Container betreten |

## Image erstellen
Ich will ein eigenes Image erstellen. dieses sollte einen Webservice starten mit meiner eigenen Webseite.
### 1. Schritt
Zuerst muss ein Container erstellt werden. Dazu verwende lade ich zuerst das neuste Centos Image herunter.
```
docker pull centos:latest
```
Um alle lokal verfügbaren Images anzuzeigen kann folgender Befehl verwendet werden
```
docker images
```
### 2. Schritt
Nun wird ein container mit dem heruntergeladenen Image erstellt.
```
docker run –it –name MyWebServer centos:latest
```
mit diesem Befehl sollte der Container erstellt werden und wir sollten automatisch dem Container beitreten.
![Apache container Test](https://github.com/petritajdari/M300-Services/blob/master/Images/Docker_erstellen-MyWebServer.PNG "Bild zu Apache container Test")
### 3. Schritt
Nun Muss ein WebService installiert werden. In meinem Fall installiere ich die Apache Module.
```
[root@Docker_Id]#yum install httpd –y
```
### 4. Schritt
Nun bearbeite ich die html Datei mit dem vi Editor
```
[root@Docker_Id]#vi /var/www/html/index.html
```
### 5. Schritt
Nun müssen wir den aktuellen Container verlassen und ausschalten

```
[root@Docker_Id]#exit
#Docker container stop [containername]
```
### 6. Schritt
Nun kann mit dem commit befehl ein Image aus einem bestehendem Container erstellt werden. Der Befehl ist so aufgebaut:
#docker commit <container_id or name of container will launching> <Name of new image>:<version name>
In meinem Fall lautet er so
![Apache container Test](https://github.com/petritajdari/M300-Services/blob/master/Images/Docker_Image-erstellen.PNG "Bild zu Apache container Test")
### 7. Schritt
Nun muss nur noch ein Container mit dem erstellten Image erstellt werden.
![Apache container Test](https://github.com/petritajdari/M300-Services/blob/master/Images/Docker_Image-test1.PNG "Bild zu Apache container Test")
### 8. Schritt
Zum Schluss kann man das ganze testen in dem man im Browser nach http://localhost:[port] sucht.
![Apache container Test](https://github.com/petritajdari/M300-Services/blob/master/Images/Docker_Image-test2.PNG "Bild zu Apache container Test")
## Sicherheit
### Capabilities einschränken
Der Linux-Kernel definiert eine Reihe von Berechtigungen, welche Prozessen zugewiesen werden können, um ihnen einen erweiterten Zugriff auf das System zu gestatten.

Die Capabilities decken einen grossen Funktionsbereich ab, vom Ändern der Systemzeit bis hin zum Öffnen von Netzwerk-Sockets. Der Command dazu ist:
```
docker run --cap-drop all --cap-add CHOWN ubuntu chown 100 /tmp
```
### Ressourcenbeschränken
Der Kernel definiert Ressourcenbeschränkungen, die für Prozesse gesetzt werden können. Diese lassen sich auch auf Docker-Container anwenden. Hierzu wäre der Command:
```
docker run --ulimit cpu=12:14 amouat/stress stress --cpu 1
```
### Speicher
Wenn man den Speicher schützt, kann man die Chancen von DDos Attacken minimieren. Dies ist wichtig, da der Speicher nicht "aufgefressen" werden darf. Hier wäre der Command dazu:
```
docker run -m 128m --memory-swap 128m amouat/stress stress --vm 1 --vm-bytes 127m -t 5s
```
### Neustarts begrenzen
Ein Neustart verhindert Zeitverluste und Ressorcenverluste von einem sterbenden Container. Auch hier kann eine DDos Attacke verhindert werden. Der Command dazu wäre:
```
docker run -d --restart=on-failure:10 my-flaky-image
```
### Moitoring
Ein sehr häufig verwendetes Monitoring Tool ist Docker Tools cAdvisor von Google. Das Programm ist als Container verfügbar. Der Command dazu wäre:
```
docker run -d --name cadvisor -v /:/rootfs:ro -v /var/run:/var/run:rw -v /sys:/sys:ro -v /var/lib/docker/:/var/lib/docker:ro -p 8080:8080 google/cadvisor:latest
```
## Wissenszuwachs
Bis anhin habe ich hauptsächlich mit virtuellen Maschinen gearbeitet. Docker war mir ein Begriff aber ich wusste nicht wirklich viel darüber. Ich vorallem viel praktische Erfahrung mit Docker erlangen können. Ich bin mir sicher, dass in der Zukunft Docker an Wichtigkeit gewinnen wird. in diesem Modul habe ich die nötige Grundkenntnisse erlangen könne, um mit Docker zu arbeiten.
## Reflexion
Ihm gegensatz zur letzten Arbeit habe ich diesesmal von Beginn an alles Dokumentiert. somit musste ich nichts nachdokumentieren und die ganze Arbeit war einfacher. Ich fand die Arbeit mit Docker sehr spannend, Deshalb habe ich mich zum Teil länger auf Aufgaben konzentriert, welche gar nicht so Wichtig für den Auftrag waren. In Zukunft werde ich den ganzen Auftrag im Blick behalten, auch wenn mir ein Teil besonders gefällt, den schlussendlich zählt die ganze Arbeit.