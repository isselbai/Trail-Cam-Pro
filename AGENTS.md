# How to work in this repo (for Codex)

## Environment
- Node LTS + pnpm
- Supabase project with `.env.local` vars:
  NEXT_PUBLIC_SUPABASE_URL=...
  NEXT_PUBLIC_SUPABASE_ANON_KEY=...
  SUPABASE_SERVICE_ROLE_KEY=...
  OPENAI_API_KEY=...
- Vercel-like environment for local dev:
  pnpm install
  pnpm lint
  pnpm typecheck
  pnpm test
  pnpm build

## Commands
- Dev: pnpm dev
- Lint: pnpm lint (eslint)
- Types: pnpm typecheck (tsc --noEmit)
- Tests: pnpm test (vitest + playwright later)
- Build: pnpm build

## Testing rules
- All new modules must include minimal unit tests.
- For media processing, include a dry-run unit test that mocks I/O.

## Project structure (target)
apps/web            # Next.js app
packages/ui         # shared UI components
packages/lib        # shared utils/clients
supabase/functions  # edge functions (webhooks, processing)
supabase/migrations # SQL migrations, RLS, policies
infra/ci            # GitHub Actions

## Definition of Done (DoD) per task
- Lint + types + tests pass
- A short CHANGELOG entry is added
- Update README with any new commands/variables

## Guardrails
- Use Supabase Storage signed URLs for client access.
- Enforce RLS policies on all tables.
- Never hardcode API keys or secrets.
- For AI: call OpenAI APIs via server-side only.
