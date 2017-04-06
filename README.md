
<h1 align="center">
  <a href="http://www.armadeus.org"><img src="http://www.armadeus.org/wiki/images/logo.png" alt="Armadeus Project" width="200"></a>
  <a href="http://www.buildroot.org"><img src="https://buildroot.org/images/logo.png" alt="Buildroot" width="200"></a>  
  <br>
  Buildroot external repository for Armadeus board
  <br>
  <br>
</h1>

## Armadeus Board support

For now this external repository only support:
- APF27 SOM + APF27_Dev_Full baseboard.
The goal is to finalize tunning before buildroot mainline submission.

## Software version

This external repository have been tested with:
- buildroot-2017.02.1
- uboot-2017.03
- linux-4.10.8

## Install
```
git clone git://git.buildroot.net/buildroot
git clone https://github.com/jcEcaSinters/armadeus-external.git
mkdir buildroot-armadeus
cd buildroot-armadeus
make 0=${PWD} -C ../buildroot BR2_EXTERNAL=../armadeus-external armadeus_apf27_dev_full_defconfig
make
```
## Known issues / ToDoList
- Uboot patches have to be mainlined
- Linux patches have to be mainlined
- FPGA is not supported within device-tree
- TSC2101 audio & touchscreen driver does not work
- TSC2101 audio & touchscreen driver have to be rewriten with MFD support and mainlined in the kernel
- AD9889 HDMI chip does not have device tree support
- CODA codec firmware loading fail
- framebuffer output on Chimei-LW700AT9003 does not work

