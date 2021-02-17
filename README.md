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


## Docker and K8s

Docker app don't recognize Ryzen as a Valid CPU and it a fact because there`s no official AMD Support on mac. To resolve this use docker-machine and run docker inside a VM. Works Great.

Install Docker App for mac

Copy docker-credential-desktop and docker to /usr/local/bin

```
ln -sf /Applications/Docker.app/Contents//Resources/bin/docker-credential-desktop /usr/local/bin/
ln -sf /Applications/Docker.app/Contents//Resources/bin/docker /usr/local/bin/
```

Install docker-compose
```
curl -L --fail https://github.com/docker/compose/releases/download/1.28.2/run.sh -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
docker-compose
```

Install docker-machine
```
curl -L https://github.com/docker/machine/releases/download/v0.5.5/docker-machine_darwin-amd64 >/usr/local/bin/docker-machine && \
    chmod +x /usr/local/bin/docker-machine
```
Install Virtualbox 

Start docker-machine
```
docker-machine create --driver virtualbox default
```

For k8s install minikube using brew
```
brew install minikube
minikube config set driver virtualbox
minikube start --driver=virtualbox
```
