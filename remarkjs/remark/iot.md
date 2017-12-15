class: center, middle, uum

# IoT
## Mein Überblick
.footnote[Vortrag "IoT - Hands On", Volker.Benders@unterschiedundmacher.com]

---
class: center, middle, uum

.left-column[
  IoT - Hand On
]
--
.right-column[
  Building the Infrastructure
]
--
.right-column[
  Sender
]
--
.right-column[
  MQTT Broker
]
--
.right-column[
  Subscriber
]


---
class: center, middle, uum

.left-column[
  Was sagt Wikipedia?
]

.right-column[
  Das Internet der Dinge bezeichnet die Vision einer durch Informations- und Kommunikationstechniken in globalen Informationsgesellschaften vernetzten Infrastruktur von Alltagsgegenständen.
]

---
class: center, middle, uum

# WTF!
---
class: center, middle, uum

.left-column[
  Und jetzt verständlich
]

--
.right-column[
  IoT ist die fixe Idee das alles und jedes kommunizieren muss.
]

---
class: center, middle, uum

# Jede Steckdose

--
# jeder Toaster

--
# jeder Lichtschalter


---
class: center, middle, uum

.left-column[
  soll am Besten
]
--
.right-column[
  - seinen Status mitteilen
]
--
.right-column[
  - sich manipulieren lassen
]

---
class: center, middle, uum

# Damit jeder mit jedem und allem sprechen kann
---
class: center, middle, uum

# Das gilt sowohl für

---
class: center, middle, uum
# Sensoren
---
class: center, middle, uum
## und
---
class: center, middle, uum
# Aktoren

---
class: center, middle, uum

#  Sensoren ermöglichen die Erfassung von Zuständen der realen (physischen) Welt


---
class: center, middle, uum

# Aktoren ermöglichen die Manipulation der realen (physischen) Welt

---
class: center, middle, uum

# Herausforderungen

--

Universalität

--

Flexibilität

--

Interoprabilität

---
class: center, middle, uum

# Universalität

## IoT kann überall sein

???
Kühlschrank, Lampe, Heizung, Stromzähler (aka SmartGrid), Rasenmäher, die Gartenbewässerung...

---
class: center, middle, uum

# Flexibilität

## Der Begriff IoT ist so allumfassend, das es möglich sein muss ALLES zu messen.

---
class: center, middle, uum

# Interoperabilität

## Ein gemeinsamer Nenner muss her
## Eine gemeinsame Kommunikationsbasis muss her

???
Bloss nicht Standard sagen!
---
class: center, middle, uum

Zentrales Konzept ist Kommunikation:


--
1. leitgewichtig
--
2. stromsparend
--
3. unterstützt QoS
--
4. flexibel
--
5. format unabhängig

---
class: center, middle, uum
Zentrales Element ist meistens ein s.g. Message-Broker

???
- [Hive MQ](www.hivemq.com)
- [Eclipse Pahoe]()

---
class: center, middle, uum

Mesage Broken implementieren eine Topic bsaierte Publish- / Subscribe-Architektur.

---
class: center, middle, uum

Dies ermöglicht eine lose Kopplung der beteiligten Komponenten

---
class: center, middle, uum
# Der Einstieg

## Erfahrung kann ganz verschieden gesammelt werden

??? Arduino, Genuiono, Raspberry-, Orange-Pi
---
class: center, middle, uum

# (Programmier-) Sprachen

---
class: center, middle, uum
## Im Prinzip eignet sich jede Sprache die Netzwerk-Verkehr initieren kann

--

JavaScript aka Node.JS

--

Python

--

C

--

Basic

???
Kennt noch jemand die Basik-Briefmarke?!
You name it!


---
class: center, middle, uum

# Hardware

---
class: center, middle, uum

## Je nach Anforderung kann die Hardware beliebig gross oder klein ausfallen

---
class: center, middle, uum

### Industrie-PC

---
class: center, middle, uum

### Hutschienen PC


---
class: center, middle, uum

### SPS (Speicher Programmierbare Steurungen)

---
class: center, middle, uum

### Arduino (Mini, Nano, Pro, Mega)

---
class: center, middle, uum

### Raspi

---
class: center, middle, uum

### ESP8266-E*

Meine Lieblingsplatform

---
class: center, middle, uum

# ESP8266-E01 & ESP8266-E12
# Warum?

--

## 0.5-4MB Speicher
--

## 80-160 MHz Taktung
--

## äusserst flexibel

???
Arduino typisch mit ~16MHz (max. ca. 400 MHz), Speicher typ. mit 16-256 kB
[Arduino Comparison](https://www.arduino.cc/en/Products/Compare)
---

class: center, top
background-image: url(./esp8266-e01.jpg)

# ESP8266-E01
---
class: center, middle, uum
# ESP8266-E01

--

## Sehr klein (21x11 mm)

--

## Gut für Batteriebetrieb
--

## Zwei GPIO-Ports (I2C, One Wire)
---
class: center, middle, uum, uum
--

### wo viel Licht ist, da ist viel Schatten
--

### Wählerisch bei der Stromversorgung (3.3 Volt)
--

### Braucht Spannnungswandler für I/O (5v -> 3v3)
--

### Umständlich zu programmieren
---
class: center, middle, uum
# ESP8266-E12

--

### rel. gross (ca. 50x30 mm)

--
### Auch für Batteriebetrieb
--

### 9 GPIO-Ports
--

### Einfach zu programmieren




---
name: unterschiedundmacher
class: center, media, uum
