# Slightly customized OpenWrt fork based on official OpenWrt 21.02 release

Customizations and patches applied to original OpenWrt 21.02 source code:

## Xunlong Orange Pi Zero changes

* Enabled 2 external USB ports (using pins 1-6 at 13-pin expansion connector).
See [this](https://github.com/openwrt/openwrt/pull/1702) pull request for more info.
* Added support for WiFi (XR819), using driver sources from [this](https://github.com/fifteenhex/xradio) repo. Build patches and kernel-module makefile based on sources from [this](https://github.com/melsem/openwrt) repo.
* SWIOTLB reserved memory size reduced to 8M: default 64M is way too much for device with 256M ram (TODO: maybe, disable PAE completely at kernel config so SWIOTLB will not be used at all)

### _WiFi NOTES:_

_WiFi was tested with board v1.5 (according to missing R66 and R69 resistors - it is a LTS model), I don’t know whether it will work with old board revisions or not._
_Setting TX-power does not seem to work. "N" mode setting is not supported, "Legacy" mode gives maximum speed of 54 mbps._
_Real speeds will be much worse because of this cheap XR819 WiFi module._
_Do not rely on it if you want to build some sort of WiFi router on top of OPI Zero (instead, you should buy some known good external USB WiFi module)._

## x86/x86_64 changes

* Enable virtio drivers for running with libvirt/QEMU/KVM

## Procd changes

* Changes to "tmpfs on zram" feature - altered options for mkfs.ext4, added some mount options in order to improve performance a bit

## Other kernel patches and config changes

* Some minor changes. TODO: verbose description.
