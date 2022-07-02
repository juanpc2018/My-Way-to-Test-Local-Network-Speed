# Test-Local-Network-Speed

Local Network Speed depends in many different variables.
the Network Adapters, the drivers, the configuration, if has Router or Switch or Direct Connection, PCIe slot, CPU PCIe lanes available, etc.. 

if you have SFP+ 10G Lc-Lc, like Marvell AQtion, Intel, etc...

The best / fastest possible method is Direct connection,
Computer1<--->Computer2

but Using more than 2 computers becomes a problem,
you need to Bridge Network Adapters to make visible the Computer1 with Computer3.
Computer1<--->Computer2<--->Computer3

Bridge is CPU intensive, Bridge computer must be Dedicated Machine for Best Performance.

Other method is using Dedicated Routers / Switch.
there are Many Brands, i like MikroTik, the OS is very complete.
Network Bridge using Windows is very limited / basic.

has NAT, UPnP, Firewall, etc...

Problem is the CPU, 
The Fastest Router for SFP+ 10G
is the 8 port ccr1072-8g+
72-Cores at 1GHz, Tile-x72 CPU,
No bottle Necks.
but very $$, has 4 fans, makes noise, fans does Not shutdown, etc...

second best option:
ccr2004 12g+
has a 4-core ARMv8 CPU, the fastest single core 1.7Ghz.
has dual SFP28 ports.

Entry level rack mount option:
CRS317 16g+
2-core ARM cpu, 800Mhz.

ther are smallers 4x port, Non rackmount.

with the lowest option, crs317,
when only 2 Networks are connected, has a "Turbo" mode,
and the maximum speed posible is 500MB/s

¿How to test that?
Easy...
Create Ram drive in both PCs,
OSX, Windows, Linux,

OSX has a free gui software,
Windows has 4GB Free software from AMD / Dataram Ramdisk / Ramdrive.
Linux best driver is rapiddisk 8.2.0, but all Linux have built-in ram drive drivers.

Transfer a 3GB / 4GB .ISO 
a Kubuntu or any other .iso
Ram to Ram.
That will avoid variables like SSD/HDD/SATA speed bottlenecks.

Move the File Back & forth, Cut&Paste.
You can optimize driver settings like MTU from 1500 to 9000,
DDR3 1333MHz is much faster, will have No bottlenecks.
DDR3 1600MHz is even faster,

$ sudo dmidecode --type 17

ECC Registered memory is a bit slower vs. Unbuffered ECC Memory.
but safer in very large configurations.
when large RAM drive is needed 24/7.

SFP+ 10G maximum speed is 1250 MB/s.

Testing Faster Network Adapters requires Faster Machines.
SFP28 = 25Gb = 3125 MB/s.
QSFP+ = 40Gb = 5000 MB/s = 5GB/s.
