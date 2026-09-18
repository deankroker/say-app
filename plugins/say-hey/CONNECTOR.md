# The bundled connector

`bin/say-hey-mcp-bin` is the standalone `say-hey-mcp` connector (server version 0.1.2), built
from the Say hey app repo, universal (arm64 + x86_64), signed with
`Developer ID Application: Spark LLC (U.S.) (5XWP46886G)` and notarized by Apple
(submission `dba67c3a-d038-46a1-88fd-e7ce6ce58766`, accepted 2026-09-18).

- sha256: `aee59b4ccd9ce40e80effc0452047e4905161b648557e39c623c22844f36b753`
- It runs in proxy mode and talks to the Say hey app on `127.0.0.1:1456`; it reads the app's
  access token from the app's own preferences, so nothing is pasted.
- The same binary ships inside `say-hey.mcpb` for Claude Desktop, attached to this repo's releases.

Rebuild: in the app repo, `MCPB_SIGN_IDENTITY=… MCPB_NOTARIZE_PROFILE=… scripts/package-claude-plugin.sh`,
then copy `dist/say-hey-mcpb/server/say-hey-mcp` here and update this file.
