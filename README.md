
# GetClipped — Electron Frontend

## Quick start
```bash
cp .env.example .env
npm install
npm run electron:dev   # runs Vite + Electron (dev)
# or
npm run electron:prod  # builds the web bundle and runs Electron off /dist
```

## Configure
- Set `VITE_API_BASE_URL` to your server (default `http://localhost:10000`).
- OAuth popups are opened via `window.open` and work in Electron because `nativeWindowOpen` is enabled.
- App JWT is used for verifyAppJwt routes. Uploads use Firebase ID token + X-Refresh-Token + device headers.

## Security
- `contextIsolation: true`, `sandbox: true`, `nodeIntegration: false`, `nativeWindowOpen: true`.
- In-memory/sessionStorage tokens only; no secrets baked into the client.
- Best-effort CSP for Electron via `onHeadersReceived` and meta tags for web preview.
