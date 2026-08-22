# BUBU.Market consolidated update

This package supersedes the earlier v5, v6, and v7 update ZIPs.

## Replace in the repository root

- `index.html`
- `supabase-adapter.js`

## Add or verify in the repository root

- `netlify.toml`
- `_redirects`

Do not overwrite a working `supabase-config.js`. If it is missing, copy
`supabase-config.example.js` to `supabase-config.js` and enter your Supabase
project URL and publishable/anon key.

## Run in Supabase SQL Editor

Run the files inside `sql/` in numerical order:

1. `0015_catalog_media_admin.sql`
2. `0016_tenders_media_history.sql`
3. `0017_buyer_profile_retry.sql`

These migrations are additive. They do not reset existing authentication users,
business accounts, products, documents, conversations, or storage objects.

After committing the files, redeploy Netlify. Use no build command and publish
from the repository root (`.`).
