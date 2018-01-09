class: center, middle, uum

# Docker
## Einführung
.footnote[Vortrag "Docker - Eine Einführung", Volker.Benders@unterschiedundmacher.com]
>>>>>>> docker

---
class: center, middle, uum

.left-column[
  Docker
]
--
.right-column[
  Worum geht es
]
--
.right-column[
  Geschichte
]
--
.right-column[
  Andere Mitspieler
]
--
.right-column[
  Wo liegen die Unterschiede
]
--
.right-column[
  Warum gerade Docker?
]


---
class: center, middle, uum

.left-column[
  Worum geht es?
]
<<<<<<< HEAD

.right-column[
  Docker ist eine weitere Möglichkeit virtuelle Maschienen zu benutzen.
]
=======
--
.right-column[
  Docker ist eine weitere Möglichkeit virtuelle Maschienen zu benutzen.
]
--
.left-column[
  Abgrenzung zum Rest
]
--
.right-column[
  Docker will Services virtualisieren
]
--
.right-column[
  Werkzeuge für
]
--
.right-column[
  Erstellung
]
--
.right-column[
  Versionierung
]
--
.right-column[
  Provisionierung
]
--
.right-column[
  Orchestrierung
]
>>>>>>> docker

---
class: center, middle, uum

.left-column[
<<<<<<< HEAD
=======
  Docker Flow
]
--
.right-column[
  Deklaration im `Dockerfile`
]
--
.right-column[
  Bauen eines `Image`
]
--
.right-column[
  Starten des `Images` - es wird zum `Container`
]
---
class: center, middle, uum

.left-column[
  Terminologie der Docker-Welt
]
--
.right-column[
  Dockerfile
]
--
.right-column[
  Docker Registry
]
--
.right-column[
  Docker Image
]
--
.right-column[
  Docker Container
]
--
.right-column[
  Docker Registry
]
---
class: center, middle, uum

.left-column[
  Das Dockerfile
]
--
.right-column[
  deklarative Beschreibung der System-Konfiguration
]
--
.right-column[
  distributionsunabhängig
]
--
.right-column[
  Plaintext mit eigener DSL
]
--
.right-column[
  gut zu versionieren
]
---
class: center, middle, uum

.left-column[
  Die Docker Registry
]
--
.right-column[
  Repo mit Images
]
--
.right-column[
  Einfache Verteilung
]
--
.right-column[
private / public Registries
]
--
.right-column[
  Analog den Maven Repositories
]
---
class: center, middle, uum

.left-column[
  Images
]
--
.right-column[
  Images sind das Ergebnis der Abarbeitung eines Dockerfiles.
]
--
---
class: center, middle, uum

.left-column[
  Was ist Anders?
]
--
.right-column[
  Infrastruktur
]
--
.right-column[
  Dependency-Managemnt
]
--
.right-column[
  Versionsverwaltung
]
--
.right-column[
  Skalierbarkeit
]
--
.right-column[
  Applikations-Upgrade mit Zero Downtime
]
--
---
class: center, middle, uum

.left-column[
>>>>>>> docker
  Geschichte
]

