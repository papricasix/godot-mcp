# Godot MCP

[![Github-sponsors](https://img.shields.io/badge/sponsor-30363D?style=for-the-badge&logo=GitHub-Sponsors&logoColor=#EA4AAA)](https://github.com/sponsors/Coding-Solo)

[![](https://badge.mcpx.dev?type=server 'MCP Server')](https://modelcontextprotocol.io/introduction)
[![Made with Godot](https://img.shields.io/badge/Made%20with-Godot-478CBF?style=flat&logo=godot%20engine&logoColor=white)](https://godotengine.org)
[![](https://img.shields.io/badge/Node.js-339933?style=flat&logo=nodedotjs&logoColor=white 'Node.js')](https://nodejs.org/en/download/)
[![](https://img.shields.io/badge/TypeScript-3178C6?style=flat&logo=typescript&logoColor=white 'TypeScript')](https://www.typescriptlang.org/)

[![](https://img.shields.io/github/last-commit/Coding-Solo/godot-mcp 'Last Commit')](https://github.com/Coding-Solo/godot-mcp/commits/main)
[![](https://img.shields.io/github/stars/Coding-Solo/godot-mcp 'Stars')](https://github.com/Coding-Solo/godot-mcp/stargazers)
[![](https://img.shields.io/github/forks/Coding-Solo/godot-mcp 'Forks')](https://github.com/Coding-Solo/godot-mcp/network/members)
[![](https://img.shields.io/badge/License-MIT-red.svg 'MIT License')](https://opensource.org/licenses/MIT)


```text
                           (((((((             (((((((
                        (((((((((((           (((((((((((
                        (((((((((((((       (((((((((((((
                        (((((((((((((((((((((((((((((((((
                        (((((((((((((((((((((((((((((((((
         (((((      (((((((((((((((((((((((((((((((((((((((((      (((((
       (((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((
     ((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((
    ((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((
      (((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((
        (((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((
         (((((((((((@@@@@@@(((((((((((((((((((((((((((@@@@@@@(((((((((((
         (((((((((@@@@,,,,,@@@(((((((((((((((((((((@@@,,,,,@@@@(((((((((
         ((((((((@@@,,,,,,,,,@@(((((((@@@@@(((((((@@,,,,,,,,,@@@((((((((
         ((((((((@@@,,,,,,,,,@@(((((((@@@@@(((((((@@,,,,,,,,,@@@((((((((
         (((((((((@@@,,,,,,,@@((((((((@@@@@((((((((@@,,,,,,,@@@(((((((((
         ((((((((((((@@@@@@(((((((((((@@@@@(((((((((((@@@@@@((((((((((((
         (((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((
         (((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((
         @@@@@@@@@@@@@((((((((((((@@@@@@@@@@@@@((((((((((((@@@@@@@@@@@@@
         ((((((((( @@@(((((((((((@@(((((((((((@@(((((((((((@@@ (((((((((
         (((((((((( @@((((((((((@@@(((((((((((@@@((((((((((@@ ((((((((((
          (((((((((((@@@@@@@@@@@@@@(((((((((((@@@@@@@@@@@@@@(((((((((((
           (((((((((((((((((((((((((((((((((((((((((((((((((((((((((((
              (((((((((((((((((((((((((((((((((((((((((((((((((((((
                 (((((((((((((((((((((((((((((((((((((((((((((((
                        (((((((((((((((((((((((((((((((((


                          /$$      /$$  /$$$$$$  /$$$$$$$
                         | $$$    /$$$ /$$__  $$| $$__  $$
                         | $$$$  /$$$$| $$  \__/| $$  \ $$
                         | $$ $$/$$ $$| $$      | $$$$$$$/
                         | $$  $$$| $$| $$      | $$____/
                         | $$\  $ | $$| $$    $$| $$
                         | $$ \/  | $$|  $$$$$$/| $$
                         |__/     |__/ \______/ |__/
```

A Model Context Protocol (MCP) server for interacting with the Godot game engine.

## Introduction

Godot MCP enables AI agents to launch the Godot editor, run projects, capture debug output, and control project execution. This direct feedback loop helps agents understand what works and what doesn't in real Godot projects, leading to better code generation and debugging assistance.

This is a fork of [Coding-Solo/godot-mcp](https://github.com/Coding-Solo/godot-mcp) with additional security hardening and a live debug command bridge (`send_debug_command` / `list_debug_commands`) for sending commands to a running game at runtime.

## Features

- **Launch Godot Editor**: Open the Godot editor for a specific project
- **Run Godot Projects**: Execute Godot projects in debug mode
- **Capture Debug Output**: Retrieve console output and error messages
- **Control Execution**: Start and stop Godot projects programmatically
- **Get Godot Version**: Retrieve the installed Godot version
- **List Godot Projects**: Find Godot projects in a specified directory
- **Project Analysis**: Get detailed information about project structure
- **Scene Management**:
  - Create new scenes with specified root node types
  - Add nodes to existing scenes with customizable properties
  - Load sprites and textures into Sprite2D nodes
  - Export 3D scenes as MeshLibrary resources for GridMap
  - Save scenes with options for creating variants
- **UID Management** (for Godot 4.4+):
  - Get UID for specific files
  - Update UID references by resaving resources

## Requirements

- [Godot Engine](https://godotengine.org/download) installed on your system
- Node.js (>=18.0.0) and npm
- An AI agent that supports MCP

## Quick Start

### Claude Code

Build from source and register the local binary:

```bash
# 1. Clone and build
git clone https://github.com/papricasix/godot-mcp.git
cd godot-mcp
npm install
npm run build

# 2. Register with Claude Code (user scope = available in every project)
claude mcp add godot -s user \
  -e GODOT_PATH=/path/to/godot \
  -- node "$PWD/build/index.js"

# 3. Verify it connected
claude mcp list
```

Restart Claude Code, then run `/mcp` in a session to see the godot tools loaded.

Notes:
- `GODOT_PATH` is optional; omit it if `godot` is already on your `$PATH`. On macOS, a typical value is `/Applications/Godot.app/Contents/MacOS/Godot`.
- Add `-e DEBUG=true` to enable verbose server-side logging.
- After changing the source, run `npm run build` again; the registered command points at `build/index.js`, so the next Claude Code session picks up the new build automatically.
- To remove later: `claude mcp remove godot -s user`.

### Environment Variables

| Variable | Description |
|----------|-------------|
| `GODOT_PATH` | Path to the Godot executable (overrides automatic detection) |
| `DEBUG` | Set to `"true"` to enable detailed server-side debug logging |

<details>
<summary><strong>Building from Source</strong></summary>

```bash
git clone https://github.com/papricasix/godot-mcp.git
cd godot-mcp
npm install
npm run build
```

Then point your MCP client to `build/index.js` instead of using `npx`.

</details>


## Live Debug Commands

`send_debug_command` and `list_debug_commands` connect to a lightweight HTTP server that runs inside the game on `localhost:9876`. You implement this server as a GDScript autoload.

### 1. Create the autoload (`DebugHTTPServer.gd`)

```gdscript
extends Node

const PORT = 9876

var _server := TCPServer.new()
var _commands: Dictionary = {}

func _ready() -> void:
    _server.listen(PORT)

func _process(_delta: float) -> void:
    if not _server.is_connection_available():
        return
    var peer := _server.take_connection()
    await get_tree().process_frame  # let data arrive
    var raw := peer.get_string(peer.get_available_bytes())

    var lines := raw.split("\r\n")
    if lines.is_empty():
        return
    var parts := lines[0].split(" ")
    if parts.size() < 2:
        return
    var method: String = parts[0]
    var path: String = parts[1]

    var blank := raw.find("\r\n\r\n")
    var body := raw.substr(blank + 4) if blank != -1 else ""

    var response_body: String
    if method == "GET" and path == "/commands":
        response_body = JSON.stringify({"commands": _commands.keys()})
    elif method == "POST" and path == "/":
        var data: Variant = JSON.parse_string(body)
        var command: String = data.get("command", "") if data is Dictionary else ""
        response_body = JSON.stringify({"result": _dispatch(command)})
    else:
        _send(peer, 404, '{"error":"not found"}')
        return

    _send(peer, 200, response_body)

func register(command: String, callable: Callable) -> void:
    _commands[command] = callable

func _dispatch(command: String) -> String:
    var parts := command.split(" ", false, 1)
    var name := parts[0] if parts.size() > 0 else ""
    var arg  := parts[1] if parts.size() > 1 else ""
    if _commands.has(name):
        return str(_commands[name].call(arg))
    return "unknown command: %s" % name

func _send(peer: StreamPeerTCP, status: int, body: String) -> void:
    var msg := "HTTP/1.1 %d OK\r\nContent-Type: application/json\r\nContent-Length: %d\r\nConnection: close\r\n\r\n%s" \
               % [status, body.length(), body]
    peer.put_data(msg.to_utf8_buffer())
```

### 2. Register it as an autoload

In **Project → Project Settings → Autoload**, add `DebugHTTPServer.gd` with the name `DebugHTTPServer`.

### 3. Register commands from your game scripts

```gdscript
func _ready() -> void:
    DebugHTTPServer.register("player.heal", func(arg):
        player.health += int(arg)
        return "healed %s hp" % arg
    )
    DebugHTTPServer.register("spawn.enemy", func(arg):
        for i in int(arg): spawn_enemy()
        return "spawned %s enemies" % arg
    )
```

Commands are called as `"name arg"` — everything after the first space is passed as the argument string. The callable's return value becomes the `result` field in the MCP response.

## Architecture

The Godot MCP server uses a bundled GDScript approach for complex operations:

1. **Direct Commands**: Simple operations like launching the editor or getting project info use Godot's built-in CLI commands directly.
2. **Bundled Operations Script**: Complex operations like creating scenes or adding nodes use a single, comprehensive GDScript file (`godot_operations.gd`) that handles all operations.

The bundled script accepts operation type and parameters as JSON, allowing for flexible and dynamic operation execution without generating temporary files for each operation.

## Troubleshooting

- **Godot Not Found**: Set the `GODOT_PATH` environment variable to your Godot executable path
- **Connection Issues**: Ensure the server is running and restart your AI assistant
- **Invalid Project Path**: Ensure the path points to a directory containing a `project.godot` file
- **Build Issues**: Make sure all dependencies are installed by running `npm install`


## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
