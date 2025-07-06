# A9 wifi camera (prefix: DGK)

## Hardware

**PCB** : "w200_v3_v0.1", "D191221"

**SoC** : HiSilicon Hi3518ev300

**Cpu** :  ARMv7 

**Wifi** : BL-M8188FU1, RTL8188FU

**Sensor** : soih62/JX-H62; "dcxyx-a9-62-300-v2 j2"

**RAM**: 64MB

**Flash**: w25q64fv/w25q64jv_iq[https://www.winbond.com/hq/product/code-storage-flash-memory/serial-nor-flash/?__locale=en&partNo=W25Q64FV] NOR, 8MB

**Manufacturer** : Shenzen Jinshuoshi International Co., Ltd

## Wi-fi

AP works; STA does not connect (driver bug).

Driver version:

```
RTW: rtl8188fu v5.3.0.1_28034.20180525
```

STA works with https://github.com/ulli-kroll/rtl8188fu.

TODO: add compiled binary

## Telnet

Enabled by default. Login 'root', no password.

# Live stream

On port 10002.

AFAICT it's RAW H264, just a series of Nal's.

Works OOTB with ffmpeg ( with errors), eg:

```
ffplay http://192.168.0.1:10002
```

## LED control

Blue: GPIO 55

Red: GPIO 52

```
echo 1 > /sys/class/gpio/gpio55/value 
```

## Images

TODO

## Info

<details>

<summary>dmesg</summary>

```
Booting Linux on physical CPU 0x0
Linux version 4.9.37 (yiqing@chana) (gcc version 6.3.0 (HC&C V100R002C00B032_20190114) ) #5 Tue Jun 30 14:22:24 CST 2020
CPU: ARMv7 Processor [410fc075] revision 5 (ARMv7), cr=10c53c7d
CPU: div instructions available: patching division code
CPU: PIPT / VIPT nonaliasing data cache, VIPT aliasing instruction cache
OF: fdt:Machine model: Hisilicon HI3518EV300 DEMO Board
Memory policy: Data cache writeback
On node 0 totalpages: 11520
free_area_init_node: node 0, pgdat c05dd410, node_mem_map c2c9b000
  Normal zone: 90 pages used for memmap
  Normal zone: 0 pages reserved
  Normal zone: 11520 pages, LIFO batch:1
CPU: All CPU(s) started in SVC mode.
pcpu-alloc: s0 r0 d32768 u32768 alloc=1*32768
pcpu-alloc: [0] 0 
Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 11430
Kernel command line: mem=45M console=ttyAMA0,115200 root=/dev/mtdblock2 rw coherent_pool=2M rootfstype=squashfs mtdparts=hi_sfc:320K(u-boot.bin),2240K(kernel),4224K(rootfs),1408K(app)
PID hash table entries: 256 (order: -2, 1024 bytes)
Dentry cache hash table entries: 8192 (order: 3, 32768 bytes)
Inode-cache hash table entries: 4096 (order: 2, 16384 bytes)
Memory: 39296K/46080K available (4567K kernel code, 134K rwdata, 1100K rodata, 164K init, 242K bss, 6784K reserved, 0K cma-reserved)
Virtual kernel memory layout:
    vector  : 0xffff0000 - 0xffff1000   (   4 kB)
    fixmap  : 0xffc00000 - 0xfff00000   (3072 kB)
    vmalloc : 0xc3000000 - 0xff800000   ( 968 MB)
    lowmem  : 0xc0000000 - 0xc2d00000   (  45 MB)
    modules : 0xbf000000 - 0xc0000000   (  16 MB)
      .text : 0xc0008000 - 0xc047de40   (4568 kB)
      .init : 0xc0593000 - 0xc05bc000   ( 164 kB)
      .data : 0xc05bc000 - 0xc05dda60   ( 135 kB)
       .bss : 0xc05df000 - 0xc061bb78   ( 243 kB)
SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
NR_IRQS:16 nr_irqs:16 16
Gic dist init...
arm_arch_timer: Architected cp15 timer(s) running at 50.00MHz (phys).
clocksource: arch_sys_counter: mask: 0xffffffffffffff max_cycles: 0xb8812736b, max_idle_ns: 440795202655 ns
sched_clock: 56 bits at 50MHz, resolution 20ns, wraps every 4398046511100ns
Switching to timer-based delay loop, resolution 20ns
clocksource: arm,sp804: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 637086815595 ns
Console: colour dummy device 80x30
Calibrating delay loop (skipped), value calculated using timer frequency.. 100.00 BogoMIPS (lpj=500000)
pid_max: default: 32768 minimum: 301
Mount-cache hash table entries: 1024 (order: 0, 4096 bytes)
Mountpoint-cache hash table entries: 1024 (order: 0, 4096 bytes)
CPU: Testing write buffer coherency: ok
Setting up static identity map for 0x40008200 - 0x40008258
devtmpfs: initialized
VFP support v0.3: implementor 41 architecture 2 part 30 variant 7 rev 5
clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 19112604462750000 ns
futex hash table entries: 256 (order: -1, 3072 bytes)
pinctrl core: initialized pinctrl subsystem
NET: Registered protocol family 16
DMA: preallocated 2048 KiB pool for atomic coherent allocations
Serial: AMBA PL011 UART driver
12040000.uart: ttyAMA0 at MMIO 0x12040000 (irq = 20, base_baud = 0) is a PL011 rev2
console [ttyAMA0] enabled
12041000.uart: ttyAMA1 at MMIO 0x12041000 (irq = 21, base_baud = 0) is a PL011 rev2
12042000.uart: ttyAMA2 at MMIO 0x12042000 (irq = 22, base_baud = 0) is a PL011 rev2
ssp-pl022 12070000.spi: ARM PL022 driver, device ID: 0x00800022
ssp-pl022 12070000.spi: mapped registers from 0x12070000 to c322f000
ssp-pl022 12071000.spi: ARM PL022 driver, device ID: 0x00800022
ssp-pl022 12071000.spi: mapped registers from 0x12071000 to c3233000
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
clocksource: Switched to clocksource arch_sys_counter
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
workingset: timestamp_bits=30 max_order=14 bucket_order=0
squashfs: version 4.0 (2009/01/31) Phillip Lougher
exFAT: Version 1.2.9
NFS: Registering the id_resolver key type
Key type id_resolver registered
Key type id_legacy registered
jffs2: version 2.2. (NAND) © 2001-2006 Red Hat, Inc.
yaffs: yaffs Installing.
Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
io scheduler noop registered
io scheduler deadline registered (default)
io scheduler cfq registered
pl061_gpio 120b0000.gpio_chip: PL061 GPIO chip @0x120b0000 registered
pl061_gpio 120b1000.gpio_chip: PL061 GPIO chip @0x120b1000 registered
pl061_gpio 120b2000.gpio_chip: PL061 GPIO chip @0x120b2000 registered
pl061_gpio 120b4000.gpio_chip: PL061 GPIO chip @0x120b4000 registered
pl061_gpio 120b5000.gpio_chip: PL061 GPIO chip @0x120b5000 registered
pl061_gpio 120b6000.gpio_chip: PL061 GPIO chip @0x120b6000 registered
pl061_gpio 120b7000.gpio_chip: PL061 GPIO chip @0x120b7000 registered
pl061_gpio 120b8000.gpio_chip: PL061 GPIO chip @0x120b8000 registered
brd: module loaded
hisi-sfc hisi_spi_nor.0: SPI Nor ID Table Version 1.2
hisi-sfc hisi_spi_nor.0: all blocks is unlocked.
hisi-sfc hisi_spi_nor.0: w25q64fv(spi)/w25q64jv_iq (Chipsize 8 Mbytes, Blocksize 64KiB)
4 cmdlinepart partitions found on MTD device hi_sfc
4 cmdlinepart partitions found on MTD device hi_sfc
Creating 4 MTD partitions on "hi_sfc":
0x000000000000-0x000000050000 : "u-boot.bin"
0x000000050000-0x000000280000 : "kernel"
0x000000280000-0x0000006a0000 : "rootfs"
0x0000006a0000-0x000000800000 : "app"
usbcore: registered new interface driver zd1201
dwc3 10030000.hidwc3: Configuration mismatch. dr_mode forced to host
xhci-hcd xhci-hcd.0.auto: xHCI Host Controller
xhci-hcd xhci-hcd.0.auto: new USB bus registered, assigned bus number 1
xhci-hcd xhci-hcd.0.auto: hcc params 0x0220fe6c hci version 0x110 quirks 0x20010010
xhci-hcd xhci-hcd.0.auto: irq 116, io mem 0x10030000
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 1 port detected
xhci-hcd xhci-hcd.0.auto: xHCI Host Controller
xhci-hcd xhci-hcd.0.auto: new USB bus registered, assigned bus number 2
usb usb2: We don't know the algorithms for LPM for this host, disabling LPM.
hub 2-0:1.0: USB hub found
hub 2-0:1.0: hub can't support USB3.0
usbcore: registered new interface driver cdc_acm
cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters
usbcore: registered new interface driver usbserial
usbcore: registered new interface driver option
usbserial: USB Serial support registered for GSM modem (1-port)
i2c /dev entries driver
hibvt-i2c 12060000.i2c: hibvt-i2c0@100000hz registered
hibvt-i2c 12061000.i2c: hibvt-i2c1@100000hz registered
hibvt-i2c 12062000.i2c: hibvt-i2c2@100000hz registered
sdhci: Secure Digital Host Controller Interface driver
sdhci: Copyright(c) Pierre Ossman
sdhci-pltfm: SDHCI platform and OF driver helper
mmc0: SDHCI controller on 10010000.sdhci [10010000.sdhci] using ADMA in legacy mode
mmc1: SDHCI controller on 10020000.sdhci [10020000.sdhci] using ADMA in legacy mode
usbcore: registered new interface driver usbhid
usbhid: USB HID core driver
Initializing XFRM netlink socket
NET: Registered protocol family 17
NET: Registered protocol family 15
Key type dns_resolver registered
VFS: Mounted root (squashfs filesystem) readonly on device 31:2.
devtmpfs: mounted
Freeing unused kernel memory: 164K (c0593000 - c05bc000)
This architecture does not have kernel memory protection.
usb 1-1: new high-speed USB device number 2 using xhci-hcd
random: init: uninitialized urandom read (4 bytes read)
udev[570]: starting version 167
rtl8188fu: loading out-of-tree module taints kernel.
RTW: module init start
RTW: rtl8188fu v5.3.0.1_28034.20180525
RTW: build time: Mar 24 2020 15:10:59
random: fast init done
RTW: HW EFUSE
RTW: 0x000: 29 81 00 FC  0B 00 00 00  00 0C 04 4C  10 07 00 00  
RTW: 0x010: 23 24 28 27  26 26 23 24  28 27 26 13  FF FF FF FF  
RTW: 0x020: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF  
RTW: 0x030: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF  
RTW: 0x040: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF  
RTW: 0x050: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF  
RTW: 0x060: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF  
RTW: 0x070: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF  
RTW: 0x080: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF  
RTW: 0x090: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF  
RTW: 0x0A0: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF  
RTW: 0x0B0: FF FF FF FF  FF FF FF FF  20 1C 1A 00  00 00 00 FF  
RTW: 0x0C0: FF 02 00 10  00 FF 00 FF  00 00 FF FF  FF FF FF FF  
RTW: 0x0D0: DA 0B 79 F1  47 66 40 44  01 BB 06 20  3E 09 03 52  
RTW: 0x0E0: 65 61 6C 74  65 6B 09 03  38 30 32 2E  31 31 6E 00  
RTW: 0x0F0: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF  
RTW: 0x100: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF  
RTW: 0x110: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF  
RTW: 0x120: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF  
RTW: 0x130: C1 B6 FF FF  FF FF FF FF  FF FF 00 11  FF FF FF FF  
RTW: 0x140: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF  
RTW: 0x150: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF  
RTW: 0x160: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF  
RTW: 0x170: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF  
RTW: 0x180: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF  
RTW: 0x190: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF  
RTW: 0x1A0: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF  
RTW: 0x1B0: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF  
RTW: 0x1C0: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF  
RTW: 0x1D0: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF  
RTW: 0x1E0: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF  
RTW: 0x1F0: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF  
RTW: hal_com_config_channel_plan chplan:0x20
RTW: rtw_regsty_chk_target_tx_power_valid return _FALSE for band:0, path:0, rs:0, t:-1
RTW: rtw_ndev_init(wlan0) if1 mac_addr=44:01:bb:06:20:3e
usbcore: registered new interface driver rtl8188fu
RTW: module init ret=0
i2c0_for_mipi_sensor_pin_mux_16ev200

==========sensor: soih62==========
====== sensor clk:27M ======
==== online_flag=0, cmos_yuv_flag=1, sensor=soih62, chip=hi3518ev300, board=demo====
==== g_quick_start_flag=0 ====
sysconfig init success!
Module himedia: init ok
Hisilicon Media Memory Zone Manager
hi_osal 1.0 init success!
hi3516ev200_base: module license 'Proprietary' taints kernel.
Disabling lock debugging due to kernel taint
load sys.ko for Hi3516EV200...OK!
load region.ko for Hi3516EV200...OK!
load vgs.ko for Hi3516EV200...OK!
load vi.ko for Hi3516EV200...OK !
ISP Mod init!
load vpss.ko for Hi3516EV200...OK!
load chnl.ko for Hi3516EV200...OK!
load vedu.ko for Hi3516EV200...OK!
load rc.ko for Hi3516EV200...OK!
load venc.ko for Hi3516EV200...OK!
load h264e.ko for Hi3516EV200...OK!
load h265e.ko for Hi3516EV200...OK!
load jpege.ko for Hi3516EV200...OK!
load ive.ko for Hi3516EV200...OK!
load mipi_rx driver successful!
register dev
Hisilicon Watchdog Timer: 0.01 initialized. default_margin=60 sec (nodeamon= 1)
hiwtdg init ok. ver=Aug 28 2019, 14:46:20.
sh (997): drop_caches: 3
RTW: wlan0- hw port(0) mac_addr =44:01:bb:06:20:3e
RTW: assoc success
RTW: ============ STA [a0:02:a5:a4:8c:97]  ===================
RTW: mac_id : 0
RTW: wireless_mode : 0x0b
RTW: mimo_type : 0
RTW: bw_mode : 20MHz, ra_bw_mode : 20MHz
RTW: rate_id : 3
RTW: rssi : -1 (%), rssi_level : 0
RTW: is_support_sgi : Y, is_vht_enable : N
RTW: disable_ra : N, disable_pt : N
RTW: is_noisy : N
RTW: txrx_state : 0
RTW: curr_tx_rate : CCK_1M (L)
RTW: curr_tx_bw : 20MHz
RTW: curr_retry_ratio : 0
RTW: ra_mask : 0x00000000000fffff

```

</details>
  
<details>

<summary>ps</summary>

```
PID   USER     TIME   COMMAND
    1 root       0:00 init
    2 root       0:00 [kthreadd]
    3 root       0:51 [ksoftirqd/0]
    5 root       0:00 [kworker/0:0H]
    7 root       0:00 [lru-add-drain]
    8 root       0:00 [kdevtmpfs]
    9 root       0:00 [netns]
  194 root       0:00 [oom_reaper]
  195 root       0:00 [writeback]
  197 root       0:00 [kcompactd0]
  198 root       0:00 [crypto]
  199 root       0:00 [bioset]
  201 root       0:00 [kblockd]
  205 root       0:00 [spi0]
  208 root       0:00 [spi1]
  209 root       0:00 [kworker/0:1]
  228 root       0:00 [cfg80211]
  309 root       0:00 [rpciod]
  310 root       0:00 [xprtiod]
  317 root       0:00 [kswapd0]
  371 root       0:00 [nfsiod]
  431 root       0:00 [bioset]
  432 root       0:00 [bioset]
  433 root       0:00 [bioset]
  434 root       0:00 [bioset]
  435 root       0:00 [bioset]
  436 root       0:00 [bioset]
  437 root       0:00 [bioset]
  438 root       0:00 [bioset]
  439 root       0:00 [bioset]
  440 root       0:00 [bioset]
  441 root       0:00 [bioset]
  442 root       0:00 [bioset]
  443 root       0:00 [bioset]
  444 root       0:00 [bioset]
  445 root       0:00 [bioset]
  446 root       0:00 [bioset]
  487 root       0:00 [bioset]
  492 root       0:00 [bioset]
  497 root       0:00 [bioset]
  502 root       0:00 [bioset]
  538 root       0:00 [irq/26-mmc0]
  540 root       0:00 [irq/27-mmc1]
  542 root       0:07 [kworker/0:2]
  553 root       0:33 [kworker/0:1H]
  570 root       0:00 udevd --daemon
  591 root       0:00 udevd --daemon
  592 root       0:00 udevd --daemon
  821 root       0:00 [jffs2_gcd_mtd3]
  823 root       0:00 -sh
  876 root       2:08 [irq/41-VI_CAP0]
  944 root      48:51 /mnt/userdata/app/target 1 0 0 0 0 0 1 0 2 0 0
  955 root       0:03 telnetd
  965 root       0:10 {appUpgrade.sh} /bin/sh /usrsys/app/appUpgrade.sh
 1064 root       0:13 [RTW_CMD_THREAD]
 1074 root       0:00 hostapd /mnt/userdata/config/wifi/rtl_hostapd_2G.conf -B
 1077 root       0:00 udhcpd /mnt/userdata/config/wifi/udhcpd.conf
 2753 root       0:00 sleep 1
 2754 root       0:00 ps
 6596 root       0:00 [kworker/u2:0]
18815 root       0:00 -sh
21507 root       0:00 [kworker/u2:2]
```

</details>

<details>

<summary>/proc/cpuinfo</summary>

```processor       : 0
model name      : ARMv7 Processor rev 5 (v7l)
BogoMIPS        : 100.00
Features        : half thumb fastmult vfp edsp neon vfpv3 tls vfpv4 idiva idivt vfpd32 lpae evtstrm
CPU implementer : 0x41
CPU architecture: 7
CPU variant     : 0x0
CPU part        : 0xc07
CPU revision    : 5

Hardware        : Generic DT based system
Revision        : 0000
Serial          : 0000000000000000
```

</details>

<details>

<summary>IPCTool</summary>

```chip:
  vendor: HiSilicon
  model: 3518EV300
  id: 02404006fe0038c1a770030ab43bad9425688918918929e3
board:
  possible-IR-cut-GPIO: 41,52,53,55
ethernet:
  mac: "44:01:bb:06:20:3e"
  u-mdio-phyaddr: 0
  phy-id: 0x00000000
  d-mdio-phyaddr: 0
rom:
- type: nor
  block: 64K
  partitions:
    - name: u-boot.bin
      size: 0x50000
      sha1: fb7a02c2
      contains:
        - name: uboot-env
          offset: 0x40000
    - name: kernel
      size: 0x230000
      sha1: c8eaa912
    - name: rootfs
      size: 0x420000
      sha1: 9e2bad9a
    - name: app
      size: 0x160000
      path: /mnt/userdata,jffs2,rw
  size: 8M
  addr-mode: 3-byte
ram:
  total: 64M
  media: 19M
firmware:
  kernel: "4.9.37 (Tue Jun 30 14:22:24 CST 2020)"
  toolchain: gcc version 6.3.0 (HC&C V100R002C00B032_20190114)
  libc: uClibc 0.9.33.2
  sdk: "Hi3516EV200_MPP_V1.0.1.1 B030 Release (Jun 17 2019, 11:19:14)"
  main-app: /mnt/userdata/app/target
sensors:
- vendor: Silicon Optronics
  model: JXH62
  control:
    bus: 0
    type: i2c
    addr: 0x60
  data:
    type: MIPI
    lane-id:
      - 0
      - 1
      - 2
      - 3
    image: 1x1
  clock: 27MHz
```

</details>

<details>

<summary>/proc/umap/*</summary>

```
[ACODEC] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time: [Jun 17 2019, 11:19:15]

-----ACODEC PARAM--------------------------------------------------------------
   LGain(dB)   RGain(dB) DacLVol(dB) DacRVol(dB) AdcLVol(dB) AdcRVol(dB) MicLMut MicRMut DacLMut DacRMut  BoostL  BoostR
      16.0      16.0         6           6           0           0           0       0       0       0       1       1

[AI] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time: [Jun 17 2019, 11:19:15]

-----AI DEV ATTR----------------------------------------------------------------
AiDev WorkMod   SampR  BitWid  ChnCnt  ClkSel SoundMod  PoiNum  ExFlag  FrmNum
    0 i2s_mas    8kHZ   16bit       1       0     mono     320       0      30

-----AI DEV STATUS0-------------------------------------------------------------
AiDev     IntCnt    fifoCnt    buffInt FrmTime MaxFrmTime TranLen IsrTime 
    0     229681          0          0   40033      42007     640     185

-----AI DEV STATUS1-------------------------------------------------------------
AiDev MaxIsrTime      CBPhy  CBSize    ROffSet    WOffSet
    0        351   437f0000    1920        280          0

-----AI DEV EXTEND STATUS-------------------------------------------------------
AiDev enTrack   bMute  Volume
    0       0       N       0

-----AI CHN STATUS--------------------------------------------------------------
AiDev   AiChn   State     BufFul UsrQueLost UsrFrmDepth   u32Data0   u32Data1    UserGet    UserRls
    0       0  enable          0          0          30          1          1     229680     229680

-----AI CHN RESAMPLE STATUS-----------------------------------------------------
AiDev AiChn   State  bResmp  PoiNum   InSampR  OutSampR
    0     0  enable       N       0    (null)    (null)

-----AI CHN VQE STATUS0---------------------------------------------------------
AiDev AiChn   State bVqe workmod    RATE  PoiNum bAgc  bEq bHpf bRnr bHdr bDrc  WrFile
    0     0  enable    Y    comm   16kHZ     320    Y    N    Y    Y    N    N       N

-----AI CHN VQE STATUS1---------------------------------------------------------
AiDev AiChn   State    bAgc bUsrmod NoiseSupSwi AdjustSpeed ImproveSNR MaxGain NoiseFloor OutputMode TargetLevel  UseHPF
    0     0  enable       Y       Y           1           0          2       2        -41          1          -2       2

-----AI CHN VQE STATUS2---------------------------------------------------------
AiDev AiChn   State    bHpf bUsrmod HpfFreq
    0     0  enable       Y       Y      80

-----AI CHN VQE STATUS3---------------------------------------------------------
AiDev AiChn   State    bRnr bUsrmod MaxNrLevel  NsThresh  NrMode
    0     0  enable       Y       Y         15       -57       1

[AO] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time: [Jun 17 2019, 11:19:14]

-----AO DEV ATTR----------------------------------------------------------------
AoDev WorkMod   SampR  BitWid  ChnCnt  ClkSel SoundMod  PoiNum  ExFlag  FrmNum
    0 i2s_mas    8kHZ   16bit       1       0     mono     320       0      30

-----AO DEV STATUS0-------------------------------------------------------------
AoDev     IntCnt    fifoCnt    buffInt FrmTime MaxFrmTime TranLen IsrTime
    0     229679          1          0   40001      40637     640      12

-----AO DEV STATUS1-------------------------------------------------------------
AoDev MaxIsrTime      CBPhy  CBSize    ROffSet    WOffSet
    0         28   4382f000    1920          0        280

-----AO DEV EXTEND STATUS-------------------------------------------------------
AoDev enTrack   bMute  Volume
    0       0       N       0

-----AO CHN STATUS--------------------------------------------------------------
AoDev   AoChn   State    Read   Write      BufEmp  u32Data0  u32Data1  bResmp  PoiNum InSampR  OutSampR
    0       0  enable       0       0      229679         0         0       N       0  (null)    (null)

-----AO CHN VQE STATUS0---------------------------------------------------------
AoDev AoChn   State bVqe workmod    RATE  PoiNum bAnr bAgc  bEq bHpf  WrFile
    0     0  enable    N    comm  (null)       0    N    N    N    N       N

[CHNL] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:14]


Total Chnl Scheduler Count: 2 

-----SCHEDULER 0 INFO----------------------------------------------------------
   SchdlId    VpuNum
         0         1

-----VPU INFO------------------------------------------------------------------
   VpuId    Name   State      IntCnt     TimeCnt      VpuCnt  ErrCnt      InqCnt     StartOk     StartNo      Config   Reset
       0  VEDU_0   PAUSE     1148579      872971      275608       0     2572475      275608           0      275608       0

-----CHNL STATE----------------------------------------------------------------
  ChnlId    Prio    Type  TskNum   State      InqCnt     StartOk     StartNo      IntPro
       0       0  H264E        0    IDLE     1286242      137804           0      137804
       2       0  H264E        0    IDLE     1286233      137804           0      137804

-----CHNL PERF-----------------------------------------------------------------
  ChnlId        Type   StartCost     IntCost    IntCostL      HWCost     HWCycle     HWCostL   HWCostAcc
       0      H264E            0           0           0           0           0           0           0
       2      H264E            0           0           0           0           0           0           0

-----CHNL CURRENT RUN STATE----------------------------------------------------
   VpuId     VpuName      ChnlId        Type
  No running channel here

-----SCHEDULER 1 INFO----------------------------------------------------------
   SchdlId    VpuNum
         1         1

-----VPU INFO------------------------------------------------------------------
   VpuId    Name   State      IntCnt     TimeCnt      VpuCnt  ErrCnt      InqCnt     StartOk     StartNo      Config   Reset
       0  JPGE_0   PAUSE      918909      918909           0       0      918757           0           0           0       0

-----CHNL STATE----------------------------------------------------------------
  ChnlId    Prio    Type  TskNum   State      InqCnt     StartOk     StartNo      IntPro
       1       0  JPEGE        0    IDLE      918757           0           0           0

-----CHNL PERF-----------------------------------------------------------------
  ChnlId        Type   StartCost     IntCost    IntCostL      HWCost     HWCycle     HWCostL   HWCostAcc
       1      JPEGE            0           0           0           0           0           0           0

-----CHNL CURRENT RUN STATE----------------------------------------------------
   VpuId     VpuName      ChnlId        Type
  No running channel here


[H264E] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:14]

-----MODULE PARAM--------------------------------------------------------------
      OnePack   H264eVBSource      PowerSaveEn     MiniBufMode     bQpHstgrmEn
            0               2                1               0               0
-----CHN ATTR------------------------------------------------------------------
     ID  MaxWidth MaxHeight     Width    Height   profile   C2GEn   BufSize   ByFrame   GopMode   MaxStrCnt
      0      1280       720      1280       720      base       Y    691200         Y   NormalP         200
      2       640       480       640       480      base       Y    230400         Y   NormalP         200

-----PICTURE INFO--------------------------------------------------------------
     ID     EncdStart   EncdSucceed        Lost        Disc       Pskip      Recode      RlsStr     UnrdStr
      0        137804        137804           0           0           0           0      137804           0
      2        137804        137804           0           0           0           0      137804           0

-----STREAM BUFFER-------------------------------------------------------------
     ID     Base                  RdTail      RdHead      WrTail      WrHead      DataLen     BufFree     
      0     0xc4000000            0x8c340     0x8c340     0x8c340     0x8c340     0           692160      

      2     0xc40c0000            0x1bdc0     0x1bdc0     0x1bdc0     0x1bdc0     0           233408      

-----RefParam INFO--------------------------------------------------------------
     ID      EnPred        Base     Enhance    RcnRefShareBuf
      0           Y           1           0                 Y
      2           Y           1           0                 Y

-----ROIBG INFO------------------------------------------------------------------
     ID   BgSrcFr   BgTarFr
      0        -1        -1
      2        -1        -1

-----Syntax INFO1--------------------------------------------------------------
     ID SlcspltEn   Slcsize   IntraRefresh    RefreshMode     RefreshNum   QpOfIDR
      0         N       N/A              N            N/A            N/A       N/A
      2         N       N/A              N            N/A            N/A       N/A

-----Syntax INFO2--------------------------------------------------------------
     ID   profile   EntrpyI   EntrpyP   EntrpyB  Itrans  Ptrans QMatrix   POC   DblkIdc   alpha    beta
      0      base     cavlc     cavlc     cavlc     4x4     4x4       N     0         0       0       0
      2      base     cavlc     cavlc     cavlc     4x4     4x4       N     0         0       0       0

-----Foreground && Scene INFO-------------------------------------------------------------
     ID  ForegroundSkipCoef  BackgroundSkipCoef SceneMode
      0                   8                   8   Scene_0
      2                   8                   8   Scene_0

-----CuPrediction-------------------------------------------------------------------
     ID  PredMode     Inter8Cost    Inter16Cost     Intra4Cost     Intra8Cost    Intra16Cost 
      0      AUTO              8              8              8              8              8
      2      AUTO              8              8              8              8              8

-----SkipBias-------------------------------------------------------------------
     ID     SkipBiasEn      Gain    Offset      ForegroundCost      BackgroundCost
      0              N         8         8                   0                   0
      2              N         8         8                   0                   0


[H265E] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:14]

-----MODULE PARAM--------------------------------------------------------------
      OnePack      H265eVBSource        PowerSaveEn        MiniBufMode       bQpHstgrmEn
            0                  2                  1                  0                 0
-----CHN ATTR------------------------------------------------------------------
     ID  MaxWidth MaxHeight     Width    Height   Profile   C2GEn   BufSize   ByFrame   GopMode   MaxStrCnt

-----PICTURE INFO--------------------------------------------------------------
     ID     EncdStart   EncdSucceed        Lost        Disc       Pskip      Recode      RlsStr     UnrdStr

-----STREAM BUFFER-------------------------------------------------------------
ID     Base                  RdTail      RdHead      WrTail      WrHead      DataLen     BufFree     
-----RefParam INFO-------------------------------------------------------------
     ID      EnPred        Base     Enhance         UsedFrame      MaxUsedFrame    RcnRefShareBuf

-----ROIBG INFO------------------------------------------------------------------
     ID   BgSrcFr   BgTarFr

-----Syntax INFO1--------------------------------------------------------------
     ID SlcspltEn   Slcsize   IntraRefresh    RefreshMode     RefreshNum   QpOfIDR

-----Syntax INFO2--------------------------------------------------------------
     ID    DblkEn      Tc    Beta   Saoluma Saochroma  EntrpyFlag

-----Syntax INFO3--------------------------------------------------------------
     ID  TimInfFlag   NumInTick    TimeScal     DiffOne

-----Pu INFO-------------------------------------------------------------------
     ID   ConsIntra IntraSmoothing

-----Trans INFO----------------------------------------------------------------
     ID  CbQpOffset  CrQpOffset

-----Foreground && Scene INFO--------------------------------------------------------------
     ID  ForegroundSkipCoef  BackgroundSkipCoef SceneMode

-----CuPrediction-------------------------------------------------------------------
     ID  PredMode  Inter8Cost Inter16Cost Inter32Cost Inter64Cost  Intra4Cost  Intra8Cost Intra16Cost Intra32Cost

-----SkipBias-------------------------------------------------------------------
     ID     SkipBiasEn      Gain    Offset      ForegroundCost      BackgroundCost


[ISP] Version: [Hi3516EV200_ISP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:14]


------------------------------------------------------------------------------
------------------------------ ISP PROC PIPE[0] -----------------------------
------------------------------------------------------------------------------

-----MODULE/CONTROL PARAM-----------------------------------------------------
    ProcParam    StatIntvl    UpdatePos   IntBothalf   IntTimeout    PwmNumber   PortIntDelay   QuickStart LdciTprFltEn
           30            1            0            0          200            3              0            0            0

-----ISP Mode------------------------------------------------------------------
      StitchMode     RunningMode
          NORMAL          ONLINE

-----DRV INFO-------------------------------------------------------------------
     ViPipe     IntCnt       IntT    MaxIntT    IntGapT    MaxGapT   IntRat IspResetCnt  IspBeStaLost
          0     137822        228       2404      66663      66876       15           1             0

    IntTpye   PtIntCnt     PtIntT  PtMaxIntT  PtIntGapT  PtMaxGapT PtIntRat SensorCfgT  SensorMaxT
      Start          0          0          0          0          0        0          4        2178

-----PubAttr INFO--------------------------------------------------------------
        WndX        WndY        WndW        WndH        SnsW        SnsH       Bayer
           0           0        1280         720        1280         720        BGGR


-----SNAPATTR INFO-----------------------------------------------------------------
    SnapType    PipeMode      OPType   ProFrmNum
      NORMAL        NONE        Auto           3


[AE] Version: [Hi3516EV200_ISP_V1.0.1.0 B050 Release], Build Time[May  9 2019, 22:51:52]
-----AE INFO-------------------------------------------------------------------
      Again      Dgain      IspDg    SysGain        Iso       Line   AEInter   Incrmnt                 Exp   1stTime
       1024       1088       1080       1126        112       1496         1       256             1686462   1000000

       Comp     EVbias     OriAve     Offset      Speed       Tole     Error       Fps   RealFps    BDelay    WDelay
         68       1024         70          0         64          2        -2     15.00      1500         5         0

    MaxLine   MaxLineT     MaxAgT     MaxDgT    MaxIDgT     MaxSgT    ManuEn    MaLine      MaAg      MaDg   MaIspDg
       1496       1890     129024       1984       2048     203840         0         0         0         0         0

    WdrMode  ExpRatio0  ExpRatio1  ExpRatio2    AnFlick    SlowMod     GainTh
       LINE         64         64         64          0          1     499968

     NodeId    IntTime    SysGain    IrisApe     UpStgy     DwStgy              Mltply
          0          2       1024          1          0          4                2048
          1       1496       1024          1          1          0             1531904
          2       1496     203840          1          4          1           304944640

   NodeIdSF  IntTimeSF  SysGainSF  IrisApeSF   UpStgySF   DwStgySF            MltplySF
          0          2       1024          1          0          4                2048
          1        710       1024          1          1          0              727040
          2        710     499968          1          4          1           354977280

     AuIrEn     IrType     MaIrEn    DbgIrSt
          0     DCIris          0          0



[AWB] Version: [Hi3516EV200_ISP_V1.0.1.0 B050 Release], Build Time[May  9 2019, 22:51:55]
-----AWB INFO------------------------------------------------------------------
   Gain0   Gain1   Gain2   Gain3  CoTemp
   0x19b   0x100   0x100   0x1e0    5681

 Color00 Color01 Color02 Color10 Color11 Color12 Color20 Color21 Color22
  0x 1ae  0x80ef  0x  41  0x8026  0x 170  0x804a  0x   4  0x805f  0x 15b

  ManuEn     Sat   Zones   Speed
       0      86      32     256

-----DEFECT INFO-----------------------------------
      Enable    Strength  BlendRatio
           1         150          90

-----GE INFO-------------------------------------------------------------
      Enable  Threshold1  Threshold3    Strength
           1       16384        4800         128

-----FrameWDR INFO------------------------------------------------------------------
       MdtEn   LongThr  ShortThr  MdThrLow  MdThrHig
           1      3008      4032         0         0

-----Black Level Actual INFO--------------------------------------------------------------
            BlcR           BlcGr           BlcGb            BlcB
              64              64              64              64

-----BAYERNR INFO----------------------------------------------------------------------------
          Enable     NrLscEnable      CoarseStr0      CoarseStr1      CoarseStr2      CoarseStr3
               1               0             110             110             110             110

-----DRC INFO------------------------------------------------------------------
              En          ManuEn        Strength
               1               1             360

-----Lcac INFO-----------------------------------
      Enable       CrCtr       CbCtr
           1           0           3

-----DEMOSAIC INFO-------------------------------------------------------------
      Enable  NoDirStr  NoDirMFStr  NoDirHFStr DeSmthRng
           1        64          32           3         1

-----AntiFalseColor INFO-------------------------------------------------------------
      Enable   Threshold    Strength
           1          10           8

-----CA INFO-----------------------------------
      Enable    isoRatio
           1        1300

-----FPN CORRECT INFO------------------------------------------------------------
      En OpType Strength Offset
       0  --       --      --

-----SHARPEN INFO--------------------------------------------------------------
      bSharpenEn
               1
LumaWgt 0--7:
      31      31      31      31      31      31      31      31

LumaWgt 8--15:
      31      31      31      31      31      31      31      31

LumaWgt 16--23:
      31      31      31      31      31      31      31      31

LumaWgt 24--31:
      31      31      31      31      31      31      31      31

TextureStr 0--7:
     420     420     390     390     360     360     360     350

TextureStr 8--15:
     350     290     290     290     270     270     270     270

TextureStr 16--23:
     270     270     266     260     260     260     260     260

TextureStr 24--31:
     260     230     230     210     210     210     200     200

EdgeStr 0--7:
     125     128     146     160     175     175     175     175

EdgeStr 8--15:
     160     160     160     160     160     210     210     210

EdgeStr 16--23:
     210     210     200     190     185     175     165     160

EdgeStr 24--31:
     160     160     160     160     160     160     160     160

 TextureFreq    EdgeFreq   OverShoot  UnderShoot ShootSupStr  DetailCtrl EdgeFiltStrEdgeFiltMaxCap       RGain       GGain       BGain    SkinGain 
         160         100          54          74           0         128          63           0          24          32          24          24

 ShootSupAdj DetailCtrlThr  MaxSharpGain    SkinUmax    SkinUmin    SkinVmax    SkinVmin  WeakDetailGain
           0           160            60         128         110         149         128               0


-----LDCI INFO------------------------------------------------------------------------------
      Enable      Manual   GaussLPFSigma    HePosWgt  HePosSigma   HePosMean    HeNegWgt  HeNegSigma   HeNegMean     BlcCtrl
           1           0              20          64          80           0          64          80           0          40

-----PreGamma INFO--------------------------------------------------------------
          Enable
               0

-----------------------------------------------------------------------------
----------------------------------- ISP PROC END[0] ------------------------
-----------------------------------------------------------------------------



[IVE] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:20]


-------------------------------MODULE PARAM--------------------------------------
      save_power     max_node_num
               0              512

-------------------------------IVE QUEUE INFO------------------------------------
    Wait      Busy   WaitCurId WaitEndId BusyCurId BusyEndId
      0        -1         0         0         0         0

--------------------------------IVE TASK INFO------------------------------------
       Hnd   TaskFsh    LastId    TaskId   HndWrap   FshWrap
    826888    826888         0         1         0         0

-----------------------------------IVE RUN-TIME INFO-----------------------------
  LastInst  CntPerSec MaxCntPerSec  TotalIntCntLastSec    TotalIntCnt     QTCnt STCnt
         1         75          113              689552         689598         0     0

    CostTm   MCostTm  CostTmPerSec MCostTmPerSec  TotalIntCostTm       RunTm
         5        47           690           872         6031300        9189

----------------------------------IVE INVOKE INFO--------------------------------

       DMA     Filter       CSC    FltCsc     Sobel    MagAng    Dilate     Erode
    138018          0         0         0         0         0         0         0

    Thresh        And       Sub        Or     Integ      Hist ThreshS16 ThreshU16
         0          0         0         0         0         0         0         0

     16to8 OrdStatFlt   BernSen       Map    EqualH       Add       Xor       NCC
         0          0         0         0         0    137774         0         0

       CCL        GMM     Canny       LBP  NormGrad        LK ShiTomasi    GradFg
    275548          0         0         0         0         0         0         0

  MatchMod  UpdateMod     Radon       ANN       SVM    AdpThr  LineFltH  NoiseRmH
         0          0         0         0         0         0         0         0

 PlateChar        SAD      GMM2    Resize       CNN PerspTrans       KCF       HOG
         0     275548         0         0         0          0         0         0 

       XNN
         0 

----------------------------------IVE UTILI INFO--------------------------------

  Utili  
    0

[IVP] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:20]


-------------------------------IVP ATTR---------------------------------------------------------------
      HDL.                   W                   H           Threshold                    LowBitrate                    AdvanceIsp            CostTime           Framerate

[JPEGE] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:14]


-----MODULE PARAM--------------------------------------------------------------
        OnePack     JpegeMiniBufMode   JpegClearStreamBuf
              0                    0                    1

-----ATTRIBUTE1----------------------------------------------------------------
ID    bMjpeg   PicType  MaxWidth   MaxHeight   Width  Height     BufSize   ByFrm     MCU   Qfactor   C2GEn   DcfEn
1          N    YUV420      1280         720    1280     720      921600       Y       0        90       N       N

-----STATUS1-------------------------------------------------------------------
ID         BufLen         FreeLen         StrmCnt         MaxStrm       
 1         921600          921536               0             200       

-----STATUS2-------------------------------------------------------------------
ID    PicRec    PicCoded    PicDroped    PicDisc    NoStmCnt    RcFail    PicRecode    UnrdStr      
1     0         0           0            0          0           0         0            0            

-----STREAM BUFFER-------------------------------------------------------------
ID  Base                RdTail      RdHead      WrTail      WrHead      BufLen      DataLen     BufFree     
1   0xc4100000            0           0           0           0           921600      0           921536      


-----RUN INFO----------------------------------------------------------------
ID         DCFSize      MpfExOffset        SrcSize        Mpf0Size        Mpf1Size          MpfCnt        JpegQueueIdx  
1                0               0               0               0               0               0                   0  
-----LOG BUFFER STATE----------------------------------------------------------
MaxLen  ReadPos WritePos ButtPos
 64(KB)       0     6581   65536

-----CURRENT LOG LEVEL---------------------------------------------------------
vb      :  3
sys     :  3
region  :  3
chnl    :  3
vpss    :  3
venc    :  3
h264e   :  3
jpege   :  3
h265e   :  3
vi      :  3
rc      :  3
aio     :  3
ai      :  3
ao      :  3
vpu     :  3
isp     :  3
ive     :  3
vgs     :  3

[MD] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:20]


-------------------------------MD CHN ATTR-------------------------------------------------------------
NO.    W    H   Alg   SadMode  SadOutCtrl        SadT   CclMode  CclInitT CclStep     XWt     YWt   FrmRate   CostTmPerFrm
  0  640  360     0         0           4        1000         0        16       4   32768   32768        15          19842

Module: [MIPI_RX], Build Time[Jun 17 2019, 11:19:14]

[RC] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release],Build Time[Jun 17 2019, 11:19:14]


------BASE PARAMS 1------------------------------------------------------------
  ChnId    Gop  StatTm  ViFr       TrgFr ProType  RcMode  Br(kbps)  FluLev  IQp  PQp  BQp 
      0     30       1    30          30      96     VBR      4352     N/A  N/A  N/A  N/A
      2     30       1    30          30      96     VBR      1280     N/A  N/A  N/A  N/A

------BASE PARAMS 2------------------------------------------------------------
  ChnId   MinQp   MaxQp  MinIQp  MaxIQp   EnableIdr    bQpMapEn   QpMapMode 
      0      24      51      24      51           Y           N         N/A
      2      24      51      24      51           Y           N         N/A

------BASE PARAMS 3------------------------------------------------------------
  ChnId    LongTermStatTime   ShortTermStatTime  LongTermMaxBitrate  LongTermMinBitrate 

-----RUN COMM PARAM 1----------------------------------------------------------
  ChnId  RowQpDelta                       ThrdI(16)
      0           1  [   0   0   0   0   3   3   5   5   8   8   8  15  15  20  25  25]
      2           1  [   0   0   0   0   3   3   5   5   8   8   8  15  15  20  25  25]

-----RUN COMM PARAM 2------------------------------------------------------------
  ChnId  FirstFrmStartQP                  ThrdP(16)
      0          -1  [   0   0   0   0   3   3   5   5   8   8   8  15  15  20  25  25]
      2          -1  [   0   0   0   0   3   3   5   5   8   8   8  15  15  20  25  25]

-----RUN COMM PARAM 3----------------------------------------------------------
  ChnId  DirectionThrd                       ThrdB(16)
      0           8  [   0   0   0   0   3   3   5   5   8   8   8  15  15  20  25  25]
      2           8  [   0   0   0   0   3   3   5   5   8   8   8  15  15  20  25  25]

-----RUN COMM PARAM 4----------------------------------------------------------
  ChnId   bLost     LostThr  LostFrmStr    EncGap  RCPriority   SprFrmMod     SprIFrm     SprPFrm     SprBFrm    bClrStat
      0       N    83886080      NORMAl         0     BITRATE        None      500000      500000      500000           1
      2       N    83886080      NORMAl         0     BITRATE        None      500000      500000      500000           1

-----RUN COMM PARAM 5----------------------------------------------------------
  ChnId       bDetectSceneChange        bAdapInsertIFrame
      0                        Y                        N
      2                        Y                        N

-----Foreground INFO 1----------------------------------------------------------
  ChnId     bThrdEn  DirectionThrd                          ThrdP(16)
      0           0           8  [   0   0   0   0   3   3   5   5   8   8   8  15  20  20  25  25]
      2           0           8  [   0   0   0   0   3   3   5   5   8   8   8  15  20  20  25  25]

-----Foreground INFO 2----------------------------------------------------------
  ChnId  ThreshGain   ThreshOffset                          ThrdB(16)
      0           8           8  [   0   0   0   0   3   3   5   5   8   8   8  15  20  20  25  25]
      2           8           8  [   0   0   0   0   3   3   5   5   8   8   8  15  20  20  25  25]

-----GOP MODE ATTR-------------------------------------------------------------
  ChnId   GopMode IpQpDelta  SPInterval SPQpDelta   BFrmNum  BQpDelta  BgInterval ViQpDelta
      0   NormalP         2         N/A       N/A       N/A       N/A         N/A       N/A
      2   NormalP         2         N/A       N/A       N/A       N/A         N/A       N/A

-----RUN CBR PARAM ------------------------------------------------------------
  ChnId  MinIprop  MaxIprop   MaxQp   MinQp  MaxIQp  MinIQp  MaxReEncTimes

-----RUN VBR COMM PARAM ------------------------------------------------------------
  ChnId   ChgPs  MinIprop  MaxIprop   MaxQp   MinQp  MaxIQp  MinIQp  MaxReEncTimes
      0      90         1        20      51      24      51      24              0
      2      90         1        20      51      24      51      24              0

-----RUN AVBR PARAM ------------------------------------------------------------
  ChnId     MaxStillQP    MotionSensi     MinPercent   MinStillPSNR     MinQpDelta

-----RUN QVBR PARAM ------------------------------------------------------------
  ChnId   BitPercentLL   BitPercentUL   PsnrFluctuateLL   PsnrFluctuateUL

-----RUN CVBR PARAM ------------------------------------------------------------
  ChnId     MinQpDelta     MaxQpDelta        ExBitPercent     LongTermStatTimeUnit

-----RUN INFO1-----------------------------------------------------------------
  ChnId   InsBr(kbps)   InsFr    WatL   CfgBt(kb)  RealBt(kb)   IPRatio  TarPercent   StartQp   MinQp   MaxQp
      0          1144      30       0         116          22         4         N/A        24      24      51
      2           224      30       0          30           4         8         N/A        24      24      51

-----RC DeBreathEffect INFO-----------------------------------------------------------------
  ChnId   bEnable Strength0 Strength1     DeBrthEfctCnt
      0         N       N/A       N/A                 0
      2         N       N/A       N/A                 0

-----RC HierarchicalQp INFO-----------------------------------------------------------------
  ChnId   bEnable FrameNum[0] FrameNum[1] FrameNum[2] FrameNum[3]  QpDelta[0]  QpDelta[1]  QpDelta[2]  QpDelta[3]
      0         N           1           1           0           0          -2          -4           0           0
      2         N           1           1           0           0          -2          -4           0           0

-----RC PERFORMANCE  INFO------------------------------------------------------
  ChnId       StaOfstaTim      TotaOfstaTim       StaOfEndTim      TotaOfEndTim         TotalTime
      0        9193099176          11245329        9193108756           1532153          12777482
      2        9193108850           8487585        9193112242           1463802           9951387

[RGN] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:14]


-----REGION STATUS OF OVERLAY------------------------------------------------------------
 Hdl     Type     Used    PiFmt        W        H  BgColor              Phy             Virt   Stride
   0        0        N        8      176       64       40         438b2000         c45c0000      352
   2        0        N        8      176       64       40         438d3000         c4600000      352

-----REGION STATUS OF OVERLAY BUF USED---------------------------------------------------
 Hdl     Type  CnvsNum     buf0     buf1     buf2     buf3     buf4     buf5
   0        0        6        0        0        0        0        0        0
   2        0        6        0        0        0        0        0        0

-----REGION CALL VGS STATUS OF OVERLAY---------------------------------------------------
 Hdl     CallCnt      JobSuc     JobFail     TaskSuc    TaskFail      EndSuc     EndFail
   0           0           0           0           0           0           0           0
   2           0           0           0           0           0           0           0

-----REGION CHN STATUS OF OVERLAY--------------------------------------------------------
 Hdl  Type   Mod   Dev   Chn   bBatch   AttachDest   bSh     X     Y  AphF  AphB  Layer  bAQp    QP  bQpDis   ColorLUT0   ColorLUT1
   0     0  VENC     0     0        N         MAIN     Y    16   656   127     0      0     N     0       N           0           0
   2     0  VENC     0     2        N         MAIN     Y    16   416   127     0      0     N     0       N           0           0


[SVP_ALG] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:20]


-----------------------------SVP ALG MODEL INFO--------------------------------------------------------
       NO.   FrmRate   CostTmPerFrm

[SYS] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:14]


-----MODULE STATUS--------------------------------------------------------------
  Status
     run

-----SCALE COEFF INFO-----------------------------------------------------------
            RangeLevel   RangeValue    HorLum    HorChr    VerLum    VerChr
           RANGE_0   (    0,  8/64)   LEVEL_0   LEVEL_0   LEVEL_0   LEVEL_0
           RANGE_1   [ 8/64, 10/64)   LEVEL_1   LEVEL_1   LEVEL_1   LEVEL_1
           RANGE_2   [10/64, 15/64)   LEVEL_2   LEVEL_2   LEVEL_2   LEVEL_2
           RANGE_3   [15/64, 19/64)   LEVEL_3   LEVEL_3   LEVEL_3   LEVEL_3
           RANGE_4   [19/64, 24/64)   LEVEL_4   LEVEL_4   LEVEL_4   LEVEL_4
           RANGE_5   [24/64, 29/64)   LEVEL_5   LEVEL_5   LEVEL_5   LEVEL_5
           RANGE_6   [29/64, 33/64)   LEVEL_6   LEVEL_6   LEVEL_6   LEVEL_6
           RANGE_7   [33/64, 35/64)   LEVEL_7   LEVEL_7   LEVEL_7   LEVEL_7
           RANGE_8   [35/64, 38/64)   LEVEL_8   LEVEL_8   LEVEL_8   LEVEL_8
           RANGE_9   [38/64, 42/64)   LEVEL_9   LEVEL_9   LEVEL_9   LEVEL_9
           RANGE_10  [42/64, 45/64)  LEVEL_10  LEVEL_10  LEVEL_10  LEVEL_10
           RANGE_11  [45/64, 48/64)  LEVEL_11  LEVEL_11  LEVEL_11  LEVEL_11
           RANGE_12  [48/64, 51/64)  LEVEL_12  LEVEL_12  LEVEL_12  LEVEL_12
           RANGE_13  [51/64, 53/64)  LEVEL_13  LEVEL_13  LEVEL_13  LEVEL_13
           RANGE_14  [53/64, 55/64)  LEVEL_14  LEVEL_14  LEVEL_14  LEVEL_14
           RANGE_15  [55/64, 57/64)  LEVEL_15  LEVEL_15  LEVEL_15  LEVEL_15
           RANGE_16  [57/64, 60/64)  LEVEL_16  LEVEL_16  LEVEL_16  LEVEL_16
           RANGE_17  [60/64,     1]  LEVEL_17  LEVEL_17  LEVEL_17  LEVEL_17
           RANGE_18  (    1,   MAX)  LEVEL_18  LEVEL_18  LEVEL_18  LEVEL_18

-----MEM TABLE------------------------------------------------------------------
     Mod         ModName     Dev     Chn         MmzName

-----BIND RELATION TABLE--------------------------------------------------------
  FirMod  FirDev  FirChn  SecMod  SecDev  SecChn  TirMod  TirDev  TirChn    SendCnt     rstCnt
    vpss       0       0    venc       0       0    null       0       0     137805          0
    vpss       0       0    venc       0       1    null       0       0     137804          0
    vpss       0       1    venc       0       2    null       0       0          0          0
      vi       0       0    vpss       0       0    venc       0       0     137805          0
      vi       0       0    vpss       0       0    venc       0       1     137805          0
      vi       0       0    vpss       0       1    venc       0       2     137805          0

[VB] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:14]

-----VB PUB CONFIG--------------------------------------------------------------
MaxPoolCnt
       512
-----VB SUPPLEMENT ATTR---------------------------------------------------------
  Config    Size   VbCnt
       0       0      74
-----COMMON POOL CONFIG---------------------------------------------------------
PoolId         0         1         2         3         4         5         6         7         8         9        10        11        12        13        14        15
Size     1382400    307200    460800         0         0         0         0         0         0         0         0         0         0         0         0         0
Count          3         1         2         0         0         0         0         0         0         0         0         0         0         0         0         0

--------------------------------------------------------------------------------
PoolId  PhysAddr            VirtAddr            IsComm  Owner  BlkSz     BlkCnt  Free    MinFree 
0       0x42d91000          0x0                 1       -1     1382400   3       1       0       
BLK   VI    VO    VGS   VENC  VDEC  H265E H264E JPEGE H264D JPEGD VPSS  DIS   USER  PCIV  AI    AENC  RC    VFMW  GDC   AVS   RECT  MATCH MCF   
2     1     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     
0     1     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     
Sum   2     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     

--------------------------------------------------------------------------------
PoolId  PhysAddr            VirtAddr            IsComm  Owner  BlkSz     BlkCnt  Free    MinFree 
1       0x43187000          0x0                 1       -1     307200    1       0       0       
BLK   VI    VO    VGS   VENC  VDEC  H265E H264E JPEGE H264D JPEGD VPSS  DIS   USER  PCIV  AI    AENC  RC    VFMW  GDC   AVS   RECT  MATCH MCF   
0     0     0     0     0     0     0     0     0     0     0     1     0     0     0     0     0     0     0     0     0     0     0     0     
Sum   0     0     0     0     0     0     0     0     0     0     1     0     0     0     0     0     0     0     0     0     0     0     0     

--------------------------------------------------------------------------------
PoolId  PhysAddr            VirtAddr            IsComm  Owner  BlkSz     BlkCnt  Free    MinFree 
2       0x431d3000          0x0                 1       -1     460800    2       2       0       

--------------------------------------------------------------------------------
PoolId  PhysAddr            VirtAddr            IsComm  Owner  BlkSz     BlkCnt  Free    MinFree 
3       0x434ab000          0x0                 0       -2     768       1       1       0       

--------------------------------------------------------------------------------
PoolId  PhysAddr            VirtAddr            IsComm  Owner  BlkSz     BlkCnt  Free    MinFree 
4       0x434ac000          0x0                 0       -2     768       1       0       0       
BLK   VI    VO    VGS   VENC  VDEC  H265E H264E JPEGE H264D JPEGD VPSS  DIS   USER  PCIV  AI    AENC  RC    VFMW  GDC   AVS   RECT  MATCH MCF   
0     0     0     0     0     0     0     1     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     
Sum   0     0     0     0     0     0     1     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     

--------------------------------------------------------------------------------
PoolId  PhysAddr            VirtAddr            IsComm  Owner  BlkSz     BlkCnt  Free    MinFree 
5       0x434ad000          0x0                 0       -2     1640448   1       0       0       
BLK   VI    VO    VGS   VENC  VDEC  H265E H264E JPEGE H264D JPEGD VPSS  DIS   USER  PCIV  AI    AENC  RC    VFMW  GDC   AVS   RECT  MATCH MCF   
0     0     0     0     0     0     0     1     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     
Sum   0     0     0     0     0     0     1     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     

--------------------------------------------------------------------------------
PoolId  PhysAddr            VirtAddr            IsComm  Owner  BlkSz     BlkCnt  Free    MinFree 
6       0x43760000          0x0                 0       -2     256       1       1       0       

--------------------------------------------------------------------------------
PoolId  PhysAddr            VirtAddr            IsComm  Owner  BlkSz     BlkCnt  Free    MinFree 
7       0x43761000          0x0                 0       -2     256       1       0       0       
BLK   VI    VO    VGS   VENC  VDEC  H265E H264E JPEGE H264D JPEGD VPSS  DIS   USER  PCIV  AI    AENC  RC    VFMW  GDC   AVS   RECT  MATCH MCF   
0     0     0     0     0     0     0     1     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     
Sum   0     0     0     0     0     0     1     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     

--------------------------------------------------------------------------------
PoolId  PhysAddr            VirtAddr            IsComm  Owner  BlkSz     BlkCnt  Free    MinFree 
8       0x43762000          0x0                 0       -2     578816    1       0       0       
BLK   VI    VO    VGS   VENC  VDEC  H265E H264E JPEGE H264D JPEGD VPSS  DIS   USER  PCIV  AI    AENC  RC    VFMW  GDC   AVS   RECT  MATCH MCF   
0     0     0     0     0     0     0     1     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     
Sum   0     0     0     0     0     0     1     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     

--------------------------------------------------------------------------------
PoolId  PhysAddr            VirtAddr            IsComm  Owner  BlkSz     BlkCnt  Free    MinFree 
9       0x437f1000          0xc43c0000          0       -2     4096      62      62      60      


[VENC] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:15]

-----MODULE PARAM--------------------------------------------------------------
    VencBufferCache   FrameBufRecycle     VencMaxChnNum
                  0                 0                16


-----VENC CHN ATTR 1-----------------------------------------------------------
      ID   Width  Height  Type  ByFrame    Sequence   LeftBytes     LeftFrm  CurPacks   GopMode  Prio
       0    1280     720    96        Y      137804           0           0         1   NormalP     0
       1    1280     720    26        Y           0           0           0         0   NormalP     0
       2     640     480    96        Y      137804           0           0         1   NormalP     0

-----VENC CHN ATTR 2-----------------------------------------------------------
      ID   VeStr   SrcFr   TarFr     Timeref  PixFmt PicAddr      WakeUpFrmCnt
       0       Y      -1      -1      275674  YVU420  0x4318b3c0           1
       1       N      -1      -1           1      NA  0x       0           1
       2       Y      -1      -1      275674  YVU420  0x431d3000           1

-----VENC JPEGE ATTR -----------------------------------------------------------
      ID   RcvMode    MpfCnt      Mpf0Width     Mpf0Height      Mpf1Width     Mpf1Height
       1    Single         0              0              0              8              0


-----VENC CHN RECEIVE STAT-----------------------------------------------------
      ID       Start     StartEx    RecvLeft     EncLeft    JpegEncodeMode
       0           1           0           0           0                NA
       1           0           0           0           0               ALL
       2           1           0           0           0                NA

-----VENC VPSS QUERY-----------------------------------------------------------
      ID       Query     QueryOk     QueryFR       Invld        Full      VbFail   QueryFail     InfoErr        Stop
       0           0           0           0           0           0           0           0           0           0
       1           0           0           0           0           0           0           0           0           0
       2           0           0           0           0           0           0           0           0           0

-----VENC SEND1----------------------------------------------------------------
      ID     VpssSnd     VInfErr     OthrSnd     OInfErr        Send        Stop        Full     CropErr    DrectSnd     SizeErr
       0           0           0      137805           0      137805           0           0           0      137805           0
       1           0           0      137804           0           0      137804           0           0           0           0
       2      137804           0           0           0      137804           0           0           0      137804           0

-----VENC SEND2----------------------------------------------------------------
      ID     SendVgs     StartOk   StartFail       IntOk     IntFail      SrcAdd      SrcSub     DestAdd     DestSub
       0           0           0           0           0           0           0           0           0           0
       1           0           0           0           0           0           0           0           0           0
       2           0           0           0           0           0           0           0           0           0

-----VENC PIC QUEUE STATE------------------------------------------------------
      ID    Free    Busy     Vgs  BFrame
       0       6       0       0       0
       1       6       0       0       0
       2       6       0       0       0

-----VENC DCF/MPF QUEUE STATE------------------------------------------------------
      ID   ThumbFree   ThumbBusy    Mpf0Free    Mpf0Busy    Mpf1Free    Mpf1Busy
       0           0           0           6           0           6           0
       1           0           0           6           0           6           0
       2           0           0           6           0           6           0

-----VENC CHNL INFO------------------------------------------------------------
      ID         Inq       InqOk       Start     StartOk      Config     VencInt  ChaResLost    OverLoad    RingSkip      RcSkip
       0     1148442      137804      137804      137804      137804      137804           0           0           1           0 
       1      918761           0           0           0           0           0           0           0           0           0 
       2     1148433      137804      137804      137804      137804      137804           0           0           0           0 

-----VENC CROP INFO------------------------------------------------------------
      ID  CropEn  StartX  StartY   Width  Height
       0       N       0       0       0       0
       1       N       0       0       0       0
       2       N       0       0       0       0


-----ROI INFO------------------------------------------------------------------
     ID      Type     Index    bRoiEn    bAbsQp    Qp     Width    Height    StartX    StartY 


-----VENC STREAM STATE---------------------------------------------------------
      ID     FreeCnt     BusyCnt     UserCnt     UserGet     UserRls    GetTimes    Interval   FrameRate
       0           1           0           0      151589      151589      137804       66664          15
       1           0           0           0           0           0           0           0           0
       2           1           0           0      151589      151589      137804       66691          15


-----VENC PTS STATE---------------------------------------------------------
      ID RcvFirstFrmPts    RcvFrmPts 
       0       5532413    9193099110
       1             0             0
       2       5576823    9193108618


[VGS] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release],                    Build Time[Jun 17 2019, 11:19:14]


-----MODULE PARAM--------------------------------------------------------
    max_job_num   max_task_num   max_node_num bVgsHdrSupport  bVgsExitInSys
            128            200            200              0              1

-----RECENT JOB INFO1----------------------------------------------------
   SeqNo ModName  JobHdl TaskNum   State      InSize     OutSize    CostTime      HwTime

-----RECENT JOB INFO2----------------------------------------------------
   SeqNo    CmpMode CropEn CoverEn VhdrEn OsdEn ZmeEn LBAEn LumaEn FpdEn QuickCopyEn RotateEn StitchEn ByPassEn

-----MAX WASTE TIME JOB INFO1--------------------------------------------
   SeqNo ModName  JobHdl TaskNum   State      InSize     OutSize    CostTime      HwTime

-----MAX WASTE TIME JOB INFO2--------------------------------------------
   SeqNo    CmpMode CropEn CoverEn VhdrEn OsdEn ZmeEn LBAEn LumaEn FpdEn QuickCopyEn RotateEn StitchEn ByPassEn

-----VGS JOB STATUS------------------------------------------------------
   Success      Fail    Cancel  AllJobNum    FreeNum   BeginNum    BusyNum ProcingNum
         0         0         0        128        128          0          0          0

-----VGS TASK STATUS-----------------------------------------------------
   Success      Fail    Cancel AllTaskNum    FreeNum    BusyNum
         0         0         0        200        200          0

-----VGS NODE STATUS-----------------------------------------------------
   AllNodeNum     BusyNum     MinFree    MaxInJob  SubmitFail   IntFail
          200           0         200           0           0         0

[VI] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:14]


-------------------------------MODULE PARAM ---------------------------------------------------------------------------
      DetectErrFrame        DropErrFrame            VbSource
                   0                   0              Common

-------------------------------VI MODE -------------------------------------------------------------
  Pipe0Mode   Pipe1Mode
     online     offline
-------------------------------VPSS MODE -------------------------------------------------------------
  Pipe0Mode   Pipe1Mode
    offline     offline

-------------------------------VI DEV ATTR1----------------------------------------------------------------------------
  DevID   DevEn  BindPipe     Width    Height               IntfM     WkM     ComMsk0     ComMsk1   ScanM
      0       Y         Y      1280       720                  DC    1Mux    ffc00000           0       P

-------------------------------VI DEV ATTR2----------------------------------------------------------------------------
  DevID   AD0   AD1   AD2   AD3     Seq  DataType   DataRev    BasW    BasH   HReph   VReph   WDRMode  CacheLine  DataRate
      0    -1    -1    -1    -1    YUYV       RGB         N    1280     720    NONE    NONE      None        720        X1

-------------------------------VI BIND ATTR----------------------------------------------------------------------------
   DevID PipeNum              PipeId
       0       1                   0

-------------------------------VI DEV TIMING ATTR----------------------------------------------------------------------
  DevID DevTimingEn  DevFrmRate  DevWidth   DevHeight

-------------------------------VI PIPE ATTR1---------------------------------------------------------------------------
  PipeID  BypassMode YuvSkip IspBypass     Width    Height    PixFmt  BitWidth    NrEn SharpenEn  CompressMode
       0  BypassNone       N         N      1280       720     RAW10        10       Y         N          None

-------------------------------VI PIPE ATTR2---------------------------------------------------------------------------
  DiscProPic    SrcFRate    DstFRate FrameSource  RepeatMode   VCNum     IntType EarlyLine  VbPoolId
           N          -1          -1         DEV        NONE       0       START       128        -1

-------------------------------VI PIPE CROP ATTR-----------------------------------------------------------------------
  PipeID CropEn    CoorX   CoorY   Width  Height

-------------------------------VI PIPE USER PIC ATTR-------------------------------------------------------------------
  PipeID  Enable   ChnID    Mode BgColor   PicID   Width  Height  Stride  PixFmt  PoolID         PhyAddr

-------------------------------VI PIPE DUMP ATTR-----------------------------------------------------------------------
  PipeID    Enable     Depth  DumpType

-------------------------------VI CHN ATTR1----------------------------------------------------------------------------
  PipeID   ChnID   Width    Height    Mirror    Flip    SrcFRate    DstFRate    PixFmt      VideoFmt  DynamicRange
       0       0    1280       720         N       N          -1          -1     SP420        LINEAR          SDR8

-------------------------------VI CHN ATTR2----------------------------------------------------------------------------
  CompressMode     Depth     Align  VbPoolId
          None         0         0        -1

-------------------------------VI EXTCHN ATTR1-------------------------------------------------------------------------
  PipeID   ChnID  Source  SrcChn   Width    Height    SrcFRate    DstFRate    PixFmt  DynamicRange  CompressMode     Depth

-------------------------------VI EXTCHN ATTR2-------------------------------------------------------------------------
  Align  VbPoolId

-------------------------------VI CHN CROP INFO------------------------------------------------------------------------
  PipeID   ChnID  CropEn  CoorType   CoorX   CoorY   Width  Height   TrimX   TrimY TrimWid TrimHgt
       0       0       N       RIT       0       0       0       0       0       0    1280     720

-------------------------------VI CHN ROTATION INFO--------------------------------------------------------------------
  PipeID   ChnID    Rotation
       0       0           0

-------------------------------VI CHN LDCV3 INFO-------------------------------------------------------------------------

-------------------------------ISP 2DofDIS INFO------------------------------------------------------------------------
  PipeID  Enable
       0       N

-------------------------------VI CHN OUTPUT RESOLUTION----------------------------------------------------------------
  PipeID   ChnID  Enable  Mirror    Flip   Width  Height  PixFmt  VideoFmt  DynamicRange  CompressMode FrameRate
       0       0       Y       N       N    1280     720   SP420    LINEAR          SDR8          None        15

-------------------------------VI PIPE STATUS--------------------------------------------------------------------------
  PipeID  Enable    IntCnt FrameRate LostFrame  VbFail   Width  Height
       0       Y    137838         0         0       0    1280     720

-------------------------------VI CHN STATUS---------------------------------------------------------------------------
  PipeID   ChnID  Enable FrameRate LostFrame  VbFail   Width  Height
       0       0       Y        15        31      16    1280     720

-------------------------------VI PIPE Statistic-----------------------------------------------------------------------
  PipeID     RecvPic     LostCnt      BufCnt   CurSoftTm   MaxSoftTm   CurTaskTm   MaxTaskTm   LowBandWidth  BeBufNum
       0           0           0           0           0           0           0           0              0         0

-------------------------------VI HW STATISTIC-------------------------------------------------------------------------
  ProcIdx    HWCostTm MaxHWCostTm    CycleCnt MaxCycleCnt
        0           0           0           0           0

-------------------------------VI PROC OFFLINE IRQ STATISTIC----------------------------------------------------------
 ProcIdx       SubmitCnt          IntCnt         ListCnt  TmOutCnt BusErrCnt  DcmpErrCnt StartErrCnt  NodeIdErrCnt
       0               0               0               0         0         0           0           0             0

-------------------------------VI PROC ONLINE IRQ STATISTIC-----------------------------------------------------------
 ProcIdx          IntCnt     FrmStartCnt FrmErrCnt  FrmFlowCnt BusErrCnt    DcmpErrCnt  CfgLossCnt   FirstIntPts
       0          137838          137838        15           0         0             0           0       4965070

-------------------------------VI PROC COST TIME STATISTIC-----------------------------------------------------------
 ProcIdx    IntCntPerSec MaxIntCntPerSec  CurIntCostTm  MaxIntCostTm  TotalIntCostTm   IntTmPerSec  MaxIntTmPerSec
       0              16              30           463           511        63819645          7367            7475

-------------------------------VI DEV DETECT INFO----------------------------------------------------------------------
   DevID  ValidWidth ValidHeight  TotalWidth
       0        1280         720        2399

-------------------------------VI BAS DETECT INFO----------------------------------------------------------------------
   DevID  ValidWidth ValidHeight  TotalWidth

-------------------------------VI ISP DETECT INFO----------------------------------------------------------------------
   ISPID  ValidWidth ValidHeight  TotalWidth
       0        1280         720        2399

[VPSS] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:14]


-------------------------------MODULE PARAM----------------------------------------------------------
u32VpssVbSource    bOneBufferforLowDelay    u32VpssSplitNodeNum    bHdrSupport    bNrQuickStart
              0                        0                      3              0                0

-------------------------------VPSS GRP ATTR---------------------------------------------------------
   GrpID    MaxW    MaxH      PixFmt    DRange  SrcFRate  DstFRate bUserCtrl    NrEn    NrType    RefCmp  MotionMode
       0    1280     720   YVU-SP420      SDR8        -1        -1         Y       Y     VIDEO         Y      Normal

-------------------------------VPSS CHN ATTR---------------------------------------------------------
   GrpID  PhyChnID  Enable    Mode   Width  Height  SrcFRate  DstFRate   Depth   Align  MirrorEn  FlipEn  bBufferShare  ProcMode
       0         0       Y    USER    1280     720        -1        -1       0       0         N       N             N     VIDEO
       0         1       Y    USER     640     480        -1        -1       0       0         N       N             N     VIDEO
       0         2       Y    USER     640     360        -1        -1       1       0         N       N             N     VIDEO

-------------------------------VPSS EXT-CHN ATTR--------------------------------------------------
   GrpID  ExtChnID  Enable  SrcChn   Width  Height  SrcFRate  DstFRate   Depth   Align  ProcMode

-------------------------------VPSS GRP CROP INFO-----------------------------------------------------
   GrpID  CropEn  CoorType   CoorX   CoorY   Width  Height    OriW    OriH   TrimX   TrimY TrimWid TrimHgt
       0       N       RAT       0       0       0       0

-------------------------------VPSS CHN CROP INFO-----------------------------------------------------
   GrpID   ChnID  CropEn  CoorType   CoorX   CoorY   Width  Height   TrimX   TrimY TrimWid TrimHgt
       0       0       N       RAT       0       0       0       0
       0       1       N       RAT       0       0       0       0
       0       2       N       RAT       0       0       0       0

-------------------------------VPSS GRP PIC QUEUE----------------------------------------------------
   GrpID  FreeLen0  BusyLen0     Delay    Backup
       0         9         0         0         0

-------------------------------VPSS GRP PIC INFO---------------------------------------------------
   GrpID   Width  Height      Pixfmt    Videofmt      DRange    Compress
       0    1280     720   YVU-SP420      LINEAR        SDR8           N

-------------------------------VPSS GRP WORK STATUS---------------------------------------------------
   GrpID    RecvPic0 ViLost0 VdecLost0       NewDo   OldDo NewUnDo     OldUnDo     StartFl  bStart  CostTm MaxCostTm
       0      137805       0         0      137805       0       0           0           0       Y   10156     10359

-------------------------------VPSS CHN OUTPUT RESOLUTION--------------------------------------------
   GrpID   ChnID  Enable   Width  Height      Pixfmt    Videofmt      DRange    Compress      SendOk   FrameRate
       0       0       Y    1280     720   YVU-SP420      LINEAR        SDR8           Y      137805          15
       0       1       Y     640     480   YVU-SP420      LINEAR        SDR8           N      137804          15
       0       2       Y     640     360   YVU-SP420      LINEAR        SDR8           N           0          15

-------------------------------VPSS 3DNR X PARAM------------------------------------------------------
-------------------------------VPSS GPR0 3DNR PARAM-------------------------------------
   GrpID    Intf   Version   OptMode       ISO     Ref
       0    NR_X     VER_3    MANUAL       110       1
   NRyEn_0                   NRyEn_1                   NRyEn_2                   NRyEn_3
         1                         1                         1                         1
    SFS2_0                    SFS2_1                    SFS2_2                    SFS2_3
        20                        20                        20                        20
    SFS4_0                    SFS4_1                    SFS4_2                    SFS4_3
        20                        20                        20                        10
     TFS_0              TFS0_1        TFS1_1             TFS_2
         1                   7            10                10
                       MATH0_1       MATH1_1            MATH_2                    MATH_3
                            60           150               120                       150

-------------------------------VPSS CHN LBA ATTR---------------------------------------------------------
   GrpID   ChnID  Aspect  videoX  videoY  videoW  videoH     BgColor

-------------------------------VPSS CHN ROTATE ATTR---------------------------------------------------
   GrpID   ChnID  Rotate

-------------------------------VPSS CHN LDCV3 ATTR----------------------------------------------------
   GrpID   ChnID  Enable  viewType   XOffset   YOffset       DistortionRatio       MinRatio

-------------------------------VPSS CHN LOWDELAY ATTR-------------------------------------------------
   GrpID   ChnID  Enable   LineCnt   OneBufEnable   OneBufAddr
       0       0       Y         1              N   0x4318b3c0

-------------------------------VPSS CHN BUF WRAP ATTR------------------------------------------------
   GrpID   ChnID  Enable   BufLine   WrapBufSize
       0       0       Y       160        307200

-------------------------------FRAME INTERRUPT ATTR---------------------------------------------------
   GrpID        IntType      EarlyLine
       0              -              0

-------------------------------VPSS GRP PIC PTS---------------------------------------------------------
   GrpID         FirstPicPTS           CurPicPTS
       0                   0                   0

-------------------------------DRV WORK STATUS--------------------------------------------------------
       StartSuc0       StartSuc1         LinkInt   StartErr0  NodeIdErr0   StartErr1  NodeIdErr1      BusErr
          137805               0          137805           0           0           0           0           0

-------------------------------DRV NODE QUEUE---------------------------------------------------------
   FreeNum   WaitNum  Busy00  Busy01    Sel0  Busy10  Busy11    Sel1    Proc
         9         0       0       0       1       0       0       0       0

-------------------------------INT WORK STATUS--------------------------------------------------------
     CntPerSec  MaxCntPerSec        CostTm    MostCostTm  CostTmPerSec MCostTmPerSec
            31            31           204           431          8304          8617
/tmp # 
/tmp # [J
/tmp # cat /proc/umap/*[J

[ACODEC] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time: [Jun 17 2019, 11:19:15]

-----ACODEC PARAM--------------------------------------------------------------
   LGain(dB)   RGain(dB) DacLVol(dB) DacRVol(dB) AdcLVol(dB) AdcRVol(dB) MicLMut MicRMut DacLMut DacRMut  BoostL  BoostR
      16.0      16.0         6           6           0           0           0       0       0       0       1       1

[AI] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time: [Jun 17 2019, 11:19:15]

-----AI DEV ATTR----------------------------------------------------------------
AiDev WorkMod   SampR  BitWid  ChnCnt  ClkSel SoundMod  PoiNum  ExFlag  FrmNum
    0 i2s_mas    8kHZ   16bit       1       0     mono     320       0      30

-----AI DEV STATUS0-------------------------------------------------------------
AiDev     IntCnt    fifoCnt    buffInt FrmTime MaxFrmTime TranLen IsrTime 
    0     230176          0          0   40031      42007     640     198

-----AI DEV STATUS1-------------------------------------------------------------
AiDev MaxIsrTime      CBPhy  CBSize    ROffSet    WOffSet
    0        351   437f0000    1920        280          0

-----AI DEV EXTEND STATUS-------------------------------------------------------
AiDev enTrack   bMute  Volume
    0       0       N       0

-----AI CHN STATUS--------------------------------------------------------------
AiDev   AiChn   State     BufFul UsrQueLost UsrFrmDepth   u32Data0   u32Data1    UserGet    UserRls
    0       0  enable          0          0          30          0          0     230176     230176

-----AI CHN RESAMPLE STATUS-----------------------------------------------------
AiDev AiChn   State  bResmp  PoiNum   InSampR  OutSampR
    0     0  enable       N       0    (null)    (null)

-----AI CHN VQE STATUS0---------------------------------------------------------
AiDev AiChn   State bVqe workmod    RATE  PoiNum bAgc  bEq bHpf bRnr bHdr bDrc  WrFile
    0     0  enable    Y    comm   16kHZ     320    Y    N    Y    Y    N    N       N

-----AI CHN VQE STATUS1---------------------------------------------------------
AiDev AiChn   State    bAgc bUsrmod NoiseSupSwi AdjustSpeed ImproveSNR MaxGain NoiseFloor OutputMode TargetLevel  UseHPF
    0     0  enable       Y       Y           1           0          2       2        -41          1          -2       2

-----AI CHN VQE STATUS2---------------------------------------------------------
AiDev AiChn   State    bHpf bUsrmod HpfFreq
    0     0  enable       Y       Y      80

-----AI CHN VQE STATUS3---------------------------------------------------------
AiDev AiChn   State    bRnr bUsrmod MaxNrLevel  NsThresh  NrMode
    0     0  enable       Y       Y         15       -57       1

[AO] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time: [Jun 17 2019, 11:19:14]

-----AO DEV ATTR----------------------------------------------------------------
AoDev WorkMod   SampR  BitWid  ChnCnt  ClkSel SoundMod  PoiNum  ExFlag  FrmNum
    0 i2s_mas    8kHZ   16bit       1       0     mono     320       0      30

-----AO DEV STATUS0-------------------------------------------------------------
AoDev     IntCnt    fifoCnt    buffInt FrmTime MaxFrmTime TranLen IsrTime
    0     230174          1          0   40000      40637     640      11

-----AO DEV STATUS1-------------------------------------------------------------
AoDev MaxIsrTime      CBPhy  CBSize    ROffSet    WOffSet
    0         28   4382f000    1920          0        280

-----AO DEV EXTEND STATUS-------------------------------------------------------
AoDev enTrack   bMute  Volume
    0       0       N       0

-----AO CHN STATUS--------------------------------------------------------------
AoDev   AoChn   State    Read   Write      BufEmp  u32Data0  u32Data1  bResmp  PoiNum InSampR  OutSampR
    0       0  enable       0       0      230174         0         0       N       0  (null)    (null)

-----AO CHN VQE STATUS0---------------------------------------------------------
AoDev AoChn   State bVqe workmod    RATE  PoiNum bAnr bAgc  bEq bHpf  WrFile
    0     0  enable    N    comm  (null)       0    N    N    N    N       N

[CHNL] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:14]


Total Chnl Scheduler Count: 2 

-----SCHEDULER 0 INFO----------------------------------------------------------
   SchdlId    VpuNum
         0         1

-----VPU INFO------------------------------------------------------------------
   VpuId    Name   State      IntCnt     TimeCnt      VpuCnt  ErrCnt      InqCnt     StartOk     StartNo      Config   Reset
       0  VEDU_0   PAUSE     1151055      874853      276202       0     2578021      276202           0      276202       0

-----CHNL STATE----------------------------------------------------------------
  ChnlId    Prio    Type  TskNum   State      InqCnt     StartOk     StartNo      IntPro
       0       0  H264E        0    IDLE     1289015      138101           0      138101
       2       0  H264E        0    IDLE     1289006      138101           0      138101

-----CHNL PERF-----------------------------------------------------------------
  ChnlId        Type   StartCost     IntCost    IntCostL      HWCost     HWCycle     HWCostL   HWCostAcc
       0      H264E            0           0           0           0           0           0           0
       2      H264E            0           0           0           0           0           0           0

-----CHNL CURRENT RUN STATE----------------------------------------------------
   VpuId     VpuName      ChnlId        Type
  No running channel here

-----SCHEDULER 1 INFO----------------------------------------------------------
   SchdlId    VpuNum
         1         1

-----VPU INFO------------------------------------------------------------------
   VpuId    Name   State      IntCnt     TimeCnt      VpuCnt  ErrCnt      InqCnt     StartOk     StartNo      Config   Reset
       0  JPGE_0   PAUSE      920890      920890           0       0      920738           0           0           0       0

-----CHNL STATE----------------------------------------------------------------
  ChnlId    Prio    Type  TskNum   State      InqCnt     StartOk     StartNo      IntPro
       1       0  JPEGE        0    IDLE      920738           0           0           0

-----CHNL PERF-----------------------------------------------------------------
  ChnlId        Type   StartCost     IntCost    IntCostL      HWCost     HWCycle     HWCostL   HWCostAcc
       1      JPEGE            0           0           0           0           0           0           0

-----CHNL CURRENT RUN STATE----------------------------------------------------
   VpuId     VpuName      ChnlId        Type
  No running channel here


[H264E] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:14]

-----MODULE PARAM--------------------------------------------------------------
      OnePack   H264eVBSource      PowerSaveEn     MiniBufMode     bQpHstgrmEn
            0               2                1               0               0
-----CHN ATTR------------------------------------------------------------------
     ID  MaxWidth MaxHeight     Width    Height   profile   C2GEn   BufSize   ByFrame   GopMode   MaxStrCnt
      0      1280       720      1280       720      base       Y    691200         Y   NormalP         200
      2       640       480       640       480      base       Y    230400         Y   NormalP         200

-----PICTURE INFO--------------------------------------------------------------
     ID     EncdStart   EncdSucceed        Lost        Disc       Pskip      Recode      RlsStr     UnrdStr
      0        138101        138101           0           0           0           0      138101           0
      2        138101        138101           0           0           0           0      138101           0

-----STREAM BUFFER-------------------------------------------------------------
     ID     Base                  RdTail      RdHead      WrTail      WrHead      DataLen     BufFree     
      0     0xc4000000            0x54e00     0x54e00     0x54e00     0x54e00     0           692160      

      2     0xc40c0000            0x15500     0x15500     0x15500     0x15500     0           233408      

-----RefParam INFO--------------------------------------------------------------
     ID      EnPred        Base     Enhance    RcnRefShareBuf
      0           Y           1           0                 Y
      2           Y           1           0                 Y

-----ROIBG INFO------------------------------------------------------------------
     ID   BgSrcFr   BgTarFr
      0        -1        -1
      2        -1        -1

-----Syntax INFO1--------------------------------------------------------------
     ID SlcspltEn   Slcsize   IntraRefresh    RefreshMode     RefreshNum   QpOfIDR
      0         N       N/A              N            N/A            N/A       N/A
      2         N       N/A              N            N/A            N/A       N/A

-----Syntax INFO2--------------------------------------------------------------
     ID   profile   EntrpyI   EntrpyP   EntrpyB  Itrans  Ptrans QMatrix   POC   DblkIdc   alpha    beta
      0      base     cavlc     cavlc     cavlc     4x4     4x4       N     0         0       0       0
      2      base     cavlc     cavlc     cavlc     4x4     4x4       N     0         0       0       0

-----Foreground && Scene INFO-------------------------------------------------------------
     ID  ForegroundSkipCoef  BackgroundSkipCoef SceneMode
      0                   8                   8   Scene_0
      2                   8                   8   Scene_0

-----CuPrediction-------------------------------------------------------------------
     ID  PredMode     Inter8Cost    Inter16Cost     Intra4Cost     Intra8Cost    Intra16Cost 
      0      AUTO              8              8              8              8              8
      2      AUTO              8              8              8              8              8

-----SkipBias-------------------------------------------------------------------
     ID     SkipBiasEn      Gain    Offset      ForegroundCost      BackgroundCost
      0              N         8         8                   0                   0
      2              N         8         8                   0                   0


[H265E] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:14]

-----MODULE PARAM--------------------------------------------------------------
      OnePack      H265eVBSource        PowerSaveEn        MiniBufMode       bQpHstgrmEn
            0                  2                  1                  0                 0
-----CHN ATTR------------------------------------------------------------------
     ID  MaxWidth MaxHeight     Width    Height   Profile   C2GEn   BufSize   ByFrame   GopMode   MaxStrCnt

-----PICTURE INFO--------------------------------------------------------------
     ID     EncdStart   EncdSucceed        Lost        Disc       Pskip      Recode      RlsStr     UnrdStr

-----STREAM BUFFER-------------------------------------------------------------
ID     Base                  RdTail      RdHead      WrTail      WrHead      DataLen     BufFree     
-----RefParam INFO-------------------------------------------------------------
     ID      EnPred        Base     Enhance         UsedFrame      MaxUsedFrame    RcnRefShareBuf

-----ROIBG INFO------------------------------------------------------------------
     ID   BgSrcFr   BgTarFr

-----Syntax INFO1--------------------------------------------------------------
     ID SlcspltEn   Slcsize   IntraRefresh    RefreshMode     RefreshNum   QpOfIDR

-----Syntax INFO2--------------------------------------------------------------
     ID    DblkEn      Tc    Beta   Saoluma Saochroma  EntrpyFlag

-----Syntax INFO3--------------------------------------------------------------
     ID  TimInfFlag   NumInTick    TimeScal     DiffOne

-----Pu INFO-------------------------------------------------------------------
     ID   ConsIntra IntraSmoothing

-----Trans INFO----------------------------------------------------------------
     ID  CbQpOffset  CrQpOffset

-----Foreground && Scene INFO--------------------------------------------------------------
     ID  ForegroundSkipCoef  BackgroundSkipCoef SceneMode

-----CuPrediction-------------------------------------------------------------------
     ID  PredMode  Inter8Cost Inter16Cost Inter32Cost Inter64Cost  Intra4Cost  Intra8Cost Intra16Cost Intra32Cost

-----SkipBias-------------------------------------------------------------------
     ID     SkipBiasEn      Gain    Offset      ForegroundCost      BackgroundCost


[ISP] Version: [Hi3516EV200_ISP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:14]


------------------------------------------------------------------------------
------------------------------ ISP PROC PIPE[0] -----------------------------
------------------------------------------------------------------------------

-----MODULE/CONTROL PARAM-----------------------------------------------------
    ProcParam    StatIntvl    UpdatePos   IntBothalf   IntTimeout    PwmNumber   PortIntDelay   QuickStart LdciTprFltEn
           30            1            0            0          200            3              0            0            0

-----ISP Mode------------------------------------------------------------------
      StitchMode     RunningMode
          NORMAL          ONLINE

-----DRV INFO-------------------------------------------------------------------
     ViPipe     IntCnt       IntT    MaxIntT    IntGapT    MaxGapT   IntRat IspResetCnt  IspBeStaLost
          0     138119        234       2404      66670      66876       16           1             0

    IntTpye   PtIntCnt     PtIntT  PtMaxIntT  PtIntGapT  PtMaxGapT PtIntRat SensorCfgT  SensorMaxT
      Start          0          0          0          0          0        0          5        2178

-----PubAttr INFO--------------------------------------------------------------
        WndX        WndY        WndW        WndH        SnsW        SnsH       Bayer
           0           0        1280         720        1280         720        BGGR


-----SNAPATTR INFO-----------------------------------------------------------------
    SnapType    PipeMode      OPType   ProFrmNum
      NORMAL        NONE        Auto           3


[AE] Version: [Hi3516EV200_ISP_V1.0.1.0 B050 Release], Build Time[May  9 2019, 22:51:52]
-----AE INFO-------------------------------------------------------------------
      Again      Dgain      IspDg    SysGain        Iso       Line   AEInter   Incrmnt                 Exp   1stTime
       1024       1088       1068       1114        110       1496         1       256             1666776   1000000

       Comp     EVbias     OriAve     Offset      Speed       Tole     Error       Fps   RealFps    BDelay    WDelay
         68       1024         70          0         64          2        -2     15.00      1500         5         0

    MaxLine   MaxLineT     MaxAgT     MaxDgT    MaxIDgT     MaxSgT    ManuEn    MaLine      MaAg      MaDg   MaIspDg
       1496       1890     129024       1984       2048     203840         0         0         0         0         0

    WdrMode  ExpRatio0  ExpRatio1  ExpRatio2    AnFlick    SlowMod     GainTh
       LINE         64         64         64          0          1     499968

     NodeId    IntTime    SysGain    IrisApe     UpStgy     DwStgy              Mltply
          0          2       1024          1          0          4                2048
          1       1496       1024          1          1          0             1531904
          2       1496     203840          1          4          1           304944640

   NodeIdSF  IntTimeSF  SysGainSF  IrisApeSF   UpStgySF   DwStgySF            MltplySF
          0          2       1024          1          0          4                2048
          1        710       1024          1          1          0              727040
          2        710     499968          1          4          1           354977280

     AuIrEn     IrType     MaIrEn    DbgIrSt
          0     DCIris          0          0



[AWB] Version: [Hi3516EV200_ISP_V1.0.1.0 B050 Release], Build Time[May  9 2019, 22:51:55]
-----AWB INFO------------------------------------------------------------------
   Gain0   Gain1   Gain2   Gain3  CoTemp
   0x19b   0x100   0x100   0x1e0    5681

 Color00 Color01 Color02 Color10 Color11 Color12 Color20 Color21 Color22
  0x 1ae  0x80ef  0x  41  0x8026  0x 170  0x804a  0x   4  0x805f  0x 15b

  ManuEn     Sat   Zones   Speed
       0      86      32     256

-----DEFECT INFO-----------------------------------
      Enable    Strength  BlendRatio
           1         150          90

-----GE INFO-------------------------------------------------------------
      Enable  Threshold1  Threshold3    Strength
           1       16384        4800         128

-----FrameWDR INFO------------------------------------------------------------------
       MdtEn   LongThr  ShortThr  MdThrLow  MdThrHig
           1      3008      4032         0         0

-----Black Level Actual INFO--------------------------------------------------------------
            BlcR           BlcGr           BlcGb            BlcB
              64              64              64              64

-----BAYERNR INFO----------------------------------------------------------------------------
          Enable     NrLscEnable      CoarseStr0      CoarseStr1      CoarseStr2      CoarseStr3
               1               0             110             110             110             110

-----DRC INFO------------------------------------------------------------------
              En          ManuEn        Strength
               1               1             360

-----Lcac INFO-----------------------------------
      Enable       CrCtr       CbCtr
           1           0           3

-----DEMOSAIC INFO-------------------------------------------------------------
      Enable  NoDirStr  NoDirMFStr  NoDirHFStr DeSmthRng
           1        64          32           3         1

-----AntiFalseColor INFO-------------------------------------------------------------
      Enable   Threshold    Strength
           1          10           8

-----CA INFO-----------------------------------
      Enable    isoRatio
           1        1300

-----FPN CORRECT INFO------------------------------------------------------------
      En OpType Strength Offset
       0  --       --      --

-----SHARPEN INFO--------------------------------------------------------------
      bSharpenEn
               1
LumaWgt 0--7:
      31      31      31      31      31      31      31      31

LumaWgt 8--15:
      31      31      31      31      31      31      31      31

LumaWgt 16--23:
      31      31      31      31      31      31      31      31

LumaWgt 24--31:
      31      31      31      31      31      31      31      31

TextureStr 0--7:
     420     420     390     390     360     360     360     350

TextureStr 8--15:
     350     290     290     290     270     270     270     270

TextureStr 16--23:
     270     270     266     260     260     260     260     260

TextureStr 24--31:
     260     230     230     210     210     210     200     200

EdgeStr 0--7:
     125     128     146     160     175     175     175     175

EdgeStr 8--15:
     160     160     160     160     160     210     210     210

EdgeStr 16--23:
     210     210     200     190     185     175     165     160

EdgeStr 24--31:
     160     160     160     160     160     160     160     160

 TextureFreq    EdgeFreq   OverShoot  UnderShoot ShootSupStr  DetailCtrl EdgeFiltStrEdgeFiltMaxCap       RGain       GGain       BGain    SkinGain 
         160         100          54          74           0         128          63           0          24          32          24          24

 ShootSupAdj DetailCtrlThr  MaxSharpGain    SkinUmax    SkinUmin    SkinVmax    SkinVmin  WeakDetailGain
           0           160            60         128         110         149         128               0


-----LDCI INFO------------------------------------------------------------------------------
      Enable      Manual   GaussLPFSigma    HePosWgt  HePosSigma   HePosMean    HeNegWgt  HeNegSigma   HeNegMean     BlcCtrl
           1           0              20          64          80           0          64          80           0          40

-----PreGamma INFO--------------------------------------------------------------
          Enable
               0

-----------------------------------------------------------------------------
----------------------------------- ISP PROC END[0] ------------------------
-----------------------------------------------------------------------------



[IVE] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:20]


-------------------------------MODULE PARAM--------------------------------------
      save_power     max_node_num
               0              512

-------------------------------IVE QUEUE INFO------------------------------------
    Wait      Busy   WaitCurId WaitEndId BusyCurId BusyEndId
      0        -1         0         0         0         0

--------------------------------IVE TASK INFO------------------------------------
       Hnd   TaskFsh    LastId    TaskId   HndWrap   FshWrap
    828670    828670         0         1         0         0

-----------------------------------IVE RUN-TIME INFO-----------------------------
  LastInst  CntPerSec MaxCntPerSec  TotalIntCntLastSec    TotalIntCnt     QTCnt STCnt
         1         76          113              691062         691084         0     0

    CostTm   MCostTm  CostTmPerSec MCostTmPerSec  TotalIntCostTm       RunTm
        12        47           739           872         6044490        9208

----------------------------------IVE INVOKE INFO--------------------------------

       DMA     Filter       CSC    FltCsc     Sobel    MagAng    Dilate     Erode
    138315          0         0         0         0         0         0         0

    Thresh        And       Sub        Or     Integ      Hist ThreshS16 ThreshU16
         0          0         0         0         0         0         0         0

     16to8 OrdStatFlt   BernSen       Map    EqualH       Add       Xor       NCC
         0          0         0         0         0    138071         0         0

       CCL        GMM     Canny       LBP  NormGrad        LK ShiTomasi    GradFg
    276142          0         0         0         0         0         0         0

  MatchMod  UpdateMod     Radon       ANN       SVM    AdpThr  LineFltH  NoiseRmH
         0          0         0         0         0         0         0         0

 PlateChar        SAD      GMM2    Resize       CNN PerspTrans       KCF       HOG
         0     276142         0         0         0          0         0         0 

       XNN
         0 

----------------------------------IVE UTILI INFO--------------------------------

  Utili  
    0

[IVP] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:20]


-------------------------------IVP ATTR---------------------------------------------------------------
      HDL.                   W                   H           Threshold                    LowBitrate                    AdvanceIsp            CostTime           Framerate

[JPEGE] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:14]


-----MODULE PARAM--------------------------------------------------------------
        OnePack     JpegeMiniBufMode   JpegClearStreamBuf
              0                    0                    1

-----ATTRIBUTE1----------------------------------------------------------------
ID    bMjpeg   PicType  MaxWidth   MaxHeight   Width  Height     BufSize   ByFrm     MCU   Qfactor   C2GEn   DcfEn
1          N    YUV420      1280         720    1280     720      921600       Y       0        90       N       N

-----STATUS1-------------------------------------------------------------------
ID         BufLen         FreeLen         StrmCnt         MaxStrm       
 1         921600          921536               0             200       

-----STATUS2-------------------------------------------------------------------
ID    PicRec    PicCoded    PicDroped    PicDisc    NoStmCnt    RcFail    PicRecode    UnrdStr      
1     0         0           0            0          0           0         0            0            

-----STREAM BUFFER-------------------------------------------------------------
ID  Base                RdTail      RdHead      WrTail      WrHead      BufLen      DataLen     BufFree     
1   0xc4100000            0           0           0           0           921600      0           921536      


-----RUN INFO----------------------------------------------------------------
ID         DCFSize      MpfExOffset        SrcSize        Mpf0Size        Mpf1Size          MpfCnt        JpegQueueIdx  
1                0               0               0               0               0               0                   0  
-----LOG BUFFER STATE----------------------------------------------------------
MaxLen  ReadPos WritePos ButtPos
 64(KB)       0     6581   65536

-----CURRENT LOG LEVEL---------------------------------------------------------
vb      :  3
sys     :  3
region  :  3
chnl    :  3
vpss    :  3
venc    :  3
h264e   :  3
jpege   :  3
h265e   :  3
vi      :  3
rc      :  3
aio     :  3
ai      :  3
ao      :  3
vpu     :  3
isp     :  3
ive     :  3
vgs     :  3

[MD] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:20]


-------------------------------MD CHN ATTR-------------------------------------------------------------
NO.    W    H   Alg   SadMode  SadOutCtrl        SadT   CclMode  CclInitT CclStep     XWt     YWt   FrmRate   CostTmPerFrm
  0  640  360     0         0           4        1000         0        16       4   32768   32768        15          19465

Module: [MIPI_RX], Build Time[Jun 17 2019, 11:19:14]

[RC] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release],Build Time[Jun 17 2019, 11:19:14]


------BASE PARAMS 1------------------------------------------------------------
  ChnId    Gop  StatTm  ViFr       TrgFr ProType  RcMode  Br(kbps)  FluLev  IQp  PQp  BQp 
      0     30       1    30          30      96     VBR      4352     N/A  N/A  N/A  N/A
      2     30       1    30          30      96     VBR      1280     N/A  N/A  N/A  N/A

------BASE PARAMS 2------------------------------------------------------------
  ChnId   MinQp   MaxQp  MinIQp  MaxIQp   EnableIdr    bQpMapEn   QpMapMode 
      0      24      51      24      51           Y           N         N/A
      2      24      51      24      51           Y           N         N/A

------BASE PARAMS 3------------------------------------------------------------
  ChnId    LongTermStatTime   ShortTermStatTime  LongTermMaxBitrate  LongTermMinBitrate 

-----RUN COMM PARAM 1----------------------------------------------------------
  ChnId  RowQpDelta                       ThrdI(16)
      0           1  [   0   0   0   0   3   3   5   5   8   8   8  15  15  20  25  25]
      2           1  [   0   0   0   0   3   3   5   5   8   8   8  15  15  20  25  25]

-----RUN COMM PARAM 2------------------------------------------------------------
  ChnId  FirstFrmStartQP                  ThrdP(16)
      0          -1  [   0   0   0   0   3   3   5   5   8   8   8  15  15  20  25  25]
      2          -1  [   0   0   0   0   3   3   5   5   8   8   8  15  15  20  25  25]

-----RUN COMM PARAM 3----------------------------------------------------------
  ChnId  DirectionThrd                       ThrdB(16)
      0           8  [   0   0   0   0   3   3   5   5   8   8   8  15  15  20  25  25]
      2           8  [   0   0   0   0   3   3   5   5   8   8   8  15  15  20  25  25]

-----RUN COMM PARAM 4----------------------------------------------------------
  ChnId   bLost     LostThr  LostFrmStr    EncGap  RCPriority   SprFrmMod     SprIFrm     SprPFrm     SprBFrm    bClrStat
      0       N    83886080      NORMAl         0     BITRATE        None      500000      500000      500000           1
      2       N    83886080      NORMAl         0     BITRATE        None      500000      500000      500000           1

-----RUN COMM PARAM 5----------------------------------------------------------
  ChnId       bDetectSceneChange        bAdapInsertIFrame
      0                        Y                        N
      2                        Y                        N

-----Foreground INFO 1----------------------------------------------------------
  ChnId     bThrdEn  DirectionThrd                          ThrdP(16)
      0           0           8  [   0   0   0   0   3   3   5   5   8   8   8  15  20  20  25  25]
      2           0           8  [   0   0   0   0   3   3   5   5   8   8   8  15  20  20  25  25]

-----Foreground INFO 2----------------------------------------------------------
  ChnId  ThreshGain   ThreshOffset                          ThrdB(16)
      0           8           8  [   0   0   0   0   3   3   5   5   8   8   8  15  20  20  25  25]
      2           8           8  [   0   0   0   0   3   3   5   5   8   8   8  15  20  20  25  25]

-----GOP MODE ATTR-------------------------------------------------------------
  ChnId   GopMode IpQpDelta  SPInterval SPQpDelta   BFrmNum  BQpDelta  BgInterval ViQpDelta
      0   NormalP         2         N/A       N/A       N/A       N/A         N/A       N/A
      2   NormalP         2         N/A       N/A       N/A       N/A         N/A       N/A

-----RUN CBR PARAM ------------------------------------------------------------
  ChnId  MinIprop  MaxIprop   MaxQp   MinQp  MaxIQp  MinIQp  MaxReEncTimes

-----RUN VBR COMM PARAM ------------------------------------------------------------
  ChnId   ChgPs  MinIprop  MaxIprop   MaxQp   MinQp  MaxIQp  MinIQp  MaxReEncTimes
      0      90         1        20      51      24      51      24              0
      2      90         1        20      51      24      51      24              0

-----RUN AVBR PARAM ------------------------------------------------------------
  ChnId     MaxStillQP    MotionSensi     MinPercent   MinStillPSNR     MinQpDelta

-----RUN QVBR PARAM ------------------------------------------------------------
  ChnId   BitPercentLL   BitPercentUL   PsnrFluctuateLL   PsnrFluctuateUL

-----RUN CVBR PARAM ------------------------------------------------------------
  ChnId     MinQpDelta     MaxQpDelta        ExBitPercent     LongTermStatTimeUnit

-----RUN INFO1-----------------------------------------------------------------
  ChnId   InsBr(kbps)   InsFr    WatL   CfgBt(kb)  RealBt(kb)   IPRatio  TarPercent   StartQp   MinQp   MaxQp
      0          1170      30       0         115          31         4         N/A        24      24      51
      2           222      30      22         241          43         7         N/A        24      24      51

-----RC DeBreathEffect INFO-----------------------------------------------------------------
  ChnId   bEnable Strength0 Strength1     DeBrthEfctCnt
      0         N       N/A       N/A                 0
      2         N       N/A       N/A                 0

-----RC HierarchicalQp INFO-----------------------------------------------------------------
  ChnId   bEnable FrameNum[0] FrameNum[1] FrameNum[2] FrameNum[3]  QpDelta[0]  QpDelta[1]  QpDelta[2]  QpDelta[3]
      0         N           1           1           0           0          -2          -4           0           0
      2         N           1           1           0           0          -2          -4           0           0

-----RC PERFORMANCE  INFO------------------------------------------------------
  ChnId       StaOfstaTim      TotaOfstaTim       StaOfEndTim      TotaOfEndTim         TotalTime
      0        9212899177          11269746        9212908809           1535460          12805206
      2        9212908906           8505923        9212911558           1466781           9972704

[RGN] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:14]


-----REGION STATUS OF OVERLAY------------------------------------------------------------
 Hdl     Type     Used    PiFmt        W        H  BgColor              Phy             Virt   Stride
   0        0        N        8      176       64       40         438b7800         c45c5800      352
   2        0        N        8      176       64       40         438d8800         c4605800      352

-----REGION STATUS OF OVERLAY BUF USED---------------------------------------------------
 Hdl     Type  CnvsNum     buf0     buf1     buf2     buf3     buf4     buf5
   0        0        6        0        0        0        0        0        0
   2        0        6        0        0        0        0        0        0

-----REGION CALL VGS STATUS OF OVERLAY---------------------------------------------------
 Hdl     CallCnt      JobSuc     JobFail     TaskSuc    TaskFail      EndSuc     EndFail
   0           0           0           0           0           0           0           0
   2           0           0           0           0           0           0           0

-----REGION CHN STATUS OF OVERLAY--------------------------------------------------------
 Hdl  Type   Mod   Dev   Chn   bBatch   AttachDest   bSh     X     Y  AphF  AphB  Layer  bAQp    QP  bQpDis   ColorLUT0   ColorLUT1
   0     0  VENC     0     0        N         MAIN     Y    16   656   127     0      0     N     0       N           0           0
   2     0  VENC     0     2        N         MAIN     Y    16   416   127     0      0     N     0       N           0           0


[SVP_ALG] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:20]


-----------------------------SVP ALG MODEL INFO--------------------------------------------------------
       NO.   FrmRate   CostTmPerFrm

[SYS] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:14]


-----MODULE STATUS--------------------------------------------------------------
  Status
     run

-----SCALE COEFF INFO-----------------------------------------------------------
            RangeLevel   RangeValue    HorLum    HorChr    VerLum    VerChr
           RANGE_0   (    0,  8/64)   LEVEL_0   LEVEL_0   LEVEL_0   LEVEL_0
           RANGE_1   [ 8/64, 10/64)   LEVEL_1   LEVEL_1   LEVEL_1   LEVEL_1
           RANGE_2   [10/64, 15/64)   LEVEL_2   LEVEL_2   LEVEL_2   LEVEL_2
           RANGE_3   [15/64, 19/64)   LEVEL_3   LEVEL_3   LEVEL_3   LEVEL_3
           RANGE_4   [19/64, 24/64)   LEVEL_4   LEVEL_4   LEVEL_4   LEVEL_4
           RANGE_5   [24/64, 29/64)   LEVEL_5   LEVEL_5   LEVEL_5   LEVEL_5
           RANGE_6   [29/64, 33/64)   LEVEL_6   LEVEL_6   LEVEL_6   LEVEL_6
           RANGE_7   [33/64, 35/64)   LEVEL_7   LEVEL_7   LEVEL_7   LEVEL_7
           RANGE_8   [35/64, 38/64)   LEVEL_8   LEVEL_8   LEVEL_8   LEVEL_8
           RANGE_9   [38/64, 42/64)   LEVEL_9   LEVEL_9   LEVEL_9   LEVEL_9
           RANGE_10  [42/64, 45/64)  LEVEL_10  LEVEL_10  LEVEL_10  LEVEL_10
           RANGE_11  [45/64, 48/64)  LEVEL_11  LEVEL_11  LEVEL_11  LEVEL_11
           RANGE_12  [48/64, 51/64)  LEVEL_12  LEVEL_12  LEVEL_12  LEVEL_12
           RANGE_13  [51/64, 53/64)  LEVEL_13  LEVEL_13  LEVEL_13  LEVEL_13
           RANGE_14  [53/64, 55/64)  LEVEL_14  LEVEL_14  LEVEL_14  LEVEL_14
           RANGE_15  [55/64, 57/64)  LEVEL_15  LEVEL_15  LEVEL_15  LEVEL_15
           RANGE_16  [57/64, 60/64)  LEVEL_16  LEVEL_16  LEVEL_16  LEVEL_16
           RANGE_17  [60/64,     1]  LEVEL_17  LEVEL_17  LEVEL_17  LEVEL_17
           RANGE_18  (    1,   MAX)  LEVEL_18  LEVEL_18  LEVEL_18  LEVEL_18

-----MEM TABLE------------------------------------------------------------------
     Mod         ModName     Dev     Chn         MmzName

-----BIND RELATION TABLE--------------------------------------------------------
  FirMod  FirDev  FirChn  SecMod  SecDev  SecChn  TirMod  TirDev  TirChn    SendCnt     rstCnt
    vpss       0       0    venc       0       0    null       0       0     138102          0
    vpss       0       0    venc       0       1    null       0       0     138101          0
    vpss       0       1    venc       0       2    null       0       0          0          0
      vi       0       0    vpss       0       0    venc       0       0     138102          0
      vi       0       0    vpss       0       0    venc       0       1     138102          0
      vi       0       0    vpss       0       1    venc       0       2     138102          0

[VB] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:14]

-----VB PUB CONFIG--------------------------------------------------------------
MaxPoolCnt
       512
-----VB SUPPLEMENT ATTR---------------------------------------------------------
  Config    Size   VbCnt
       0       0      74
-----COMMON POOL CONFIG---------------------------------------------------------
PoolId         0         1         2         3         4         5         6         7         8         9        10        11        12        13        14        15
Size     1382400    307200    460800         0         0         0         0         0         0         0         0         0         0         0         0         0
Count          3         1         2         0         0         0         0         0         0         0         0         0         0         0         0         0

--------------------------------------------------------------------------------
PoolId  PhysAddr            VirtAddr            IsComm  Owner  BlkSz     BlkCnt  Free    MinFree 
0       0x42d91000          0x0                 1       -1     1382400   3       1       0       
BLK   VI    VO    VGS   VENC  VDEC  H265E H264E JPEGE H264D JPEGD VPSS  DIS   USER  PCIV  AI    AENC  RC    VFMW  GDC   AVS   RECT  MATCH MCF   
2     1     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     
0     1     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     
Sum   2     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     

--------------------------------------------------------------------------------
PoolId  PhysAddr            VirtAddr            IsComm  Owner  BlkSz     BlkCnt  Free    MinFree 
1       0x43187000          0x0                 1       -1     307200    1       0       0       
BLK   VI    VO    VGS   VENC  VDEC  H265E H264E JPEGE H264D JPEGD VPSS  DIS   USER  PCIV  AI    AENC  RC    VFMW  GDC   AVS   RECT  MATCH MCF   
0     0     0     0     0     0     0     0     0     0     0     1     0     0     0     0     0     0     0     0     0     0     0     0     
Sum   0     0     0     0     0     0     0     0     0     0     1     0     0     0     0     0     0     0     0     0     0     0     0     

--------------------------------------------------------------------------------
PoolId  PhysAddr            VirtAddr            IsComm  Owner  BlkSz     BlkCnt  Free    MinFree 
2       0x431d3000          0x0                 1       -1     460800    2       2       0       

--------------------------------------------------------------------------------
PoolId  PhysAddr            VirtAddr            IsComm  Owner  BlkSz     BlkCnt  Free    MinFree 
3       0x434ab000          0x0                 0       -2     768       1       0       0       
BLK   VI    VO    VGS   VENC  VDEC  H265E H264E JPEGE H264D JPEGD VPSS  DIS   USER  PCIV  AI    AENC  RC    VFMW  GDC   AVS   RECT  MATCH MCF   
0     0     0     0     0     0     0     1     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     
Sum   0     0     0     0     0     0     1     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     

--------------------------------------------------------------------------------
PoolId  PhysAddr            VirtAddr            IsComm  Owner  BlkSz     BlkCnt  Free    MinFree 
4       0x434ac000          0x0                 0       -2     768       1       1       0       

--------------------------------------------------------------------------------
PoolId  PhysAddr            VirtAddr            IsComm  Owner  BlkSz     BlkCnt  Free    MinFree 
5       0x434ad000          0x0                 0       -2     1640448   1       0       0       
BLK   VI    VO    VGS   VENC  VDEC  H265E H264E JPEGE H264D JPEGD VPSS  DIS   USER  PCIV  AI    AENC  RC    VFMW  GDC   AVS   RECT  MATCH MCF   
0     0     0     0     0     0     0     1     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     
Sum   0     0     0     0     0     0     1     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     

--------------------------------------------------------------------------------
PoolId  PhysAddr            VirtAddr            IsComm  Owner  BlkSz     BlkCnt  Free    MinFree 
6       0x43760000          0x0                 0       -2     256       1       0       0       
BLK   VI    VO    VGS   VENC  VDEC  H265E H264E JPEGE H264D JPEGD VPSS  DIS   USER  PCIV  AI    AENC  RC    VFMW  GDC   AVS   RECT  MATCH MCF   
0     0     0     0     0     0     0     1     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     
Sum   0     0     0     0     0     0     1     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     

--------------------------------------------------------------------------------
PoolId  PhysAddr            VirtAddr            IsComm  Owner  BlkSz     BlkCnt  Free    MinFree 
7       0x43761000          0x0                 0       -2     256       1       1       0       

--------------------------------------------------------------------------------
PoolId  PhysAddr            VirtAddr            IsComm  Owner  BlkSz     BlkCnt  Free    MinFree 
8       0x43762000          0x0                 0       -2     578816    1       0       0       
BLK   VI    VO    VGS   VENC  VDEC  H265E H264E JPEGE H264D JPEGD VPSS  DIS   USER  PCIV  AI    AENC  RC    VFMW  GDC   AVS   RECT  MATCH MCF   
0     0     0     0     0     0     0     1     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     
Sum   0     0     0     0     0     0     1     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     0     

--------------------------------------------------------------------------------
PoolId  PhysAddr            VirtAddr            IsComm  Owner  BlkSz     BlkCnt  Free    MinFree 
9       0x437f1000          0xc43c0000          0       -2     4096      62      61      60      
BLK   VI    VO    VGS   VENC  VDEC  H265E H264E JPEGE H264D JPEGD VPSS  DIS   USER  PCIV  AI    AENC  RC    VFMW  GDC   AVS   RECT  MATCH MCF   
32    0     0     0     0     0     0     0     0     0     0     0     0     0     0     1     0     0     0     0     0     0     0     0     
Sum   0     0     0     0     0     0     0     0     0     0     0     0     0     0     1     0     0     0     0     0     0     0     0     


[VENC] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:15]

-----MODULE PARAM--------------------------------------------------------------
    VencBufferCache   FrameBufRecycle     VencMaxChnNum
                  0                 0                16


-----VENC CHN ATTR 1-----------------------------------------------------------
      ID   Width  Height  Type  ByFrame    Sequence   LeftBytes     LeftFrm  CurPacks   GopMode  Prio
       0    1280     720    96        Y      138101           0           0         1   NormalP     0
       1    1280     720    26        Y           0           0           0         0   NormalP     0
       2     640     480    96        Y      138101           0           0         4   NormalP     0

-----VENC CHN ATTR 2-----------------------------------------------------------
      ID   VeStr   SrcFr   TarFr     Timeref  PixFmt PicAddr      WakeUpFrmCnt
       0       Y      -1      -1      276268  YVU420  0x4318b3c0           1
       1       N      -1      -1           1      NA  0x       0           1
       2       Y      -1      -1      276268  YVU420  0x431d3000           1

-----VENC JPEGE ATTR -----------------------------------------------------------
      ID   RcvMode    MpfCnt      Mpf0Width     Mpf0Height      Mpf1Width     Mpf1Height
       1    Single         0              0              0              8              0


-----VENC CHN RECEIVE STAT-----------------------------------------------------
      ID       Start     StartEx    RecvLeft     EncLeft    JpegEncodeMode
       0           1           0           0           0                NA
       1           0           0           0           0               ALL
       2           1           0           0           0                NA

-----VENC VPSS QUERY-----------------------------------------------------------
      ID       Query     QueryOk     QueryFR       Invld        Full      VbFail   QueryFail     InfoErr        Stop
       0           0           0           0           0           0           0           0           0           0
       1           0           0           0           0           0           0           0           0           0
       2           0           0           0           0           0           0           0           0           0

-----VENC SEND1----------------------------------------------------------------
      ID     VpssSnd     VInfErr     OthrSnd     OInfErr        Send        Stop        Full     CropErr    DrectSnd     SizeErr
       0           0           0      138102           0      138102           0           0           0      138102           0
       1           0           0      138101           0           0      138101           0           0           0           0
       2      138101           0           0           0      138101           0           0           0      138101           0

-----VENC SEND2----------------------------------------------------------------
      ID     SendVgs     StartOk   StartFail       IntOk     IntFail      SrcAdd      SrcSub     DestAdd     DestSub
       0           0           0           0           0           0           0           0           0           0
       1           0           0           0           0           0           0           0           0           0
       2           0           0           0           0           0           0           0           0           0

-----VENC PIC QUEUE STATE------------------------------------------------------
      ID    Free    Busy     Vgs  BFrame
       0       6       0       0       0
       1       6       0       0       0
       2       6       0       0       0

-----VENC DCF/MPF QUEUE STATE------------------------------------------------------
      ID   ThumbFree   ThumbBusy    Mpf0Free    Mpf0Busy    Mpf1Free    Mpf1Busy
       0           0           0           6           0           6           0
       1           0           0           6           0           6           0
       2           0           0           6           0           6           0

-----VENC CHNL INFO------------------------------------------------------------
      ID         Inq       InqOk       Start     StartOk      Config     VencInt  ChaResLost    OverLoad    RingSkip      RcSkip
       0     1150917      138101      138101      138101      138101      138101           0           0           1           0 
       1      920741           0           0           0           0           0           0           0           0           0 
       2     1150908      138101      138101      138101      138101      138101           0           0           0           0 

-----VENC CROP INFO------------------------------------------------------------
      ID  CropEn  StartX  StartY   Width  Height
       0       N       0       0       0       0
       1       N       0       0       0       0
       2       N       0       0       0       0


-----ROI INFO------------------------------------------------------------------
     ID      Type     Index    bRoiEn    bAbsQp    Qp     Width    Height    StartX    StartY 


-----VENC STREAM STATE---------------------------------------------------------
      ID     FreeCnt     BusyCnt     UserCnt     UserGet     UserRls    GetTimes    Interval   FrameRate
       0           1           0           0      151913      151913      138101       66679          15
       1           0           0           0           0           0           0           0           0
       2           1           0           0      151916      151916      138101       65942          15


-----VENC PTS STATE---------------------------------------------------------
      ID RcvFirstFrmPts    RcvFrmPts 
       0       5532413    9212899112
       1             0             0
       2       5576823    9212908663


[VGS] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release],                    Build Time[Jun 17 2019, 11:19:14]


-----MODULE PARAM--------------------------------------------------------
    max_job_num   max_task_num   max_node_num bVgsHdrSupport  bVgsExitInSys
            128            200            200              0              1

-----RECENT JOB INFO1----------------------------------------------------
   SeqNo ModName  JobHdl TaskNum   State      InSize     OutSize    CostTime      HwTime

-----RECENT JOB INFO2----------------------------------------------------
   SeqNo    CmpMode CropEn CoverEn VhdrEn OsdEn ZmeEn LBAEn LumaEn FpdEn QuickCopyEn RotateEn StitchEn ByPassEn

-----MAX WASTE TIME JOB INFO1--------------------------------------------
   SeqNo ModName  JobHdl TaskNum   State      InSize     OutSize    CostTime      HwTime

-----MAX WASTE TIME JOB INFO2--------------------------------------------
   SeqNo    CmpMode CropEn CoverEn VhdrEn OsdEn ZmeEn LBAEn LumaEn FpdEn QuickCopyEn RotateEn StitchEn ByPassEn

-----VGS JOB STATUS------------------------------------------------------
   Success      Fail    Cancel  AllJobNum    FreeNum   BeginNum    BusyNum ProcingNum
         0         0         0        128        128          0          0          0

-----VGS TASK STATUS-----------------------------------------------------
   Success      Fail    Cancel AllTaskNum    FreeNum    BusyNum
         0         0         0        200        200          0

-----VGS NODE STATUS-----------------------------------------------------
   AllNodeNum     BusyNum     MinFree    MaxInJob  SubmitFail   IntFail
          200           0         200           0           0         0

[VI] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:14]


-------------------------------MODULE PARAM ---------------------------------------------------------------------------
      DetectErrFrame        DropErrFrame            VbSource
                   0                   0              Common

-------------------------------VI MODE -------------------------------------------------------------
  Pipe0Mode   Pipe1Mode
     online     offline
-------------------------------VPSS MODE -------------------------------------------------------------
  Pipe0Mode   Pipe1Mode
    offline     offline

-------------------------------VI DEV ATTR1----------------------------------------------------------------------------
  DevID   DevEn  BindPipe     Width    Height               IntfM     WkM     ComMsk0     ComMsk1   ScanM
      0       Y         Y      1280       720                  DC    1Mux    ffc00000           0       P

-------------------------------VI DEV ATTR2----------------------------------------------------------------------------
  DevID   AD0   AD1   AD2   AD3     Seq  DataType   DataRev    BasW    BasH   HReph   VReph   WDRMode  CacheLine  DataRate
      0    -1    -1    -1    -1    YUYV       RGB         N    1280     720    NONE    NONE      None        720        X1

-------------------------------VI BIND ATTR----------------------------------------------------------------------------
   DevID PipeNum              PipeId
       0       1                   0

-------------------------------VI DEV TIMING ATTR----------------------------------------------------------------------
  DevID DevTimingEn  DevFrmRate  DevWidth   DevHeight

-------------------------------VI PIPE ATTR1---------------------------------------------------------------------------
  PipeID  BypassMode YuvSkip IspBypass     Width    Height    PixFmt  BitWidth    NrEn SharpenEn  CompressMode
       0  BypassNone       N         N      1280       720     RAW10        10       Y         N          None

-------------------------------VI PIPE ATTR2---------------------------------------------------------------------------
  DiscProPic    SrcFRate    DstFRate FrameSource  RepeatMode   VCNum     IntType EarlyLine  VbPoolId
           N          -1          -1         DEV        NONE       0       START       128        -1

-------------------------------VI PIPE CROP ATTR-----------------------------------------------------------------------
  PipeID CropEn    CoorX   CoorY   Width  Height

-------------------------------VI PIPE USER PIC ATTR-------------------------------------------------------------------
  PipeID  Enable   ChnID    Mode BgColor   PicID   Width  Height  Stride  PixFmt  PoolID         PhyAddr

-------------------------------VI PIPE DUMP ATTR-----------------------------------------------------------------------
  PipeID    Enable     Depth  DumpType

-------------------------------VI CHN ATTR1----------------------------------------------------------------------------
  PipeID   ChnID   Width    Height    Mirror    Flip    SrcFRate    DstFRate    PixFmt      VideoFmt  DynamicRange
       0       0    1280       720         N       N          -1          -1     SP420        LINEAR          SDR8

-------------------------------VI CHN ATTR2----------------------------------------------------------------------------
  CompressMode     Depth     Align  VbPoolId
          None         0         0        -1

-------------------------------VI EXTCHN ATTR1-------------------------------------------------------------------------
  PipeID   ChnID  Source  SrcChn   Width    Height    SrcFRate    DstFRate    PixFmt  DynamicRange  CompressMode     Depth

-------------------------------VI EXTCHN ATTR2-------------------------------------------------------------------------
  Align  VbPoolId

-------------------------------VI CHN CROP INFO------------------------------------------------------------------------
  PipeID   ChnID  CropEn  CoorType   CoorX   CoorY   Width  Height   TrimX   TrimY TrimWid TrimHgt
       0       0       N       RIT       0       0       0       0       0       0    1280     720

-------------------------------VI CHN ROTATION INFO--------------------------------------------------------------------
  PipeID   ChnID    Rotation
       0       0           0

-------------------------------VI CHN LDCV3 INFO-------------------------------------------------------------------------

-------------------------------ISP 2DofDIS INFO------------------------------------------------------------------------
  PipeID  Enable
       0       N

-------------------------------VI CHN OUTPUT RESOLUTION----------------------------------------------------------------
  PipeID   ChnID  Enable  Mirror    Flip   Width  Height  PixFmt  VideoFmt  DynamicRange  CompressMode FrameRate
       0       0       Y       N       N    1280     720   SP420    LINEAR          SDR8          None        15

-------------------------------VI PIPE STATUS--------------------------------------------------------------------------
  PipeID  Enable    IntCnt FrameRate LostFrame  VbFail   Width  Height
       0       Y    138135         0         0       0    1280     720

-------------------------------VI CHN STATUS---------------------------------------------------------------------------
  PipeID   ChnID  Enable FrameRate LostFrame  VbFail   Width  Height
       0       0       Y        15        31      16    1280     720

-------------------------------VI PIPE Statistic-----------------------------------------------------------------------
  PipeID     RecvPic     LostCnt      BufCnt   CurSoftTm   MaxSoftTm   CurTaskTm   MaxTaskTm   LowBandWidth  BeBufNum
       0           0           0           0           0           0           0           0              0         0

-------------------------------VI HW STATISTIC-------------------------------------------------------------------------
  ProcIdx    HWCostTm MaxHWCostTm    CycleCnt MaxCycleCnt
        0           0           0           0           0

-------------------------------VI PROC OFFLINE IRQ STATISTIC----------------------------------------------------------
 ProcIdx       SubmitCnt          IntCnt         ListCnt  TmOutCnt BusErrCnt  DcmpErrCnt StartErrCnt  NodeIdErrCnt
       0               0               0               0         0         0           0           0             0

-------------------------------VI PROC ONLINE IRQ STATISTIC-----------------------------------------------------------
 ProcIdx          IntCnt     FrmStartCnt FrmErrCnt  FrmFlowCnt BusErrCnt    DcmpErrCnt  CfgLossCnt   FirstIntPts
       0          138135          138135        15           0         0             0           0       4965070

-------------------------------VI PROC COST TIME STATISTIC-----------------------------------------------------------
 ProcIdx    IntCntPerSec MaxIntCntPerSec  CurIntCostTm  MaxIntCostTm  TotalIntCostTm   IntTmPerSec  MaxIntTmPerSec
       0              16              30           466           511        63956679          7397            7475

-------------------------------VI DEV DETECT INFO----------------------------------------------------------------------
   DevID  ValidWidth ValidHeight  TotalWidth
       0        1280         720        2399

-------------------------------VI BAS DETECT INFO----------------------------------------------------------------------
   DevID  ValidWidth ValidHeight  TotalWidth

-------------------------------VI ISP DETECT INFO----------------------------------------------------------------------
   ISPID  ValidWidth ValidHeight  TotalWidth
       0        1280         720        2399

[VPSS] Version: [Hi3516EV200_MPP_V1.0.1.1 B030 Release], Build Time[Jun 17 2019, 11:19:14]


-------------------------------MODULE PARAM----------------------------------------------------------
u32VpssVbSource    bOneBufferforLowDelay    u32VpssSplitNodeNum    bHdrSupport    bNrQuickStart
              0                        0                      3              0                0

-------------------------------VPSS GRP ATTR---------------------------------------------------------
   GrpID    MaxW    MaxH      PixFmt    DRange  SrcFRate  DstFRate bUserCtrl    NrEn    NrType    RefCmp  MotionMode
       0    1280     720   YVU-SP420      SDR8        -1        -1         Y       Y     VIDEO         Y      Normal

-------------------------------VPSS CHN ATTR---------------------------------------------------------
   GrpID  PhyChnID  Enable    Mode   Width  Height  SrcFRate  DstFRate   Depth   Align  MirrorEn  FlipEn  bBufferShare  ProcMode
       0         0       Y    USER    1280     720        -1        -1       0       0         N       N             N     VIDEO
       0         1       Y    USER     640     480        -1        -1       0       0         N       N             N     VIDEO
       0         2       Y    USER     640     360        -1        -1       1       0         N       N             N     VIDEO

-------------------------------VPSS EXT-CHN ATTR--------------------------------------------------
   GrpID  ExtChnID  Enable  SrcChn   Width  Height  SrcFRate  DstFRate   Depth   Align  ProcMode

-------------------------------VPSS GRP CROP INFO-----------------------------------------------------
   GrpID  CropEn  CoorType   CoorX   CoorY   Width  Height    OriW    OriH   TrimX   TrimY TrimWid TrimHgt
       0       N       RAT       0       0       0       0

-------------------------------VPSS CHN CROP INFO-----------------------------------------------------
   GrpID   ChnID  CropEn  CoorType   CoorX   CoorY   Width  Height   TrimX   TrimY TrimWid TrimHgt
       0       0       N       RAT       0       0       0       0
       0       1       N       RAT       0       0       0       0
       0       2       N       RAT       0       0       0       0

-------------------------------VPSS GRP PIC QUEUE----------------------------------------------------
   GrpID  FreeLen0  BusyLen0     Delay    Backup
       0         8         0         0         0

-------------------------------VPSS GRP PIC INFO---------------------------------------------------
   GrpID   Width  Height      Pixfmt    Videofmt      DRange    Compress
       0    1280     720   YVU-SP420      LINEAR        SDR8           N

-------------------------------VPSS GRP WORK STATUS---------------------------------------------------
   GrpID    RecvPic0 ViLost0 VdecLost0       NewDo   OldDo NewUnDo     OldUnDo     StartFl  bStart  CostTm MaxCostTm
       0      138103       0         0      138103       0       0           0           0       Y   10201     10359

-------------------------------VPSS CHN OUTPUT RESOLUTION--------------------------------------------
   GrpID   ChnID  Enable   Width  Height      Pixfmt    Videofmt      DRange    Compress      SendOk   FrameRate
       0       0       Y    1280     720   YVU-SP420      LINEAR        SDR8           Y      138103          15
       0       1       Y     640     480   YVU-SP420      LINEAR        SDR8           N      138101          15
       0       2       Y     640     360   YVU-SP420      LINEAR        SDR8           N           0          15

-------------------------------VPSS 3DNR X PARAM------------------------------------------------------
-------------------------------VPSS GPR0 3DNR PARAM-------------------------------------
   GrpID    Intf   Version   OptMode       ISO     Ref
       0    NR_X     VER_3    MANUAL       110       1
   NRyEn_0                   NRyEn_1                   NRyEn_2                   NRyEn_3
         1                         1                         1                         1
    SFS2_0                    SFS2_1                    SFS2_2                    SFS2_3
        20                        20                        20                        20
    SFS4_0                    SFS4_1                    SFS4_2                    SFS4_3
        20                        20                        20                        10
     TFS_0              TFS0_1        TFS1_1             TFS_2
         1                   7            10                10
                       MATH0_1       MATH1_1            MATH_2                    MATH_3
                            60           150               120                       150

-------------------------------VPSS CHN LBA ATTR---------------------------------------------------------
   GrpID   ChnID  Aspect  videoX  videoY  videoW  videoH     BgColor

-------------------------------VPSS CHN ROTATE ATTR---------------------------------------------------
   GrpID   ChnID  Rotate

-------------------------------VPSS CHN LDCV3 ATTR----------------------------------------------------
   GrpID   ChnID  Enable  viewType   XOffset   YOffset       DistortionRatio       MinRatio

-------------------------------VPSS CHN LOWDELAY ATTR-------------------------------------------------
   GrpID   ChnID  Enable   LineCnt   OneBufEnable   OneBufAddr
       0       0       Y         1              N   0x4318b3c0

-------------------------------VPSS CHN BUF WRAP ATTR------------------------------------------------
   GrpID   ChnID  Enable   BufLine   WrapBufSize
       0       0       Y       160        307200

-------------------------------FRAME INTERRUPT ATTR---------------------------------------------------
   GrpID        IntType      EarlyLine
       0              -              0

-------------------------------VPSS GRP PIC PTS---------------------------------------------------------
   GrpID         FirstPicPTS           CurPicPTS
       0                   0                   0

-------------------------------DRV WORK STATUS--------------------------------------------------------
       StartSuc0       StartSuc1         LinkInt   StartErr0  NodeIdErr0   StartErr1  NodeIdErr1      BusErr
          138103               0          138102           0           0           0           0           0

-------------------------------DRV NODE QUEUE---------------------------------------------------------
   FreeNum   WaitNum  Busy00  Busy01    Sel0  Busy10  Busy11    Sel1    Proc
         8         0       1       0       0       0       0       0       1

-------------------------------INT WORK STATUS--------------------------------------------------------
     CntPerSec  MaxCntPerSec        CostTm    MostCostTm  CostTmPerSec MCostTmPerSec
            31            31           407           431          8443          8617

```

</details>
