# Say hey — Claude Code plugin

Ask your own iMessage history from Claude Code. *What did I promise Maya? Who do I owe a
reply to? When did I last talk to Sam?* Every answer cites the real message.

Say hey runs on your Mac and answers from it. This plugin ships no binary and reads no
database — it hands each question to the Say hey app you already have installed.

## Install

1. Install [Say hey](https://apps.apple.com/us/app/say-hey-message-memory/id6767099766) and open it once.
2. In Say hey, open **Connect** in the sidebar and make sure it's listening. (It is, unless you turned it off.)
3. In Claude Code:

```
/plugin marketplace add deankroker/say-app
/plugin install say-hey@say
```

Then ask: *"What did I promise recently?"*

## How it works

`bin/say-hey-mcp` is a small wrapper. It reads your access token from the app's own
preferences and runs Say hey's MCP connector in proxy mode: the connector talks to the
running app on `127.0.0.1:1456` and the app answers from its index. Nothing is pasted,
nothing leaves the Mac.

Which connector it runs: the standalone one shipped at `bin/say-hey-mcp-bin` when present,
otherwise the helper inside `Say hey.app` — but only on builds where that helper isn't
sandboxed. **The App Store build's helper is sandboxed and can't be launched from outside
the app**, so with that build the plugin needs the standalone connector (the same one the
Claude Desktop `.mcpb` uses). `SAYHEY_MCP_BIN` overrides both.

The `skills/say-hey` skill teaches Claude Code *when* to reach for these tools and to
cite the source message every time.

## Troubleshooting

| You see | It means |
|---|---|
| "Say hey isn't reachable" | The app isn't running, or Connect is switched off. |
| "this connection is not authorized" (`-32001`) | The token didn't resolve. Open Say hey once so it creates one, or set `SAYHEY_MCP_TOKEN` yourself. |
| The server doesn't appear in `/mcp` | Say hey isn't installed, or this is the App Store build without the standalone connector. Run `claude --debug` to see the wrapper's message. |

## Develop

```
claude plugin validate . --strict
claude --plugin-dir .
```
