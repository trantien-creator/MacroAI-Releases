# Local HTTP API

SmartMacroAI provides an optional local API for controlling the desktop application.
The default endpoint is `http://127.0.0.1:5100`.

## Security boundary

- The server binds to loopback only.
- CORS is not enabled.
- Do not expose the port to a LAN or the public Internet.
- Keep the generated API token private.
- Do not include the token in screenshots, issues, logs, or shared scripts.

## Authentication

`GET /health` does not require authentication.
All other endpoints require one of these headers:

```text
X-API-Key: <local token>
Authorization: Bearer <local token>
```

The token is stored in the local SmartMacroAI application settings.

## Endpoints

| Method | Endpoint | Purpose |
|---|---|---|
| `GET` | `/health` | Check whether the API process is available. |
| `GET` | `/status` | Read current workflow, backend, timing, and error state. |
| `GET` | `/scripts` | List scripts from the local Scripts directory. |
| `POST` | `/start` | Start a saved script. |
| `POST` | `/stop` | Request cancellation of the active run. |
| `GET` | `/screenshot` | Capture the current target as PNG. |
| `GET` | `/log?tail=200` | Read recent application log lines. |

`backendOverride` accepts `script`, `windows`, `hwnd`, or `adb`.
The override applies to the in-memory run and does not rewrite the saved script.

## Operational notes

- UI and API starts share the same run coordinator.
- A second workflow cannot start while another run owns the coordinator.
- ADB scripts require a saved device serial that is currently available.
- Windows scripts require a matching target window unless the workflow can launch its own target.

[Back to English README](../README.md) · [Về README tiếng Việt](../README.vi.md)
