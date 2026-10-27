# Documentation language conventions

> Scope: Work Performance repository | Status: Active | Date: 2026-10-27

## Required language pair
Every human-authored Markdown documentation file must have two equivalent versions:
- **English (agent/source-facing):** `NAME.md` (e.g. `docs/product/PRD.md`).
- **Vietnamese (product-owner-facing):** `NAME.vi.md` (e.g. `docs/product/PRD.vi.md`).

Exceptions: repository/tool-prescribed files requiring exact filenames (such as `README.md`, `AGENTS.md`, GitHub issue/PR templates) keep their canonical English names and include a paired `.vi.md` file when user-facing documentation is present. Machine-readable formats (JSON, YAML, OpenAPI) are not Markdown and are not duplicated unless explicitly requested.

## Synchronization rules
1. Create/update both language versions in the same task or PR.
2. Preserve requirement IDs, task IDs, lifecycle states, equations, version numbers, milestones, and acceptance criteria.
3. Translate explanations, not identifiers, code examples, API names, or paths.
4. Never silently leave the Vietnamese version stale; if blocked, mark the pair as incomplete and do not claim the documentation is done.
5. English is the agent's operational reference; Vietnamese is the product owner's review copy. **Neither language may silently override the other's agreed requirements.** If inconsistent, block sign-off and reconcile both.
6. Reviewers approve scope in Vietnamese; finalized decisions must be reflected identically in English.

## Review checklist
- [ ] Both files exist.
- [ ] Same document version and status.
- [ ] All headings/requirements/acceptance criteria and decisions are represented.
- [ ] Relative links work within repository.
- [ ] Changes are reflected in both languages.
- [ ] Product owner review is recorded before merge.

Apply to PRD, roadmap, task reports, architecture, API documentation, testing guides, deployment, and project handoff.
