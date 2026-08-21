# BUBU.Market — clean installation

1. Create a new Supabase project.
2. If reusing an old BUBU project, empty/delete the `media` bucket in Storage, then run `FINAL_RESET.sql` once. It is destructive. For a brand-new Supabase project, skip the reset.
3. Run `FINAL_REBUILD.sql` once in the Supabase SQL Editor.
4. In Authentication, enable Email/password and disable Confirm email for this development build. Save the provider settings.
5. Create a public Storage bucket named `media` if the rebuild has not created it automatically.
6. Copy `deploy/supabase-config.example.js` to `deploy/supabase-config.js` and enter the new project URL and publishable/anon key.
7. In Authentication -> Users, create `nidhi@bubumarket.com` with password `Bubu@2027` and Auto-confirm enabled. Then run `deploy/supabase/seed_admin.sql` unchanged.
8. Serve the `deploy` directory over HTTP. Use `index.html` as the entry point.

Default development password policy used by this build: `Bubu@2026`. The Nidhi test admin used `Bubu@2027`; change all production passwords before launch.

Supplier registration requires a district selected from the provided Uganda district list. The UI validates it before creating the Auth account.

The universal development OTP is `079757`. Disable it before production and connect a real SMS/email provider.

## Database order

`FINAL_REBUILD.sql` contains all migrations in their required order. The original individual migrations remain under `deploy/supabase/migrations` for future upgrades.

## Profiles

- Buyer: immediate registration/login, marketplace, requirements, Quotes Manager, supplier chats and decisions.
- Supplier: approval, profile/storefront, catalog, media/documents, matched leads, lead credits, quotes and chats.
- Admin: supplier verification, categories/subcategories, plans and members.

Marketplace goods are paid directly between Buyer and Supplier. BUBU payment records are used for plans and paid lead access only.
