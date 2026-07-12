# Celestica DU-PCB-001-003 Board Repository

Celestica DU-PCB-001-003, also known as SCH-001-003 or *Baidu 2015 FPGA board,* is a
proprietary accelerator card. This card based on an AMD (Xilinx) XC7K480T FPGA
chip.

DU-PCB-001-003 has some compatibility with YPCB-00338-1P1 that can be programmed with free and
open-source tools [thanks to Tifer King].

## Hardware Specification

- FPGA: AMD (Xilinx) XC7K480T-2FFG1156I
  - Package: 1156-pin BGA
  - Speed grade: -2
  - Temperature range: Industrial
- DRAM: 18x SK Hynix H5TC2G83FFR (256 MiB)
  - 4 GiB Data + 512 MiB ECC Parity (?)
- Flash: Micron MT28GU512AAA1EGC-0SIT (64 MiB)
  - FBGA code: RB119
- Data transfer interface: PCI Express 2.0 x8
- Debug interface: AMD (Xilinx) standard JTAG (14-pin)

(If you have a DU-PCB-001-003 with a different DRAM or flash chip, inform me or [omasanori] via GitHub issues.)

## Contents

 - constraints: The constraint file describes the function of the pins.
 - documents: Reference document.
 - examples: Sample project.
 - ypcb003381p1: Board files.

## How to use Vivado Board Package

Copy the folder ypcb003381p1 into Vivado/\<version\>/data/boards/board_files/. If the board_files directory does not exist, create it yourself.

To create a new project in Vivado, select "YPCB-00338-1P1 Accelerator Card".

## How to Dump the Original Configuration from Flash

1. Connect to the device's 14-pin debug interface. I used JTAG-HS3.
2. Launch Vivado Hardware Manager. Lab Edition is fine.
3. Click the *Open Target* and choose *Auto Connect*
4. Right-click *xc7k480t_0* and choose *Add Configuration Memory Device...*
5. Filter with:
   - Manufacturer: Micron
   - Density: 512
   - Width: 16
   - Type: bpi
6. Choose *mt28gu512aax1e-bpi-x16* or similar.
7. Right-click *mt28gu512aax1e-bpi-x16* (or similar) and choose *Readback
   Configuration Memory Device...*
8. Set appropriate options and click *OK*

## Detailed information

For more detailed information, please refer blog:

https://www.tiferking.cn/index.php/2024/12/19/650/

## Special Thanks

- [Tifer King](https://github.com/TiferKing)
- [omasanori](https://github.com/omasanori)

## License

Unless otherwise noted, this project is published under the terms of the MIT
license. See LICENSE for details.

[thanks to Tifer King]: https://github.com/TiferKing/ypcb_00338_1p1_hack
[omasanori]: https://github.com/omasanori/sch-001-003-hack.git

<!--
  -- SPDX-FileCopyrightText: 2026 Masanori Ogino
  --
  -- SPDX-License-Identifier: MIT
  -->
