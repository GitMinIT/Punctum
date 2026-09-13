# Punctum

Stoppuhr, Timer, Wecker und Pomodoro — präzise Zeit-Instrumente, selbst
gehostet auf [punctum.pompui.de](https://punctum.pompui.de).

## What it is

A static web app (no backend, no tracking). All settings and data live in
your browser's localStorage:

- **Stoppuhr** — millisecond-precise stopwatch with laps
- **Timer** — countdown with alarm
- **Wecker** — alarm clock (browser must stay open)
- **Pomodoro** — work/break cycles with configurable durations

The header/footer chrome (POMPUI branding) is loaded at runtime from
`https://pompui.de/shared/pompui-chrome.css` / `.js`.

## Repository structure

- `html/` — pages (`index.html`, `404.html`)
- `assets/` — CSS/JS
- `nginx.conf` — container nginx config (port 8080)
- `Dockerfile` — nginx-unprivileged image build
- `test/` — node test runner tests (`npm test`)

## Development

```bash
npm install        # no runtime deps needed for tests beyond node
npm test           # runs node --test test/
```

Or with Docker:

```bash
docker run --rm -v "$PWD":/app -w /app node:22-alpine npm test
```

## Deployment

Punctum is hosted via the [pompui.de infrastructure](https://github.com/GitMinIT/pompui.de)
(`repos/` workflow): the repo is cloned into `repos/punctum`, built by
`docker-compose.yml` as service `pompui-punctum` and routed through the
global proxy at `punctum.pompui.de` — see
[pompui.de → repos/README.md](https://github.com/GitMinIT/pompui.de/blob/main/repos/README.md)
for the full integration guide.

## Licence

[MIT](LICENSE)