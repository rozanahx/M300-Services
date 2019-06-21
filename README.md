# M300
M300 - LB2 Dokumentation 
===


## Inhaltsverzeichnis
- [M300](#M300)
- [M300 - LB2 Dokumentation](#M300---LB2-Dokumentation)
  - [Inhaltsverzeichnis](#Inhaltsverzeichnis)
- [K1](#K1)
  - [VirtualBox](#VirtualBox)
  - [Vagrant](#Vagrant)
  - [Visual Studio Code](#Visual-Studio-Code)
  - [Git-Client](#Git-Client)
  - [SSH-Key](#SSH-Key)
- [K2](#K2)
  - [GitHub Account](#GitHub-Account)
  - [Persönlicher Wissenststand](#Pers%C3%B6nlicher-Wissenststand)
	-[Linux](#Linux)
	-[Vagrant](#Vagrant)
	-[Virtualisierung](#Virtualisierung)
	-[Systemsicherheit](#Systemsicherheit)
- [K3](#k3)
	
  - [Testen](#testen)
    - [Apache](#apache)
    - [Users and Groups](#users-and-groups)
    - [Ports](#ports)
- [K4](#k4)
  - [Firewall](#firewall)
  - [Reverse-Proxy](#reverse-proxy)
  - [Benutzer und Rechtevergabe](#benutzer-und-rechtevergabe)
  - [SSH](#ssh)
- [K5](#k5)
  - [Reflexion](#reflexion)
_

K1
======

> [⇧ Nach oben](#inhaltsverzeichnis)
 
## VirtualBox

1. Virtual Box unter folgender Seite (https://www.virtualbox.org) herunterladen.
2. Die Virtual Box GUI - Basiert installieren und Standarteinstellungen verwenden.  
3. Danach die ISO Datei Ubuntu Desktop 18.04.02 auf der Ubuntu Webseite (https://ubuntu.com/download/desktop/thank-you?country=CH&version=18.04.2&architecture=amd64) herunterladen . 

Nachdem die ISO Datei vollständig heruntergeladen wurde, kann die VM erstellt werden:
1. VirtualBox starten 
2. `Neu` wählen und eine neue VM erstellen, dannach öffnet sich ein Fenster.
3. Folgende Informationen im Fenster eintragen:
   *  Name:           `M300_Ubuntu_XX.04_Desktop`
   *  Typ:            `Linux`
   *  Version:        `Ubuntu (64-bit)`
   *  Speichergrösse: `2048 MB`
   *  Platte:         `[X] Festplatte erzeugen`
4. Nun `Erzeugen` auswählen
5. Im nächsten Fenster, folgende Informationen eintragen:
   *  Dateipfad:                       standard
   *  Dateigrösse:                     `10.00 GB`
   *  Dateityp der Festplatte:         `VMDK (Virtual Maschine Disk)`
   *  Storage on physical hard disk:   `dynamisch alloziert`
6. Erneut auf `Erzeugen` klicken, dann im Hauptmenü die VM anwählen (blau markiert) und den Punkt `Ändern` aufrufen
7. Im Abschnitt `Massenspeicher` den SATA-Controller anwählen und auf das CD+Symbol klicken
8. Unter `Medium auswählen` das zuvor heruntergeladene Systemabbild (ISO-Datei) anwählen
9. Alle Änderungen speichern und die VM starten
10. Nun den Installationsanweisungen der OS-Installation folgen. 

Die VM sollte nun betriebsbereit sein.

1. Die Ubuntu-VM starten
2. Anmelden und Terminal (Bash) öffnen
3. Im Terminal folgende Befehle eingeben:
Paketliste neu einlesen und Pakete aktualisieren:
   ```Shell 
   $  sudo apt-get update   #Paketlisten des Paketmanagement-Systems "APT" neu einlesen
   
   $  sudo apt-get update   #Installierte Pakete wenn möglich auf verbesserte Versionen aktualisieren

   $  sudo reboot           #System-Neustart durchführen
   ```
2. Software Controlcenter "Synaptic" installieren:
   ```Shell 
   $  sudo apt-get install synaptic
   ```
3. Nach erfolgreicher Installation in der Suche nach "Synaptic Package Manager" suchen und diesen starten
4. Innerhalb des Managers nach "apache" (Webserver-Programm) suchen und dieses (inkl. aller Abhängigkeiten) installieren
5. System-Neustart durchführen:
   ```Shell 
   $  sudo reboot
   ```
6. Prüfen, ob der Standard-Content des Webservers unter "http://127.0.0.01:80" erreichbar ist


## Vagrant
> [⇧ Nach oben](#inhaltsverzeichnis)

Vagrant auf [dieser Webseite](https://www.vagrantup.com/ "vagrantup.com")   herunterladen und GUI-Basiert installiert.

Mit Vagrant eine VM erstellen.
1. Terminal (GIT Bash) öffnen
2. Einen neuen Ordner für die VM erstellen:
    ```Shell
      $ cd C:\Users\hisa_r\VagrantVM
      $ mkdir virtual boxen
      $ cd MeineVagrantVM
     ```
3. Vagrantfile erzeugen, VM erstellen und starten:
    ```Shell
      $ vagrant box add http://10.1.66.11/vagrant/ubuntu/xenial64.box --name ubuntu/xenial64  #Vagrant-Box vom Netzwerkshare hinzufügen
      $ vagrant init ubuntu/xenial64        #Vagrantfile erzeugen
      $ vagrant up --provider virtualbox    #Virtuelle Maschine erstellen & starten
     ```
4. Die VM ist nun bereit und kann mit SSH-Zugriff bedient werden:
    ```Shell
      $ cd C:\Users\hisa_r\VagrantVM\MeineVagrantVM   #Zum Verzeichnis der VM wechseln
      $ vagrant ssh                     			  #SSH-Verbindung zur VM aufbauen
     ```

Apache Webserver automatisiert aufsetzen

1. Git Bash Terminal öffnen
2. In das LB2-Verzeichnis wechseln:
    ```Shell
      $ cd C:\Users\hisa_r\M300_Vagrant\.vagrant\machines\default\virtualbox
     ```
3. VM erstellen und starten:
    ```Shell
      $ vagrant up
     ```
4. Danach im Webbrowser prüfen, ob der Standard-Content des Webservers unter "http://127.0.0.01:8080" (localhost) erreichbar ist
5. Im Ordner `\web` die Hauptseite `index.html` editiert und das Resultat überprüfen.
6. Abschliessend die VM wieder löschen:
    ```Shell
      $ vagrant destroy -f
    ```

## Visual Studio Code
> [⇧ Nach oben](#inhaltsverzeichnis)

Visual Studio ist eine von dem Unternehmen Microsoft angebotene integrierte Entwicklungsumgebung für verschiedene Hochsprachen.
Darüber hinaus lassen sich mit Visual Studio Windows-Apps, dynamische Webseiten bzw. Webservices für das Internet/Intranet entwickeln.

1. Visual Studio Code auf [dieser](https://code.visualstudio.com/"visualstudio.com") Seite herunterladen und GUI-basiert installiert.
2. Nach der installation im Editor drei wichtige Extensions hinzufügen:

* Markdown All in One (von Yu Zhang)
* Vagrant Extension (von Marco Stanzi)
* vscode-pdf Extension (von tomiko1207)

Folgende Anweisungen befolgen: 

  1. Visual Studio Code öffnen
  2. Die Tastenkombination `CTRL` + `SHIFT` + `X` drücken und in der Suchleiste die erwähnten Extensions suchen
  3. Auf `Install` klicken und anschliessend auf `Reload`, um die Extension in den Arbeitsbereich zu laden.

Um die Dokumentation lokal mit Visual Studio Code zu bearbeiten, arbeite ich folgendermassen:

  1. Änderungen am Readme-File von meinem Repositorys vornehmen
  2. Datei speichern und in der linken Leiste das Symbol mit einer "1" aufrufen
  3. Unter dem Abschnitt Changes die betroffenen Files bezüglich ihres Changes "stagen"
  4. Nachricht hinterlegen und Haken setzen
  5. Bei den 3 Punkten (...) auf Push klicken
  6. Warten, bis Dateien vollständig gepusht wurden

## Git-Client
> [⇧ Nach oben](#inhaltsverzeichnis)

Um die Arbeiten Lokal auf dem eigenen PC machen zu können, sollte das Programm "Git Client", auf Windows "Git Bash" installiert werden.
 
Client installieren
Die Client-Installation kann auf [dieser](https://git-scm.com/downloads) Seite heruntergeladen und GUI-basiert installiert werden.

Danach den Client konfigurieren:
1. Terminal öffnen
2. Git konfigurieren mit Informationen des GitHub-Accounts:
    ```Shell
      $ git config --global user.name "<rozanahx>"
      $ git config --global user.email "<rozana.hisa@hotmail.com>"
     ```

Repository herunterladen & aktualisieren

1. Git Bash Terminal öffnen
2. Ordner für Repository erstellen:
    ```Shell
      $ cd C:\Users\hisa_R\M300-Services
      $ mkdir MeinLokalesRepository
     ```
3. Repository mit SSH klonen:
    ```Shell
      $ git clone git@github.com:rozanahx/M300-Services
```
      Cloning into 'lb2'...
     
4. Repository aktualisieren und Status anzeigen:
    ```Shell
      $ git pull
```
      Already up to date.
    

## SSH-Key 
> [⇧ Nach oben](#inhaltsverzeichnis)

SSH-Key erstellen:

1.  Folgenden Befehl mit der Account-E-Mail von GitHub in Bash einfügen:
    ```Shell
      $  ssh-keygen -t rsa -b 4096 -C "rozana.hisa@hotmail.com"
    ```
2. Neuer SSH-Key wird erstellt:
    ```Shell
      Generating public/private rsa key pair.
    ```
3. Bei der Abfrage, unter welchem Namen der Schlüssel gespeichert werden soll, die Enter-Taste drücken (für Standard):
    ```Shell
      Enter a file in which to save the key (~/.ssh/id_rsa): [Press enter]
    ```
4. Passwort für den Key festlegen:
    ```Shell
      Enter passphrase (empty for no passphrase): [Passwort]
      Enter same passphrase again: [Passwort wiederholen]
    ```
Danach kann der SSH-Key dem Client hinzufügt werden:
1.  Auf www.github.com im Benutzerkonto Settings aufrufen
2.  Unter den Menübereichen auf der linken Seite zum Abschnitt SSH und GPG keys wechseln
3.  Auf New SSH key klicken
4.  Im Formular unter Title die Bezeichnung MB SSH-Key vergeben
5.  Den Key von der Datei C:\Users\Rozana Hisa\.ssh\id_rsa.pub einfügen und auf Add SSH key klicken

SSH Zugriff auf VM

Um Zugriff via SSH auf die VM aufzubauen, muss man bloss einen kurzen Befehl eingeben.
```shell
vagrant ssh
```

K2
======
## GitHub Account
> [⇧ Nach oben](#inhaltsverzeichnis)

Zuerst sollte ein Github Account erstellt werden:
1. Auf [GitHub.com](https://github.com) gehen
2. Auf Sign up klicken
3. Username, E-mail und Passwort eingeben sowie Aufgabe zum verifizieren lösen
4. Auf Create an Account klicken


## Persönlicher Wissenststand
> [⇧ Nach oben](#inhaltsverzeichnis)

Linux

Linux ist ein kostenloses Betriebssystem, welches immer wieder weiterentwickelt wird. Die neusten Versionen sind immer Online. 
Ich bin nicht so ein Linux fan, aber was mir ziemlich gut an das Betriebssystem gefällt, ist die eindeutige Fehlermeldungen.
Ich habe schon sehr oft mit Linux gearbeitet, jedoch ist Linux wirklich nicht meine Stärke. 

Virtualisierung



Vagrant
Vagrant kannte ich vor diesem Modul überhaupt nicht, jetzt kenne ich es. Ich kenne mitlerweile verschiedene Vagrantbefehle 
und kann auch nun Vagrant Files erstellen.

Markdown
Systemsicherheit
