---
description: Dynamically Reverse-Engineer Code
---

# General

## Frida

Trace the execution of a process to analyze its behavior.

**Website**: [https://frida.re](https://frida.re)\
**Author**: Ole Andre Vadla Ravnas\
**License**: wxWindows Library License 3.1: [https://github.com/frida/frida/blob/main/COPYING](https://github.com/frida/frida/blob/main/COPYING)\
**Notes**: frida, frida-ps, frida-trace, frida-discover, frida-ls-devices, frida-kill\
**State File**: [remnux.python3-packages.frida](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/frida.sls)


## Wine

Run Windows applications.

**Website**: [https://www.winehq.org](https://www.winehq.org)  
**Author**: [https://wiki.winehq.org/Acknowledgements](https://wiki.winehq.org/Acknowledgements)  
**License**: GNU Lesser General Public License \(LGPL\) v2.1 or later: [https://wiki.winehq.org/Licensing](https://wiki.winehq.org/Licensing)  
**Notes**: wine  
**State File**: [remnux.packages.wine](https://github.com/REMnux/salt-states/blob/master/remnux/packages/wine.sls)

## radare2

Examine binary files, including disassembling and debugging. Includes r2ai and decai plugins for LLM-powered analysis (API key or local Ollama required), plus the r2ghidra plugin for Ghidra decompilation via the pdg command.

**Website**: [https://www.radare.org/n/radare2.html](https://www.radare.org/n/radare2.html)\
**Author**: [https://github.com/radareorg/radare2/blob/master/AUTHORS.md](https://github.com/radareorg/radare2/blob/master/AUTHORS.md)\
**License**: GNU Lesser General Public License (LGPL) v3: [https://github.com/radareorg/radare2/blob/master/COPYING](https://github.com/radareorg/radare2/blob/master/COPYING)\
**Notes**: r2, rasm2, rabin2, rahash2, rafind2, r2ai, decai, pdg\
**State File**: [remnux.packages.radare2](https://github.com/REMnux/salt-states/blob/master/remnux/packages/radare2.sls)






## r2pipe

Examine binary files, including disassembling and debugging.

**Website**: [https://rada.re/n/r2pipe.html](https://rada.re/n/r2pipe.html)\
**Author**: radareorg\
**License**: MIT\
**State File**: [remnux.python3-packages.r2pipe](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/r2pipe.sls)

## x64dbg Automate MCP (OpenCode skills)

Drive x64dbg on a remote Windows VM from OpenCode on REMnux, with eight AI commands for tracing, unpacking, state snapshots, decompiling, YARA scanning, and vulnerability hunting.

**Website**: [https://github.com/REMnux/x64dbg-skills-opencode](https://github.com/REMnux/x64dbg-skills-opencode)\
**Author**: Darius Houle: [https://x.com/dariushoule](https://x.com/dariushoule)\
**License**: MIT License: [https://github.com/REMnux/x64dbg-skills-opencode/blob/main/LICENSE](https://github.com/REMnux/x64dbg-skills-opencode/blob/main/LICENSE)\
**Notes**: Ships disabled by default in OpenCode. It only works once x64dbg runs with the x64dbg-automate plugin in Remote mode on a separate Windows VM and you connect to it from OpenCode. The skills add OpenCode commands that begin with /x64dbg. Forked from dariushoule/x64dbg-skills (a Claude Code plugin) and adapted for OpenCode on REMnux.\
**State File**: [remnux.tools.x64dbg-automate-mcp](https://github.com/REMnux/salt-states/blob/master/remnux/tools/x64dbg-automate-mcp.sls)

