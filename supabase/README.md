# G-buys real product backend

This folder contains the one-time database foundation for replacing the fragile GitHub-token product publishing flow.

## Target flow

Customer website -> Supabase products table -> customer sees products

Admin -> Supabase Auth -> products table + product image storage -> customer sees product immediately

No GitHub Personal Access Token is needed for normal product management.

## One-time setup

1. Create/connect a Supabase project for G-buys.
2. Run `schema.sql` in the Supabase SQL Editor.
3. Create the G-buys admin user in Supabase Auth.
4. Add that user's UUID to `public.admin_users`.
5. The website/admin frontend will then use the Supabase project URL and public anon key.

Do not put a Supabase service-role key in the website. The browser should only use the public anon key with the RLS policies in schema.sql.

The existing `products.json` is deliberately preserved during the migration. It is the fallback until the database-backed storefront is verified.
