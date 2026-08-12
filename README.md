# KingMind

Paquete distribuible de la app PWA de ajedrez, en español, con estética púrpura oscuro y dorado.

## Listo en este paquete

- `kingmind-prototype.html`: interfaz responsive, chat lateral colapsado, controles sin micrófono, tablero 8×8 cuadrado y legible, selección de color, reinicio y oponente local.
- Reglas legales implementadas: movimiento de piezas, jaque, jaque mate, ahogado, enroque, captura al paso, promoción, triple repetición, regla de 50 movimientos y material insuficiente.
- `manifest.webmanifest`, `sw.js` e iconos PWA (`icon-192.png`, `icon-512.png`, `apple-touch-icon.png`).
- `server.js`, `package.json`, `.env.example`: backend seguro opcional. El navegador usa únicamente `POST /api/chat` same-origin; nunca contiene la clave OpenAI.
- Adaptador y controles de Stockfish conservados. Busca `/stockfish.js` o `/stockfish.wasm.js` como Web Worker same-origin y vuelve al motor local si no existe o falla.

## Ejecución

Requiere Node.js 18+ (por `fetch` nativo). Copiá `.env.example` a `.env` o exportá las variables en el entorno del servidor y ejecutá:

```sh
npm start
```

Abrí `http://localhost:3000/`. Para una experiencia PWA, serví el directorio por HTTP/HTTPS; abrir el HTML con `file://` no habilita `/api/chat`, Service Worker ni el Worker de Stockfish.

## Requiere deployment/runtime

- Hace falta un runtime Node.js 18+ para `server.js` y, para chat real, `OPENAI_API_KEY` configurada solo en el servidor.
- El binario/worker de Stockfish **no está incluido**: hay que añadir un build compatible como `/stockfish.js` o `/stockfish.wasm.js` si se quiere ese motor. El motor local funciona sin él.
- La app no está publicada ni desplegada públicamente.
