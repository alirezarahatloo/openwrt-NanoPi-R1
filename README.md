# OpenWrt for NanoPi R1

This repository provides instructions for building an OpenWrt image for the NanoPi R1.

---

## Prerequisites

Before starting, ensure you have the following installed on your system:

- Ubuntu 20.04 or later (recommended)
- Required packages:
  ```bash
  sudo apt update
  sudo apt install build-essential libncurses5-dev libncursesw5-dev zlib1g-dev gawk git gettext libssl-dev xsltproc rsync wget unzip python3
  ```
## Build image
  ```bash
  git clone https://git.openwrt.org/openwrt/openwrt.git
  cd openwrt
  ./scripts/feeds update -a
  ./scripts/feeds install -a
  make menuconfig
  ```
![Alt text](images/menuconfig-nanopi-R1.png) 

  ```bash
  make 
  ```
## Writing the OpenWrt image to an SD card
  ```bash
  cd bin/targets/sunxi/cortexa7/
  gzip -d openwrt-sunxi-cortexa7-friendlyarm_nanopi-r1-ext4-sdcard.img.gz  
  sudo dd if=openwrt-sunxi-cortexa7-friendlyarm_nanopi-r1-ext4-sdcard.img of=/dev/sdc
  ```
## Adding Luci

- In the menuconfig interface:

    1.Navigate to **LuCI** → **Collections**.

    2.Select luci (this includes the basic Luci web interface).

    3.Optionally, select additional Luci modules (e.g., luci-ssl for HTTPS support).

    4.Save and exit the configuration.

## How to add a C program to the image

- add my_program folder to the **package** directory in the OpenWrt build system
  ```bash
    make package/my_program/compile -j1 v=s
  ```




