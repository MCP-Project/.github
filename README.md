# MCP (Model Context Protocol) Tools

## Overview

This repository contains two main components for the Model Context Protocol ecosystem:

1. **MCP Gateway**: A central service for registering, discovering, and executing various tools.
2. **MCP Client**: A simplified client that uses natural language processing to interact with the MCP Gateway.

## MCP Gateway

The Gateway serves as a central hub for tool management with these key features:

- Tool discovery and registration
- Standardized tool execution interface
- Support for multiple tool types through a common API
- Remote service integration capabilities

The Gateway runs on port 8080 by default and exposes REST endpoints for tool management and execution.

## MCP Client

The Client provides a natural language interface to the Gateway with these features:

- Natural language processing to access Gateway tools
- REST communication with the Gateway
- Query interpretation and mapping to appropriate tools
- Simple health check functionality

The Client runs on port 8081 by default and offers an endpoint for processing natural language queries.

## How They Work Together

The Client interprets natural language requests, maps them to the appropriate tools registered in the Gateway, and returns the execution results to the user. This simplifies tool access by allowing users to interact with the system using ordinary language rather than specific API calls.

## Quick Start

For MCP Gateway:
```bash
cd mcp-gateway
mvn clean install
java -jar target/mcp-gateway-0.0.1-SNAPSHOT.jar
```

For MCP Client:
```bash
cd mcp-client/mcp-java-client
mvn clean install
java -jar target/mcp-java-client-0.0.1-SNAPSHOT.jar
```

## API Usage

### MCP Gateway Endpoints

- `GET /mcp/api/tools` - List all available tools
- `GET /mcp/api/tools/{toolName}` - Get details about a specific tool
- `POST /mcp/api/tools/{toolName}/execute` - Execute a specific tool
- `GET /mcp/api/health` - Check gateway health

### MCP Client Endpoints

- `POST /ai/ask` - Process natural language queries
- `GET /client/api/health` - Check gateway connection status

### Example Request to Client

```bash
curl -X POST http://localhost:8081/ai/ask \
  -H "Content-Type: application/json" \
  -d '{"query": "What is the sum of 25 and 17?"}'
```
```
