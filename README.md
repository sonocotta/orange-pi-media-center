# Orange Pi Media Center

![Open Source Hardware](/doc/images/open-source-hardware-logo.png)
![Open Source Software](/doc/images/open-source-software-logo.png)
<a href="https://www.tindie.com/stores/sonocotta/?ref=offsite_badges&utm_source=sellers_andrey-malyshenko&utm_medium=badges&utm_campaign=badge_medium"><img src="https://d2ss6ovg47m0r5.cloudfront.net/badges/tindie-mediums.png" alt="I sell on Tindie" width="150" height="78"></a>
<br />
[![Dev Chat](https://img.shields.io/discord/1233306441469657140?logo=discord&label=discord&style=flat-square)](https://discord.gg/PtnaAaQMpS)
![DSC_0029](https://github.com/sonocotta/orange-pi-media-center/assets/5459747/eaf22234-3698-4ffb-8bf8-64190738be24)

Orange Pi Media Center is a series of Orange Pi One-based media center devices. They share a similar look, and compared to my earlier designs, they have a great-looking aluminum case.

## Table of Contents

- [Orange Pi Media Center](#orange-pi-media-center)
	- [Motivation](#motivation)
	- [Early prototypes](#early-prototypes)
	- [HiFi Orange Pi Media Center](#hifi-orange-pi-media-center)
	- [Loud Orange Pi Media Center](#loud-orange-pi-media-center)
		- [Power considerations](#power-considerations)
	- [Louder Orange Pi Media Center](#louder-orange-pi-media-center)
	- [Features](#features)
	- [Board Pinout](#board-pinout)
		- [Audio](#audio)
		- [Peripheral (built-in)](#peripheral-built-in)
		- [Peripheral (optional TFT screen)](#peripheral-optional-tft-screen)
		- [Peripheral (optional rotary encoder)](#peripheral-optional-rotary-encoder)
		- [Peripheral (Louder)](#peripheral-louder)
	- [Software](#software)
		- [DAC Configuration - HiFi Orange Pi Media Center](#dac-configuration---hifi-orange-pi-media-center)
		- [DAC Configuration - Loud Orange Pi Media Center](#dac-configuration---loud-orange-pi-media-center)
		- [Automated deployment using Ansible](#automated-deployment-using-ansible)
		- [Manual installation steps](#manual-installation-steps)
	- [Hardware](#hardware)
		- [HiFi Orange Pi Media Center](#hifi-orange-pi-media-center-1)
		- [Loud Orange Pi Media Center](#loud-orange-pi-media-center-1)
		- [Earlier designs](#earlier-designs)
	- [Demo](#demo)
	- [Where to buy](#where-to-buy)
		- [Current designs](#current-designs)
		- [Legacy designs](#legacy-designs)
 
  
## Motivation

I did a few audio projects in the past, some using [ESP32](https://hackaday.io/project/173620-loud-esp), some using popular [Raspberry Pi](https://hackaday.io/project/195272-raspberry-pi-media-center) devices. Each has its pros and cons, and with each iteration, I'm trying to focus on the details that were working best for me, while using them myself on a daily basis. 

What is special about the Orange Pi is the amount of hardware power that you get for your buck. Surely, the ecosystem is not as rich as Raspberry Pi, and the community is not so vast. But Armbian is still a Debian-based system and most of the things you'd want to run, just work!

## Early prototypes

The Media center didn't appear from the thin air. A series of Hat prototypes were created before. 

Orange Pi Hi-Fi Hat adds Hi-Fi audio capability to your Pi. It uses the native I2S output of Orange Pi together with Texas Instruments' fantastic PCM5100 Hi-Fi DAC.

![image](https://user-images.githubusercontent.com/5459747/209653155-5d475646-525a-4f9a-a561-1d854e3b34ee.png)

Loud Orange Pi Hat uses dual MAX98357 DAC to spit out two channels of 3W music power each

![DSC_0433](https://github.com/sonocotta/orange-pi-hi-fi-hat/assets/5459747/28e6fa61-931e-42fc-841b-1774a86752a5)

Finally, the early design of the Orange Pi Media Center was based on the Loud Orange Pi Hat design, but turn out too expensive to build.

![DSC_0509](https://github.com/sonocotta/orange-pi-hi-fi-hat/assets/5459747/5b477e8e-8844-40bd-acaa-fbc27555e032)

## HiFi Orange Pi Media Center

Orange Pi HiFi is a first-in-line product that uses the legendary PCM5100 series DAC with supreme audio quality. It exposes line-level output that you can plug into a stereo amplifier. Spend as much as you need on the external amp to deliver the sound you like (personally I prefer late 80's audio gear).

![DSC_0005](https://github.com/sonocotta/orange-pi-media-center/assets/5459747/b85e2cca-3003-4278-bbe3-fd8affea67b8)

It is a simple yet powerful solution that adds audio capabilities to your Orange Pi-based project. Audio quality complies with Hi-Fi standards, which means it is suitable for high-quality audio streaming, just like Big Pi

## Loud Orange Pi Media Center 

Loud Orange Pi uses a dual MAX98357 HiFi DAC with a built-in highly efficient D-class amp to deliver 3 to 5W of music power directly to your speakers.

![DSC_0008](https://github.com/sonocotta/orange-pi-media-center/assets/5459747/db5014e1-c861-421e-a34c-26a6a3c0e241)

It's capable reasonably priced, and great value for money. In terms of audio quality, there is no compromise, and that is what matters most

### Power considerations

According to the manufacturer Orange Pi One requires at least 2 Amps of 5V line, and each DAC needs at least 1 Amp extra. With the total budget requirement of 5 Amps, it is not reasonable to count on a USB-C 5V power line alone. I've decided to use a USB-PD over a type-C cable. Pretty much any 9V/12V/20V PD-enabled power adapter will work, most typically phone chargers with a quick charge option. The smallest of the family is 25W models, which is plenty enough for both Orange Pi and DACs.

Tested and perfectly working models are (others may be available)

| Model   | Image   |
|-------------------------------|---------------------------------|
| [65W USB-C Lenovo ThinkPad Laptop Charger Replacement Power Adapter](https://www.aliexpress.com/item/1005005994445557.html)  | ![image](https://github.com/sonocotta/orange-pi-media-center/assets/5459747/27614db3-de35-4054-8450-9845a09f6381)
| [65W 45W 20V 3.25A Type-C PD Laptop Charger](https://www.aliexpress.com/item/1005006086701848.html) | ![image](https://github.com/sonocotta/orange-pi-media-center/assets/5459747/266a9bed-dde5-4869-aa31-84176b0a6608)
| [120W Gan Type-C PD Charger](https://www.aliexpress.com/item/1005006806666186.html) | ![image](https://github.com/sonocotta/orange-pi-media-center/assets/5459747/f42d4c8c-879b-494c-ac18-dd18ace322e7)
| [45W Type-C PD Mobile Phone Wall Adapter](https://www.aliexpress.com/item/1005006713008533.html) | ![image](https://github.com/sonocotta/orange-pi-media-center/assets/5459747/110bb6f9-7014-4dfc-8fd8-3bc99b269e9c)

## Louder Orange Pi Media Center

(Work-In-Progress, spoiler alert)

Louder Orange Pi is a top-of-the-range model that uses a modern highly capable TAS5805M DAC and is aimed to be paired with medium-to-large speaker systems. With 25W per channel stereo output, it packs a punch and can easily enliven living quarters or dorm rooms. It is highly efficient, but much more demanding for power when cranked, therefore it uses USB-C Power Delivery to pull up to 65W from the wall power adapter. 

(no picture yet)


## Features

|                               | HiFi Orange Pi Media Center                                   | Loud Orange Pi Media Center                         | Louder Orange Pi Media Center               |
|-------------------------------|---------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------|
| Image                         |  ![DSC_0005](https://github.com/sonocotta/orange-pi-media-center/assets/5459747/b85e2cca-3003-4278-bbe3-fd8affea67b8)     | ![DSC_0008](https://github.com/sonocotta/orange-pi-media-center/assets/5459747/db5014e1-c861-421e-a34c-26a6a3c0e241) | WIP  |
| DAC                           | [PCM5100A](https://www.ti.com/product/PCM5100A) 32bit Stereo DAC                                                    | Dual I2S DAC [MAX98357](https://www.analog.com/en/products/max98357a.html) with built in D-Class amp | Stereo I2S DAC [TAS5805M](https://www.ti.com/product/TAS5805M) with built in D-Class amp |
| Output                        | 2.1 VRMS Line level output <br/> -100 dB typical noise level                                                        | 2x 3W (8Ω);   2x 5W (4Ω)                                 | 2x 22W (8Ω, 1% THD+N); 2x 32W (4Ω, 1% THD+N)                                                                   |
| IR reader                     | yes                                                                                                                 | yes                                                                                                  | yes                                                                                      |
| RGB LED                       | yes                                                                                                                 | yes                                                                                                  | yes                                                                                      |
| External relay driver         | yes                                                                                                                 | no                                                                                                   | yes                                                                                       |
| Ethernet                      | built-in                                              | built-in                               | built-in                   |
| Powers from                   | 5V USB-C power adapter <br/>Triple [LP5907](https://www.ti.com/lit/ds/symlink/lp5907.pdf) 3.3 V Ultra-Low-Noise LDO | 25W+ USB-C PD power adapter                                                                       | 65W USB-C PD power adapter (25W/45W with limited power)                                                                |
| Mechanical dimensions (WxHxD) | 88mm x 38mm x 100mm                                                                                                 | 88mm x 38mm x 100mm                                                                                  | 88mm x 38mm x 100mm                                                                      |

## Board Pinout

### Audio

|       | I2S CLK | I2S DATA | I2S WS |  CE (MAX98357 only)
|-------|---------|----------|--------|--------|
| Orange Pi One | PA19      | PA20       | PA18     | PA8 

### Peripheral (built-in)

|       | WS2812 RGB LED |  RELAY EN | IR INPUT |
|-------|----------|--------|----------|
| Orange Pi One |  PA7      |  PA2    |   PA9      |  

### Peripheral (optional TFT screen)

|       | SPI CLK  |SPI MOSI| SPI MISO | TFT CS   | TFT DC   | TFT RES  |  TFT LED |   
|-------|----------|--------|----------|-----------|-----------|-----------|---------|
| Orange Pi One |  PC2     |  PC0    |  PC1      |   PC3      | PA0         | PA1        |    PA3 |  

### Peripheral (optional rotary encoder)

|       |  A  |    B | BTN  |   
|-------|----------|--------|----------|
| Orange Pi One |  PC7     |  PC4    |  PA6      | 

### Peripheral (Louder)

TBD

## Software

Being a Debian-based Orange Pi Media Center is a vast space for experimentation. First things first, for any OS you need to configure DAC. Below instruction is based on [Armbian](https://www.armbian.com/) experience, that supports the current kernel (thus already having DAC kernel modules).

### DAC Configuration - HiFi Orange Pi Media Center

Create a `i2s-sound.dts` file somewhere in the filesystem with the following contents

```
/dts-v1/;
/plugin/;

/ {
	compatible = "allwinner,sun8i-h2-plus";

 	fragment@0 { 
 		target-path = "/"; 
 		__overlay__ { 
			pcm5102a: pcm5102a {
			#sound-dai-cells = <0>;
			compatible = "ti,pcm5102a";
			pcm510x,format = "i2s";
			};
 		}; 
 	}; 

	fragment@1 {
		target = <&i2s0>;
		__overlay__ {
			status = "okay";
			pinctrl-0 = <&i2s0_pins>;
			sound-dai = <&pcm5102a>;
			pinctrl-names = "default";
		};
	};

	fragment@2 {
		target-path = "/";
		__overlay__ {
			sound_i2s {
				compatible = "simple-audio-card";
				simple-audio-card,name = "hifi-orange-pi";
				simple-audio-card,mclk-fs = <256>;
				simple-audio-card,format = "i2s";
		                status = "okay";

				simple-audio-card,cpu {
					sound-dai = <&i2s0>;
				};

				simple-audio-card,codec {
					sound-dai = <&pcm5102a>;
				};
			};
		};
	};
};
```

### DAC Configuration - Loud Orange Pi Media Center

```
/dts-v1/;
/plugin/;

/ {
	compatible = "allwinner,sun8i-h2-plus";

 	fragment@0 { 
 		target-path = "/"; 
 		__overlay__ { 
			max98357a: max98357a {
			#sound-dai-cells = <0>;
			compatible = "maxim,max98357a";
			sdmode-gpios = <&pio 0 8 0>; /* PA8, active high */
			status = "okay";
			};
 		}; 
 	};

	fragment@1 {
		target = <&i2s0>;
		__overlay__ {
			status = "okay";
			pinctrl-0 = <&i2s0_pins>;
			sound-dai = <&max98357a>;
			pinctrl-names = "default";
		};
	};

	fragment@2 {
		target-path = "/";
		__overlay__ {
			sound_i2s {
				compatible = "simple-audio-card";
				simple-audio-card,name = "loud-orange-pi";
				simple-audio-card,mclk-fs = <256>;
				simple-audio-card,format = "i2s";
		                status = "okay";

				simple-audio-card,cpu {
					sound-dai = <&i2s0>;
				};

				simple-audio-card,codec {
					sound-dai = <&max98357a>;
				};
			};
		};
	};
};

```

Next, run the following command 

```bash
sudo armbian-add-overlay i2s-sound.dts
```

This will compile the device tree overlay, copy it to the `/boot/user-overlays` folder and add a line to the `/boot/armbianEnv.txt` with `user_overlays=i2s-sound`. After reboot you will see a new audio card available

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: hifiorangepi [hifi-orange-pi], device 0: 1c22000.i2s-pcm5102a-hifi pcm5102a-hifi-0 [1c22000.i2s-pcm5102a-hifi pcm5102a-hifi-0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: sun9ihdmi [sun9i-hdmi], device 0: SUN9I-HDMI PCM i2s-hifi-0 [SUN9I-HDMI PCM i2s-hifi-0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

You can test the audio with the following command

```bash
$ speaker-test -t wav -c 2
```

### Automated deployment using Ansible

[Ansible](https://www.ansible.com/) is an automation suite that allows you to configure systems remotely using redistributable configurations called playbooks.

A few playbooks were created to allow 2-clicks deployment for Orange Pi Hi-Fi Hat. Those are based on Armbian Ubuntu Focal images, can be download here: [Orange Pi PC](https://imola.armbian.com/archive/orangepipc/archive/Armbian_21.02.1_Orangepipc_focal_current_5.10.12.img.xz) and [Orange Pi One](https://fi.mirror.armbian.de/archive/orangepione/archive/Armbian_21.02.1_Orangepione_focal_current_5.10.12.img.xz)

The below steps are run on your laptop or PC, all configurations will be delivered remotely via ssh

- Write the downloaded Armbian image onto an SD card of your choice. Start your Orange Pi and find its IP address. The next steps will assume that the IP address of each node stays the same after reboot. You might need to configure your router to lease static IP to Orange Pi to make it stable.
- Open [firmware](/firmware) folder in vscode. In case you don't want to install vscode, you can run commands in plain terminal as well. Please use [tasks.json](/firmware/.vscode/tasks.json) file for reference
- Prepare [hosts](/firmware/hosts) file. Add your node's IP address and name
- Run `0. install prerequisites` task. It will install necessary tools on your laptop/PC, like Ansible client and such
- Run `1. apply with root password` task. It will ask for the root password, which is `1234` by default on Armbian. This task will install and update packages, as well as create a new user and configure ssh on your Pi
- (Obsolete, see above) Open [2-audio-hardware.yml](/firmware/playbooks/2-audio-hardware.yml) file and run `2. apply ${file} without password` task. It will build and configure the kernel module for PCM510X DAC as well as configure Device Tree overlay to inform Linux about the new DAC is has
- (Optional) Do the same with [3-pulseaudio.yml](firmware/playbooks/3-pulseaudio.yml), [4-mopidy.yml](firmware/playbooks/4-mopidy.yml), [5-libre-spotify.yml](firmware/playbooks/5-libre-spotify.yml) playbooks. That will install [Pulseaudio](https://www.freedesktop.org/wiki/Software/PulseAudio/) network node, [Mopidy](https://mopidy.com/) and [Libre-Spotify](https://github.com/dtcooper/raspotify) smart speaker software accordingly

### Manual installation steps

All of the above can be done manually, basically following [instructions](https://hackaday.io/project/162373/instructions) created before for another Orange Pi board with the same DAC. 

## Hardware

Please visit the [hardware](/hardware/) section for board schematics and PCB designs. Note that PCBs are shared as multi-layer PDFs as well as Gerber archives.

### HiFi Orange Pi Media Center

| Front | Back | PCB |
|---|---|---|
| ![DSC_0002_small JPG-mh](https://github.com/sonocotta/orange-pi-media-center/assets/5459747/9a5ebd9c-379e-481e-a9cf-932aa880da58) | ![DSC_0005_small JPG-mh](https://github.com/sonocotta/orange-pi-media-center/assets/5459747/68d6b6d8-cc70-4592-a3ae-fbd6974bcbbb) | ![DSC_0023_small JPG-mh](https://github.com/sonocotta/orange-pi-media-center/assets/5459747/837f02d7-7a3f-4a7f-890a-b3fe79d24d12)


### Loud Orange Pi Media Center

| Front | Back | PCB |
|---|---|---|
| ![DSC_0002_small JPG-mh](https://github.com/sonocotta/orange-pi-media-center/assets/5459747/85fdc9c3-852d-4012-bbf2-506308a8949f) |  ![DSC_0008_small JPG-mh](https://github.com/sonocotta/orange-pi-media-center/assets/5459747/68717b4a-322b-4d06-b58f-aef7d605d6f5) | ![DSC_0020_small JPG-mh](https://github.com/sonocotta/orange-pi-media-center/assets/5459747/076abbca-94ea-41d3-9600-b478c4cb1fda)


### Earlier designs 

| Legend | Photo 1 | Photo 2 |
|-----------|-----------|-----------|
| Orange Pi One | ![image](https://user-images.githubusercontent.com/5459747/209653238-e1d93dc3-8c1f-4b69-94c1-c0ca967b8e86.png) | ![image](https://user-images.githubusercontent.com/5459747/209653254-e99c16c2-5480-4c46-8801-a08646382ccb.png)
| Orange Pi PC | ![image](https://user-images.githubusercontent.com/5459747/209653361-29e2cff6-6f71-405b-bc1e-7d4f22a72046.png) | ![image](https://user-images.githubusercontent.com/5459747/209653386-3736780d-dade-45c7-b182-718f26f47ff5.png)
| Loud Orange Pi with optional TFT screen | ![DSC_0433](https://github.com/sonocotta/orange-pi-hi-fi-hat/assets/5459747/28e6fa61-931e-42fc-841b-1774a86752a5) | ![DSC_0437](https://github.com/sonocotta/orange-pi-hi-fi-hat/assets/5459747/f3cc4fb3-8fc6-4810-a096-cbe7c65547d0)
| Orange Pi Media Center | ![DSC_0509](https://github.com/sonocotta/orange-pi-hi-fi-hat/assets/5459747/5b477e8e-8844-40bd-acaa-fbc27555e032) ![DSC_0506](https://github.com/sonocotta/orange-pi-hi-fi-hat/assets/5459747/dcd36078-74b0-4744-bd0e-191f12fd5c39) | ![DSC_0504](https://github.com/sonocotta/orange-pi-hi-fi-hat/assets/5459747/f6d266f6-c94b-4148-8f30-3e29ab946653)

## Demo

[![Loud Orange Pi Media Center audio test](http://img.youtube.com/vi/NVYHHE_ENYY/0.jpg)](http://www.youtube.com/watch?v=NVYHHE_ENYY "Loud Orange Pi Media Center audio test")

## Where to buy

### Current designs

- [HiFi Orange Pi Media Center](https://www.tindie.com/products/sonocotta/hifi-orange-pi-media-center/)
- Loud Orange Pi Media Center (coming soon)
 
### Legacy designs

- [Orange Pi Hi-Fi hat](https://www.tindie.com/products/sonocotta/orange-pi-hi-fi-hat/)
- [Loud Orange Pi](https://www.tindie.com/products/sonocotta/loud-orange-pi-hat/)
- [Orange Pi Media Center](https://www.tindie.com/products/sonocotta/orange-pi-media-center/)
