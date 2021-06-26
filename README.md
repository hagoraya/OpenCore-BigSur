# OpenCore-Hackintosh B450M PRO-VDH Ryzen 5 3600
[OpenCore](https://github.com/acidanthera/OpenCorePkg) bootloader ONLY, Clover not supported (Let it go).

## B450M PRO-VDH MAX hackintosh w/ OpenCore

Verified working with macOS version 11.4 Big Sur and OpenCore 0.7.0.

![image](https://user-images.githubusercontent.com/9339148/123524725-123c5080-d681-11eb-84b9-de277db4ff8e.png)


## Important!

***Apple sign in fix***
After post install you will get `Cannot communicate with server` when you try to sign in with Apple Id
This is because the network devices must be marked as built-in. This is an easy fix, which is require added new kexts and editing your `config.plist` file. 

1. Download [Hackintool](https://github.com/headkaze/Hackintool) (this will help you find PCIe device path)
2. Under the PCIe tab you will need to find your either device ![image](https://user-images.githubusercontent.com/9339148/123525056-19fcf480-d683-11eb-984a-ce6fb2ad0ad0.png)
The device path will be unique to your computer e.g.`PciRoot(0x0)/...` copy the full device path
3. Now to edit your `config.plist` file, use MountEFI to open the EFI folder on your macOS drive and open the `config.plist` file using ProperTree

4. Under `DeviceProperties` > `Add` add a new child as `directory` with its name as your network device path.
	Create a new child under your device path with name:`built-in`,  datatype: `Data`, and value: `01`
	 ![image](https://user-images.githubusercontent.com/9339148/123525247-19b12900-d684-11eb-9334-99c5cc39e336.png)
5. Last step is to installed two kexts file 
	1. [NullInternet](https://bitbucket.org/RehabMan/os-x-null-ethernet/downloads/) Put this in your `OC/Kexts` folder
	2. [ssdt-rmne](https://github.com/RehabMan/OS-X-Null-Ethernet/blob/master/ssdt-rmne.aml) Put this in your `OC/ACPI` folder
	Remember to add these to your `config.plist` (taking a snapshot from ProperTree should add this automatically)


**Important! Important! Important!**

**Highly recommended to make sure to use the latest BIOS
## Overview
Installation procedure is quite straightforward, but requires prior knowledge or experience with Hackintoshes. 
It can be simple and complicated at the same time, refer directly to this manual for a better experience.

## Hardware
Components | SKU | Comments
------------ | ------------- | -------------
**CPU** | Ryzen 5 3600 | 17h/18h
**Motherboard** | B450M PRO-VDH MAX | No bios settings were needed (just updated to latest version)
**Graphics Card** | MSI RX 580 8G | 
**RAM** | # Corsair Vengeance LPX 16GB


## Geekbench 5 Scores
[Geekbench CPU Score](https://browser.geekbench.com/v5/cpu/8575471)
[Geekbench GPU Score](https://browser.geekbench.com/v5/compute/3031515)

![image](https://user-images.githubusercontent.com/9339148/123525823-639c0e00-d688-11eb-9933-fd86c7f21c55.png)

## References
* [https://dortania.github.io/OpenCore-Install-Guide/](https://dortania.github.io/OpenCore-Install-Guide/)
* [https://dortania.github.io/Getting-Started-With-ACPI/](https://dortania.github.io/Getting-Started-With-ACPI/)
