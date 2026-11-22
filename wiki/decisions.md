# Decisions

Each line: the decision, who made it, why. Dates are in [log.md](log.md).

## By the user

- **Phase 1 first**, later phases afterwards.
- **AI through OpenAI API calls.** This overrides the PRD's "no paid API" constraint. The PRD text has not been updated.
- **English-only UI** (left to right).
- **Cloud Supabase**, in a new organisation created for this product.
- **UI follows the Stitch project** "AI Interior Design Platform" ([design.md](design.md)).
- **GitHub repository is public.** The user chose to publish with the existing commit author address.
- **Stitch screens for later phases stay as references** in `design/stitch/`; the two that match Phase 1 (client portal, studio dashboard) are built with real data only.
- **Working rules** in `CLAUDE.md`: plan first, Opus 5.5 for plan, Sonnet 5.5 for execute, three kinds of tests, security review at every stage, commit per finished piece of code, subagents for specialist work, memory in `wiki/`.

## By Claude (open to change)

- **FastAPI**, managed with `uv`; **no-build frontend** with plain ES modules. Smallest stack that meets the PRD's "Python backend, HTML/CSS frontend".
- **All writes go through the backend with the service key; users have SELECT only.** The approved plan limited the service key to three operations. Widened so geometry validation and the audit trail cannot be bypassed through the Supabase Data API ([architecture.md](architecture.md)).
- **One JSON document per plan version**, in centimetres. The current plan is the latest version; no separate floor-plan table.
- **supabase-js is vendored**, not loaded from a CDN, with a `script-src 'self'` policy. Came out of the security review.
- **Product name "ATELIER"** in the UI, taken from Stitch. The PRD leaves the name undecided.
- **Later-phase widgets shown in Stitch are left out** (AI advisor, credits, budget, compliance badges) so the UI shows no fake data.
