---
description: Discover the Tools
---

# Investigate System Interactions

## ProcDOT

Visualize and examine the output of Process Monitor.

**Website**: [https://www.procdot.com](https://www.procdot.com)  
**Author**: Christian Wojner: [https://x.com/Didelphodon](https://x.com/Didelphodon)  
**License**: Free, custom license: [https://cert.at/media/files/downloads/software/procdot/files/license.txt](https://cert.at/media/files/downloads/software/procdot/files/license.txt)  
**Notes**: procdot  
**State File**: [remnux.packages.procdot](https://github.com/REMnux/salt-states/blob/master/remnux/packages/procdot.sls)

## sandfly-processdecloak

Find hidden processes on the local Linux system.

**Website**: [https://github.com/sandflysecurity/sandfly-processdecloak](https://github.com/sandflysecurity/sandfly-processdecloak)\
**Author**: Sandfly Security: [https://x.com/SandflySecurity](https://x.com/SandflySecurity)\
**License**: MIT License: [https://github.com/sandflysecurity/sandfly-processdecloak/blob/master/LICENSE](https://github.com/sandflysecurity/sandfly-processdecloak/blob/master/LICENSE)\
**State File**: [remnux.packages.sandfly-processdecloak](https://github.com/REMnux/salt-states/blob/master/remnux/packages/sandfly-processdecloak.sls)


## Unhide

Find hidden processes or connections on the local Linux system.

**Website**: [http://www.unhide-forensics.info](http://www.unhide-forensics.info)\
**Author**: Yago Jesus: [https://x.com/YJesus](https://x.com/YJesus)\
**License**: GNU General Public License (GPL) v3: [https://www.gnu.org/licenses/gpl-3.0.html](https://www.gnu.org/licenses/gpl-3.0.html)\
**State File**: [remnux.packages.unhide](https://github.com/REMnux/salt-states/blob/master/remnux/packages/unhide.sls)



## ProcmonMCP

MCP server that lets AI assistants analyze Process Monitor (Procmon) XML captures.

**Website**: [https://github.com/JameZUK/ProcmonMCP](https://github.com/JameZUK/ProcmonMCP)\
**Author**: James (JameZUK): [https://x.com/JameZUK](https://x.com/JameZUK)\
**License**: MIT License: [https://github.com/JameZUK/ProcmonMCP/blob/procmon_parser/LICENSE](https://github.com/JameZUK/ProcmonMCP/blob/procmon_parser/LICENSE)\
**Notes**: Pre-configured for OpenCode as the "procmon" MCP server. On Windows, export the Procmon capture to XML (the native .PML format is not supported), copy the XML to REMnux, then ask the assistant to load it. Large captures with millions of events can take several minutes to load.\
**State File**: [remnux.tools.procmon-mcp](https://github.com/REMnux/salt-states/blob/master/remnux/tools/procmon-mcp.sls)

