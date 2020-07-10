---
description: Statically Analyze Code
---

# General

## BinNavi

IDE that allows to inspect, navigate, edit and annotate control flow graphs and call graphs of disassembled code.

**Website**: [https://github.com/google/binnavi](https://github.com/google/binnavi)  
**Author**: Google/Zynamics  
**License**: Apache License 2.0: [https://github.com/google/binnavi/blob/master/LICENSE](https://github.com/google/binnavi/blob/master/LICENSE)  
**Notes**: binnavi  
**State File**: [remnux.tools.binnavi](https://github.com/REMnux/salt-states/blob/master/./remnux/tools/binnavi.sls)

## Ghidra

Software reverse engineering tool suite

**Website**: [https://ghidra-sre.org](https://ghidra-sre.org)  
**Author**: National Security Agency  
**License**: Apache License 2.0: [https://github.com/NationalSecurityAgency/ghidra/blob/master/LICENSE](https://github.com/NationalSecurityAgency/ghidra/blob/master/LICENSE)  
**Notes**: Close CodeBrowser before exiting Ghidra to prevent Ghidra from freezing when you reopen the tool \(it's a Ghidra bug\).  
**State File**: [remnux.tools.ghidra](https://github.com/REMnux/salt-states/blob/master/./remnux/tools/ghidra.sls)

## Cutter

Reverse engineering platform powered by radare2

**Website**: [https://cutter.re](https://cutter.re)  
**Author**: Unknown  
**License**: GNU General Public License \(GPL\) v3.0: [https://github.com/radareorg/cutter/blob/master/COPYING](https://github.com/radareorg/cutter/blob/master/COPYING)  
**State File**: [remnux.tools.cutter](https://github.com/REMnux/salt-states/blob/master/./remnux/tools/cutter.sls)

## Vivisect

Statically examine and emulate binary files.

**Website**: [https://github.com/vivisect/vivisect](https://github.com/vivisect/vivisect)  
**Author**: invisigoth: invisigoth@kenshoto.com, installable vivisect module by Willi Ballenthin: [https://twitter.com/williballenthin](https://twitter.com/williballenthin)  
**License**: Apache License 2.0: [https://github.com/vivisect/vivisect/blob/master/LICENSE.txt](https://github.com/vivisect/vivisect/blob/master/LICENSE.txt)  
**Notes**: vivbin, vdbbin  
**State File**: [remnux.python-packages.vivisect](https://github.com/REMnux/salt-states/blob/master/./remnux/python-packages/vivisect.sls)

## objdump

Disassemble binary files.

**Website**: [https://en.wikipedia.org/wiki/Objdump](https://en.wikipedia.org/wiki/Objdump)  
**Author**: Unknown  
**License**: GNU General Public License \(GPL\)  
**State File**: [remnux.packages.binutils](https://github.com/REMnux/salt-states/blob/master/./remnux/packages/binutils.sls)

## pyew

Statically examine properties and code of suspicious PE and ELF executables.

**Website**: [https://github.com/joxeankoret/pyew](https://github.com/joxeankoret/pyew)  
**Author**: Joxean Koret  
**License**: GNU General Public License \(GPL\): [https://github.com/joxeankoret/pyew/blob/VERSION\_3X/COPYING](https://github.com/joxeankoret/pyew/blob/VERSION_3X/COPYING)  
**State File**: [remnux.packages.pyew](https://github.com/REMnux/salt-states/blob/master/./remnux/packages/pyew.sls)

