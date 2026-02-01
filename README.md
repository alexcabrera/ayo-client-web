# ayo Web Client

Web clients for [ayo](https://github.com/alexcabrera/ayo) - available in both connected and offline modes.

## Live Demos

| Mode | Description | Link |
|------|-------------|------|
| **Connected** | Connect to a running ayo server | [Open Connected Client](https://alexcabrera.github.io/ayo-client-web/) |
| **Offline** | Run entirely in browser (no server needed) | [Open Offline Client](https://alexcabrera.github.io/ayo-client-web/offline/) |

---

## Connected Mode

The connected client connects to a running ayo server for full agent capabilities.

### Usage

1. Start the ayo server on your machine:
   ```bash
   ayo serve --port 8080
   ```

2. Open the [connected web client](https://alexcabrera.github.io/ayo-client-web/)

3. Connect using one of these methods:
   - **Scan QR Code**: Point your camera at the QR code displayed in your terminal
   - **Manual Entry**: Enter the server URL and token shown in the terminal output

4. Select an agent and start chatting

### Features

- Single HTML file (no build step required)
- Dark/light theme based on system preference
- QR code scanning for easy pairing
- SSE streaming for real-time responses
- Session management with history
- Tool call visualization
- Reasoning block display (collapsible)
- Connection persistence via localStorage

---

## Offline Mode

The offline client runs entirely in your browser with no server required.

### Usage

1. Open the [offline web client](https://alexcabrera.github.io/ayo-client-web/offline/)

2. Configure an LLM provider in Settings:
   - **WebLLM** (local): Download a model for local GPU inference
   - **Cloud API**: Enter an API key for OpenAI, Anthropic, or OpenRouter

3. Start chatting!

### Features

- **Chat with AI**: WebLLM for local inference or cloud APIs
- **Terminal**: Full Linux shell via TinyEMU WASM
- **Files**: Browse and edit the browser-based filesystem
- **Settings**: API key management, model downloads, storage

### Requirements

For local models (WebLLM):
- Chrome 113+ or Edge 113+ (WebGPU required)
- GPU with 2-8GB VRAM depending on model

For cloud APIs:
- Any modern browser
- API key for OpenAI, Anthropic, or OpenRouter

### How It Works

The offline client uses:
- **WebLLM** for local model inference on your GPU
- **TinyEMU** RISC-V emulator compiled to WebAssembly for shell access
- **IndexedDB** for persistent storage (models, sessions, files)
- **AES-256-GCM** encryption for API key storage

---

## Development

### Connected Client

The connected client is a self-contained HTML file:
```
index.html    # Single-file connected client
```

### Offline Client

The offline client consists of:
```
offline/
├── index.html      # Main UI
├── worker.js       # Web Worker for TinyEMU
├── js/
│   ├── app.js      # Application logic
│   ├── storage.js  # IndexedDB with encryption
│   ├── llm-router.js  # WebLLM/API routing
│   ├── emulator.js # TinyEMU controller
│   ├── terminal.js # xterm.js wrapper
│   └── protocol.js # VM-LLM communication
├── assets/
│   ├── tinyemu.wasm
│   └── wasm_exec.js
└── tests/          # Test suites
```

### Local Development

1. Clone the repository
2. Serve with any static file server:
   ```bash
   python -m http.server 8000
   # or
   npx serve .
   ```
3. Open `http://localhost:8000` for connected mode
4. Open `http://localhost:8000/offline/` for offline mode

## License

MIT
