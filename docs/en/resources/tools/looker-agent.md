---
title: Looker Agent
description: Manage Looker Agents
keywords:
  - looker
  - looker-agent
  - agent
---

# Looker Agent

The `looker-agent` tool allows LLMs to manage Looker Agents. It supports listing, retrieving, creating, and deleting agents using the Looker Go SDK.

## Configuration

To use the `looker-agent` tool, you must define it in your `server.yaml` file.

```yaml
tools:
  - name: looker_agent_manage
    type: looker-agent
    source: my_looker_source
    description: Manage Looker AI Agents.
```

## Parameters

| Parameter   | Type     | Required | Description |
| :---------- | :------- | :------- | :---------- |
| `operation` | `string` | Yes      | The operation to perform. Must be one of: `list`, `get`, `create`, or `delete`. |
| `agent_id`  | `string` | No       | The ID of the agent. Required for `get` and `delete` operations. |
| `name`      | `string` | No       | The name of the agent. Required for `create` operation. |

## Operations

### List Agents
Retrieve a list of all agents.
```json
{
  "operation": "list"
}
```

### Get Agent
Retrieve details of a specific agent by its ID.
```json
{
  "operation": "get",
  "agent_id": "12345"
}
```

### Create Agent
Create a new agent with the given name.
```json
{
  "operation": "create",
  "name": "My AI Assistant"
}
```

### Delete Agent
Delete an agent by its ID.
```json
{
  "operation": "delete",
  "agent_id": "12345"
}
```

## Dependencies
This tool requires the underlying Looker Go SDK to support the `Agent` API resource (v4.0.26+).
