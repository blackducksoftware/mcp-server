# Black Duck MCP Server

A Model Context Protocol (MCP) server that enables AI-powered security scanning of your code using [Black Duck Signal](https://www.blackduck.com/).

## Features

- **Git Diff Security Scanning** - Analyze only changed code for faster, more efficient security reviews
- **File-based Security Scanning** - Scan specific files for security vulnerabilities
- **AI-Native Integration** - Seamlessly integrates with Claude, VS Code, and other MCP-compatible tools

## Installation

### npm

```bash
npm install -g @black-duck/mcp-server
```

### Configuration

Add to your MCP client configuration:

**VS Code (settings.json):**
```json
{
  "mcp": {
    "servers": {
      "black-duck": {
        "command": "npx",
        "args": ["@black-duck/mcp-server"]
      }
    }
  }
}
```

**Claude Desktop (claude_desktop_config.json):**
```json
{
  "mcpServers": {
    "black-duck": {
      "command": "npx",
      "args": ["@black-duck/mcp-server"]
    }
  }
}
```

## Available Tools

### `run_diff_security_scan`

**Recommended** - Analyzes git diffs for security vulnerabilities. This is the most efficient way to scan code changes.

**Parameters:**
- `projectPath` (required) - Path to the git project directory
- `gitPatchMode` (required) - Git patch generation mode:
  - `all-uncommitted` - Scans all uncommitted changes (staged + unstaged)
  - `reference-branch` - Scans changes compared to a reference branch
- `referenceBranch` - Reference branch name (required for `reference-branch` mode)

**Example usage:**
```
Scan my uncommitted changes for security issues
```

### `run_security_scan`

Analyzes specific files for security vulnerabilities.

**Parameters:**
- `projectPath` (required) - Path to the project directory
- `filePaths` (required) - List of absolute file paths to scan

**Example usage:**
```
Scan src/auth.js for security vulnerabilities
```

## Requirements

- Node.js 18 or higher
- Git (for diff-based scanning)

## Links

- [npm package](https://www.npmjs.com/package/@black-duck/mcp-server)
- [Black Duck](https://www.blackduck.com/)
- [Model Context Protocol](https://modelcontextprotocol.io/)

## License

See [LICENSE](./LICENSE) for details.
