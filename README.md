# ryzentosh-a320
Using OpenCore 0.6.6 (https://github.com/acidanthera/OpenCorePkg)

Fully working MacOS 10.15 Catalina on Ryzen PC

## Build

**Processor:** AMD Ryzen 5 3400G

**Motherboard:** Asus EX-A320M-GAMING

**Audio:** Realtek ALC 887

**Ethernet:** Realtek RTL8111

**Graphics:** Galax NVidia GeForce GT710 2GB GK208

**Wifi:** TP-Link Archer T6e

## Disclaimer
- iGPU Ryzen works but is crap.
- Audio really works but there's a little crackling and sound is not loud. There's a lot of audio layout you can try but alcid 18 works.

## Working
- Ethernet(Using Realtek RTL8111 Kext)
- Audio (Using audio fix https://github.com/astrihale/1plus1-audio-fix and VoodooHDA)
- Graphic Acceleration (native)
- Docker (boot2docker https://gist.github.com/slykar/e92732be9bf81a71e08068245656d70e)
- Kubernetes (minikube with virtualbox driver)
- Discord App (need this patch but i don't know why this works https://github.com/Pavo-IM/amd_hackintosh_discord_fix, launchctl setenv MKL_DEBUG_CPU_TYPE 5)
- Wifi (no kext required, 2/5Ghz)
- Graphical Boot (OpenCanopy Modern)

## Not Working
- Ryzen iGPU (recognized has a Graphic Card 7MB)
- MacOS BigSur
