# KingMind prototype

## Secure chat backend
Requires Node.js 18+. Set `OPENAI_API_KEY` in the server process environment (not in HTML), then run `npm start` and open `http://localhost:3000/`. The browser calls same-origin `POST /api/chat`; the server forwards to OpenAI. The key never reaches client code.

## Standalone HTML limitations
Opening `kingmind-prototype.html` with `file://` cannot provide `/api/chat`; it uses clearly labeled local chat responses. Browser worker/network restrictions may also prevent engine loading.

## Stockfish adapter
Deploy a browser-compatible UCI Web Worker at `/stockfish.js` (or `/stockfish.wasm.js`) that accepts `postMessage` UCI commands and emits UCI lines. Click **Conectar Stockfish**, then select the Stockfish level. If absent/incompatible, local legal play remains active. No engine binary or third-party script is bundled.
