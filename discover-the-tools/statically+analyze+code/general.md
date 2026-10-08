---
description: Statically Analyze Code
---

# General

## Ghidra

Software reverse engineering tool suite.

**Website**: [https://ghidra-sre.org](https://ghidra-sre.org)\
**Author**: National Security Agency\
**License**: Apache License 2.0: [https://github.com/NationalSecurityAgency/ghidra/blob/master/LICENSE](https://github.com/NationalSecurityAgency/ghidra/blob/master/LICENSE)\
**Available on**: Intel/AMD (amd64) and ARM (arm64)\
**Limitations on arm64**: Ghidra can't open 7-Zip archives.\
**Notes**: Close CodeBrowser before exiting Ghidra to prevent Ghidra from freezing when you reopen the tool (it's a Ghidra bug).\
**State File**: [remnux.packages.ghidra](https://github.com/REMnux/salt-states/blob/master/remnux/packages/ghidra.sls)

## Cutter

Reverse engineering platform powered by Rizin.

**Website**: [https://cutter.re](https://cutter.re)\
**Author**: [https://github.com/rizinorg/cutter/graphs/contributors](https://github.com/rizinorg/cutter/graphs/contributors)\
**License**: GNU General Public License (GPL) v3.0: [https://github.com/rizinorg/cutter/blob/master/COPYING](https://github.com/rizinorg/cutter/blob/master/COPYING)\
**Available on**: Intel/AMD (amd64) and ARM (arm64)\
**Notes**: If you're planning to use Cutter when running REMnux as a Docker container, you'll need to include the `--privileged` parameter when invoking the REMnux distro image in Docker.\
**State File**: [remnux.tools.cutter](https://github.com/REMnux/salt-states/blob/master/remnux/tools/cutter.sls)

## Qiling

Emulate code execution of PE files, shellcode, etc. for a variety of OS and hardware platforms.

**Website**: [https://www.qiling.io](https://www.qiling.io)\
**Author**: [https://github.com/qilingframework/qiling/blob/master/AUTHORS.TXT](https://github.com/qilingframework/qiling/blob/master/AUTHORS.TXT)\
**License**: GNU General Public License (GPL) v2.0: [https://github.com/qilingframework/qiling/blob/master/COPYING](https://github.com/qilingframework/qiling/blob/master/COPYING)\
**Available on**: Intel/AMD (amd64) and ARM (arm64)\
**Notes**: Use `qltool` to analyze artifacts. Before analyzing Windows artifacts, gather Windows DLLs and other components using the [dllscollector.bat](https://github.com/qilingframework/qiling/blob/master/examples/scripts/dllscollector.bat) script. Read the tool's [documentation](https://docs.qiling.io) to get started.\
**State File**: [remnux.python3-packages.qiling](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/qiling.sls)

## Vivisect

Statically examine and emulate binary files.

**Website**: [https://github.com/vivisect/vivisect](https://github.com/vivisect/vivisect)\
**Author**: invisigoth: invisigoth@kenshoto.com, installable vivisect module by Willi Ballenthin: [https://x.com/williballenthin](https://x.com/williballenthin)\
**License**: Apache License 2.0: [https://github.com/vivisect/vivisect/blob/master/LICENSE.txt](https://github.com/vivisect/vivisect/blob/master/LICENSE.txt)\
**Available on**: Intel/AMD (amd64) and ARM (arm64)\
**Limitations on arm64**: The graphical interface is unavailable.\
**Notes**: vivbin, vdbbin\
**State File**: [remnux.python3-packages.vivisect](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/vivisect.sls)

## objdump

Disassemble binary files.

**Website**: [https://en.wikipedia.org/wiki/Objdump](https://en.wikipedia.org/wiki/Objdump)\
**Author**: Unknown\
**License**: GNU General Public License (GPL)\
**Available on**: Intel/AMD (amd64) and ARM (arm64)\
**State File**: [remnux.packages.binutils](https://github.com/REMnux/salt-states/blob/master/remnux/packages/binutils.sls)

## radare2

Examine binary files, including disassembling and debugging. Includes r2ai and decai plugins for LLM-powered analysis (API key or local Ollama required), plus the r2ghidra plugin for Ghidra decompilation via the pdg command.

**Website**: [https://www.radare.org/n/radare2.html](https://www.radare.org/n/radare2.html)\
**Author**: [https://github.com/radareorg/radare2/blob/master/AUTHORS.md](https://github.com/radareorg/radare2/blob/master/AUTHORS.md)\
**License**: GNU Lesser General Public License (LGPL) v3: [https://github.com/radareorg/radare2/blob/master/COPYING](https://github.com/radareorg/radare2/blob/master/COPYING)\
**Available on**: Intel/AMD (amd64) and ARM (arm64)\
**Notes**: r2, rasm2, rabin2, rahash2, rafind2, r2ai, decai, pdg\
**State File**: [remnux.packages.radare2](https://github.com/REMnux/salt-states/blob/master/remnux/packages/radare2.sls)

## r2decomp

Decompile the function behind a capa match using radare2 and the Ghidra decompiler.

**Website**: [https://github.com/lennyzeltser/r2decomp](https://github.com/lennyzeltser/r2decomp)\
**Author**: Lenny Zeltser: [https://x.com/lennyzeltser](https://x.com/lennyzeltser)\
**License**: MIT: [https://github.com/lennyzeltser/r2decomp/blob/master/LICENSE](https://github.com/lennyzeltser/r2decomp/blob/master/LICENSE)\
**Available on**: Intel/AMD (amd64) and ARM (arm64)\
**Notes**: Pairs with capa. Run "r2decomp doctor" to confirm radare2 and the r2ghidra pdg decompiler are present.\
**State File**: [remnux.scripts.r2decomp](https://github.com/REMnux/salt-states/blob/master/remnux/scripts/r2decomp.sls)

## AIDebug

AI-assisted malware reverse-engineering debugger with ATT&CK, YARA, IOC, JSON, and analyst report output.

**Website**: [https://github.com/anpa1200/AIDebug](https://github.com/anpa1200/AIDebug)\
**Author**: Andrey Pautov: [https://1200km.com](https://1200km.com)\
**License**: MIT: [https://github.com/anpa1200/AIDebug/blob/main/LICENSE](https://github.com/anpa1200/AIDebug/blob/main/LICENSE)\
**Available on**: Intel/AMD (amd64) and ARM (arm64)\
**Notes**: To run the tool, use the command "aidebug". Add --offline to keep analysis local. Otherwise it sends sample data to the LLM provider whose API key is set in the environment.\
**State File**: [remnux.python3-packages.aidebug](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/aidebug.sls)
