# pern-template

A minimal **PERN** starter: Postgres, Express, React, Node. Client and server live in separate packages in one repo.

## Stack

| Layer  | Tech                                           |
| ------ | ---------------------------------------------- |
| Client | React 19, Vite, Tailwind CSS 4, React Router 7 |
| Server | Node (ESM), Express 5, CORS, dotenv            |
| Shared | Prettier, ESLint, Jest, Husky + lint-staged    |

> Postgres is not wired up yet — add `pg`, a connection module, and mount your routes in `server/src/app.js`.

## Layout

```
client/            React app (Vite dev server)
  src/App.jsx      root component
  src/main.jsx     entry point
server/            Express API
  src/app.js       Express app (routes/middleware)
  src/server.js    HTTP server entry
.husky/            pre-commit hook
.github/workflows/ CI (if configured)
```

## Setup

Install both packages:

```bash
npm install                 # root: formatting + git hooks
npm install --prefix client
npm install --prefix server
```

Create `server/.env` for secrets (dotenv is already wired into the server deps).

## Development

Run the API and the client in two terminals:

```bash
npm run dev --prefix server   # nodemon on server/src/server.js
npm run dev --prefix client   # vite
```

Point the client at the API with `VITE_API_URL` in a `client/.env` file, then use `import.meta.env.VITE_API_URL` in fetch calls.

## Scripts

Root:

- `npm run format` / `npm run format:check` — Prettier across the repo

Client (`--prefix client`):

- `dev`, `build`, `preview`, `lint`, `format`

Server (`--prefix server`):

- `dev`, `start`, `lint`, `test`, `format`

## Formatting & hooks

Prettier config is in `.prettierrc` (3-space tabs, single quotes, semicolons). Husky runs `lint-staged` on commit, formatting staged JS/TS/JSON/CSS/HTML/MD files.

## License

MIT — see [LICENSE](./LICENSE).
