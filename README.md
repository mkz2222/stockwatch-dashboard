# Stockwatch Dashboard

A responsive, public website displaying recent monitoring runs and alerts from
an existing Supabase database. Built with HTML, CSS, and JavaScript, plus a
read-only Netlify Function that keeps the Supabase secret key on the server.

## Deploy on Netlify

Import this repository into Netlify. Leave the build command empty; the included
`netlify.toml` configures the publish and functions directories. Set these server
environment variables before deploying:

- `BASE_L`
- `BASE_Y`
- `STOCKWATCH_DEVICE_ID` (defaults to `raspberrypi`)

See [deployment and credential instructions](DEPLOY-DASHBOARD.md) for details.
The dashboard uses the existing `stockwatch_runs` and `stockwatch_alerts` tables.
Database provisioning and the Raspberry Pi monitor are maintained separately.

## Website files

- `dashboard/`: responsive website, styles, and browser code
- `netlify/functions/`: public read-only activity API
- `netlify.toml`: Netlify deployment settings
- `scripts/dashboard-preview.mjs`: local website preview
- `tests/activity.test.mjs`: activity API tests

## Local preview

Requires Node.js 22 or newer:

```sh
node scripts/dashboard-preview.mjs --demo
node --test tests/activity.test.mjs
```

Open http://localhost:8888. Demo mode uses labeled sample data. To preview live
data, configure the environment variables and omit `--demo`.
