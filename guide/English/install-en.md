<img align="right" src="../../assets/nabu.png" width="425" alt="Linux Running On A Xiaomi Pad 5">


# Running Windows on the Xiaomi Pad 5
> [!WARNING]
> PLEASE DON'T USE ANY VIDEO GUIDE ON YOUTUBE OR ANY OTHER PLATFORM! THOSE VIDEOS ARE OUT OF DATED!

## Installation

## Installing Windows

### Prerequisites
- Brain
  
- [Windows on ARM image](https://uupdump.net/)
  
- [UEFI image](https://raw.githubusercontent.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/main/images/xiaomi-nabu_secureboot-v2.img)
  
- [Drivers](https://github.com/map220v/MiPad5-Drivers/releases/latest)

### Boot recovery back to start installing Windows

```cmd
fastboot boot <recovery.img>
```

#### Execute the msc script

> If it asks you to run it once again, do so

```cmd
adb shell msc
```
### Assign letters to disks
  

#### Start the Windows disk manager

> Once the Xiaomi Pad 5 is detected as a disk

```cmd
diskpart
```


#### Assign `X` to Windows volume

#### Select the Windows volume of the tablet
> Use `list volume` to find it, it's the one named "WINNABU"

```diskpart
select volume <number>
```

#### Assign the letter X
```diskpart
assign letter=x
```

### Assign `Y` to ESP volume

#### Select the esp volume of the tablet
> Use `list volume` to find it, it's the one named "ESPNABU"

```diskpart
select volume <number>
```

#### Assign the letter Y

```diskpart
assign letter=y
```

#### Exit diskpart
```diskpart
exit
```

  
  

### Install

> Replace `<path/to/install.wim>` with the actual install.wim path,

> `install.wim` is located in sources folder inside your ISO
> You can get it either by mounting or extracting it

```cmd
dism /apply-image /ImageFile:<path/to/install.wim> /index:1 /ApplyDir:X:\
```

### Install Drivers

> You can download Drivers [here](https://github.com/map220v/MiPad5-Drivers/releases/latest)

> When it ask you "Enter Drive letter..." type X:

```cmd
 Open folder with Drivers and run OfflineUpdater.cmd
```

### Create Windows bootloader files for the EFI

```cmd
bcdboot X:\Windows /s Y: /f UEFI
```




## Boot into Windows

### Make a backup of your existing boot image

```cmd
adb shell "dd if=/dev/block/platform/soc/1d84000.ufshc/by-name/boot$(getprop ro.boot.slot_suffix) of=/tmp/boot.img"
```

### Pull backup to computer

```cmd
adb pull /tmp/boot.img
```



### Reboot to bootloader 

```cmd
adb reboot bootloader
```

### Download and flash UEFI image
> Download [UEFI image](https://raw.githubusercontent.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/main/images/xiaomi-nabu_secureboot-v2.img)

```cmd
fastboot flash boot <path to image>
```

> [!NOTE]
> On the first Windows boot, it will not see any Wi-Fi networks, just restart it by holding down the power button, and after reboot when you try connect to yuor network and you see "ice-cream" click "try again" 7 times
### Boot back into Android
> Use your backup boot image and flash from fastboot

```cmd
fastboot flash boot boot.img
```
### Remove phantom drive letters (if they are not removed automatically)
> Run theese commands as admin to remove letter
```cmd
mountvol x: /d
mountvol y: /d
```
## Finished!
> You can join our [Telegram chat](https://t.me/nabuwoa) to receive latest news about project

### [Last step: Setup Dualboot](dualboot-en.md)
