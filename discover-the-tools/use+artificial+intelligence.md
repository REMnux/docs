---
description: Discover the Tools
---

# Use Artificial Intelligence


## OpenCode

Open-source AI coding agent for the terminal.

**Website**: [https://opencode.ai](https://opencode.ai)\
**Author**: Anomaly: [https://github.com/anomalyco](https://github.com/anomalyco)\
**License**: Apache License 2.0: [https://github.com/anomalyco/opencode/blob/main/LICENSE](https://github.com/anomalyco/opencode/blob/main/LICENSE)\
**Available on**: Intel/AMD (amd64) and ARM (arm64)\
**Notes**: OpenCode might come with a default model that's free, but that might use the data you supply for training. Consider changing the model to your own to ensure confidentiality.\
**State File**: [remnux.node-packages.opencode](https://github.com/REMnux/salt-states/blob/master/remnux/node-packages/opencode.sls)

## REMnux MCP Server

MCP server for using the REMnux malware analysis toolkit via AI assistants.

**Website**: [https://github.com/REMnux/remnux-mcp-server](https://github.com/REMnux/remnux-mcp-server)\
**Author**: Lenny Zeltser\
**License**: GPL-3.0: [https://github.com/REMnux/remnux-mcp-server/blob/main/LICENSE](https://github.com/REMnux/remnux-mcp-server/blob/main/LICENSE)\
**Available on**: Intel/AMD (amd64) and ARM (arm64)\
**Notes**: remnux-mcp-server\
**State File**: [remnux.node-packages.remnux-mcp-server](https://github.com/REMnux/salt-states/blob/master/remnux/node-packages/remnux-mcp-server.sls)

## GhidrAssistMCP

MCP server for AI-assisted reverse engineering in Ghidra.

**Website**: [https://github.com/jtang613/GhidrAssistMCP](https://github.com/jtang613/GhidrAssistMCP)\
**Author**: Jason Tang: [https://www.linkedin.com/in/jason-tang-174652157/](https://www.linkedin.com/in/jason-tang-174652157/)\
**License**: MIT: [https://github.com/jtang613/GhidrAssistMCP/blob/master/LICENSE](https://github.com/jtang613/GhidrAssistMCP/blob/master/LICENSE)\
**Available on**: Intel/AMD (amd64) and ARM (arm64)\
**Notes**: After installation, enable the plugin in Ghidra: File → Configure → Miscellaneous → GhidrAssistMCPPlugin. Then start the MCP server: Window → GhidrAssistMCP. The server listens on port 8080. OpenCode is pre-configured to connect at http://localhost:8080/mcp.\
**State File**: [remnux.tools.ghidrassist-mcp](https://github.com/REMnux/salt-states/blob/master/remnux/tools/ghidrassist-mcp.sls)

## radare2

Examine binary files, including disassembling and debugging. Includes r2ai and decai plugins for LLM-powered analysis (API key or local Ollama required), plus the r2ghidra plugin for Ghidra decompilation via the pdg command.

**Website**: [https://www.radare.org/n/radare2.html](https://www.radare.org/n/radare2.html)\
**Author**: [https://github.com/radareorg/radare2/blob/master/AUTHORS.md](https://github.com/radareorg/radare2/blob/master/AUTHORS.md)\
**License**: GNU Lesser General Public License (LGPL) v3: [https://github.com/radareorg/radare2/blob/master/COPYING](https://github.com/radareorg/radare2/blob/master/COPYING)\
**Available on**: Intel/AMD (amd64) and ARM (arm64)\
**Notes**: r2, rasm2, rabin2, rahash2, rafind2, r2ai, decai, pdg\
**State File**: [remnux.packages.radare2](https://github.com/REMnux/salt-states/blob/master/remnux/packages/radare2.sls)

## ProcmonMCP

MCP server that lets AI assistants analyze Process Monitor (Procmon) XML captures.

**Website**: [https://github.com/JameZUK/ProcmonMCP](https://github.com/JameZUK/ProcmonMCP)\
**Author**: James (JameZUK): [https://x.com/JameZUK](https://x.com/JameZUK)\
**License**: MIT License: [https://github.com/JameZUK/ProcmonMCP/blob/procmon_parser/LICENSE](https://github.com/JameZUK/ProcmonMCP/blob/procmon_parser/LICENSE)\
**Available on**: Intel/AMD (amd64) and ARM (arm64)\
**Notes**: Pre-configured for OpenCode as the "procmon" MCP server. On Windows, export the Procmon capture to XML (the native .PML format is not supported), copy the XML to REMnux, then ask the assistant to load it. Large captures with millions of events can take several minutes to load.\
**State File**: [remnux.tools.procmon-mcp](https://github.com/REMnux/salt-states/blob/master/remnux/tools/procmon-mcp.sls)

## x64dbg Automate MCP (OpenCode skills)

Drive x64dbg on a remote Windows VM from OpenCode on REMnux, with eight AI commands for tracing, unpacking, state snapshots, decompiling, YARA scanning, and vulnerability hunting.

**Website**: [https://github.com/REMnux/x64dbg-skills-opencode](https://github.com/REMnux/x64dbg-skills-opencode)\
**Author**: Darius Houle: [https://x.com/dariushoule](https://x.com/dariushoule)\
**License**: MIT License: [https://github.com/REMnux/x64dbg-skills-opencode/blob/main/LICENSE](https://github.com/REMnux/x64dbg-skills-opencode/blob/main/LICENSE)\
**Available on**: Intel/AMD (amd64) and ARM (arm64)\
**Notes**: Ships disabled by default in OpenCode. It only works once x64dbg runs with the x64dbg-automate plugin in Remote mode on a separate Windows VM and you connect to it from OpenCode. The skills add OpenCode commands that begin with /x64dbg. Forked from dariushoule/x64dbg-skills (a Claude Code plugin) and adapted for OpenCode on REMnux.\
**State File**: [remnux.tools.x64dbg-automate-mcp](https://github.com/REMnux/salt-states/blob/master/remnux/tools/x64dbg-automate-mcp.sls)

## AIDebug

AI-assisted malware reverse-engineering debugger with ATT&CK, YARA, IOC, JSON, and analyst report output.

**Website**: [https://github.com/anpa1200/AIDebug](https://github.com/anpa1200/AIDebug)\
**Author**: Andrey Pautov: [https://1200km.com](https://1200km.com)\
**License**: MIT: [https://github.com/anpa1200/AIDebug/blob/main/LICENSE](https://github.com/anpa1200/AIDebug/blob/main/LICENSE)\
**Available on**: Intel/AMD (amd64) and ARM (arm64)\
**Notes**: To run the tool, use the command "aidebug". Add --offline to keep analysis local. Otherwise it sends sample data to the LLM provider whose API key is set in the environment.\
**State File**: [remnux.python3-packages.aidebug](https://github.com/REMnux/salt-states/blob/master/remnux/python3-packages/aidebug.sls)

## r2mcp

Model Context Protocol server that lets AI agents drive radare2 to open binaries, analyze code, decompile functions, and find vulnerabilities. Pre-configured for OpenCode as the radare2 MCP server.

**Website**: [https://github.com/radareorg/radare2-mcp](https://github.com/radareorg/radare2-mcp)\
**Author**: pancake: [https://github.com/radareorg/radare2-mcp](https://github.com/radareorg/radare2-mcp)\
**License**: MIT: [https://github.com/radareorg/radare2-mcp/blob/main/LICENSE](https://github.com/radareorg/radare2-mcp/blob/main/LICENSE)\
**Available on**: Intel/AMD (amd64) only\
**Alternative on arm64**: No alternative identified.\
**Notes**: r2mcp, r2mcp-svc\
**State File**: [remnux.packages.r2mcp](https://github.com/REMnux/salt-states/blob/master/remnux/packages/r2mcp.sls)