## Bootlog
```
U-Boot 2017.03 (Apr 06 2017 - 14:11:58 +0200) apf27 patch 4.00

CPU:   Freescale i.MX27 at 399 MHz

Board: Armadeus APF27 revision 1
I2C:   ready
DRAM:  128 MiB
NAND:  256 MiB
MMC:   MXC MCI: 0
In:    serial
Out:   serial
Err:   serial
Net:   FEC
NAND flash successfully locked
device 0 offset 0x100000, size 0x80000
NAND flash successfully unlocked
Hit any key to stop autoboot:  0 

NAND read: device 0 offset 0x280000, size 0x80000
 524288 bytes read: OK

Loading from nand0, offset 0x300000
   Image Name:   Linux-4.10.0
   Created:      2017-04-07  13:09:12 UTC
   Image Type:   ARM Linux Kernel Image (uncompressed)
   Data Size:    3951528 Bytes = 3.8 MiB
   Load Address: a0008000
   Entry Point:  a0008000
## Booting kernel from Legacy Image at a0000000 ...
   Image Name:   Linux-4.10.0
   Created:      2017-04-07  13:09:12 UTC
   Image Type:   ARM Linux Kernel Image (uncompressed)
   Data Size:    3951528 Bytes = 3.8 MiB
   Load Address: a0008000
   Entry Point:  a0008000
   Verifying Checksum ... OK
## Flattened Device Tree blob at a1000000
   Booting using the fdt blob at 0xa1000000
   Loading Kernel Image ... OK
   Loading Device Tree to a3ff7000, end a3fff2b9 ... OK

Starting kernel ...

Booting Linux on physical CPU 0x0
Linux version 4.10.0 (jc@mic341-linux) (gcc version 5.4.0 (Buildroot 2017.05-git-00774-gea3f540) ) #3 PREEMPT Fri Apr 7 15:09:09 CEST 2017
CPU: ARM926EJ-S [41069264] revision 4 (ARMv5TEJ), cr=0005317f
CPU: VIVT data cache, VIVT instruction cache
OF: fdt:Machine model: Armadeus APF27_Dev_Full kit
Memory policy: Data cache writeback
Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 32128
Kernel command line: console=ttymxc0,115200 video=imxfb:Chimei-LW700AT9003 ubi.mtd=rootfs root=ubi0:rootfs rootfstype=ubifs
PID hash table entries: 512 (order: -1, 2048 bytes)
Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
Memory: 121584K/131072K available (5725K kernel code, 394K rwdata, 1448K rodata, 324K init, 146K bss, 9488K reserved, 0K cma-reserved)
Virtual kernel memory layout:
    vector  : 0xffff0000 - 0xffff1000   (   4 kB)
    fixmap  : 0xffc00000 - 0xfff00000   (3072 kB)
    vmalloc : 0xd4800000 - 0xff800000   ( 688 MB)
    lowmem  : 0xc0000000 - 0xd4000000   ( 320 MB)
    modules : 0xbf000000 - 0xc0000000   (  16 MB)
      .text : 0xc0008000 - 0xc059f9e4   (5727 kB)
      .init : 0xc0733000 - 0xc0784000   ( 324 kB)
      .data : 0xc0784000 - 0xc07e6ac4   ( 395 kB)
       .bss : 0xc07e6ac4 - 0xc080b620   ( 147 kB)
Preemptible hierarchical RCU implementation.
	Build-time adjustment of leaf fanout to 32.
NR_IRQS:16 nr_irqs:16 16
MXC IRQ initialized
CPU identified as i.MX27, silicon rev 2.1
Switching to timer-based delay loop, resolution 60ns
sched_clock: 32 bits at 16MHz, resolution 60ns, wraps every 129171917793ns
clocksource: mxc_timer1: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 114963006693 ns
Console: colour dummy device 80x30
Calibrating delay loop (skipped), value calculated using timer frequency.. 33.25 BogoMIPS (lpj=166250)
pid_max: default: 32768 minimum: 301
Mount-cache hash table entries: 1024 (order: 0, 4096 bytes)
Mountpoint-cache hash table entries: 1024 (order: 0, 4096 bytes)
CPU: Testing write buffer coherency: ok
Setting up static identity map for 0xa0008400 - 0xa000847c
devtmpfs: initialized
clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 19112604462750000 ns
futex hash table entries: 256 (order: -1, 3072 bytes)
pinctrl core: initialized pinctrl subsystem
NET: Registered protocol family 16
DMA: preallocated 256 KiB pool for atomic coherent allocations
imx27-pinctrl 10015000.iomuxc: initialized IMX pinctrl driver
SCSI subsystem initialized
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
i2c i2c-0: IMX I2C adapter registered
i2c i2c-0: can't use DMA, using PIO instead.
i2c i2c-1: IMX I2C adapter registered
i2c i2c-1: can't use DMA, using PIO instead.
Linux video capture interface: v2.00
pps_core: LinuxPPS API ver. 1 registered
pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
PTP clock support registered
Advanced Linux Sound Architecture Driver Initialized.
clocksource: Switched to clocksource mxc_timer1
NET: Registered protocol family 2
TCP established hash table entries: 1024 (order: 0, 4096 bytes)
TCP bind hash table entries: 1024 (order: 0, 4096 bytes)
TCP: Hash tables configured (established 1024 bind 1024)
UDP hash table entries: 256 (order: 0, 4096 bytes)
UDP-Lite hash table entries: 256 (order: 0, 4096 bytes)
NET: Registered protocol family 1
RPC: Registered named UNIX socket transport module.
RPC: Registered udp transport module.
RPC: Registered tcp transport module.
RPC: Registered tcp NFSv4.1 backchannel transport module.
workingset: timestamp_bits=30 max_order=15 bucket_order=0
jffs2: version 2.2. (NAND) © 2001-2006 Red Hat, Inc.
io scheduler noop registered (default)
imx-weim d8002000.weim: Driver registered.
imx-fb 10021000.fb: i.MX Framebuffer driver
Console: switching to colour frame buffer device 100x60
1000a000.serial: ttymxc0 at MMIO 0x1000a000 (irq = 36, base_baud = 1039062) is a IMX
console [ttymxc0] enabled
at24 1-0050: 256 byte 24c02 EEPROM, writable, 8 bytes/write
nand: device found, Manufacturer ID: 0x2c, Chip ID: 0xba
nand: Micron MT29F2G16ABBEAHC
nand: 256 MiB, SLC, erase size: 128 KiB, page size: 2048, OOB size: 64
nand: WARNING: mxc_nand: the ECC used on your system is too weak compared to the one required by the NAND chip
Bad block table found at page 131008, version 0x01
Bad block table found at page 130944, version 0x01
7 ofpart partitions found on MTD device mxc_nand
Creating 7 MTD partitions on "mxc_nand":
0x000000000000-0x000000100000 : "u-boot"
0x000000100000-0x000000180000 : "env"
0x000000180000-0x000000200000 : "env2"
0x000000200000-0x000000280000 : "firmware"
0x000000280000-0x000000300000 : "dtb"
0x000000300000-0x000000800000 : "kernel"
0x000000800000-0x000010000000 : "rootfs"
spi_imx 1000e000.cspi: probed
spi_imx 1000f000.cspi: probed
TI TSC210x driver initializing
No TI TSC210x chip found! Bad revision: 0
libphy: Fixed MDIO Bus: probed
CAN device driver interface
mcp251x spi1.1 can0: MCP2515 successfully initialized.
libphy: fec_enet_mii_bus: probed
ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
ehci-mxc: Freescale On-Chip EHCI Host driver
usbcore: registered new interface driver usb-storage
ci_hdrc ci_hdrc.0: EHCI Host Controller
ci_hdrc ci_hdrc.0: new USB bus registered, assigned bus number 1
ci_hdrc ci_hdrc.0: USB 2.0 started, EHCI 1.00
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 1 port detected
ci_hdrc ci_hdrc.1: EHCI Host Controller
ci_hdrc ci_hdrc.1: new USB bus registered, assigned bus number 2
ci_hdrc ci_hdrc.1: USB 2.0 started, EHCI 1.00
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 1 port detected
mxc_rtc 10007000.rtc: rtc core: registered 10007000.rtc as rtc0
i2c /dev entries driver
coda 10023000.coda: Direct firmware load for vpu_fw_imx27_TO2.bin failed with error -2
coda 10023000.coda: Direct firmware load for v4l-codadx6-imx27.bin failed with error -2
Driver for 1-wire Dallas network protocol.
imx2-wdt 10002000.wdog: timeout 60 sec (nowayout=0)
i.MX/MPC512x SDHC driver
mxc-mmc 10014000.sdhci: Got CD GPIO
coda 10023000.coda: firmware request failed
random: fast init done
sdhci: Secure Digital Host Controller Interface driver
sdhci: Copyright(c) Pierre Ossman
sdhci-pltfm: SDHCI platform and OF driver helper
oprofile: no performance counters
oprofile: using timer interrupt.
NET: Registered protocol family 17
can: controller area network core (rev 20120528 abi 9)
NET: Registered protocol family 29
can: raw protocol (rev 20120528)
can: broadcast manager protocol (rev 20161123 t)
can: netlink gateway (rev 20130117) max_hops=1
ubi0: attaching mtd6
mmc0: host does not support reading read-only switch, assuming write-enable
mmc0: new SDHC card at address 0001
mmcblk0: mmc0:0001 SD8GB 7.32 GiB 
 mmcblk0: p1
usb 2-1: new full-speed USB device number 2 using ci_hdrc
usb 2-1: not running at top speed; connect to a high speed hub
usb-storage 2-1:1.0: USB Mass Storage device detected
scsi host0: usb-storage 2-1:1.0
ubi0: scanning is finished
ubi0: attached mtd6 (name "rootfs", size 248 MiB)
ubi0: PEB size: 131072 bytes (128 KiB), LEB size: 129024 bytes
ubi0: min./max. I/O unit sizes: 2048/2048, sub-page size 512
ubi0: VID header offset: 512 (aligned 512), data offset: 2048
ubi0: good PEBs: 1980, bad PEBs: 4, corrupted PEBs: 0
ubi0: user volume: 1, internal volumes: 1, max. volumes count: 128
ubi0: max/mean erase counter: 2/0, WL threshold: 4096, image sequence number: 602284664
ubi0: available PEBs: 0, total reserved PEBs: 1980, PEBs reserved for bad PEB handling: 36
ubi0: background thread "ubi_bgt0d" started, PID 639
input: gpio-keys as /devices/platform/gpio-keys/input/input0
mxc_rtc 10007000.rtc: setting system clock to 1970-01-01 00:00:14 UTC (14)
ALSA device list:
  No soundcards found.
UBIFS (ubi0:0): recovery needed
random: crng init done
UBIFS (ubi0:0): recovery deferred
UBIFS (ubi0:0): UBIFS: mounted UBI device 0, volume 0, name "rootfs", R/O mode
UBIFS (ubi0:0): LEB size: 129024 bytes (126 KiB), min./max. I/O unit sizes: 2048 bytes/2048 bytes
UBIFS (ubi0:0): FS size: 248887296 bytes (237 MiB, 1929 LEBs), journal size 9033728 bytes (8 MiB, 71 LEBs)
UBIFS (ubi0:0): reserved for root: 0 bytes (0 KiB)
UBIFS (ubi0:0): media format: w4/r0 (latest is w5/r0), UUID 471FDCF3-A763-498C-A61A-117679AD8B58, small LPT model
VFS: Mounted root (ubifs filesystem) readonly on device 0:14.
devtmpfs: mounted
Freeing unused kernel memory: 324K
This architecture does not have kernel memory protection.
scsi 0:0:0:0: Direct-Access     USB      Flash Disk       1100 PQ: 0 ANSI: 4
sd 0:0:0:0: [sda] 7831552 512-byte logical blocks: (4.01 GB/3.73 GiB)
sd 0:0:0:0: [sda] Write Protect is off
sd 0:0:0:0: [sda] No Caching mode page found
sd 0:0:0:0: [sda] Assuming drive cache: write through
UBIFS (ubi0:0): completing deferred recovery
UBIFS (ubi0:0): background thread "ubifs_bgt0_0" started, PID 654
 sda: sda1
UBIFS (ubi0:0): deferred recovery completed
sd 0:0:0:0: [sda] Attached SCSI removable disk
Starting logging: OK
Initializing random number generator... done.
Starting network: OK

Welcome to Buildroot
buildroot login: 
```

## License

[GPLv2](LICENSE). Copyright (c) [ECA SINTERS](http://www.ecagroup.com).

