# Desktop Commander (optional contributor tool)

Desktop Commander is an optional MCP server for local file operations and terminal commands. It is not part of DeepSeek-V3 inference, and contributors do not need it to run the model or use this repository.

## Set it up for your own client

Install or connect the server in the AI client you use; setup is per contributor and per client. For clients that support a local stdio MCP server, Desktop Commander's published configuration is:

```json
{
  "mcpServers": {
    "desktop-commander": {
      "command": "npx",
      "args": ["-y", "@wonderwhy-er/desktop-commander@latest"]
    }
  }
}
```

In VS Code with GitHub Copilot, use **MCP: Add Server**, choose **Command (stdio)**, enter `npx -y @wonderwhy-er/desktop-commander@latest`, and choose a personal/global destination unless the team has agreed to share a workspace configuration. Review the server trust and tool-approval prompts before accepting them. Other clients may use a different configuration format; follow their current MCP setup instructions.

The `npx ... setup` command in Desktop Commander's README is documented for Claude Desktop. The supplied `curl ... | bash` command is a Bash installer and should not be run in Windows PowerShell. Do not run installers from a project prompt; install only through a client setup path you have reviewed.

For the hosted endpoint at <https://mcp.desktopcommander.app/mcp>, follow the service's current sign-in and connection flow. A URL alone does not grant access; the endpoint returned HTTP 401 when checked without authentication. Do not put credentials or access tokens in this repository.

## Safety and usage limits

Desktop Commander can read and modify files and run commands with the local user's permissions; treat it as a powerful local tool, not a sandbox. Review commands and requested access, and scope filesystem access to the project when your client supports it.

A prompt or a repository license cannot increase an MCP service's quota, bypass authentication, or change a provider's plan. The repository's MIT code license and DeepSeek model license cover this project's code and model under their respective terms; they do not grant unlimited access to third-party hosted services. Local inference avoids a hosted API quota only when run on hardware you control, and remains subject to hardware capacity and the model license.

## Reusable analysis prompt

Use the [Desktop Commander codebase-analysis prompt](../.github/prompts/desktop-commander-codebase-analysis.prompt.md) for a bounded, technical exploration of this repository. It uses Desktop Commander only when the current client has it configured.

## References

- [Desktop Commander setup and client configuration](https://github.com/wonderwhy-er/DesktopCommanderMCP#how-to-install)
- [VS Code MCP server setup](https://code.visualstudio.com/docs/agent-customization/mcp-servers)
- [Code license](../LICENSE-CODE)
- [Model license](../LICENSE-MODEL)
