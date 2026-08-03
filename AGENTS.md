<!-- BEGIN:nextjs-agent-rules -->
# This is NOT the Next.js you know

This version has breaking changes — APIs, conventions, and file structure may all differ from your training data. Read the relevant guide in `node_modules/next/dist/docs/` before writing any code. Heed deprecation notices.
<!-- END:nextjs-agent-rules -->

## Learned User Preferences

- Regularly sync with upstream (`ArnasDon/wacrm`) — merge upstream/main frequently to keep the fork close
- Use `supabase db push --linked` to apply SQL migrations to the remote Supabase project
- Replace `uuid_generate_v4()` with `gen_random_uuid()` in migration SQL from upstream (uuid-ossp extension is not available on this Supabase project)
- Use additive architecture — do not modify core upstream files; build business features alongside in isolated directories like `business/`
- Structure code as a modular monolith with clean module boundaries (lib/ → components/ → app/)
- Use `gh auth switch` between `abubackerm` and `tekrexllp` GitHub accounts as needed for pushing
- Push to the `dev_merged` remote (`tekrexllp/dev_merged`) for integration work

## Learned Workspace Facts

- The wacrm workspace (`D:\Projects\Tekhive\wacrm`) is a fork of `ArnasDon/wacrm` — Next.js 16 + Supabase + Tailwind v4 + shadcn/ui
- The revolucom workspace (`D:\Projects\Tekhive\revolucom`) is a separate-stack rewrite: NestJS 11 + Prisma 7 + Better Auth + BullMQ + Redis
- Git remotes: `upstream` to `ArnasDon/wacrm`, `origin` to `abubackerm/wacrm`, `dev_merged` to `tekrexllp/dev_merged`
- The Supabase project ref is `azxybdutbqohwsixazhs` (managed Supabase, not self-hosted)
- Database uses sequential SQL migrations (001-036+) with no Prisma ORM in wacrm
- Account-based multi-tenancy with 4 roles (owner > admin > agent > viewer) enforced via RLS and `is_account_member()`
- Custom migration fixes applied: migration 017 (schema search_path), migration 027 (renamed from 023), migration 035 (`gen_random_uuid()`)
- Dev server runs on port 1005
- Two GitHub accounts in use: `abubackerm` (personal) and `tekrexllp` (organization)
- Architecture goal: build business/SaaS features additively without modifying upstream core files, maintaining upstream merge compatibility
