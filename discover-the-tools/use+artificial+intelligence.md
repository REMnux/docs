---
description: Discover the Tools
---

# Use Artificial Intelligence


## OpenCode

Open-source AI coding agent for the terminal.

**Website**: [https://opencode.ai](https://opencode.ai)\
**Author**: Anomaly: [https://github.com/anomalyco](https://github.com/anomalyco)\
**License**: Apache License 2.0: [https://github.com/anomalyco/opencode/blob/main/LICENSE](https://github.com/anomalyco/opencode/blob/main/LICENSE)\
**Notes**: OpenCode might come with a default model that's free, but that might use the data you supply for training. Consider changing the model to your own to ensure confidentiality.\
**State File**: [remnux.node-packages.opencode](https://github.com/REMnux/salt-states/blob/master/remnux/node-packages/opencode.sls)


## REMnux MCP Server

MCP server for using the REMnux malware analysis toolkit via AI assistants.

**Website**: [https://github.com/REMnux/remnux-mcp-server](https://github.com/REMnux/remnux-mcp-server)\
**Author**: Lenny Zeltser\
**License**: GPL-3.0: [https://github.com/REMnux/remnux-mcp-server/blob/main/LICENSE](https://github.com/REMnux/remnux-mcp-server/blob/main/LICENSE)\
**Notes**: remnux-mcp-server\
**State File**: [remnux.node-packages.remnux-mcp-server](https://github.com/REMnux/salt-states/blob/master/remnux/node-packages/remnux-mcp-server.sls)


## GhidrAssistMCP

MCP server for AI-assisted reverse engineering in Ghidra.

**Website**: [https://github.com/jtang613/GhidrAssistMCP](https://github.com/jtang613/GhidrAssistMCP)\
**Author**: Jason Tang: [https://www.linkedin.com/in/jason-tang-174652157/](https://www.linkedin.com/in/jason-tang-174652157/)\
**License**: MIT: [https://github.com/jtang613/GhidrAssistMCP/blob/master/LICENSE](https://github.com/jtang613/GhidrAssistMCP/blob/master/LICENSE)\
**Notes**: After installation, enable the plugin in Ghidra: File → Configure → Miscellaneous → GhidrAssistMCPPlugin. Then start the MCP server: Window → GhidrAssistMCP. The server listens on port 8080. OpenCode is pre-configured to connect at http://localhost:8080/mcp.\
**State File**: [remnux.tools.ghidrassist-mcp](https://github.com/REMnux/salt-states/blob/master/remnux/tools/ghidrassist-mcp.sls)
