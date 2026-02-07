# Using AI with REMnux

REMnux includes tools that let AI assistants run malware analysis tools via the [Model Context Protocol](https://modelcontextprotocol.io) (MCP). MCP is an open protocol that lets AI assistants use external tools and data sources. Any MCP-compatible AI agent can use the REMnux MCP server to analyze samples. [OpenCode](../discover-the-tools/use+artificial+intelligence.md), a terminal-based AI assistant, is pre-installed and pre-configured as the quickest way to get started.

For details about the individual AI tools included in REMnux, see the [Use Artificial Intelligence](../discover-the-tools/use+artificial+intelligence.md) page.

## Using AI Assistants on REMnux <a href="#ai-assistants" id="ai-assistants"></a>

Once an AI assistant is connected to the REMnux MCP server, you can tell it what you'd like to analyze. The AI uses the REMnux MCP server to run the appropriate REMnux tools automatically. The MCP server offers guidance regarding the tools that the AI should consider, but it's up to the AI agent to decide on the analysis workflow. And, of course, your interactions, requests, and observations can also direct the AI regarding the analysis steps.

Key capabilities available to AI assistants through the REMnux MCP server:

* Analyze files based on detected type (PE, PDF, Office docs, scripts, ELF, etc.)
* Get tool recommendations for a specific file without running them
* Run specific REMnux tools directly, including piped commands
* Extract indicators of compromise (IOCs) from text
* Get usage help for any installed REMnux tool

The AI assistant can upload your sample to REMnux. Or you can place samples in `/home/remnux/files/samples` or provide absolute file paths. Analysis output goes to `/home/remnux/files/output`.

### Example Prompts

Here are a few examples of how you might start a conversation with your AI assistant:

* `Analyze the file sample.exe and summarize its capabilities`
* `What tools should I use to examine this PDF?`
* `Download the file at https://example.com/suspicious.bin and analyze it`
* `Extract IOCs from this text: <paste the suspicious content here>`

The AI decides which REMnux tools to run based on your request. You can also ask it to run a specific tool if you prefer.

### Using OpenCode

[OpenCode](../discover-the-tools/use+artificial+intelligence.md) and the REMnux MCP server are pre-installed and pre-configured on REMnux. You can launch OpenCode with the `opencode` command in the terminal.

As of this writing, OpenCode comes with a default AI model that lets you experiment immediately.

{% hint style="warning" %}
The default model may be in trial mode and might use the data you supply for training. For real analysis, configure your own AI model provider's API key in OpenCode's settings, or use your preferred AI tool as described in the next section.
{% endhint %}

OpenCode on REMnux comes with three MCP servers pre-configured:

* **remnux** — connects to the local REMnux analysis toolkit
* **remnux-docs** — provides access to REMnux documentation for tool guidance
* **ghidra** — connects to [GhidrAssistMCP](../discover-the-tools/use+artificial+intelligence.md) for AI-assisted reverse engineering when the plugin is activated in Ghidra

## Connecting Other AI Tools to REMnux <a href="#other-ai-tools" id="other-ai-tools"></a>

You can also use AI tools running outside REMnux (such as Claude Code or Cursor) and connect them to the REMnux MCP server running in the VM or container. They get the same MCP capabilities described above. Two approaches:

* **MCP server on your workstation**: Install the server on your machine using `npx @remnux/mcp-server`. It connects to REMnux via Docker exec or SSH to run analysis tools.
* **MCP server inside REMnux over HTTP**: The MCP server is already installed in REMnux. Start it with HTTP transport so it listens on a network port. Your AI tool connects over the network using bearer token authentication.

See the [REMnux MCP server documentation](https://github.com/REMnux/remnux-mcp-server) for setup instructions and configuration examples for each scenario.

## Security Considerations <a href="#security" id="security"></a>

As always, be careful in all your interactions with malware. Consider dedicating a system to your research tasks. Keep the following design principles and precautions in mind.

### AI Model Provider Data Handling

When using AI tools for analysis, details about your samples are sent to the AI model provider's API. Choose a provider whose data handling policies you trust. Avoid using default or free models that might train on your data for real analysis work.

### Disposable Environment

Always run REMnux in a disposable VM or container when analyzing malware, regardless of whether you use AI tools.

### MCP Connection Security

The security of the MCP connection depends on how you deploy it:

* **MCP server and AI agent on REMnux**: The MCP connection stays entirely local; however, unless you're using a local LLM, the REMnux VM or container will need internet access. If necessary, you can use network security measures to restrict outbound activity so the system can only communicate with the LLM provider.
* **MCP server and AI agent on your workstation**: MCP traffic stays on your machine via Docker exec, travels over encrypted SSH to the VM, or uses HTTP with a bearer token for authentication. In this case, the REMnux VM or container doesn't need internet access. If using HTTP, generate a strong token (e.g., `openssl rand -hex 32`) and consider HTTPS via a reverse proxy if the network path between your AI tool and REMnux is untrusted.

### Prompt Injection from Malware

Malware samples can contain strings designed to manipulate AI assistants. The MCP server includes mitigations, but container and VM isolation, as well as the isolation of your system and your judgment are the primary defenses.

When the MCP server runs on your workstation, there is a small chance that malicious tool output could inject into the prompt returned to your AI agent and influence its behavior. Review AI-generated analysis critically. AI assists your analysis but does not replace analyst judgment.