.right-column[
1974:
Anfänge [IBM MVS, 1970er](https://de.wikipedia.org/wiki/Multiple_Virtual_Storage).
]
--
.right-column[
Time Sharing Option [TSO](https://de.wikipedia.org/wiki/Time-Sharing_Option)
]
--
.right-column[
Hauptmotivation war die (sauteuren) Rechner besser zu nutzen
]

---
class: center, middle, uum

.left-column[
<<<<<<< HEAD
  Timewarp
]

=======
  Timewarp nach 2013
]
--
>>>>>>> docker
.right-column[
Heute hat jeder Aldi-Rechner genug Schwuppdizität um mehrere Applikationen zugleich auszuführen
]

<<<<<<< HEAD
=======
--
.rigth-column[
03/2013 dotCloud stellt "Docker" vor
]

>>>>>>> docker
---
class: center, middle, uum

.left-column[
  Wie sieht es mit Alternativen aus?
]

.right-column[
[VMWare](https://www.vmware.com/de.html)
]
--
.right-column[
[Vagrant](https://de.wikipedia.org/wiki/Vagrant_(Software)
]
--
.right-column[
[Parallels](https://www.parallels.com/de/all-products/)
]
--
.right-column[
[Microsoft Hyper-V](https://de.wikipedia.org/wiki/Hyper-V)
]
--
.right-column[
[Virtualbox](https://www.virtualbox.org/)
]
<<<<<<< HEAD
--
(sehr viele Images)[https://app.vagrantup.com/boxes/search]
(einige Images - z.Bsp mit Oracle 12c unter)[http://www.oracle.com/technetwork/community/developer-vm/index.html]


=======
>>>>>>> docker
---
class: center, middle, uum

.left-column[
<<<<<<< HEAD
  Wie virtualisiert die Konkurenz
]
--
.right-column[
 (ISO-) Image erzeugen
=======
  Muss ich bei Null anfangen?
]
--
.right-column[
[Docker - 100.000+ Images](https://hub.docker.com/)
]
--
.right-column[
[Vagrant - sehr viele Images](https://app.vagrantup.com/boxes/search)
]
--
.right-column[
[Oracle VirtualBox - einige Images - z.Bsp mit Oracle 12c unter](http://www.oracle.com/technetwork/community/developer-vm/index.html)
]
.right-column[
...
]
---
class: center, middle, uum

.left-column[
 Wie virtualisiert die Konkurenz
>>>>>>> docker
]
--
.right-column[
 Manuell oder mit ansible, puppet,salt, chef...
]
--
.right-column[
<<<<<<< HEAD
=======
 Ergenis ist ein vollständiges OS
]
--
.right-column[
>>>>>>> docker
Verteilen
]
--
.right-column[
verwenden
]

--

Resultat: Es entsteht ein Monolith

---
class: center, middle, uum

.left-column[
<<<<<<< HEAD
  Wie macht es Docker
=======
 Docker-Philosophie
]
--
.right-column[
 Ein Container -> ein Dienst
]
--
.right-column[
 Maximale Wiederverwendung
]
--
.right-column[
 Reduce to the Max
]
---
class: center, middle, uum

.left-column[
 Wie macht es Docker
]
--
.right-column[
 Ausgehend von einem Basis Image werden diesem die benötigten Dienste hinzugefügt.
]
--
.right-column[
 Docker bedeutet Infrastruktur
]
--
.right-column[
 *Dockerfile*: Deklative Beschreibung
]
--
.right-column[
 `Dockerfile`: Deklative Beschreibung
>>>>>>> docker
]
--
.right-column[
 `Dockerfile`: Systeme werden scheibchenweise definiert
]
--
.right-column[
 `Image`: Read-only Vorlage
]
--
.right-column[
 Image bauen
]
--
.right-column[
 Image starten
]
--
.right-column[
 Ein gestartetes Image wird als Container bezeichnet
]
--
.right-column[
 Ausgangspunkt für eigne [ Images ist Dockerhub ](https://hub.docker.com/)
]
---
class: center, middle, uum

.left-column[
  Ablauf
]
--
.right-column[
 Image bauen
]
--
.right-column[
 Image starten
]

---
class: center, middle, uum

.left-column[
  Wie macht es Docker
]
.right-column[
 Ausgangspunkt für eigne [ Images ist Dockerhub ](https://hub.docker.com/)
]
--
.right-column[
 Für interne Images kann meine eine eigene Registry betreiben
]
--
.right-column[
 Natürlich auch als [Docker-Image](https://hub.docker.com/_/registry/)
]

---
class: middle, uum

Docker beschreibt den Aufbau eines Docker Images in einer ASCII Text-Datei.
Hier als Beispiel unser [Oracle Image](http://vbe@info.syngenio.net/rhodecode2/ruv/docker_java_8)

```
FROM ubuntu:16.04

ENV JAVA_VER 8
RUN rm -rf /var/lib/apt/lists/*
RUN apt-get -y update
RUN apt-get -y install software-properties-common wget tar

USER root

RUN add-apt-repository ppa:webupd8team/java && apt-get -y update
RUN echo oracle-java$JAVA_VER-installer shared/accepted-oracle-license-v1-1 select true |  /usr/bin/debconf-set-selections && \
    apt-get install -y --force-yes --no-install-recommends oracle-java$JAVA_VER-installer oracle-java$JAVA_VER-set-default

RUN apt-get install -y oracle-java$JAVA_VER-unlimited-jce-policy

# EOF
```

---
class: center, middle, uum

Wie sieht die Ausführung aus?
--
Ich hab' da mal was vorbereitet :-)
---
class: middle, uum
# Das einfachste vom Einfachen

```
public fun main(args: Array<String>) {
  println("Hallo")
}
```
---
class: middle, uum
# Einfach Bauen
```
$> kotlinc simple.kt -include-runtime -d simple.jar
$> ll
-rw-r--r--   1 vbe  staff   845K 22 Nov 12:13 simple.jar
-rw-r--r--   1 vbe  staff    61B 22 Nov 10:30 simple.kt
```
---
class: middle, uum
# Einfach Ausführen
```
$> java -jar simple.jar
Hallo
```

Aber wo ist hier Docker im Spiel?
---
class: middle, uum
# Hier mit Docker
```
$> docker run \
    --rm \
    -v "$PWD":/tmp \
    -w /tmp \
    java:openjdk-8-jre \
    java -jar simple.jar
Hallo
```
---
<<<<<<< HEAD

class: center, middle, uum

=======
class: center, middle, uum

# Zusammenarbeit

Ein Container alleine macht noch nicht viel.
--
Docker stellt virtulle Netzwerke bereit
--
darüber könnne Container Daten austauschen.

```
docker network create ruv
sh startWildfly.sh

sh startMailcatcher.sh
```

>>>>>>> docker




---
name: unterschiedundmacher
class: center, media, uum
