---
description: Statically Analyze Code
---

# General

## Ghidra

Software reverse engineering tool suite.

**Website**: [https://ghidra-sre.org](https://ghidra-sre.org)\
**Author**: National Security Agency\
**License**: Apache License 2.0: [https://github.com/NationalSecurityAgency/ghidra/blob/master/LICENSE](https://github.com/NationalSecurityAgency/ghidra/blob/master/LICENSE)\
**Notes**: Close CodeBrowser before exiting Ghidra to prevent Ghidra from freezing when you reopen the tool (it's a Ghidra bug).\
**State File**: [remnux.packages.ghidra](https://github.com/REMnux/salt-states/blob/master/remnux/packages/ghidra.sls)


## Cutter

Reverse engineering platform powered by Rizin.

**Website**: [https://cutter.re](https://cutter.re)\
**Author**: [https://github.com/rizinorg/cutter/graphs/contributors](https://github.com/rizinorg/cutter/graphs/contributors)\
**License**: GNU General Public License (GPL) v3.0: [https://github.com/rizinorg/cutter/blob/master/COPYING](https://github.com/rizinorg/cutter/blob/master/COPYING)\
**Notes**: If you're planning to use Cutter when running REMnux as a Docker container, you'll need to include the `--privileged` parameter when invoking the REMnux distro image in Docker.\
**State File**: [remnux.tools.cutter](https://github.com/REMnux/salt-states/blob/master/remnux/tools/cutter.sls)


## Detect-It-Easy <a id="detect-it-easy"></a>

Determine types of files and examine file properties.

**Website**: [https://github.com/horsicq/Detect-It-Easy](https://github.com/horsicq/Detect-It-Easy)  
**Author**: hors: [https://x.com/horsicq](https://x.com/horsicq)  
**License**: MIT License: [https://github.com/horsicq/Detect-It-Easy/blob/master/LICENSE](https://github.com/horsicq/Detect-It-Easy/blob/master/LICENSE)  
**Notes**: GUI tool: `die`, command-line tool: `diec`.  
**State File**: [remnux.tools.detect-it-easy](https://github.com/REMnux/salt-states/blob/master/remnux/tools/detect-it-easy.sls)

## Qiling

Emulate code execution of PE files, shellcode, etc. for a variety of OS and hardware platforms.

**Website**: [https://www.qiling.io](https://www.qiling.io)  
**Author**: [https://github.com/qilingframework/qiling/blob/master/AUTHORS.TXT](https://github.com/qilingframework/qiling/blob/master/AUTHORS.TXT)  
**License**: GNU General Public License \(GPL\) v2.0: [https://github.com/qilingframework/qiling/blob/master/COPYING](https://github.com/qilingframework/qiling/blob/master/COPYING)  
**Notes**: Use `qltool` to analyze artifacts. Before analyzing Windows artifacts, gather Windows DLLs and other components using the [dllscollector.bat](https://github.com/qilingframework/qiling/blob/master/examples/scripts/dllscollector.bat) script. Read the tool's [documentation](https://docs.qiling.io) to get started.  
**State File**: [remnux.python3-packages.qiling](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/qiling.sls)

## Vivisect

Statically examine and emulate binary files.

**Website**: [https://github.com/vivisect/vivisect](https://github.com/vivisect/vivisect)\
**Author**: invisigoth: invisigoth@kenshoto.com, installable vivisect module by Willi Ballenthin: [https://x.com/williballenthin](https://x.com/williballenthin)\
**License**: Apache License 2.0: [https://github.com/vivisect/vivisect/blob/master/LICENSE.txt](https://github.com/vivisect/vivisect/blob/master/LICENSE.txt)\
**Notes**: vivbin, vdbbin\
**State File**: [remnux.python3-packages.vivisect](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/vivisect.sls)


## objdump

Disassemble binary files.

**Website**: [https://en.wikipedia.org/wiki/Objdump](https://en.wikipedia.org/wiki/Objdump)  
**Author**: Unknown  
**License**: GNU General Public License \(GPL\)  
**State File**: [remnux.packages.binutils](https://github.com/REMnux/salt-states/blob/master/remnux/packages/binutils.sls)

