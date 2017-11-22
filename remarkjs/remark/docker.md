class: center, middle, uum

# Docker
## einführung
.footnote[Vortrag "IoT - Hands On", Volker.Benders@unterschiedundmacher.com]

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

.right-column[
  Docker ist eine weitere Möglichkeit virtuelle Maschienen zu benutzen.
]

---
class: center, middle, uum

.left-column[
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
  Timewarp
]

.right-column[
Heute hat jeder Aldi-Rechner genug Schwuppdizität um mehrere Applikationen zugleich auszuführen
]

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
--
(sehr viele Images)[https://app.vagrantup.com/boxes/search]
(einige Images - z.Bsp mit Oracle 12c unter)[http://www.oracle.com/technetwork/community/developer-vm/index.html]


---
class: center, middle, uum

.left-column[
  Wie virtualisiert die Konkurenz
]
--
.right-column[
 (ISO-) Image erzeugen
]
--
.right-column[
 Manuell oder mit ansible, puppet,salt, chef...
]
--
.right-column[
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
  Wie macht es Docker
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

class: center, middle, uum





---
name: unterschiedundmacher
class: center, media, uum
