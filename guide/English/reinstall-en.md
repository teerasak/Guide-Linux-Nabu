<img align="right" src="../../assets/nabu.png" width="425" alt="Linux Running On A Xiaomi Pad 5">


# Running Windows on the Xiaomi Pad 5

## Reinstallation

### Reinstalling Windows if something goes wrong

- If you don't like your windows version or you've bricked your windows install, or anything else, you would probably just reinstall Windows. Thankfully this process is very easy.

- If you haven't restored your partition table, you can use this guide with your existing partitions.

### Prerequisites

- Existing Windows and boot partitions (*If not met, [go back and just pretend this guide never existed](/guide/English/1-partition-en.md)*)

- [Recovery Image](../../../../releases/tag/1.0)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)


### Boot recovery to format the Windows and boot partitions

```cmd
fastboot boot <recovery.img>
```
### Format the partitions
> If it asks you to run it once again, do so
```cmd
adb shell format
```
## [Next step: Reinstalling Windows](/guide/English/install-en.md#Execute-the-msc-script)
