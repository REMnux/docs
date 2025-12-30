---
description: Statically Analyze Code
---

# PE Files

## Malchive

Perform static analysis of various aspects of malicious code.

**Website**: [https://github.com/MITRECND/malchive](https://github.com/MITRECND/malchive)\
**Author**: The MITRE Corporation, [https://github.com/MITRECND/malchive/graphs/contributors](https://github.com/MITRECND/malchive/graphs/contributors)\
**License**: License 2.0: [https://github.com/MITRECND/malchive/blob/main/LICENSE](https://github.com/MITRECND/malchive/blob/main/LICENSE)\
**Notes**: Malchive command-line tools start with the prefix `malutil-`. See [utilities documentation](https://github.com/MITRECND/malchive/wiki/Utilities) for details.\
**State File**: [remnux.python3-packages.malchive](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/malchive.sls)

## Speakeasy

Emulate code execution, including shellcode, Windows drivers, and Windows PE files.

**Website**: [https://github.com/fireeye/speakeasy](https://github.com/fireeye/speakeasy)\
**Author**: FireEye Inc, Andrew Davis\
**License**: MIT License: [https://github.com/fireeye/speakeasy/blob/master/LICENSE.txt](https://github.com/fireeye/speakeasy/blob/master/LICENSE.txt)\
**Notes**: To run the tool, use `speakeasy`, `emu_exe.py`, and `emu_dll.py` commands.\
**State File**: [remnux.python3-packages.speakeasy](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/speakeasy.sls)



## binee (Binary Emulation Environment)

Analyze I/O operations of a suspicious PE file by emulating its execution.

**Website**: [https://github.com/carbonblack/binee](https://github.com/carbonblack/binee)\
**Author**: Carbon Black, Kyle Gwinnup, John Holowczak\
**License**: GNU General Public License (GPL) v2: [https://github.com/carbonblack/binee/blob/master/LICENSE](https://github.com/carbonblack/binee/blob/master/LICENSE)\
**Notes**: Before using this tool, place the files your sample requires under /opt/binee-files/win10\_32. For example, the Windows DLLs it needs should go /opt/binee-files/win10\_32/windows/system32. If you have a Windows 10 64-bit system, you can get the 32-bit DLLs from C:\Windows\SysWOW64 To check which DLLs you might need by examining the import table using the "-i" parameter.\
**State File**: [remnux.packages.binee](https://github.com/REMnux/salt-states/blob/master/remnux/packages/binee.sls)

## mbcscan

Scan a PE file to list the associated Malware Behavior Catalog (MBC) details.

**Website**: [https://github.com/accidentalrebel/mbcscan](https://github.com/accidentalrebel/mbcscan)\
**Author**: Karlo Licudine: [https://twitter.com/accidentalrebel](https://twitter.com/accidentalrebel)\
**License**: GNU General Public License (GPL) v3.0: [https://github.com/accidentalrebel/mbcscan/blob/master/LICENSE](https://github.com/accidentalrebel/mbcscan/blob/master/LICENSE)\
**Notes**: mbcscan.py\
**State File**: [remnux.scripts.mbcscan](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/mbcscan.sls)

## capa

Detect suspicious capabilities in PE files.

**Website**: [https://github.com/fireeye/capa](https://github.com/fireeye/capa)\
**Author**: FireEye Inc, Willi Ballenthin: [https://twitter.com/williballenthin](https://twitter.com/williballenthin), Moritz Raabe: [https://twitter.com/m\_r\_tz](https://twitter.com/m_r_tz)\
**License**: Apache License 2.0: [https://github.com/fireeye/capa/blob/master/LICENSE.txt](https://github.com/fireeye/capa/blob/master/LICENSE.txt)\
**State File**: [remnux.tools.capa](https://github.com/REMnux/salt-states/blob/master/remnux/tools/capa.sls)
