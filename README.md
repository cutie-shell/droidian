Droidian
========

<p float="left">
<img src="https://github.com/cutie-shell/cutie-shell-qt5/raw/bookworm/cutie.png" width="100px">
<img src="https://avatars.githubusercontent.com/u/69109445?s=200&v=4" width="100px">
</p>

Droidian is a GNU/Linux distribution based on top of Mobian, a Debian-based distribution for mobile devices. The goal of Droidian is to be able to run Mobian on Android phones.

This repository is for Droidian builds containing a development snapshot of Cutie Shell.

# Which image to get?

The recovery flashable zipfile needs to be flashed via a suitable Android recovery (such as TWRP). Recovery flashable zipfiles are generic, and are useful to test drive Droidian or in early device porting stages.  
You should pick up the correct zipfile for your specific device:

* Device with an Android 9 vendor: api28
* Device with an Android 10 vendor: api29
* Device with an Android 11 vendor: api30

## Recovery-flashable zipfile: bundles

Recovery flashable zipfiles support the addition of *bundles*, which allow to add functionality directly during the flashing process.

Currently available bundles:

* Devtools: Useful development tools for porters, not available in nightlies as they're embedded in the rootfs
* Adaptation bundle: Device specific bundle (containing kernel, device-specific settings, etc)

# Recovery-flashable zipfile: installation instructions

## Preparations

If your device is A/B device, it is necessary to have both slots on same Android version.

Then, boot your favourite Android recovery.

## Installation

From recovery open adb sideload mode (under advanced on TWRP) and run following commands on your computer replacing `ARCH_YYYYMMDD` with the version of Droidian and `vendor-device` with the vendor and device codenames:

* `adb sideload droidian-OFFICIAL-cutie-phone-rootfs-apiXX-ARCH-VERSION_DATE.zip`

If you want to sideload devtools:

* `adb sideload droidian-devtools-ARCH_YYYYMMDD.zip`

If you want to sideload an adaptation bundle:

* `adb sideload droidian-adapatation-vendor-device-ARCH_YYYYMMDD.zip`

Note that you have to restart the sideload mode by tapping back and starting sideload again before every `adb sideload command`.

## Finalizing installation

Now, you have to reboot the device. It should boot to Cutie after rebooting once more automatically.

## Troubleshooting

If the image does not boot and your userdata is not an ext4 partition, you might try formatting it. **Note that this is a destructive operation, you cannot recover files from userdata afterwards!**

* `fastboot format:ext4 userdata`
