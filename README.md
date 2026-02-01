# ayo Web Client

A single-file web client for connecting to [ayo](https://github.com/alexcabrera/ayo) agents remotely.

## Live Demo

**[Open Web Client](https://alexcabrera.github.io/ayo-client-web/)**

## Usage

1. Start the ayo server on your machine:
   ```bash
   ayo serve --port 8080
   ```

2. Open the web client (either the live demo above or `index.html` locally)

3. Connect using one of these methods:
   - **Scan QR Code**: Point your camera at the QR code displayed in your terminal
   - **Manual Entry**: Enter the server URL and token shown in the terminal output

4. Select an agent and start chatting

## Features

- Single HTML file (no build step required)
- Dark/light theme based on system preference
- QR code scanning for easy pairing
- SSE streaming for real-time responses
- Session management with history
- Tool call visualization
- Reasoning block display (collapsible)
- Connection persistence via localStorage

## Development

The web client is a self-contained HTML file with embedded CSS and JavaScript. To modify:

1. Edit `index.html`
2. Test locally by opening in a browser
3. For server integration, copy to `ayo-server/internal/server/webclient/index.html`

## License

MIT
