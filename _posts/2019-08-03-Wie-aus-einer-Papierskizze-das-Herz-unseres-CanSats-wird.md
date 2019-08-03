---
layout: post
title: Wie aus einer Papierskizze das Herz unseres CanSats wird 
lang: DE
ref: Platinendesign2019
categories: [cansat2019]
teaserImage: /images/posts/TODO
---

## Welche Komponenten müssen verbaut werden?

Insgesamt verwenden wir 17 Sensoren in unserem CanSat. Damit messen wir an mehreren Stellen Luftdruck und Temperatur, aber auch Position, Drehung, Beschleunigung, interne Temperaturen, Stromverbrauch und Lichteinfall werden teilweise mit je mehr als einem Sensor erfasst.

Dazu kommen noch Spannungsregler, Speicherchips, SD-Kartenslots, der Motortreiber, das Funkmodul und natürlich die Mikrocontrollor. 

## Schaltplan-Design: SMD statt Breakouts

[Letztes Jahr](https://apoapsishgv.github.io/Schaltplan-und-Platinen-Design/) haben wir für die einzelnen Komponenten verschiedene Breakouts verwendet. ([Was ist ein Breakout-Board?](https://programmingelectronics.com/what-is-a-breakout-board-for-arduino/)) Dieser Ansatz hat auch funktioniert, allerdings ist er alles andere als platzsparend.

Daher haben wir uns entschieden, die SMD-Bauelemente direkt auf eine selbstdesignte Platine zu setzen. Dazu mussten wir zunächst mehrere hunderte Seiten von Datenblättern durchkämmen, um zu verstehen, wie die einzelnen Chips und Sensoren platziert werden können. Auch gibt es für einige der Breakouts, die wir zum Testen verwendet haben, öffentliche Referenzdesigns, die wir direkt in unsere Schaltung einbauen konnten.

Nach und nach entstand so der erste wichtige Meilenstein: Unser Schaltplan. Diesen haben wir in [KiCad](http://www.kicad-pcb.org/) designt, einer Open-Source-Designumgebung für Schaltungsdesign.

## Die Platinen

<figure class="right">
  <a href="https://jlcpcb.com">
    <img src="{{ site.baseurl }}/images/2019-sponsoren/JLCPCB.png" />
  </a>
</figure>

Die Herrstellung der Platinen hat unser Sponsor [JLCPCB](https://jlcpcb.com) übernommen. JLCPCB ist ein führender Herrsteller für Leitplatten aller Art und prdouziert schnell und kosteneffektiv fertige Designs.

Insgesamt verwenden wir fünf Platinen für unser Projekt:

- **Eine Hauptplatine**: Diese sitzt ganz oben im CanSat und beherbergt die Steuerung, die Stromversorgung und so gut wie alle Sensoren. Da wir sehr viele Leitungen verbinden müssen (1397, um genau zu sein), verwenden wir sechs Schichten, da wir sonst nicht genügend Platz für alle Verbindungen hätten.

- **Ein Motormodul**: Diese Platine beherbergt den Motor, die Motorsteuerung, ein zusätzliches Gyroskop und ein Thermometer. Sie wird ganz unten im CanSat befestigt und mit Flachbandkabeln mit der Hauptplatine verbunden.

- **Zwei Kameraadapter**: Hier werden die beiden OV5640 Kameras befestigt, zusammen mit je einem Spannungswandler, welcher die Kamera mit den unterschiedlichen Spannungsleveln versorgt. Auch die Kameramodule werden über Flachbandkabel mit der Hauptplatine verbunden.

- **Eine Bodenstationssteuerung**: Wie auch letztes Jahr wollen wir wieder unsere selbstausrichtende Bodenstation verwenden. Dafür haben wir eine neue Platine mit mehreren Upgrades designt: ein effizienterer Spannungswandler, ein 32-Bit Mikrocontrollor, native HS-USB Verbindung und Support für ein OLED-Display sind nur ein paar davon. In einem zukünftigen Blogpost gehen wir auch näher auf die Bodenstation ein.

Nachdem wir die Platinen erhalten haben, gings an die Bestückung. Mithilfe von Schablonen haben wir Lötpaste aufgetragen und danach mit ruhiger Hand die einzelnen Komponenten platziert. Sobald alle Chips und passive Komponenten an der richtigen Stelle waren, verflüssigten wir die Lötpaste mit einer Heißluftlötstation.

## Kein Plan ist perfekt

Schon bald haben wir mehrere kleine Probleme in unserem Platinendesign gefunden, die wir in einer zweiten Revision der Hauptplatine beheben wollen. Dazu gehören unter anderem, dass wir die Sensoren aus Redundanzgründen nicht alle an einem I²C/SPI Bus hängen wollen. Zudem hat sich die Bit-Bang-Implementierung des DVP (Digital Video Port), den wir für die Kameras verwenden wollen, als schwieriger herausgestellt als gedacht. Daher werden wir beide Kameras an einen Bus hängen und mit dem DCMI (Digial Camera Interface) verbinden, das der STM32 nativ zur Verfügung stellt. Auch müssen ein paar Footprints aktualisiert werden und das Layout für die Befestigung im CanSat angepasst werden.

Bisher war das Elektronikdesign für uns eine herausragende Lernerfahrung – nicht nur, was das Layout und die Bestückung angeht, sondern die Implementierung von verschiedenen Kommunikationsprotokollen (wie bspw. I2C, SPI, USART, SDMMC und USB) sowie die Umsetzung von Designstandards. Sobald wir die nächste Version unserer Platine haben, können wir einen ersten Prototypen fertigstellen.
