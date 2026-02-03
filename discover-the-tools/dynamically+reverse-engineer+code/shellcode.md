---
description: Dynamically Reverse-Engineer Code
---

# Shellcode

## shcode2exe

Convert 32 and 64-bit shellcode to a Windows executable file.

**Website**: [https://github.com/accidentalrebel/shcode2exe](https://github.com/accidentalrebel/shcode2exe)\
**Author**: Karlo Licudine: [https://x.com/accidentalrebel](https://x.com/accidentalrebel)\
**License**: GNU General Public License (GPL) v3.0: [https://github.com/accidentalrebel/shcode2exe/blob/master/LICENSE](https://github.com/accidentalrebel/shcode2exe/blob/master/LICENSE)\
**State File**: [remnux.scripts.shcode2exe](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/shcode2exe.sls)


## shellcode2exe.bat

Convert 32 and 64-bit shellcode to a Windows executable file.

**Website**: [https://github.com/repnz/shellcode2exe](https://github.com/repnz/shellcode2exe)\
**Author**: Ori Damari: [https://x.com/0xrepnz](https://x.com/0xrepnz)\
**License**: Free, unknown license\
**Notes**: Use full path name to specify the input file; look for the output file in /usr/local/shellcode2exe-bat\
**State File**: [remnux.tools.shellcode2exe-bat](https://github.com/REMnux/salt-states/blob/master/remnux/tools/shellcode2exe-bat.sls)


## scdbg

Analyze shellcode by emulating its execution.

**Website**: [http://sandsprite.com/blogs/index.php?uid=7\&pid=152](http://sandsprite.com/blogs/index.php?uid=7\&pid=152)\
**Author**: David Zimmer\
**License**: Free, unknown license\
**Notes**: scdbg (GUI), scdbgc (console). Due to a compatibility issue, this tool is not available on an Ubuntu 20.04 SIFT Workstation system to which REMnux was added.\
**State File**: [remnux.packages.scdbg](https://github.com/REMnux/salt-states/blob/master/remnux/packages/scdbg.sls)

## runsc

Run shellcode to trace and analyze its execution.

**Website**: [https://github.com/edygert/runsc](https://github.com/edygert/runsc)\
**Author**: Evan Dygert: [https://x.com/edygert](https://x.com/edygert)\
**License**: MIT License: [https://github.com/edygert/runsc/blob/main/LICENSE](https://github.com/edygert/runsc/blob/main/LICENSE)\
**Notes**: Use the `tracesc` command to execute runsc within Wine in a way that traces the execution of shellcode. WARNING! This wrapper will actually execute the shellcode on the system, which might lead to your system becoming infected. Only use this wrapper in an properly configured, isolated laboratory environment, which you can return to a pristine state at the end of your analysis.\
**State File**: [remnux.packages.runsc](https://github.com/REMnux/salt-states/blob/master/remnux/packages/runsc.sls)


## Speakeasy

Emulate code execution, including shellcode, Windows drivers, and Windows PE files.

**Website**: [https://github.com/fireeye/speakeasy](https://github.com/fireeye/speakeasy)\
**Author**: FireEye Inc, Andrew Davis\
**License**: MIT License: [https://github.com/fireeye/speakeasy/blob/master/LICENSE.txt](https://github.com/fireeye/speakeasy/blob/master/LICENSE.txt)\
**Notes**: To run the tool, use `speakeasy`, `emu_exe.py`, and `emu_dll.py` commands.\
**State File**: [remnux.python3-packages.speakeasy](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/speakeasy.sls)



## Qiling

Emulate code execution of PE files, shellcode, etc. for a variety of OS and hardware platforms.

**Website**: [https://www.qiling.io](https://www.qiling.io)\
**Author**: [https://github.com/qilingframework/qiling/blob/master/AUTHORS.TXT](https://github.com/qilingframework/qiling/blob/master/AUTHORS.TXT)\
**License**: GNU General Public License (GPL) v2.0: [https://github.com/qilingframework/qiling/blob/master/COPYING](https://github.com/qilingframework/qiling/blob/master/COPYING)\
**Notes**: Use `qltool` to analyze artifacts. Before analyzing Windows artifacts, gather Windows DLLs and other components using the [dllscollector.bat](https://github.com/qilingframework/qiling/blob/master/examples/scripts/dllscollector.bat) script. Read the tool's [documentation](https://docs.qiling.io) to get started.\
**State File**: [remnux.python3-packages.qiling](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/qiling.sls)

## cut-bytes.py

Cut out a part of a data stream.

**Website**: [https://blog.didierstevens.com/2015/10/14/cut-bytes-py/](https://blog.didierstevens.com/2015/10/14/cut-bytes-py/)\
**Author**: Didier Stevens: [https://twitter.com/DidierStevens](https://twitter.com/DidierStevens)\
**License**: Public Domain\
**State File**: [remnux.scripts.cut-bytes](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/cut-bytes.sls)

## libemu

A library for x86 code emulation and shellcode detection.

**Website**: [https://github.com/buffer/libemu](https://github.com/buffer/libemu)\
**Author**: [https://github.com/buffer/libemu/blob/master/AUTHORS](https://github.com/buffer/libemu/blob/master/AUTHORS)\
**License**: Free, unknown license\
**State File**: [remnux.packages.libemu](https://github.com/REMnux/salt-states/blob/master/remnux/packages/libemu.sls)


## XORSearch

Locate and decode strings obfuscated using common techniques.

**Website**: [https://blog.didierstevens.com/programs/xorsearch/](https://blog.didierstevens.com/programs/xorsearch/)\
**Author**: Didier Stevens: [https://x.com/DidierStevens](https://x.com/DidierStevens)\
**License**: Public Domain\
**Notes**: xorsearch\
**State File**: [remnux.packages.xorsearch](https://github.com/REMnux/salt-states/blob/master/remnux/packages/xorsearch.sls)

