# OpenCore Dell Optiplex 3050 (i5-7500t)
OpenCore Hackintosh configuration example for the DELL Optiplex 3050 Micro with a i5-7500t. 

<img src="Desktop.png" alt="Image" width="1400"/>
<p align="center"><i>Dell Optiplex 3050 micro running MacOS Sequoia.</i></p>

<br>

***

## OpenCore

<img align="left" width="100" height="100" src="https://dortania.github.io/docs/latest/Logos/Logo.png">
<img align="left" src="https://github.com/Coopydood/ultimate-macOS-KVM/assets/39441479/8f69f9b9-cf23-4e8b-adf3-95862a23e2ba" height=100 width=2 />
<h3>OpenCore<br><sub>1.0.6</sub></h3>

This is the version of OpenCore used, including bundled files. The included ``config.plist`` targets this version.
<br>


## macOS

<img align="left" width="90" height="90" src="https://github.com/user-attachments/assets/7b9b72ee-5a89-49b4-ae17-7a188ed533ab">
<!-- CHANGE THE IMAGE URL TO THE MAIN OS YOUR CONFIG TARGETS. IMAGE URL LIST BELOW! -->

<img align="left" src="https://github.com/Coopydood/ultimate-macOS-KVM/assets/39441479/8f69f9b9-cf23-4e8b-adf3-95862a23e2ba" height=520 width=2 /> 
<!-- CHANGE THE HEIGHT WHEN ADDING OR REMOVING SUPPORTED OSES TO THE LIST (Default: 520) -->

<h3>MacOS Sequoia<br><sub>15.7.4</sub></h3>

This is the version of macOS that this OpenCore configuration currently targets. Other versions of macOS that are compatible with it are listed below.<br>

#### Supported

<img align="left" width="35" height="35" src="https://github.com/Coopydood/OpenCore-Z490E-CometLake/assets/39441479/aa49b5ba-6cca-4dab-bcfc-6bf21909e738"> 
<h5>macOS Sonoma</h5>
<img align="left" width="35" height="35" src="https://github.com/Coopydood/OpenCore-Z490E-CometLake/assets/39441479/4829ebb4-ce7f-4ecf-8309-d691c9361f6b"> 
<h5>macOS Ventura</h5>
<img align="left" width="35" height="35" src="https://github.com/Coopydood/OpenCore-Z490E-CometLake/assets/39441479/7d341cce-4370-4430-b3d5-bf1868afe4a3"> 
<h5>macOS Monterey</h5>
<img align="left" width="35" height="35" src="https://github.com/Coopydood/OpenCore-Z490E-CometLake/assets/39441479/79a7a051-0f5a-419e-8544-b51b1572d3b9"> 
<h5>macOS Big Sur</h5>
<img align="left" width="35" height="35" src="https://github.com/Coopydood/OpenCore-Z490E-CometLake/assets/39441479/cd8029e8-c256-4295-9908-37809d64dcfe"> 
<h5>macOS Catalina</h5>
<img align="left" width="35" height="35" src="https://github.com/Coopydood/OpenCore-Z490E-CometLake/assets/39441479/184bb2ef-c447-4cbd-b07c-8b4b096e3944"> 
<h5>macOS Mojave</h5>
<img align="left" width="35" height="35" src="https://github.com/Coopydood/OpenCore-Z490E-CometLake/assets/39441479/bd4a791d-1ac2-4a9a-8ee0-22e4d5f88cd3"> 
<h5>macOS High Sierra</h5>
<img align="left" width="35" height="35" src="https://github.com/Coopydood/OpenCore-Z490E-CometLake/assets/39441479/788860d8-207a-4d15-928a-ed78f08962cf"> 
<h5>macOS Sierra</h5>

<br>

***


## What works?

### macOS

- [x] MacOS Sequoia
- [x] MacOS Sonoma

### Hardware

- [x] iGPU (Intel HD 630)
- [x] NVMe drives
- [x] SATA drives 
- [x] USB 3.1 (XHCI)
- [x] Ethernet
- [x] Wi-Fi (was working fine with Airportitlwm but randomly stopped working when working on audio. Currently disabled and using itwlm + hellport)
- [x] Bluetooth 
- [x] Sound
  
### Software

- [ ] AirDrop
- [x] iMessage
- [x] FaceTime
- [ ] Unlock with Apple Watch
- [x] QE/CI graphics acceleration
- [x] Metal support (Metal 3)
- [x] Temperature sensors
- [ ] Sleep / Wake
- [x] RTC (protection)
- [x] Hyperthreading
- [x] Virtualization
- [x] Memory bank configuration
  
<br>

***

## Problems

<ul>
<li><b>No display after waking up from sleep</b></li>
Not sure if it is even booting.
<br><br>

<li><b><s>Audio out and internal speakers</s> ‏‏‎ ‏‏‎ ‎‎‏‏‎ ‎ 🎉 FIXED!</b></li>
<s>Internal speakers, audio out, and mic in can be succefully recognized and used.</s>

> [!TIP]
> Fixed with custom SSDT-HPET.
<br>
<li><b><s>HDMI brief works during boot and blacks out</s> ‏‏‎ ‏‏‎ ‎‎‏‏‎ ‎ 🎉 FIXED!</b></li>
<s>Onboard HDMI port or DP to HDMI adapter both give green tint</s>

> [!TIP]
> Fixed by add following values to config under HD graphics PCI root.
```
AAPL,ig-platform-id: 0900A53E
framebuffer-patch-enable: 01000000
framebuffer-con2-enable: 01000000
framebuffer-con2-type: 00080000
```
<br>
<li><b><s>HDMI green tint</s> ‏‏‎ ‏‏‎ ‎‎‏‏‎ ‎ 🎉 FIXED!</b></li>
<s>Onboard HDMI port or DP to HDMI adapter both give green tint</s>

> [!TIP]
> Fixed by mapping LVDS to HDMI.

<br>

<li><b><s>Display connectors only works when connected pre-boot</s> ‏‏‎ ‏‏‎ ‎‎‏‏‎ ‎ 🎉 FIXED!</b></li>
<s>Unplug replug breaks the connection</s>

> [!TIP]
> Fixed by adding ```igfxonln=1``` to boot arg.


</ul>


***


## ACPI

SSDTs used:
- SSDT-EC
- SSDT-MCHC
- SSDT-PLUG
- SSDT-SBUS
- SSDT-HPET
***

## Kernel

The following shows the kernel configuration.

### Kexts

Kexts used:
- AMFIPass.kext
- <s>AirportItlwm.kext </s> Disabled
- Itlwm.text
- AppleALC.kext
- BlueToolFixup.kext
- IO80211FamilyLegacy.kext
- IOSkywalkFamily.kext
- IntelBTPatcher.kext
- IntelBluetoothFirmware.kext
- Lilu.kext
- NVMeFix.kext
- RealtekRTL8111.kext
- RestrictEvents.kext
- SMCDellSensors.kext
- SMCProcessor.kext
- SMCSuperIO.kext
- USBToolBox.kext
- UTBMap.kext
- VirtualSMC.kext
- WhateverGreen.kext
- XHCI-unsupported.kext


## SMBIOS

### Macmini8,1

Mac Mini model that most closely resembles this USFF.
***



## UEFI

Drivers in use:

- HFSPlus
- OpenRuntime
- OpenCanopy
- ResetNvramEntry
  
***

## Disclaimer

Feel free to try out my configuration. However, I am not responsible for anything caused by using these configurations.
