---
description: Dynamically Reverse-Engineer Code
---

# Shellcode

## XORSearch

Locate and decode strings obfuscated using common techniques.

**Website**: [https://blog.didierstevens.com/programs/xorsearch/](https://blog.didierstevens.com/programs/xorsearch/)  
**Author**: Didier Stevens: [https://twitter.com/DidierStevens](https://twitter.com/DidierStevens)  
**License**: Public Domain  
**Notes**: xorsearch  
**State File**: [remnux.tools.xorsearch](https://github.com/REMnux/salt-states/blob/master/./remnux/tools/xorsearch.sls)

## shellcode2exe.bat

Convert 32 and 64-bit shellcode to a Windows executable file.

**Website**: [https://github.com/repnz/shellcode2exe](https://github.com/repnz/shellcode2exe)  
**Author**: Ori Damari: [https://twitter.com/0xrepnz](https://twitter.com/0xrepnz)  
**License**: Free, unknown license  
**Notes**: Use full path name to specify the input file; look for the output file in /usr/local/shellcode2exe-bat  
**State File**: [remnux.tools.shellcode2exe-bat](https://github.com/REMnux/salt-states/blob/master/./remnux/tools/shellcode2exe-bat.sls)

## cut-bytes.py

Cut out a part of a data stream.

**Website**: [https://blog.didierstevens.com/2015/10/14/cut-bytes-py/](https://blog.didierstevens.com/2015/10/14/cut-bytes-py/)  
**Author**: Didier Stevens: [https://twitter.com/DidierStevens](https://twitter.com/DidierStevens)  
**License**: Public Domain  
**State File**: [remnux.scripts.cut-bytes](https://github.com/REMnux/salt-states/blob/master/./remnux/scripts/cut-bytes.sls)

## scdbg

Analyze shellcode by emulating its execution.

**Website**: [http://sandsprite.com/blogs/index.php?uid=7&pid=152](http://sandsprite.com/blogs/index.php?uid=7&pid=152)  
**Author**: David Zimmer  
**License**: Free, unknown license  
**Notes**: scdbg \(GUI\), scdbgc \(console\)  
**State File**: [remnux.packages.scdbg](https://github.com/REMnux/salt-states/blob/master/./remnux/packages/scdbg.sls)

## libemu

A library for x86 code emulation and shellcode detection

**Website**: [https://github.com/buffer/libemu](https://github.com/buffer/libemu)  
**Author**: [https://github.com/buffer/libemu/blob/master/AUTHORS](https://github.com/buffer/libemu/blob/master/AUTHORS)  
**License**: Free, unknown license  
**State File**: [remnux.packages.libemu](https://github.com/REMnux/salt-states/blob/master/./remnux/packages/libemu.sls)

