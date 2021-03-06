---
layout: post
title: From a paper sketch to our CanSat's brain
lang: EN
ref: Platinendesign2019
categories: [cansat2019]
teaserImage: /images/posts/2019-08-23_Platinen_mit_Schaltplan.jpg
---

The printed circuit boards (PCBs) are our CanSat's heart. They hold all electronic components and connect the sensors to our microcontroller. The PCBs also accommodate the power supply, storage, memory and the backup system. However, the design and assembly of the circuit boards is quite complex. We'll explain you in this blogpost how to turn an idea and a sketch into finished printed circuit boards.

## Which components have to be installed?

{% include post-figure.html path="/images/posts/2019-08-23_SMD_Komponenten.jpg" caption="Some components are quite tiny, like this little 0402 capacitor." alignment="right" image_size="small" %}

In total, 17 sensors are used in our CanSat. We measure air pressure and temperature in several places, but also position, rotation, acceleration, internal temperatures, power consumption and light intensity are captured and recorded – often with more than one sensor each.

In addition, there are voltage regulators, memory chips, SD card slots, the motor driver, the radio module and of course the microcontroller. 

## Schematics design: SMD instead of breakouts

[Last year](https://apoapsishgv.github.io/Schematic-and-PCB-Design/) we used different breakouts for the individual components. ([What is a breakout board?](https://programmingelectronics.com/what-is-a-breakout-board-for-arduino/)) This approach worked, but it required a lot of space inside the CanSat.

That's why we decided to place SMD components directly onto a self-designed circuit board. We first had to comb through hundreds of pages of datasheets to understand how to place and interface the individual chips and sensors. There are also public available reference designs for some of the breakouts we used for testing which we could incorporate directly into our circuit.

Eventually, the first important milestone was reached: our circuit diagram. We designed it in [KiCad](http://www.kicad-pcb.org/), an open source design environment for circuit design.

{% include post-figure.html path="/images/posts/2019-08-23_Platinenlayout_EDA.png" caption="The finished layout" %}


## The PCBs

<figure class="right">
  <a href="https://jlcpcb.com">
    <img src="{{ site.baseurl }}/images/2019-sponsoren/JLCPCB.png" />
  </a>
</figure>

Our sponsor [JLCPCB](https://jlcpcb.com) has taken over the production of the PCBs. JLCPCB is a leading manufacturer of all kinds of printed circuit boards and produces designs quickly and cost-effectively.

In total, we use five circuit boards for our project:

- **One main board**: It is located at the top of the CanSat and houses the control logic, the power supply and almost all sensors. Since we have to connect a lot of nets (1397 to be exact), we use six layers; otherwise we wouldn't have enough space for all connections.

- **One motor module**: This board accommodates the motor, the motor controller, an additional gyroscope and a thermometer. It is mounted at the bottom of the CanSat and is connected to the main board with ribbon cables.

- **Two camera adapters**: The two OV5640 cameras are mounted here, together with two voltage regulator each, which supplies the camera with the different voltage levels. The camera modules are connected to the motherboard via ribbon cables, too.

- **One ground station controller**: Like last year, we want to use our self-orienting ground station. For this, we have designed a new board with several upgrades: a more efficient voltage regulator, a 32-bit microcontroller, native High Speed USB connection and support for an OLED display are just a few of them. In a future blog post we'll also go into more detail about the ground station.

After we had received the circuit boards, the assembly started. Using a stencil, we applied solder paste and then placed the individual components with a steady hand. Once all the chips and passive components were in place, we liquefied the solder paste with a hot air soldering station.

{% include post-figure.html path="/images/posts/2019-08-23_Lötpaste_auftragen.jpg" caption="Coating of the circuit boards" %}

## No plan is perfect

Soon we found several small problems in our board design, which we want to fix in a second revision of the main board. For example, we don't want to connect all the sensors to a asingle I²C/SPI bus for redundancy reasons. In addition, the bit-bang implementation of the DVP (Digital Video Port) we want to use for the cameras has turned out to be more difficult than expected. Therefore, we will connect both cameras to a single bus and connect them to the DCMI (Digial Camera Interface) provided natively by the STM32. Also some footprints have to be updated and the layout has to be adapted for the mounting in our CanSat.

{% include post-figure.html path="/images/posts/2019-08-23_Platine_durch_Lupe.jpg" caption="The assembled circuit board" %}

So far, designing the electronics in our CanSat has been an outstanding learning experience for us – not only in terms of layout and assembly, but also the implementation of various communication protocols (such as I2C, SPI, USART, SDMMC and USB) and the realization of design standards. As soon as we have the next version of our board, we can build a first prototype CanSat.
