# baseline_cdistro_mgmt

#### Table of Contents

1. [Overview](#overview)
2. [Common Switches to use with dmidecode](#common-switches-to-use-with-dmidecode)
3. [Example Results from a VM](#example-results-from-a-vm)
    * [-s (string) Checks VM](#-s-string-checks-vm)
    * [-t (string) Checks VM](#-t-string-checks-vm)
4. [Example Results from Physical Machine](#example-results-from-physical-machine)
    * [-s (string) Checks Physical](#-s-string-checks-physical)
    * [-t (string) Checks Physical](#-t-string-checks-physical)

## Overview

__dmidecode__ is a linux command, found commonly on any Red Hat variant of Linux, and possibly
 on others too.
 Execute `man dmidecode` in order to learn more about this tool.

__ALWAYS execute dmidecode as the Root User.__

## Common Switches to use with dmidecode

`-s or --string`    : is for string matching _KEYWORD_ as __dmidecode__ refers to it, and
> Only display the value of the DMI string identified by KEYWORD.

> __KEYWORD__ must be a keyword  from  the  following list:
__bios-vendor,  bios-version,  bios-release-date, system-manufacturer, system-product-name, system-version, system-serial-number, system-uuid,
baseboard-manufacturer, baseboard-product-name, baseboard-version, baseboard-serial-number,  baseboard-asset-tag, chassis-manufacturer,
chassis-type, chassis-version, chassis-serial-number, chassis-asset-tag, processor-family, processor-manufacturer, processor-version, processor-frequency__.
Each  keyword corresponds to a given DMI type and a given offset within this entry type.  Not all strings may be meaningful or even defined on all systems.
Some keywords may return more than one result on some systems (e.g.  processor-version on a multi-processor system).

> If __KEYWORD__ is not provided or not valid, a list of all valid keywords is printed and dmidecode exits with an error.  This option cannot be used more than once.


`-t`    : is for the __TYPE__ matching as defined by the __dmidecode__ command.
> Only display the entries of type TYPE.
> TYPE can be either a DMI type number, or a comma-separated list  of  type numbers,  or a keyword from the following list:
__(0)bios, (1)system, (2)baseboard, (3)chassis, (4)processor, (5)memory, (6)cache, (7)connector, (8)slot__.
Refer to the DMI TYPES section below for details.  If this option is used more than once, the  set of displayed entries will be the union of all the given
types.

> If TYPE is not provided or not valid, a list of all valid keywords is printed and dmidecode exits with an error.

With these two (2) switch options you can learn a lot of detail about systems.


## Example Results from a VM
###  -s (string) Checks VM
`dmidecode -s bios-vendor`
> Phoenix Technologies LTD

`dmidecode -s bios-version`
> 6.00

`dmidecode -s bios-release-date`
> 04/14/2014

`dmidecode -s system-manufacturer`
> VMware, Inc.

`dmidecode -s system-product-name`
> VMware Virtual Platform

`dmidecode -s system-serial-number`
> VMware-42 3c 77 ea 6a c3 3f d4-62 2c 2c 01 3b 55 bc 8e

`dmidecode -s system-uuid`
> 423C77EA-6AC3-3FD4-622C-2C013B55BC8E

`dmidecode -s chassis-type`
> Other

`dmidecode -s baseboard-version`
> None

`dmidecode -s processor-family`
> Unknown
> Unknown
> .......
> Unknown

`dmidecode -s processor-manufacturer`
> GenuineIntel
> 000000000000
> 000000000000
> 000000000000
> 000000000000
> 000000000000
> ............
> 000000000000

`dmidecode -s processor-version`
> Intel(R) Xeon(R) CPU E7- 4830  @ 2.13GHz
> Unknown Processor
> Unknown Processor
> Unknown Processor
> .................
> Unknown Processor

`dmidecode -s processor-frequency`
> 2133 MHz
> Unknown
> Unknown
> .......
> Unknown



###  -t (string) Checks VM
`dmidecode -t 0`
> # dmidecode 2.12
> SMBIOS 2.4 present.
> 
> Handle 0x0000, DMI type 0, 24 bytes

> BIOS Information

>         Vendor: Phoenix Technologies LTD
>         Version: 6.00
>         Release Date: 04/14/2014
>         Address: 0xEA050
>         Runtime Size: 90032 bytes
>         ROM Size: 64 kB
>         Characteristics:
>                  ISA is supported
>                  PCI is supported
>                  PC Card (PCMCIA) is supported
>                  PNP is supported
>                  APM is supported
>                  BIOS is upgradeable
>                  BIOS shadowing is allowed
>                  ESCD support is available
>                  Boot from CD is supported
>                  Selectable boot is supported
>                  EDD is supported
>                  Print screen service is supported (int 5h)
>                  8042 keyboard services are supported (int 9h)
>                  Serial services are supported (int 14h)
>                  Printer services are supported (int 17h)
>                  CGA/mono video services are supported (int 10h)
>                  ACPI is supported
>                  Smart battery is supported
>                  BIOS boot specification is supported
>                  Function key-initiated network boot is supported
>                  Targeted content distribution is supported
>                  BIOS Revision: 4.6
>                  Firmware Revision: 0.0


`dmidecode -t 1`
> # dmidecode 2.12
> SMBIOS 2.4 present.

> Handle 0x0001, DMI type 1, 27 bytes

> System Information

>         Manufacturer: VMware, Inc.
>         Product Name: VMware Virtual Platform
>         Version: None
>         Serial Number: VMware-42 3c 77 ea 6a c3 3f d4-62 2c 2c 01 3b 55 bc 8e
>         UUID: 423C77EA-6AC3-3FD4-622C-2C013B55BC8E
>         Wake-up Type: Power Switch
>         SKU Number: Not Specified
>         Family: Not Specified


`dmidecode -t 2`
> # dmidecode 2.12
> SMBIOS 2.4 present.
> 
> Handle 0x0002, DMI type 2, 15 bytes

> Base Board Information

>         Manufacturer: Intel Corporation
>         Product Name: 440BX Desktop Reference Platform
>         Version: None
>         Serial Number: None
>         Asset Tag: Not Specified
>         Features: None
>         Location In Chassis: Not Specified
>         Chassis Handle: 0x0000
>         Type: Unknown
>         Contained Object Handles: 0

`dmidecode -t 4`
> # dmidecode 2.12
> SMBIOS 2.4 present.
> 
> Handle 0x0004, DMI type 4, 35 bytes

> Processor Information

>         Socket Designation: CPU socket #0
>         Type: Central Processor
>         Family: Unknown
>         Manufacturer: GenuineIntel
>         ID: 51 06 02 00 FF FB AB 0F
>         Version:        Intel(R) Xeon(R) CPU E7- 4830  @ 2.13GHz
>         Voltage: 3.3 V
>         External Clock: Unknown
>         Max Speed: 30000 MHz
>         Current Speed: 2133 MHz
>         Status: Populated, Enabled
>         Upgrade: ZIF Socket
>         L1 Cache Handle: 0x0054
>         L2 Cache Handle: 0x0055
>         L3 Cache Handle: Not Provided
>         Serial Number: Not Specified
>         Asset Tag: Not Specified
>         Part Number: Not Specified
> 
> Handle 0x0005, DMI type 4, 35 bytes

> Processor Information

>         Socket Designation: CPU socket #1
>         Type: Central Processor
>         Family: Unknown
>         Manufacturer: 000000000000
>         ID: 00 00 00 00 00 00 00 00
>         Version: Unknown Processor
>         Voltage: 3.3 V
>         External Clock: Unknown
>         Max Speed: 30000 MHz
>         Current Speed: Unknown
>         Status: Unpopulated
>         Upgrade: ZIF Socket
>         L1 Cache Handle: 0x0056
>         L2 Cache Handle: 0x0057
>         L3 Cache Handle: Not Provided
>         Serial Number: Not Specified
>         Asset Tag: Not Specified
>         Part Number: Not Specified

## Example Results from Physical Machine 
###  -s (string) Checks Physical
`dmidecode -s bios-vendor`
> Dell Inc.

`dmidecode -s bios-version`
> A15

`dmidecode -s bios-release-date`
> 02/02/2015

`dmidecode -s system-manufacturer`
> Dell Inc.

`dmidecode -s system-product-name`
> Precision T1700

`dmidecode -s system-serial-number`
> HFQ5R52

`dmidecode -s system-uuid`
> 4C4C4544-0046-5110-8035-C8C04F523532

`dmidecode -s processor-family`
> Core i7

`dmidecode -s processor-manufacturer`
> Intel

`dmidecode -s processor-version`
> Intel(R) Core(TM) i7-4790 CPU @ 3.60GHz

`dmidecode -s processor-frequency`
> 3600 MHz



###  -t (string) Checks Physical
`dmidecode -t 0`
> # dmidecode 2.12-dmifs
> SMBIOS 2.7 present.
> 
> Handle 0x0000, DMI type 0, 24 bytes

> BIOS Information

>         Vendor: Dell Inc.
>         Version: A15
>         Release Date: 02/02/2015
>         Address: 0xF0000
>         Runtime Size: 64 kB
>         ROM Size: 12288 kB
>         Characteristics:
>                 PCI is supported
>                 PNP is supported
>                 BIOS is upgradeable
>                 BIOS shadowing is allowed
>                 Boot from CD is supported
>                 Selectable boot is supported
>                 EDD is supported
>                 5.25"/1.2 MB floppy services are supported (int 13h)
>                 3.5"/720 kB floppy services are supported (int 13h)
>                 3.5"/2.88 MB floppy services are supported (int 13h)
>                 Print screen service is supported (int 5h)
>                 8042 keyboard services are supported (int 9h)
>                 Serial services are supported (int 14h)
>                 Printer services are supported (int 17h)
>                 ACPI is supported
>                 USB legacy is supported
>                 BIOS boot specification is supported
>                 Function key-initiated network boot is supported
>                 Targeted content distribution is supported
>                 UEFI is supported
>                 BIOS Revision: 4.6


`dmidecode -t 1`
> # dmidecode 2.12-dmifs
> SMBIOS 2.7 present.
 
> Handle 0x0001, DMI type 1, 27 bytes

> System Information

>         Manufacturer: Dell Inc.
>         Product Name: Precision T1700
>         Version: 01
>         Serial Number: HFQ5R52
>         UUID: 4C4C4544-0046-5110-8035-C8C04F523532
>         Wake-up Type: Power Switch
>         SKU Number: Precision T1700
>         Family: Not Specified


`dmidecode -t 2`
> # dmidecode 2.12-dmifs
> SMBIOS 2.7 present.
 
> Handle 0x0002, DMI type 2, 15 bytes

> Base Board Information

>         Manufacturer: Dell Inc.
>         Product Name: 048DY8
>         Version: A01
>         Serial Number: /HFQ5R52/CN7220054F01C3/
>         Asset Tag: Not Specified
>         Features:
>                 Board is a hosting board
>                 Board is replaceable
>         Location In Chassis: Not Specified
>         Chassis Handle: 0x0003
>         Type: Motherboard
>         Contained Object Handles: 0


`dmidecode -t 4`
> # dmidecode 2.12-dmifs
> SMBIOS 2.7 present.
 
> Handle 0x003A, DMI type 4, 42 bytes

> Processor Information

>         Socket Designation: SOCKET 0
>         Type: Central Processor
>         Family: Core i7
>         Manufacturer: Intel
>         ID: C3 06 03 00 FF FB EB BF
>         Signature: Type 0, Family 6, Model 60, Stepping 3
>         Flags:
>                 FPU (Floating-point unit on-chip)
>                 VME (Virtual mode extension)
>                 DE (Debugging extension)
>                 PSE (Page size extension)
>                 TSC (Time stamp counter)
>                 MSR (Model specific registers)
>                 PAE (Physical address extension)
>                 MCE (Machine check exception)
>                 CX8 (CMPXCHG8 instruction supported)
>                 APIC (On-chip APIC hardware supported)
>                 SEP (Fast system call)
>                 MTRR (Memory type range registers)
>                 PGE (Page global enable)
>                 MCA (Machine check architecture)
>                 CMOV (Conditional move instruction supported)
>                 PAT (Page attribute table)
>                 PSE-36 (36-bit page size extension)
>                 CLFSH (CLFLUSH instruction supported)
>                 DS (Debug store)
>                 ACPI (ACPI supported)
>                 MMX (MMX technology supported)
>                 FXSR (FXSAVE and FXSTOR instructions supported)
>                 SSE (Streaming SIMD extensions)
>                 SSE2 (Streaming SIMD extensions 2)
>                 SS (Self-snoop)
>                 HTT (Multi-threading)
>                 TM (Thermal monitor supported)
>                 PBE (Pending break enabled)
>         Version: Intel(R) Core(TM) i7-4790 CPU @ 3.60GHz
>         Voltage: 1.2 V
>         External Clock: 100 MHz
>         Max Speed: 3800 MHz
>         Current Speed: 3600 MHz
>         Status: Populated, Enabled
>         Upgrade: Other
>         L1 Cache Handle: 0x003B
>         L2 Cache Handle: 0x003C
>         L3 Cache Handle: 0x003D
>         Serial Number: Not Specified
>         Asset Tag: Fill By OEM
>         Part Number: Fill By OEM
>         Core Count: 4
>         Core Enabled: 4
>         Thread Count: 8
>         Characteristics:
>                 64-bit capable

