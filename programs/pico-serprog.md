# Building your own chip flasher with the Raspberry Pi Pico H

The Raspberry Pi Pico H is a $5 micro controller in the USA that can be turned
into an inexpensive chip flasher that can easily fit into your bag.

What do you need?

* Raspberry Pi Pico H
* MicroUSB cable
* A computer with GNU/Linux and flashrom
* 6x Dupont Female To Female To Female Jumper Wires
* SOIC8 or SOIC16 chip clip

For this, I am using the Raspberry Pi Pico H, but it may work for all of the
Raspberry Pi Pico boards.

I prices out all of these parts based on Cambridge, MA prices includes sales tax on 2026-02-05.

$5.31 [Raspberry Pico H](https://www.microcenter.com/product/650107/raspberry-pi-pico-h-raspberry-pi-pico-with-headers-pre-installed)
$6.45 [SOIC8 chip clip](https://www.ebay.com/itm/316562966853) (Can save buying in larger quantities.)
$8.88 [SOIC8 chip clip](https://www.ebay.com/itm/358148638213) (Can save buying in larger quantities.)
$5.31 [Dupont jumper cables](https://www.microcenter.com/product/613879/inland-dupont-jumper-wire-20cm-3-pack)
$6.37 [MicroUSB cable](https://www.microcenter.com/product/485276/inland-usb-20-(type-a)-to-micro-usb-(type-b)-male-cable-3-ft-black) (You probably have one of these already.)
I assume everyone already has a computer.

Total $32.32 USD

## Configuring your environment

I am using Triquel 11 which is a variation of Ubuntu 22.04, but these
instructions should work for most Debian-based distributions. My username is
`user` so change your home directory accordingly.

### Update your system

Update your system and make sure `git` is installed.

```
sudo apt update
sudo apt upgrade
sudo apt install -y git
```

### pico-sdk

Configure the pico-sdk. When using the pico-sdk, all of the submodules are not
necessary.


```
sudo apt install -y cmake python3 build-essential gcc-arm-none-eabi
sudo apt install -y libnewlib-arm-none-eabi libstdc++-arm-none-eabi-newlib
mkdir -p ~/pico
cd ~/pico
git clone https://github.com/raspberrypi/pico-sdk
cd pico-sdk/
git submodule update --init -- lib/tinyusb
```

Do note that some of the optional submodules that are not pulled in are nonfree
such as cyw43-driver.

### picotool

Compile the picotool.

```
cd ~/pico
sudo apt update
sudo apt install -y build-essential pkg-config libusb-1.0-0-dev cmake
git clone https://github.com/raspberrypi/picotool.git
cd picotool
mkdir build
cd build
cmake -DPICO_SDK_PATH=/home/user/pico/pico-sdk/ ..
make
sudo make install
sudo ln -s ~/pico/picotool/build/picotool /usr/local/bin/picotool
sudo cp ~/pico/picotool/udev/*-picotool.rules /etc/udev/rules.d
```

If that worked, you should be able to run `picotool version` without any notes
about USB support missing.

```
picotool version
```

## Configure pico-serprog

`pico-serprog` is a repository to configure the Raspberry Pi Pico as a chip
flasher. Riku_V's repository is at fork of a fork, and it seems to be the best
one as of December 2025.

```
cd ~/pico
git clone https://codeberg.org/Riku_V/pico-serprog
cd pico-serprog/
cmake -DPICO_SDK_PATH=/home/user/pico/pico-sdk/ .
make
```

If that worked, you should have a `pico_serprog.uf2` file.

```
ls pico_serprog.uf2
```

Plug in a Rapsberry Pi Pico and the system should mount it as a drive. If it was
 not mounted, unplug, hold the button, and plug it in again. In my case, it was
 mounted as the `/media/user/RPI-RP2/` directory.

```
cp pico_serprog.uf2 /media/user/RPI-RP2/
```

After placing the file in the directory, the Raspberry Pi Pico should unmount
automatically and become a chip flasher now.

Reading dmesg shows that the new device is `/dev/ttyACM0` for me, but your
number might be different.

```
sudo dmesg -wH
```

Install flashrom.

```
sudo apt install -y flashrom
```

Follow the instructions on https://codeberg.org/Riku_V/pico-serprog to flash
your first chip.

Free BIOS files can be found at the
[GNU Boot](https://www.gnu.org/software/gnuboot/) project.
