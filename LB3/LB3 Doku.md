# M300 - LB3 Dokumentation 

## Inhaltsverzeichnis
- [M300 - LB3 Dokumentation](#M300---LB3-Dokumentation)
  - [Inhaltsverzeichnis](#Inhaltsverzeichnis)
- [K1](#K1)
    - [VirtualBox Installiert](#VirtualBox-Installiert)
    - [Vagrant WebServer](#Vagrant-WebServer)
    - [Vagrant Installiert](#Vagrant-Installiert)
    - [Visual Studio Code Installiert](#Visual-Studio-Code-Installiert)
    - [Git Client Installiert](#Git-Client-Installiert)
- [K2](#K2)
    - [GitHub Account erstellt](#GitHub-Account-erstellt)
    - [Eigenes Repository erstellt](#Eigenes-Repository-erstellt)
    - [Markdown Editor](#Markdown-Editor)
    - [Wissensstand:](#Wissensstand)
    - [Wissenszuwachs:](#Wissenszuwachs)
- [K3](#K3)
    - [Vagrant AWS Plugin](#Vagrant-AWS-Plugin)
    - [Vagrant Info - Sammlung:](#Vagrant-Info---Sammlung)
    - [Vagrant Config Detail Infos:](#Vagrant-Config-Detail-Infos)
    - [Docker Befehle](#Docker-Befehle)
    - [Projekt](#Projekt)
- [K4](#K4)
    - [Sicherheitsaspekte](#Sicherheitsaspekte)
    - [Testing](#Testing)
    - [Kubernetes](#Kubernetes)
- [K5](#K5)
    - [Reflexion](#Reflexion)

K1
======

### VirtualBox Installiert
  - Virtualbox ist ein Virtualisierungstool, welches wir in diesem Modul verwenden. 
  - div. Linux VMs mit Virtualbox Installiert
  - VirtualBox war neu für mich, VMWare Workstation kenne ich bereits. Funktionen sind sehr ähnlich

### Vagrant WebServer
  - Vagrant Apache Server Installiert, nach Anleitung keine Probleme festgestellt, vom Client aus Verbindung auf 127.0.0.1 Problemlos funktioniert

### Vagrant Installiert
  - div. VMs mit Vagrant Installiert
  - Vagrant habe ich erst in der LB2 kennengelernt, Funktionen sind sehr praktisch und nicht zu schwierig.

### Visual Studio Code Installiert
  - Die Dokumentation wird mit Visual Studio geschrieben. Man kann die Dokumentation direkt über das GitHub "pushen".
  - Visual Studio Code wurde schon in der LB2 problemlos installiert und verwendet.
  - Mit GitHub / Bash eingerichtet

### Git Client Installiert
  - Nach Anleitung Problemlos schon in der LB2 Installiert. Sowie Portable getestet.
  - SSH Key für client erstellt

K2
======

### GitHub Account erstellt
  - Account wurde schon in der LB2 erstellt.

### Eigenes Repository erstellt
   - Repository wurde erstellt
   - SSH Key generiert und hinterlegt
   - Erster Upload getestet
Hat alles nach Anleitung geklappt
Alle Aufgaben für die Toolumgebung 10 wurden erledigt.

### Markdown Editor
  - Ich kann sehr gut mit Visual Studio umgehen, die Dokumentation ist als Markdown vorhanden. 

### Wissensstand:
Containerisierung 
Vor diesem Modul hatte ich noch keinen Bezug zu Containern
Container sind eine Virtualisierungstechnik im Computerumfeld, die Anwendungen inklusive ihrer Laufzeitumgebungen voneinander trennt. Im Gegensatz zu einer virtuellen Maschine beinhalten Container kein eigenes Betriebssystem, sondern verwenden das des Systems, auf dem sie installiert sind.

Docker 
Docker kannte ich vor diesem Modul auch noch nicht
Docker ist eine Freie Software zur Isolierung von Anwendungen mit     Containervirtualisierung. Docker vereinfacht die Bereitstellung von Anwendungen, weil sich Container, die alle nötigen Pakete enthalten, leicht als Dateien transportieren und installieren lassen

### Wissenszuwachs:
  - Ich weiss jetzt ungefähr was ein Container ist
  - Ich verstehe jetzt wie ein Container aufgebaut ist
  - Ich weiss jetzt wofür Container eingesetzt werden
  - Ich kann jetzt meine eigenen Container erstellen
  - Ich kenne jetzt Docker und dessen Möglichkeit Container zu Verwalten/erstellen/Löschen
  - Ich weiss jetzt wie ich Docker verwende
  - Ich verstehe den Ausdruck Microservices jetzt und was damit gemeint ist und wofür diese verwendet werden können

K3
======

### Vagrant AWS Plugin
  - Habe ich mit den Befehl "vagrant plugin install vagrant-aws" installiert

### Vagrant Info - Sammlung: 
  - vagrant init - Initialisiert am aktuellen Pfad eine Vagrant Umgebung und erstellt ein Vagrantfile
  - vagrant up - Erstellt und konfiguriert eine neue VM, anhand der Konfigdatei 
  - vagrant ssh - Stellt Verbindung via SSH zu einer gewählten VM auf
  - vagrant status - Zeigt aktuellen Stand der VM an
  - vagrant port - Zeigt alle Forwarded Ports der VM an
  - vagrant halt - Stoppt laufende VM
  - vagrant destroy - Stoppt die VM und löscht sie

### Vagrant Config Detail Infos: 
  - config.vm.box = "ubuntu/bionic64" Hier wird bestimmt welche BOX von der Vagrant Cloud bezogen wird
  - config.ssh.config Hier wird der Pfad des SSH Schlüssels angegeben

### Docker Befehle
  - docker run -it ubuntu /bin/bash   Startet einen Container mit einer interaktiven Shell
  - docker run -d ubuntu sleep 20
  Startet einen Container, der im Hintergrund läuft und nach 20 Sekunden sich beendet
  - docker run -d --rm ubuntu sleep 20
  Hier löscht sich der Container nach 20 Sekunden.
  - docker run -d ubuntu touch /tmp/lock
  Startet einen Container und legt eine Datei an.
  - docker ps -a
  Zeigt Aktive und Beendete Container an
  - docker images
  Gibt Lokale Images aus
  - docker rm `docker ps -a -q`
  Alle beendeten COntainer werden gelöscht
  - docker start [id]
  Docker Container neu starten, Daten bleiben erhalten
  - docker build -t mysql .
  Erstellt Container als MYSQL
  - docker network ls
  Listet bestehende Netzwerke auf

### Projekt
  - Webserver mit PHP, MYSQL und Monitoring mit GUI siehe docker-compose.yml

K4
======

### Sicherheitsaspekte

  - CPU Leistung limitiert: `cpus: 1`
  - RAM Limitert: `mem_limit: 1024m`
  - Neustart funktion: `restart: on-failure`
  - SYSLOG Monitoring 

### Testing
  - Webserver erreichbar über localhost                                     Erfolgreich
  - Datenbank "Test" ist über SQL ersichtlich nach Neustart                 Erfolgreich
  - MySQL ist über PHPmyadmin erreichbar                                    Erfolgreich
  - Monitoring via CAdvisor via Webbrowser funktioniert                     Erfolgreich
  - Monitoring überschreitet limitierte Ressourcen Werte nicht              Erfolgreich

### Kubernetes
  - Ich habe via Hands-On ein config.yaml generiert
  - Ich konnte mich auch via http://localhost:32188 auf die Kubernetes Umgebung verbinden.
  - Ich habe die Kubernetes Umgebung via Hands-On auf meinem Notebook generiert.
  - Kubernetes kümmert sich um Container und deren Verteilung zum Beispiel bei einer Cluster Umgebung.
  - Bei der Aufgabe meine yml Datei in eine yaml Datei zu konvertieren scheiterte ich. 


K5
======

### Reflexion
  - Ich habe sehr viele neue Dinge gelernt über Service Deployment, was am anfang eine Weile gedauert hat, um es zu verstehen und um damit arbeiten zu können
  - Viel ärger hatte ich wegen eines Notebook wechsels inklusive AD-Profile anpassungen von unserem Geschäft aus
  - Bis jetzt finde ich dieses Modul eines der besseren Module, weil sehr viel ausprobiert werden kann
  - Es hat mich zwar viel mehr Aufwand gekostet wie andere Module, aber ich habe dabei auch sehr viel gelernt
  - Ich weiss jetzt +/- was ein Container ist
  - Ich verstehe jetzt wie ein Container aufgebaut ist
  - Ich weiss jetzt wofür Container eingesetzt werden
  - Ich kann jetzt meine eigenen Container erstellen
  - Ich kenne jetzt Docker und dessen Möglichkeit Container zu Verwalten/erstellen/Löschen
  - Ich weiss jetzt wie ich Docker verwende
  - Ich verstehe den Ausdruck Microservices jetzt und was damit gemeint ist und wofür diese verwendet werden können

