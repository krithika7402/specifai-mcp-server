# Specifai MCP Server

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![npm version](https://img.shields.io/npm/v/@presidio-dev/specifai-mcp-server.svg)](https://www.npmjs.com/package/@presidio-dev/specifai-mcp-server)
[<img alt="Install in VS Code (npx)" src="https://img.shields.io/badge/VS_Code-VS_Code?style=plastic&label=Install&color=0098FF">](https://insiders.vscode.dev/redirect?url=vscode:mcp/install?{"name":"specifai","command":"npx","args":["-y","@presidio-dev/specifai-mcp-server@latest"]})
[<img alt="Install in VS Code Insiders (npx)" src="https://img.shields.io/badge/VS_Code_Insiders-VS_Code_Insiders?style=plastic&label=Install&color=24bfa5">](https://insiders.vscode.dev/redirect?url=vscode-insiders:mcp/install?{"name":"specifai","command":"npx","args":["-y","@presidio-dev/specifai-mcp-server@latest"]})
[<img alt="Install in Cursor (npx)" src="https://img.shields.io/badge/Cursor-Cursor?style=plastic&label=Install&color=1A1A1A">](https://cursor.com/install-mcp?name=specifai&config=eyJjb21tYW5kIjoibnB4IC15IEBwcmVzaWRpby1kZXYvc3BlY2lmYWktbWNwLXNlcnZlckBsYXRlc3QifQ==)

<p>
  <img style="margin-right:18px;" src="assets/img/hai.png" alt="Hai Build" />
  <img style="margin-right:18px;" src="assets/img/amazon-q.png" alt="Amazon Q" />
  <img style="margin-right:18px;" src="assets/img/vsc.png" alt="VS Code" />
  <img style="margin-right:18px;" src="assets/img/cursor.png" alt="Cursor" />
  <img style="margin-right:18px;" src="assets/img/windsurf.png" alt="Windsurf" />
  <img style="margin-right:18px;" src="assets/img/zed.png" alt="Zed" />
</p>

A Model Context Protocol (MCP) server for [Specifai](https://github.com/presidio-oss/specifai) project integration and automation with any MCP-compatible AI tool. This server is designed to be tool-agnostic, meaning it can be used with any tool that supports the MCP protocol. This server currently exposes tools to read all documents generated by the Specifai project.

> [!WARNING]
> This server is currently experimental. The functionality and available tools are subject to change and expansion as we continue to develop and improve the server.

## Table of Contents

- [Requirements](#requirements)
- [Installation](#installation)
- [Configuration](#configuration)
- [Preparing Your Project](#preparing-your-project)
- [IDE Integration](#specifai-mcp-integration-with-popular-ide-and-extension)
- [Available Tools](#available-tools)
- [Contributing](#contributing)
- [Security](#security)
- [License](#license)

## Requirements

- Node.js >= 16.0.0
- Bun >= 1.0.0 (if using Bun runtime)
- Hai Build, Cursor, Windsurf, Claude Desktop or any MCP Client

## Installation

```bash
# Latest version
npx --yes @presidio-dev/specifai-mcp-server@latest

# Specific version
npx --yes @presidio-dev/specifai-mcp-server@1.2.3
```

We recommend `npx` to install the server, but you can use any node package manager of your preference such as `yarn`, `pnpm`, `bun`, etc.

## Configuration

with [`npx`](https://docs.npmjs.com/cli/v8/commands/npx) with latest version:

```json
{
  "specifai": {
    "command": "npx",
    "args": ["--yes", "@presidio-dev/specifai-mcp-server@latest"],
    "disabled": false,
    "autoApprove": []
  }
}
```

with [`npx`](https://docs.npmjs.com/cli/v8/commands/npx) with specific version:

```json
{
  "specifai": {
    "command": "npx",
    "args": ["--yes", "@presidio-dev/specifai-mcp-server@1.2.3"],
    "disabled": false,
    "autoApprove": []
  }
}
```

### Preparing your project

> This is completely optional, but it's recommended to use it to avoid having to specify the project directory path every time you access the server. For AI IDE / Extension (Hai Build), it's recommended to use a `.specifai-path` file to specify the project directory path.

Make sure your project root directory contains a `.specifai-path` file. It's how the Specifai MCP server knows where to find the specification documents generated by Specifai.

The file is a plain text file containing the absolute path to the project directory where the specification documents for a project are stored.

For example, if your project directory is located at `/path/to/project`, the `.specifai-path` file should contain the following line:

```
/path/to/project
```

## Specifai MCP integration with popular IDE and extension

See the setup instructions for each

<details>

<summary><b>Install in Hai Build</b></summary>

Add the following to your `hai_mcp_settings.json` file. To open this file from Hai Build, click the "MCP Servers" icon, select the "Installed" tab, and then click "Configure MCP Servers".

See the [Hai Build MCP documentation](https://github.com/presidio-oss/cline-based-code-generator/blob/main/docs/mcp/configuring-mcp-servers.mdx) for more info.

```json
{
  "mcpServers": {
    "specifai": {
      "command": "npx",
      "args": ["-y", "@presidio-dev/specifai-mcp-server@latest"]
    }
  }
}
```

</details>

<details>

<summary><b>Install in Amazon Q Developer</b></summary>

Add the following to your Amazon Q Developer configuration file. See [MCP configuration for Q Developer in the IDE](https://docs.aws.amazon.com/amazonq/latest/qdeveloper-ug/mcp-ide.html#mcp-ide-configuration-add-server) for more details.

The configuration file can be stored globally at `~/.aws/amazonq/mcp.json` to be available across all your projects, or locally within your project at `.amazonq/mcp.json`.

```json
{
  "mcpServers": {
    "specifai": {
      "command": "npx",
      "args": ["-y", "@presidio-dev/specifai-mcp-server@latest"]
    }
  }
}
```

</details>

<details>

<summary><b>Install in VS Code (Copilot)</b></summary>

[<img alt="Install in VS Code (npx)" src="https://img.shields.io/badge/VS_Code-VS_Code?style=plastic&label=Install&color=0098FF">](https://insiders.vscode.dev/redirect?url=vscode:mcp/install?{"name":"specifai","command":"npx","args":["-y","@presidio-dev/specifai-mcp-server@latest"]})
[<img alt="Install in VS Code Insiders (npx)" src="https://img.shields.io/badge/VS_Code_Insiders-VS_Code_Insiders?style=plastic&label=Install&color=24bfa5">](https://insiders.vscode.dev/redirect?url=vscode-insiders:mcp/install?{"name":"specifai","command":"npx","args":["-y","@presidio-dev/specifai-mcp-server@latest"]})

First, enable MCP support in VS Code by opening Settings (`Ctrl+,`), searching for `mcp.enabled`, and checking the box.

Then, add the following configuration to your user or workspace `settings.json` file. See the [VS Code MCP documentation](https://code.visualstudio.com/docs/copilot/chat/mcp-servers) for more info.

```json
"mcp": {
  "servers": {
    "specifai": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@presidio-dev/specifai-mcp-server@latest"]
    }
  }
}
```

</details>

<details>
<summary><b>Install in Cursor</b></summary>

The easiest way to install is with the one-click installation button below.

[<img alt="Install in Cursor (npx)" src="https://img.shields.io/badge/Cursor-Cursor?style=plastic&label=Install&color=1A1A1A">](https://cursor.com/install-mcp?name=specifai&config=eyJjb21tYW5kIjoibnB4IC15IEBwcmVzaWRpby1kZXYvc3BlY2lmYWktbWNwLXNlcnZlckBsYXRlc3QifQ==)

Alternatively, you can manually configure the server by adding the following to your `mcp.json` file. This file can be located globally at `~/.cursor/mcp.json` or within a specific project at `.cursor/mcp.json`. See the [Cursor MCP documentation](https://docs.cursor.com/context/model-context-protocol) for more information.

```json
{
  "mcpServers": {
    "specifai": {
      "command": "npx",
      "args": ["--yes", "@presidio-dev/specifai-mcp-server@latest"]
    }
  }
}
```

</details>

<details>
<summary><b>Install in Windsurf</b></summary>

Add the following to your `~/.codeium/windsurf/mcp_config.json` file. See the [Windsurf MCP documentation](https://docs.windsurf.com/windsurf/cascade/mcp) for more information.

```json
{
  "mcpServers": {
    "specifai": {
      "command": "npx",
      "args": ["-y", "@presidio-dev/specifai-mcp-server@latest"]
    }
  }
}
```

</details>

<details>
<summary><b>Install in Zed</b></summary>

You can add the Specifai MCP server in Zed by editing your `settings.json` file (accessible via the `zed: settings` action) or by using the Agent Panel's configuration UI (`agent: open configuration`). See the [Zed MCP documentation](https://zed.dev/docs/ai/mcp#add-your-own-mcp-server) for more information.

Add the following to your `settings.json`:

```json
{
  "context_servers": {
    "specifai": {
      "command": {
        "path": "npx",
        "args": ["-y", "@presidio-dev/specifai-mcp-server@latest"]
      }
    }
  }
}
```

</details>

### Available Tools

The server provides several tools for interacting with your specification documents:

| Tool Name          | Description                              |
| ------------------ | ---------------------------------------- |
| `get-brds`         | Get Business Requirement Documents       |
| `get-prds`         | Get Product Requirement Documents        |
| `get-nfrs`         | Get Non-Functional Requirements          |
| `get-uirs`         | Get User Interface Requirements          |
| `get-bpds`         | Get Business Process Documents           |
| `get-user-stories` | Get User Stories for a specific PRD      |
| `get-tasks`        | Get Tasks for a specific User Story      |
| `get-task`         | Get details of a specific Task           |
| `set-project-path` | Set or change the project directory path |
| `get-task-by-id`   | Get details of a specific Task by ID     |
| `list-all-tasks`   | List all available tasks                 |
| `search`           | Full text search across all documents    |

## Contributing

We welcome contributions to the Specifai MCP Server! Please see our [Contributing Guide](CONTRIBUTING.md) for more information on how to get started.

### Development Setup

For detailed instructions on setting up your development environment, please refer to our [Development Setup Guide](docs/dev/02-development-setup.md).

### Architecture

To understand the project architecture, please see our [Architecture Guide](docs/dev/03-architecture-guide.md).

## Security

For information about our security policy and how to report security vulnerabilities, please see our [Security Policy](SECURITY.md).

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgements

- [Model Context Protocol](https://modelcontextprotocol.io/) - The protocol specification this server implements
- [Specifai](https://github.com/presidio-oss/specifai) - The project this server integrates with
