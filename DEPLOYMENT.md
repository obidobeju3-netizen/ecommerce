# Deployment notes (Render)

This project is configured to deploy on Render using the `backend/` root directory.

Render settings (recommended):

- Repository: `https://github.com/obidobeju/ecommer`
- Branch: `main`
- Root Directory: `backend`
- Build Command (runs in `backend/`): `npm install`
- Start Command (runs in `backend/`): `node server.js` or `npm start`

Environment variables to set in Render (Environment → New Variable):

- `MONGO_URI` — MongoDB connection string (do not commit secrets to repo)
- `JWT_SECRET` — JWT secret for signing tokens
- Any other secrets you need (email SMTP creds, API keys, etc.)

Notes:
- We replaced native `bcrypt` with `bcryptjs` to avoid native binary builds on Render.
- The repository previously included a `npm rebuild bcrypt` step and `.render-build.sh`; these were removed as they are unnecessary now.
- The server listens on `process.env.PORT` (Render sets `PORT` automatically).

Manual deploy (UI): Service → Manual Deploy → Deploy latest commit

If you want me to remove the `render.yaml` (repo-level Render config) and switch to building from repo root instead, say so and I will update the file accordingly.
