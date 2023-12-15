# Orange Pi Hi-Fi Hat

![Open Source Hardware](/doc/images/open-source-hardware-logo.png)
![Open Source Software](/doc/images/open-source-software-logo.png)

Orange Pi Hi-Fi Hat adds Hi-Fi audio capability to your Pi. It uses native I2S output of Orange Pi together with Texas Instruments' fantastic PCM5100 Hi-Fi DAC.

![image](https://user-images.githubusercontent.com/5459747/209653155-5d475646-525a-4f9a-a561-1d854e3b34ee.png)

## Why did I build it

I want to bring modern hobbyist technologies to the world of classic speakers and amps gear. I build systems that keep that old-school ish look, but add online streaming and smart remote capabilities. I build this project as a possible core of such solution, where small but much capable box with Orange Pi in it drives large Pro-sized and Pro-sounded audio

## Why Hi-Fi Hat?

It is a simple yet powerful solution that adds audio capabilities to your Orange Pi based project. Audio quality complies with Hi-Fi standards, which means it is suitable for high quality audio streaming, just like Big Pi

## Why Orange Pi?

It's capable and reasonably priced, and great value for money. But most notably, Raspberry's availability is nil at the moment of writing. Orange Pi is not a perfect alternative, not nearly as good support level as Big Pi. But in terms of audio quality it is no compromise, and that what matters most

## Key features

- PCM5100A 32bit DAC
- Up to 384 kHz sampling rate
- -100 dB typical noise level
- Triple ultra-low-noise voltage regulator for audio interface 
- Single mini-jack output
- Dual RCA output


## How to use

Orange Pi runs [Armbian](https://www.armbian.com/), [Volumio](https://volumio.com/en/) and [Mopidy](https://mopidy.com/), but before any of then can utilize Hi-Fi DAC, it needs to be configured.

Setting up an external DAC is not a trivial task, therefore some examples were provided in [firmware](/firmware) section.

### Automated deployment using Ansible

[Ansible](https://www.ansible.com/) is an automation suite that allows you to configure systems remotely using redistributable configurations called playbooks.

Few playbooks were created to allow 2-clicks deployment for Orange Pi Hi-Fi Hat. Those are based on Armbian Ubuntu Focal images, can be download here: [Orange Pi PC](https://imola.armbian.com/archive/orangepipc/archive/Armbian_21.02.1_Orangepipc_focal_current_5.10.12.img.xz) and [Orange Pi One](https://fi.mirror.armbian.de/archive/orangepione/archive/Armbian_21.02.1_Orangepione_focal_current_5.10.12.img.xz)

Below steps are run on your laptop or PC, all configurations will be delivered remotely via ssh

- Write downloaded Armbian image onto a cd-card of your choice. Start your Orange Pi and find its IP address. Next steps will assume that the IP address of each node stays the same after reboot. You might need to configure your router to lease static IP to Orange Pi to make it stable.
- Open [firmware](/firmware) folder in vscode. In case you don't want to install vscode, you can run commands in plain terminal as well. Please use [tasks.json](/firmware/.vscode/tasks.json) file for reference
- Prepare [hosts](/firmware/hosts) file. Add your node's IP address and name
- Run `0. install prerequisites` task. It will install necessary tools on your laptop/PC, like Ansible client and such
- Run `1. apply with root password` task. It will ask for the root password, which is `1234` by default on Armbian. This task will install and update packages, as well as create new user and configure ssh on your Pi
- Open [2-audio-hardware.yml](/firmware/playbooks/2-audio-hardware.yml) file and run `2. apply ${file} without password` task. It will build and configure kernel module for PCM510X DAC as well as configure Device Tree overlay to inform Linux about new DAC is has
- (Optional) Do the same with [3-pulseaudio.yml](firmware/playbooks/3-pulseaudio.yml), [4-mopidy.yml](firmware/playbooks/4-mopidy.yml), [5-libre-spotify.yml](firmware/playbooks/5-libre-spotify.yml) playbooks. That will install [Pulseaudio](https://www.freedesktop.org/wiki/Software/PulseAudio/) network node, [Mopidy](https://mopidy.com/) and [Libre-Spotify](https://github.com/dtcooper/raspotify) smart speaker software accordingly


### Manual installation steps

All above can be done manually, basically following [instructions](https://hackaday.io/project/162373/instructions) created before for another Orange Pi board with the same DAC. 

## Hardware

Design files can be found in [hardware](/hardware) section.

## Look

| Legend | Photo |
|-----------|-----------|
| Orange Pi One | ![image](https://user-images.githubusercontent.com/5459747/209653238-e1d93dc3-8c1f-4b69-94c1-c0ca967b8e86.png) ![image](https://user-images.githubusercontent.com/5459747/209653254-e99c16c2-5480-4c46-8801-a08646382ccb.png)
| Orange Pi PC | ![image](https://user-images.githubusercontent.com/5459747/209653361-29e2cff6-6f71-405b-bc1e-7d4f22a72046.png) ![image](https://user-images.githubusercontent.com/5459747/209653386-3736780d-dade-45c7-b182-718f26f47ff5.png)
| Loud Orange Pi with optional TFT screen | ![DSC_0433](https://github.com/sonocotta/orange-pi-hi-fi-hat/assets/5459747/28e6fa61-931e-42fc-841b-1774a86752a5) ![DSC_0437](https://github.com/sonocotta/orange-pi-hi-fi-hat/assets/5459747/f3cc4fb3-8fc6-4810-a096-cbe7c65547d0)
| Orange Pi Media Center | ![DSC_0509](https://github.com/sonocotta/orange-pi-hi-fi-hat/assets/5459747/5b477e8e-8844-40bd-acaa-fbc27555e032) ![DSC_0506](https://github.com/sonocotta/orange-pi-hi-fi-hat/assets/5459747/dcd36078-74b0-4744-bd0e-191f12fd5c39) ![DSC_0504](https://github.com/sonocotta/orange-pi-hi-fi-hat/assets/5459747/f6d266f6-c94b-4148-8f30-3e29ab946653)

## Where to buy

Available at Tindie
- [Orange Pi Hi-Fi hat](https://www.tindie.com/products/sonocotta/orange-pi-hi-fi-hat/)
- [Loud Orange Pi](https://www.tindie.com/products/sonocotta/loud-orange-pi-hat/)
- [Orange Pi Media Center](https://www.tindie.com/products/sonocotta/orange-pi-media-center/)



