# custom-etc-control

Browser-based ETC Element/Eos OSC controller UI.

## Deploy On Vercel

1. Push this repository to GitHub.
2. In Vercel, import the repository and deploy.
3. No build step is required. Vercel serves `index.html` as a static site.

This repository includes `vercel.json` so deployment works out of the box.

## Cloudflare Tunnel + IP Support

The bridge connection field now accepts:

- Raw IPs, for example `192.168.1.50`
- Hostnames, for example `bridge.example.com`
- Full URLs, for example `https://bridge.example.com/ws` or `wss://bridge.example.com/ws`

Connection behavior:

- If you enter `https://...`, the app uses `wss://...` automatically.
- If you enter `http://...`, the app uses `ws://...` automatically.
- If you enter a hostname or IP without a scheme, the app auto-selects:
	- `wss://` when the page is loaded over HTTPS (for Vercel)
	- `ws://` when the page is loaded over HTTP
- Port is optional and can be set separately in the `Bridge Port` field.

## Important Network Note

When this app is hosted on Vercel (`https`), browsers block insecure WebSocket targets (`ws://`).
Use a secure WebSocket endpoint (`wss://`) for remote access, such as a Cloudflare Tunnel domain that forwards to your OSC bridge.