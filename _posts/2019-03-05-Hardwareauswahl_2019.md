---
layout: post
title: Neue Teilnahme, Neue Sekundärmission, Neue Hardware!
lang: DE
ref: Hardwareauswahl_2019
categories: [cansat2019]
teaserImage: /images/posts/2019-03-06_Blockdiagram.jpg
---

Wir haben uns für unsere Sekundärmission dieses Jahr viel vorgenommen, und um das alles zu erreichen brauchen wir um einiges bessere Hardware als im Vorjahr - denn mit einem Arduino und ein paar Sensor Breakouts ist es noch lange nicht getan.

{% include image.html path="/images/posts/2019-03-06_Blockdiagram.jpg" %}

## Primärmission

Die Primärmission besteht darin, die Temperatur und den Luftdruck während des Flugs zu messen. Dazu verwenden wir nicht einen, sondern gleich zwei *BME280* Module von Bosch. Diese sind extrem kompakt, sind gut dokumentiert und lassen sich leicht über I2C einsteuern. Der Sensor hat eine Druckauflösung von ±1 hPa und kann die Umgebungstemperatur auf ±1 °C genau messen. Warum zwei? Weil wir's können. Außerdem auch noch als Backup - Wer weiß was noch passieren kann.

## Sekundärmission

### Kameras

Unsere Kamera muss klein sein aber gleichzeitig eine Auflösung hoch genug haben, um zuverlässig Bodenmerkmale auf den Bildern ausmachen zu können. Dafür haben wir uns für die *OV5640* von OmniVision entschieden. Die Auflösung und Bildrate sind von 2592 x 1944 Pixel bei 15 Fps bis hinzu 320 x 240 Pixel bei 120 Fps in Stufen einstellbar was uns genug Freiheit zum Einstellen und Aussuchen der für uns besten Kombination gibt. Angesteuert wird die Kamera zum einen über SCCB (Serial Camera Control Bus) welches dem typischen I2C Protokoll nicht unähnlich ist, die Bilddaten selber werden über ein 8-bit DVP (Digital Video Port) ausgegeben. Eventuell bauen wir noch einen DVP-UART Converter zwischen Controller und Kamera um die Kamera über eine serielle Schnittstelle anzusteuern, das muss aber noch getestet werden.

### Motortreiber

Unser Reaktionsradmotor dreht sich nicht von alleine, dafür verwenden wir den *DRV8838* Motortreiber von Texas Instruments. Dieser Single-Channel Treiber kann einen Motor mit 1,7 A (maximal 1,8 A) bei bis zu 11 V steuern. Dabei sind nicht nur Richtung sondern auch Geschwindigkeit frei einstellbar. Der Motortreiber wird selber wiederum über 2 Pins vom Controller angesteuert und direkt mit der Hauptbatterie verbunden um die nötige Leistung zu liefern.

### Gyroskop

Ein sich drehender Motor ist schon was tolles, noch besser wärs zu wissen, in welche Richtung er sich drehen muss um die Drehung des CanSats auszugleichen. Das 9 DOF Gyroskop / Accelerometer / Kompass *BNO055* von Bosch bietet nicht nur Daten zur Rotation sondern zu gesamten Lage des CanSats im Raum. Da sich das Errechnen der Drehung und Beschleunigung aus den Rohdaten eines MEMS Sensor als erstaunlich umständlich erweist, integriert der BNO055 zusätzlich einen ARM Cortex M0, der alle Sensordaten direkt verrechnet und in unterschiedlichsten Formaten ausgibt, was unserem Hauptprozessor viel Zeit und Rechenleistung spart. 

## System und zusätzliche Sensoren

### Prozessor

Um zwei Video Livefeeds gleichzeitg verarbeiten zu können bedarf es mehr Rechenleistung, als ein ATMega328P je liefern könnte. Deswegen wollen wir den *STM32H743ZI* von STMicroelectronics verwenden. Den Chip haben wir uns nicht nur wegen seines leicht einprägsamen Namens ausgesucht, sondern aufgrund seiner herausragenden Performance. Der Prozessor basiert auf dem ARM Coretx M7 und mit 400 MHz (25 mal schneller als ein Arduino) und 1 MByte RAM (500 mal mehr als ein Arduino) wird es ein leichtes sein, mehrere Messdaten sowie die Bilder gleichzeitig aufzuzeichnen.
Um den Chip einfacher programmieren zu können implementieren wir ein HAL (Hardware Abstraction Layer). Dies sorgt dafür, dass unser Programm weitesgehend unabhängig von der Hardware funktioniert, was hilfreich sein kann falls wir uns doch für einen anderen Chip entscheiden. Auf die Programmierung werden wir in einem späteren Blogpost nochmal genauer eingehen.

### Interne Thermometer

