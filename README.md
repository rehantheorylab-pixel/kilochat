# KiloChat

A single-file web client for an OpenAI-compatible gateway. No build step, no framework, no
dependencies — one `index.html` you can open directly or serve statically.

Built to exercise the full model catalog of the KiloAPI gateway: model list, filtering,
streaming responses, and per-request parameters.

---

## Features

- **Streaming chat** — server-sent events, rendered token by token
- **Model browser** — full catalog with search and provider filtering
- **Provider facets** — group by OpenAI / Anthropic / Google / Meta / DeepSeek / Qwen / GLM
- **Configurable endpoint** — point it at any OpenAI-compatible base URL
- **Local settings** — base URL, token, temperature, max tokens persisted in the browser
- **No backend** — static hosting is enough

## Running it

Open `index.html` in a browser, or serve the directory:

```bash
python -m http.server 8080
```

Then open `http://localhost:8080` and set **Base URL** to your gateway, e.g.
`http://localhost:8000/v1`.

### Connecting to a gateway

| Field | Example |
|---|---|
| Base URL | `http://localhost:8000/v1` |
| Bearer token | your gateway's key |

The gateway must send CORS headers for browser use, and must serve HTTPS if this page is
hosted over HTTPS (mixed content will otherwise be blocked).

---

## Security notes

- **No credentials are stored in this repository.** Bring your own gateway and key.
- The client keeps your token in browser `localStorage` for convenience. Use a throwaway key
  on shared machines.
- **Do not expose a gateway publicly without authentication.** A gateway reachable from the
  internet with no key requirement will be consumed by strangers within hours.

## Limitations

- Single conversation at a time; no conversation history persistence.
- No function calling or tool use.
- Model list is read from the gateway; stale catalogs are the gateway's responsibility.

## License

MIT.
