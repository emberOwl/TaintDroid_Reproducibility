# TaintDroid Reproducibility

## Description

By using TaintDroid with a different project setup, we verify its reproducibility and check Google Keyboard for potential privacy violations. TaintDroid Notify 4.1.1 application analysis is unreproducible on the Nexus 4 with Android 4.3 due to a linker issue that Google claimed has been fixed, which is caused by TaintDroid’s implementation of taint propagation. 

For future projects with TaintDroid, we recommend following their exact setup. The experiment was tested multiple times on Android 2.1 on multiple Nexus One devices. We also recommend using the [ROMs provided by other members of the Google Group](https://groups.google.com/d/msg/taintdroid/uUaScRPVgb4/NqgUuXtIDhEJ), since they have succeeded in successfully using TaintDroid.

This repository contains the JDK 6 installer binary, the images to flash Android 4.3 with a ROM containing TaintDroid version 4.1 and our documentation of Google Keyboard analysis.

## Getting Started

### Prerequesites 

You will need:
- [adb](https://www.xda-developers.com/install-adb-windows-macos-linux/)
- a Nexus 4
- an unlocked bootloader

### Flashing the ROM

Reboot your phone into recovery mode. You can do by holding down the power, volume up, and volume down button simultaneaously. You can also reboot into recovery mode with adb.

```
adb reboot recovery
```

Unlock your bootloader.

```
fastboot oem unlock
```


Flush the radio image to the original factory image by [downloading "occam" for Nexus 4 here](https://developers.google.com/android/images#occam).

```
fastboot flash occam-jwr66y/radio-mako-m9615a-cefwmazm-2.0.1700.84.img
```

Navigate to the directory containing the images and flash the images.

```
cd TaintDroid_Reproducibility/imgs
fastboot flash boot boot.img
fastboot flash system system.img
fastboot flash userdata userdata.img
```

## Building TaintDroid 

If you want to build TaintDroid yourself, follow the [instructions from the official website](http://www.appanalysis.org/download.html). You will need JDK 6 for Android 4.3, which is only available to support customers with an account. A copy of the JDK self installer is provided in this repository. [Here are instructions on how to install JDK 6.](http://www.oracle.com/technetwork/java/javase/install-linux-64-self-extracting-142068.html)

## [TaintDroid Discussion Group](https://groups.google.com/forum/#!forum/taintdroid)

This is a Google Group for all questions relating to TaintDroid.