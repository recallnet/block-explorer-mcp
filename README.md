# Recall Block Explorer MCP Service

FIXME: Currently, this doesn't work. It requires the json file to be local to the client, and our block explorer api is too large to fit in most context windows.

This Model Context Protocol (MCP) service enables MCP-aware AI assistants to query and access the Recall block explorer, creating a powerful knowledge extension for your AI assistant.

## Features

TODO

## Prerequisites

- [Node.js](https://nodejs.org/) (v14 or later)
- [npm](https://www.npmjs.com/) or [yarn](https://yarnpkg.com/)
- [Cursor IDE](https://cursor.sh/) and/or any other MCP-aware IDE
- [Claude Desktop](https://claude.ai/download) and/or any other MCP-aware assistant
  
## Basic Setup

1. **Configure Claude Desktop:**
   Add this to your `claude_desktop_config.json`:
   ```json
   {
     "mcpServers": {
       "recall-block-explorer": {
         "command": "npx",
         "args": ["openapi-mcp-server", "https://raw.githubusercontent.com/recall/explorer-mcp/refs/heads/main/openapi.json"]
       }
     }
   }
   ```
2. **Restart Claude Desktop** and start interacting with your API!

## Configure Cursor

1. Open Cursor IDE
2. Navigate to Settings → MCP
3. Click "Add new MCP server"
4. Configure as follows:
   - **Name**: Recall Block Explorer
   - **Type**: command
   - **Command**: `npx https://raw.githubusercontent.com/recall/explorer-mcp/refs/heads/main/openapi.json`
5. Click "Create" and ensure the server shows as "Enabled"

## Usage

Once installed, you can interact with the Recall Block Explorer in two ways:

### 1. Natural Language Queries

Simply ask the AI assistant questions about the network:

```
"What is the latest block status on the Recall testnet?"
"Get me the latest stats on the Recall testnet"
"What is the current balance for the account 0x....?"
```

The AI will use your MCP to query the block explorer and provide relevant information.

### 2. Direct Tool Usage

You can also use the MCP tools directly:

```javascript
// Get the latest stats
API-get_stats();

// Get a specific document by ID
API-get_transaction_summary({
  txn: "0x..."
});
```

## License

MIT

## Acknowledgements

- [OpenAPI MCP Server](https://github.com/snaggle-ai/openapi-mcp-server) which handles everything
- [Model Context Protocol](https://modelcontextprotocol.ai/) for enabling custom tool integration
