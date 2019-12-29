# OrangePi Zero

[TOC]



## Hardware

<img src="./assets/images/orangepi_zero.png" alt="Orange Pi Zero" style="zoom:25%;" />

The OrangePi Zero is a Single Board Computer made by [Shenzhen Xunlong Software CO., Limited](http://www.xunlong.tv/), a company located in Shenzhen, Guangdong, China.

### SoC

It is based on a downgraded version of the famous AllWinner [H3](http://www.allwinnertech.com/index.php?c=product&a=index&id=47) (it lacks Gigabit MAC and 4K HDMI output support), named [H2+](http://www.allwinnertech.com/index.php?c=product&a=index&id=62).

<figure>
  <img src="./assets/images/h2.jpg" alt="h2" style="zoom:50%;display: block; margin: 0 auto"/>
  <figcaption>H2 description by AllWinner</figcaption>
</figure>

On the Zero, not all the features of the H2+ are hardwired. So we don't have any camera, HDMI nor Nand Flash.

CPU

- Quad-core Cortex™-A7 running from 480MHz to 1008MHz

GPU

- Muti-Core Mali400 GPU 
- Supports OpenGL ES 2.0

Display

- ~~Supports 1080P HDMI output with HDCP~~
- ~~Supports HDMI CEC~~ 
- ~~Supports HDMI 30 function~~ 
- Integrated [CVBS](https://en.wikipedia.org/wiki/Composite_video) 
- ~~Supports simultaneous output of HDMI and CVBS~~
  	

Memory

- Supports LPDDR2/ LPDDR3/ DDR3/ DDR3L SDRAM 
- Supports 8-bit SLC/MLC/TLC/EF NANO with 64-bit ECC 
- Supports SD/~~eMMC/tSD/fSD/efSD~~



Video

- Supports multi-format 1080p@60fps video decoding, including H.265/HEVC, H.264 BP/MP/HP, VP8, MPEGl/2, MPEG4 SP/ASP GMC, H.263 including Sorenson Spark, WMV9/VC- l,JPEG/MJPEG, etc
- Supports H.264 1080p@30fps video encoding
  	

~~Camera~~

- ~~Supports 8-bit YUV422 CMOS sensor interface~~ 
- ~~Supports CCIR656 protocol for NTSC and PAL~~ 
- ~~Supports 5M pixel camera sensor~~ 
- ~~Supports video capture solution up to 1080p@30fps~~ 

### Pinout

#### 1x13 Header

<figure>
  <img src="./assets/images/OPiZero_pinout.jpg" alt="h2" style="zoom:50%;display: block; margin: 0 auto"/>
  <figcaption>OrangePi Zero Pinout by OSHLab.com</figcaption>
</figure>

On the board itself, there is a first row of pins that reflect a few features of the SoC:

| 1x13 Header |                                                              |
| ----------- | ------------------------------------------------------------ |
| 1           | *5V*                                                         |
| 2           | *GND*                                                        |
| 3           | USB-DM2 (combined to the pin #4, 5V and GND, this makes a USB port) |
| 4           | USB-DP2                                                      |
| 5           | USB-DM3 (combined to the pin #6, 5V and GND, this makes a USB port) |
| 6           | USB-DP3                                                      |
| 7           | LINEOUTR (audio output Right side)                           |
| 8           | LINEOUTL (audio output Left side)                            |
| 9           | TV-OUT (The default mode is PAL, with 720x576 resolution)    |
| 10          | MIC-BIAS                                                     |
| 11          | MIC1P                                                        |
| 12          | MIC1N                                                        |
| 13          | [CIR](http://linux-sunxi.org/CIR)-RX (Infrared input)        |

#### 2x13 Header

On the opposite side, we'll find an unpopulated series of holes. To connect more easily Dupont cables, one could solder a 2 x 13-pin header, angled, pitch 2.54 like this [one](https://www.reichelt.de/2-x-13-pin-header-angled-pitch-2-54-sl-2x13w-2-54-p19491.html?&trstct=pol_10):


<figure>
  <img src="./assets/images/header.png" alt="h2" style="zoom:25%;display: block; margin: 0 auto"/>
  <figcaption>2 x 13-pin header, angled, pitch 2.54 by Reichelt.de</figcaption>
</figure>

| 2 × 13 Header |                |      |                |
| ------------- | -------------- | ---- | -------------- |
| 1             | *3,3 V*        | 2    | *5V*           |
| 3             | PB21 TWI2-SDA  | 4    | *5V*           |
| 5             | PB20 TWI2-SCK  | 6    | *GND*          |
| 7             | PI3 PWM1       | 8    | PH0 UART3_TX   |
| 9             | *GND*          | 10   | PH1 UART3_RX   |
| 11            | PI19 UART2_RX  | 12   | PH2            |
| 13            | PI18 UART2_TX  | 14   | *GND*          |
| 15            | PI17 UART2_CTS | 16   | PH20 CAN_TX    |
| 17            | *3,3 V*        | 18   | PH21 CAN_RX    |
| 19            | PI12 SPI0_MOSI | 20   | *GND*          |
| 21            | PI13 SPI0_MISO | 22   | PI16 UART2_RTS |
| 23            | PI11 SPI0_CLK  | 24   | PI10 SPI0_CS0  |
| 25            | *GND*          | 26   | PI14 SPI0_CS1  |

The numbers on the board are not the numbers that you will be able to use in your program.

<figure>
  <img src="./assets/images/Orange-Pi-26pin-pinout-PIN-definition.bmp" alt="orangepi zero pinout" style="zoom:50%;display: block; margin: 0 auto"/>
  <figcaption>OrangePi Zero Pinout by micro-pi.ru</figcaption>
</figure>

As seen [there](https://kaspars.net/blog/orange-pi-zero-gpio), there is a formula that will help you to get the GPIO number when you have the pin number:

```bash
(Position of letter in alphabet - 1) * 32 + Pin number
```

For example, port `PB12` would map to `GPIO 44`:

```bash
(2 - 1) * 32 + 12 = 44
```

<figure>
  <img src="./assets/images/orange-pi-zero-gpio-pins-800x746.png" alt="h2" style="zoom:50%;display: block; margin: 0 auto"/>
  <figcaption>OrangePi Zero Pinout by kaspars.net</figcaption>
</figure>

#### Serial console

A UART or serial console will be a life-saver when anything goes  wrong. The serial interface pins lies next to the Ethernet plug:


<figure>
  <img src="./assets/images/orangepi_zero-top.png" alt="orangepi zero pinout" style="zoom:80%;display: block; margin: 0 auto"/>
  <figcaption>OrangePi Zero top by OrangePi</figcaption>
</figure>

To connect to the board in case of problem, or if you don't have SSH installed, you need a TTL to USB converter like this [one](https://fr.aliexpress.com/item/32844850903.html?spm=a2g0w.12010615.8148356.2.302667c4KZJ6eL):

<figure>
  <img src="./assets/images/uart2usb_converter.png" alt="orangepi zero pinout" style="zoom:80%;display: block; margin: 0 auto"/>
  <figcaption>OrangePi USB2UART</figcaption>
</figure>

The RX an TX pins have to be connected to the TX and RX pins of the USB Serial converter respectively.

<figure>
  <img src="./assets/images/orangepiserialpin.png" alt="orangepi zero pinout" style="zoom:80%;display: block; margin: 0 auto"/>
  <figcaption>UART by Codelectron</figcaption>
</figure>

So TX goes to RX, RX goes to TX, GND goes to GND. We could also connect the converter to the pins 11 or 10 (RX, to connect to TX) and 13 or 8 (TX, to connect to RX).

Setting up the connection from another machine (Windows or Linux) will be detailed later in this document.



## Linux

### OrangePi's Debian

OrangePi [supplies](https://drive.google.com/open?id=1DAQEVauaeIq3p257zpm4-cHQY7AvxNR6) a Debian desktop version for the Zero LTS (supposedly the v1.5), the latest being from September 2019 (orangepi/orangepi).
OrangePi [supplies](https://mega.nz/#!ilt1RbrC!pS6C4km53HefFg_G-RWAN2ucJNb1b7T8REVQSa88Wf8) a Debian xfce desktop version for the Zero, the latest being from 2016-12-05 (root/orangepi).
OrangePi [supplies](https://mega.nz/#!fg911AIZ!QY0vxXeh-kzCuqI9zGWkRCKbuXdWiqhC3-f_SopR560) a Debian server version for the Zero, the latest being from 2016-12-01 (root/orangepi).

### OrangePi's Ubuntu

OrangePi [supplies](https://mega.nz/#!CtkTRSTZ!ekaVjnbuy7R6wpR9KDGZEaLa5vv437Guqlx3HDmYYDc) a Ubuntu server version for the Zero, the latest being from 2016-11-24. (orangepi/orangepi)
The Ubuntu Core they [supply](https://mega.nz/#F!MKQSUIbS!reCl8EK0QqjnOoC-e2ZwBg) is from 2018-02-05. (orangepi/orangepi)
The Lubuntu they [supply](https://mega.nz/#!KpN3wDaB!o5NW2tSrPMFDVYZfrySauhvkpLDBjZ4pkHQFnCUfvdY) is from 2016-11-25. (orangepi/orangepi)

### Armbian

Armbian [supplies](https://dl.armbian.com/orangepizero/Buster_current.torrent) Armbian Buster with mainline based kernel 5.3.y.
Armbian [supplies](https://dl.armbian.com/orangepizero/Bionic_current.torrent) Armbian Bionic with mainline based kernel 5.3.y.
They also supply other versions of Armbian, not all of them are supported: [Bionic server](https://dl.armbian.com/orangepizero/Bionic_current), [Buster server](https://dl.armbian.com/orangepizero/Buster_current), [Buster minimal](https://dl.armbian.com/orangepizero/Buster_dev_minimal_nightly), [Disco server](https://dl.armbian.com/orangepizero/Disco_current), [Stretch server](https://dl.armbian.com/orangepizero/Stretch_current).

### Others

OrangePi [supplies](https://mega.nz/#F!MKQSUIbS!reCl8EK0QqjnOoC-e2ZwBg) a Raspbian server version for the Zero, the latest being from  2018-02-05 (orangepi/orangepi).
OrangePi [supplies](https://mega.nz/#F!bpcngYxL!Dfqczf4BpDjtanPMbBv4Kg) an OpenWRT version for the Zero, the latest being from 2016-12-05 (root/orangepi).

## Android

### OrangePi Android

OrangePi [supplies](https://drive.google.com/open?id=1Vc2GZmQFq9O__V4pUwsW4Afh7zbfA7cL) an Android KitKat (4.4) version for the Zero LTS, the latest being from August 2019.
OrangePi [supplies](https://mega.nz/#F!X85DSK7S!RJGS50m78y3ZI3TTjy4YBQ) an Android version for the Zero, the latest being from 2018-3-15.
OrangePi [supplies](https://mega.nz/#F!X85DSK7S!RJGS50m78y3ZI3TTjy4YBQ) an Android 7.0 version for the Zero, the latest being from 2018-3-15.

### H3Droid

[H3Droid](https://h3droid.com/) is an Android built for Allwinner H3 and H2+ based devices. The universal installer can be downloaded [there](http://cdn.h3droid.com/h3droid/images/h3droid_installer.img.xz), or on this page: https://h3droid.com/download .

## Connecting the Zero to the outside world

### TVOUT

As seen [there](https://forum.armbian.com/topic/6582-orange-pi-zero-h2h3-tv-out-on-mainline-working/), if you want to get a correct image on the OrangePi Zero, as it is missing  filter circuity from its Composite Output, the most important thing one needs to do is put a 50 ohm resistor between the signal and GND. It is [RCA](https://en.wikipedia.org/wiki/RCA_connector) or "[composite](https://en.wikipedia.org/wiki/Composite_video)" signal: usually on a TV the yellow RCA connector is for composite signal, the white for left audio channel and  the red for right audio channel. Use an RCA connector and get TVOUT from pin 9, left audio from pin 8, right audio from pin 7 and GROUND from where you want.

Then use "TV" or "AV" or "Audio Video" on your TV. 
One could also add the cheap Zero [hat](https://fr.aliexpress.com/item/32770665186.html?spm=a2g0w.12010612.8148356.3.106c7fdd5HGbr9) to get audio/tvout and more USB ports.

<figure>
  <img src="./assets/images/hat top.png" alt="orangepi zero pinout" style="zoom:80%;display: block; margin: 0 auto"/>
  <figcaption>OrangePi Zero hat by OrangePi</figcaption>
</figure>

### Microphone

Once more, the cheapest and easiest way to connect a microphone to the OrangePi Zero is to use the OrangePi [hat](https://fr.aliexpress.com/item/32770665186.html?spm=a2g0w.12010612.8148356.3.106c7fdd5HGbr9).

The other way is to connect a circuit like this [one](http://www.orangepi.org/orangepibbsen/forum.php?mod=redirect&goto=findpost&ptid=2619&pid=18579&fromuid=1594746) to the three available pins:

<figure>
  <img src="./assets/images/mic.png" alt="orangepi zero pinout" style="zoom:80%;display: block; margin: 0 auto"/>
  <figcaption>Mic circuit by edu_viccini</figcaption>
</figure>

The MIC1N, MIC1P, MIC_MBIAS have to be connected to the respective pins of the 1x13 Header (12, 11, 10).

### Sound out

Connect the pins #7 and #8 to a Jack cable, and you're done. If you don't get any sound from it, create a .asoundrc file in your home folder, and put this code in it:

```bash
pcm.!default {
  type hw
  card audiocodec
}
ctl.!default {
  type hw
  card audiocodec
}
```

### InfraRed

## Temperature

### Passive cooling

The H2+ chip can run pretty hot, especially on some versions (the infamous 1.4) so a heat sink is not a bad idea. The chip measures 14mmx14mm so [any](https://fr.aliexpress.com/item/32555183226.html?spm=a2g0o.productlist.0.0.2f9c759041qn0w&algo_pvid=c9e3b3cb-787a-4a19-8bd0-23406e02f391&algo_expid=c9e3b3cb-787a-4a19-8bd0-23406e02f391-4&btsid=85e26822-67a9-4bb4-9c2f-8f24a48afc9f&ws_ab_test=searchweb0_0,searchweb201602_7,searchweb201603_53) heat sink of this size could help maintaining a correct temperature.

One can glue the heat sink to the H2+ chip using “heat sink plaster”. This is a thermally conductive substance that  hardens after some time. Another option is to use thermally  conductive double sided adhesive tape. 
If you're thinking of an enclosure to keep dust out of your board, think twice, or upgrade to active cooling.

### Active cooling

[fan](https://github.com/nopnop2002/OrangePi-ZERO-FAN-HAT)