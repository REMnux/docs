---
description: Statically Analyze Code
---

# PE Files

## binee \(Binary Emulation Environment\)

Analyze I/O operations of a suspicious PE file by emulating its execution.

**Website**: [https://github.com/carbonblack/binee](https://github.com/carbonblack/binee)  
**Author**: Carbon Black, Kyle Gwinnup, John Holowczak  
**License**: GNU General Public License \(GPL\) v2: [https://github.com/carbonblack/binee/blob/master/LICENSE](https://github.com/carbonblack/binee/blob/master/LICENSE)  
**Notes**: Before using this tool, place the files your sample requires under /opt/binee-files/win10\_32. For example, the Windows DLLs it needs should go /opt/binee-files/win10\_32/windows/system32. If you have a Windows 10 64-bit system, you can get the 32-bit DLLs from C:\Windows\SysWOW64 To check which DLLs you might need by examining the import table using the "-i" parameter.  
**State File**: [remnux.packages.binee](https://github.com/REMnux/salt-states/blob/master/remnux/packages/binee.sls)

## capa

Detect suspicious capabilites in PE files.

**Website**: [https://github.com/fireeye/capa](https://github.com/fireeye/capa)  
**Author**: FireEye Inc, Willi Ballenthin: [https://twitter.com/williballenthin](https://twitter.com/williballenthin), Moritz Raabe: [https://twitter.com/m\_r\_tz](https://twitter.com/m_r_tz)  
**License**: Apache License 2.0: [https://github.com/fireeye/capa/blob/master/LICENSE.txt](https://github.com/fireeye/capa/blob/master/LICENSE.txt)  
**State File**: [remnux.packages.capa](https://github.com/REMnux/salt-states/blob/master/remnux/packages/capa.sls)