Im CanSat befinden sich viele Komponenten, die Hitze abgeben können (und werden). Spannungswandler, Motoren, Motortreiber und Prozessoren werden sich während des Fluges erhitzen, was die Messdaten unserer Primärmission verfälschen könnte. Um besser zu verstehen, wie sich die Hitze im CanSat verteilt bauen wir 5 *DS18B20* Thermometer von Maxim Integrated in verschiedenen Stellen im CanSat ein. Diese sind sehr klein und lassen sich über das von Maxim entwickelte OneWire Protokoll über nur eine Verbindung zum Prozessor verbinden.

### GPS

Zur Positions- und Zeitbestimmung verwenden wir das *MTK3339* GPS Modul von MediaTek mit integrierter Patch Antenne. Das Modul kann auf bis zu 22 Kanälen gleichzeitig Satelliten tracken und wird über UART angesprochen.

### Funkmodul

Zum Übertragen der Telemetriedaten verwenden wir das Funkmodul *RFM69HCW* von HopeRF. Es operiert mit 433 MHz im ISM Band (auf dem jeder der will ohne Lizenz senden kann) mit einer maximalen Übertragungsleistung von 20 dBm. Zwar macht es die geringe Datenrate von 300 kb/s für uns unmöglich, Live Bilder in einer akzeptablen Geschwindigkeit zu empfangen, dafür können wir unsere Sensordaten relativ einfach an unsere Bodenstation übertragen.

### Speicher

Da unser Prozessor direkte SDMMC Unterstützung hat können wir unsere Bilder und Messdaten direkt auf eine SD-Karte schreiben. Da wir allerdings letztes Jahr schlechte Erfahrung mit SD-Karten gemacht haben haben wir uns entschieden, zusätzlich einen externen EEPROM (Electrically Eraseable Programmable Read-Only Memory) anzuschließen. Der *M24M01* von STMicroelectronics bietet mit einem MBit zwar keinen Speicherplatz für unsere Bilder, dafür können wir unsere wichtigesten Messdaten (vor allem für die Primärmission) so zusätzlich abspeichern. Der Chip nimmt im CanSat kaum Platz weg und wird (wie so viele andere) über I2C angesteuert.

## Stromversorgung

### Spannungswandler

Unsere gesamte Elektronik arbeitet mit 3,3 V Spannungsleveln und ist kaum resistent gegen höhere Spannungen. Um alle Komponenten zuverlässig mit Strom zu versorgen verwenden wir den *TPS62110* von Texas Instruments. Der DC/DC Step-Down Converter ist in der Lage bis zu 1,5 A bei Eingangsspannungen von 3,1 bis 17 V zu liefern. Im Gegensatz zu einem linearen Spannungswandler ist der Schaltregler um einiges effizienter (~95%), was besonders für kompakte und batteriebetriebene Projete wie unseres relevant ist.

## Backup

Und was wenn's nicht klappt? Was passiert wenn der Spannungswandler überhitzt?? Was passiert wenn der Prozessor auf einmal kaputt geht? Oder was wenn die Batterie durch die Erschütterungen rausgelöst wird und die gesamte Stromversorgung trennt? Es ist immer gut ein Backup zu haben, das so weit wie möglich von dem restlichen System abgetrennt ist. Deswegen wollen wir, zusätzlich zu unserer Hauptelektronik ein Zweitsystem einbauen, das gerade so in der Lage ist die Primärmission zu erfüllen. Mit eigener Stromversorgung, eigenem Speicher und eigenem Prozessor.

### Backupprozessor

Der *ATTiny85* gehört so zu den kleinsten und leistungsschwachsten Mikrocontrollern, die Atmel herstellt. Mit einer 1 MHz interner Clock und 512 Byte an RAM ist er kaum in der Lage, auch nur ansatzweise so viel zu schaffen wie der STM32H7x3. Trotzdem kann einen Sensor und ein Speichermodul anzusteuern. Die Stromversorgung erfolgt über eine Knopfzelle.

### Barometer / Thermometer

Zum Erfüllen der Primärmission verwenden wir einen BMP280 von Bosch. Dieser hat, ähnlich wie der BME280, eine Druckauflösung von ±1 hPa und eine Temperaturmessgenauigkeit von ± 1 °C. Dafür kann er keine Luftfeuchtigkeit messen - Das ist ja auch nicht Teil der Primärmission.

### Speichermodul

Auch hier verwenden wir wieder den *M24M01* von STMicroelectronics (siehe oben).

<br />

Vermutlich wird sich diese Liste ständig weiterentwickeln während wir selber entwickeln, designen und testen. Vielleicht tauschen wir einige Komponenten durch andere aus oder streichen sie ganz weg. Aber jetzt werden wir erstmal mit dem arbeiten was wir haben, denn damit sollten wir schon weit kommen,
