# iCEstick Glitcher

The iCEstick Glitcher is a simple voltage glitcher for a Lattice iCEstick Evaluation Kit.

This glitcher is based on and inspired by glitcher implementations by
Dmitry Nedospasov (@nedos) from [Toothless Consulting](https://toothless.co/)
and Grazfather (@Grazfather).

This glitcher implementation demonstrates how the code read protection (CRP) of
NXP LPC-family microcontrollers can be bypassed as presented by Chris
Gerlinsky (@akacastor) in his talk [Breaking Code Read Protection on the NXP LPC-family Microcontrollers](Breaking Code Read Protection on the NXP LPC-family Microcontrollers)
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

## Test Setup

The following two images show a working test setup for the iCEstick Glitcher.

![iCEstick Glitcher test setup](/images/icestick_glitcher_test_setup.jpg)

![MAX4619 wiring using iCEstick Glitcher](/images/glitcher_max4619_wiring.jpg)

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
