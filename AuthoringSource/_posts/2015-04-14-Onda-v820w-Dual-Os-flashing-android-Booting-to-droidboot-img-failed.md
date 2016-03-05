--- 
layout: post
title: "Onda v820w flash os - Booting to droidboot.img failed"
author: "Ke"
comments: true
---

Onda v820w Dual OS 32 GB

Deleted all the Android partitions and was trying to restore the stock setup. 

Followed the offical guide, but when I plugged in the device, flashing hangs and throw error:

>Booting to droidboot.img failed

Here is the full log:

```
04/14/15 21:02:21.619  DEBUG  : Initializing state hash (BYT)
04/14/15 21:02:21.633  INFO   : Manufacturing Flash Tool V 6.0.43 (build on Sun May 18 12:29:29 PDT 2014)
04/14/15 21:02:21.638  INFO   : Loading settings from C:/ProgramData/INTEL/Manufacturing Flash Tool.ini
04/14/15 21:02:21.650  INFO   : LogLevel is set to DEBUG
04/14/15 21:02:21.650  DEBUG  : FlashStats saves the logs into C:/Users/xx/mfgft-stats.csv
04/14/15 21:02:21.650  INFO   : Using Qt version: 4.8.1
04/14/15 21:02:21.650  INFO   : Using XFSTK version: 1.5.5.
04/14/15 21:02:21.658  WARNING: Please select a flash file...
04/14/15 21:02:28.630  INFO   : Loading Flash file (D:/1/flash.xml)
04/14/15 21:02:28.632  INFO   : GP_Flag is set to 0x80000045
04/14/15 21:02:28.633  DEBUG  : Fastboot sequence in flash file is used.
04/14/15 21:02:28.633  DEBUG  : Flash image type: system
04/14/15 21:02:28.633  DEBUG  : droidboot : D:/1/droidboot.img
04/14/15 21:02:28.633  DEBUG  : esp : D:/1/esp.img
04/14/15 21:02:28.633  DEBUG  : osloader : D:/1/efilinux-userdebug.efi
04/14/15 21:02:28.633  DEBUG  : stage2_BAYTRAIL_EDK2_BYT_CRV2_IA32 : 
04/14/15 21:02:28.633  DEBUG  : stage2_BAYTRAIL_EDK2_BYT_CRV2_X64 : 
04/14/15 21:02:28.633  DEBUG  : FASTBOOT : 
04/14/15 21:02:28.633  DEBUG  : SOFTFUSE : 
04/14/15 21:02:28.633  DEBUG  : FW_DNX : 
04/14/15 21:02:28.633  DEBUG  : IFWI : 
04/14/15 21:02:28.634  DEBUG  : OS_DNX : 
04/14/15 21:02:28.634  DEBUG  : XXR_DNX : 
04/14/15 21:02:28.634  DEBUG  : KBOOT : 
04/14/15 21:02:28.634  DEBUG  : KERNEL : 
04/14/15 21:02:28.634  DEBUG  : RECOVERY : 
04/14/15 21:02:28.634  DEBUG  : SYSTEM : 
04/14/15 21:02:28.634  DEBUG  : MODEM : 
04/14/15 21:02:28.634  DEBUG  : OTA : 
04/14/15 21:02:28.634  DEBUG  : cmd[0] {timeout=60000, retry=2} : fastboot oem start_partitioning
04/14/15 21:02:28.634  DEBUG  : cmd[1] {timeout=60000, retry=2} : fastboot flash /tmp/partition.tbl "D:\1\partition.tbl"
04/14/15 21:02:28.634  DEBUG  : cmd[2] {timeout=60000, retry=2} : fastboot oem partition /tmp/partition.tbl
04/14/15 21:02:28.634  DEBUG  : cmd[3] {timeout=60000, retry=2} : fastboot erase system
04/14/15 21:02:28.634  DEBUG  : cmd[4] {timeout=60000, retry=2} : fastboot erase cache
04/14/15 21:02:28.634  DEBUG  : cmd[5] {timeout=60000, retry=2} : fastboot erase factory
04/14/15 21:02:28.634  DEBUG  : cmd[6] {timeout=60000, retry=2} : fastboot erase config
04/14/15 21:02:28.634  DEBUG  : cmd[7] {timeout=60000, retry=2} : fastboot erase logs
04/14/15 21:02:28.634  DEBUG  : cmd[8] {timeout=60000, retry=2} : fastboot erase data
04/14/15 21:02:28.634  DEBUG  : cmd[9] {timeout=60000, retry=2} : fastboot oem stop_partitioning
04/14/15 21:02:28.634  DEBUG  : cmd[10] {timeout=60000, retry=2} : fastboot oem wipe ESP
04/14/15 21:02:28.634  DEBUG  : cmd[11] {timeout=60000, retry=2} : fastboot flash ESP "D:\1\esp.img"
04/14/15 21:02:28.634  DEBUG  : cmd[12] {timeout=60000, retry=2} : fastboot flash fastboot "D:\1\droidboot.img"
04/14/15 21:02:28.634  DEBUG  : cmd[13] {timeout=60000, retry=2} : fastboot flash boot "D:\1\boot.img"
04/14/15 21:02:28.634  DEBUG  : cmd[14] {timeout=60000, retry=2} : fastboot flash recovery "D:\1\recovery.img"
04/14/15 21:02:28.634  DEBUG  : cmd[15] {timeout=920000, retry=2} : fastboot -S 200M flash system "D:\1\system.img"
04/14/15 21:02:28.634  DEBUG  : cmd[16] {timeout=60000, retry=2} : fastboot continue
04/14/15 21:02:28.634  DEBUG  : Using GPFlag from flash file : 0x80000045
04/14/15 21:02:28.634  INFO   : Ready to flash!
04/14/15 21:02:54.685  DEBUG  : Port 0/0/1   #0: FlashManager::do_new_soc_device on port 1
04/14/15 21:02:54.685  INFO   : do_new_medfield_device STARTING TO FLASH
04/14/15 21:02:54.686  DEBUG  : Port 0/0/1   #0: New device detected - SN : BaytrailEF9xxxx
04/14/15 21:02:54.686  DEBUG  : New SOC device -> serial: BaytrailEF9xxxx port: 1 
04/14/15 21:02:54.686  INFO   : Port 0/0/1   #0: DNX/droidboot phase - SN : BaytrailEF90xxxxx
04/14/15 21:02:54.687  DEBUG  : Port 0/0/1   #0: OSLOADER = D:/1/efilinux-userdebug.efi
04/14/15 21:02:54.687  DEBUG  : Port 0/0/1   #0: Flashing osloader ... "C:/Program Files (x86)/Intel/Manufacturing Flash Tool/fastboot.exe" -s BaytrailEF9xxxx flash osloader "D:/1/efilinux-userdebug.efi"
04/14/15 21:03:55.896  DEBUG  : Port 0/0/1   #0: Process TIMEOUT wait for finished. Retrying ... "C:/Program Files (x86)/Intel/Manufacturing Flash Tool/fastboot.exe" -s BaytrailEF9xxxxx flash osloader "D:/1/efilinux-userdebug.efi"
```

After a little while, realized that the device driver is not properly installed(a yellow question mark in device manager)

So I uninstalled the IntelAndroidDrvSetup1.5.0.exe driver that comes with the download. Downloaded one from [here](https://software.intel.com/en-us/android/articles/intel-usb-driver-for-android-devices) instead, and installed it.

Then in device manager, I manually selected the device. Tried everything again, all worked.