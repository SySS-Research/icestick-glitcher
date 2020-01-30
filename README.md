# iCEstick Glitcher

The iCEstick Glitcher is a simple voltage glitcher for a Lattice iCEstick Evaluation Kit.

This glitcher is based on and inspired by glitcher implementations by
Dmitry Nedospasov ([@nedos](https://twitter.com/nedos)) from [Toothless Consulting](https://toothless.co/)
and Grazfather ([@Grazfather](https://twitter.com/Grazfather)).

This glitcher implementation demonstrates how the code read protection (CRP) of
NXP LPC-family microcontrollers can be bypassed as presented by Chris
Gerlinsky (@akacastor) in his talk [Breaking Code Read Protection on the NXP LPC-family Microcontrollers](https://recon.cx/2017/brussels/resources/slides/RECON-BRX-2017-Breaking_CRP_on_NXP_LPC_Microcontrollers_slides.pdf)
at REcon Brussles 2017.

## Hardware Requirements

- [Lattice iCEstick Evaluation Kit](http://www.latticesemi.com/icestick)
- Analog switch, for instance [MAX4619](https://www.maximintegrated.com/en/products/analog/analog-switches-multiplexers/MAX4619.html)
- Power supply (2 externally supplied voltages required), for instance [Rigol DP832](https://www.rigolna.com/products/dc-power-loads/dp800/)

## Software Requirements

- [Python 3](https://www.python.org/)
- [pylibftdi](https://pypi.org/project/pylibftdi/)
- [sty](https://pypi.org/project/sty/)
- [yosys](https://github.com/YosysHQ/yosys)
- [nextpnr-ice40](https://github.com/YosysHQ/nextpnr)
- [Project IceStorm Tools](https://github.com/cliffordwolf/icestorm)

## Installation

The iCEstick Glitcher can be downloaded and built using the SymbiFlow toolchain in the following way:
```
git clone https://github.com/SySS-Research/icestick-glitcher.git
cd icestick-glitcher
make
make prog
 
virtualenv glitching
source glitching/bin/activate
pip install -r python/requirements.txt
```

## Test Setup

The following two images show a working test setup for the iCEstick Glitcher.

![iCEstick Glitcher test setup](/images/icestick_glitcher_test_setup.jpg)

![MAX4619 wiring using iCEstick Glitcher](/images/glitcher_max4619_wiring.jpg)


## Usage

The iCEstick Glitcher is used via the Python command tool **iCE iCE Baby Glitcher**.

```
$ python ice-glitcher.py --help
 
 ██▓ ▄████▄  ▓█████     ██▓ ▄████▄  ▓█████     ▄▄▄▄    ▄▄▄       ▄▄▄▄ ▓██   ██▓     ▄████  ██▓     ██▓▄▄▄█████▓ ▄████▄   ██░ ██ ▓█████  ██▀███ 
▓██▒▒██▀ ▀█  ▓█   ▀    ▓██▒▒██▀ ▀█  ▓█   ▀    ▓█████▄ ▒████▄    ▓█████▄▒██  ██▒    ██▒ ▀█▒▓██▒    ▓██▒▓  ██▒ ▓▒▒██▀ ▀█  ▓██░ ██▒▓█   ▀ ▓██ ▒ ██▒
▒██▒▒▓█    ▄ ▒███      ▒██▒▒▓█    ▄ ▒███      ▒██▒ ▄██▒██  ▀█▄  ▒██▒ ▄██▒██ ██░   ▒██░▄▄▄░▒██░    ▒██▒▒ ▓██░ ▒░▒▓█    ▄ ▒██▀▀██░▒███   ▓██ ░▄█ ▒
░██░▒▓▓▄ ▄██▒▒▓█  ▄    ░██░▒▓▓▄ ▄██▒▒▓█  ▄    ▒██░█▀  ░██▄▄▄▄██ ▒██░█▀  ░ ▐██▓░   ░▓█  ██▓▒██░    ░██░░ ▓██▓ ░ ▒▓▓▄ ▄██▒░▓█ ░██ ▒▓█  ▄ ▒██▀▀█▄ 
░██░▒ ▓███▀ ░░▒████▒   ░██░▒ ▓███▀ ░░▒████▒   ░▓█  ▀█▓ ▓█   ▓██▒░▓█  ▀█▓░ ██▒▓░   ░▒▓███▀▒░██████▒░██░  ▒██▒ ░ ▒ ▓███▀ ░░▓█▒░██▓░▒████▒░██▓ ▒██▒
░▓  ░ ░▒ ▒  ░░░ ▒░ ░   ░▓  ░ ░▒ ▒  ░░░ ▒░ ░   ░▒▓███▀▒ ▒▒   ▓▒█░░▒▓███▀▒ ██▒▒▒     ░▒   ▒ ░ ▒░▓  ░░▓    ▒ ░░   ░ ░▒ ▒  ░ ▒ ░░▒░▒░░ ▒░ ░░ ▒▓ ░▒▓░
 ▒ ░  ░  ▒    ░ ░  ░    ▒ ░  ░  ▒    ░ ░  ░   ▒░▒   ░   ▒   ▒▒ ░▒░▒   ░▓██ ░▒░      ░   ░ ░ ░ ▒  ░ ▒ ░    ░      ░  ▒    ▒ ░▒░ ░ ░ ░  ░  ░▒ ░ ▒░
 ▒ ░░           ░       ▒ ░░           ░       ░    ░   ░   ▒    ░    ░▒ ▒ ░░     ░ ░   ░   ░ ░    ▒ ░  ░      ░         ░  ░░ ░   ░     ░░   ░
 ░  ░ ░         ░  ░    ░  ░ ░         ░  ░    ░            ░  ░ ░     ░ ░              ░     ░  ░ ░           ░ ░       ░  ░  ░   ░  ░   ░    
    ░                      ░                        ░                 ░░ ░                                     ░                               
iCE iCE Baby Glitcher v0.5 by Matthias Deeg - SySS GmbH
A very simple voltage glitcher implementation for the Lattice iCEstick Evaluation Kit
Based on and inspired by voltage glitcher implementations by Dmitry Nedospasov (@nedos)
and Grazfather (@Grazfather)
---
usage: ./glitcher.py [-h] [--start_offset START_OFFSET] [--end_offset END_OFFSET] [--start_duration START_DURATION] [--end_duration END_DURATION] [--offset_step OFFSET_STEP] [--duration_step DURATION_STEP] [--retries RETRIES]
 
optional arguments:
  -h, --help            show this help message and exit
  --start_offset START_OFFSET
                        start offset for glitch (default is 100)
  --end_offset END_OFFSET
                        end offset for glitch (default is 10000)
  --start_duration START_DURATION
                        start duration for glitch (default is 1)
  --end_duration END_DURATION
                        end duration for glitch (default is 30)
  --offset_step OFFSET_STEP
                        offset step (default is 1)
  --duration_step DURATION_STEP
                        duration step (default is 1)
  --retries RETRIES     number of retries per configuration (default is 2)
```

The configuration of a voltage glitching attack can be changed via different command line arguments, for example:
```
python ice-glitcher.py --start_offset 5400 --end_offset 5430 --start_duration 10 --end_duration 25 --retries 3
```


## Demo

This demo video exemplarily shows how the code read protection (CRP) of an [NXP LPC1343 chip](https://www.nxp.com/docs/en/user-guide/UM10375.pdf) can be bypassed by using a voltage glitching attack in order to dump the flash memory containing the firmware.

[![SySS PoC Video: Voltage Glitching Attack using SySS iCEstick Glitcher](/images/icestick_glitcher_poc_video.jpg)](https://www.youtube.com/watch?v=FVUhVewFmxw "Voltage Glitching Attack using SySS iCEstick Glitcher")

## References

- [Lattice iCEstick Evaluation Kit](http://www.latticesemi.com/icestick)
- [Breaking Code Read Protection on the NXP LPC-family Microcontrollers](https://recon.cx/2017/brussels/resources/slides/RECON-BRX-2017-Breaking_CRP_on_NXP_LPC_Microcontrollers_slides.pdf)
- [Toothless Arty-Glitcher](https://github.com/toothlessco/arty-glitcher)
- [NXP LPC1343 Bootloader Bypass (Part 1) - Communicating with the bootloader](https://toothless.co/blog/bootloader-bypass-part1/)
- [NXP LPC1343 Bootloader Bypass (Part 2) - Dumping firmware with Python and building the logic for the glitcher](https://toothless.co/blog/bootloader-bypass-part2/)
- [NXP LPC1343 Bootloader Bypass (Part 3) - Putting it all together](https://toothless.co/blog/bootloader-bypass-part3/)
- [Grazfather's glitcher for the iCEBreaker FPGA board](https://github.com/Grazfather/glitcher)
- [Glitching the Olimex LPC-P1343](http://grazfather.github.io/re/pwn/electronics/fpga/2019/12/08/Glitcher.html)

## Disclaimer

Use at your own risk. Do not use without full consent of everyone involved.
For educational purposes only.
