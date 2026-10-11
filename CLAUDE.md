# Project Aryabhata — guide for Claude Code

Project Aryabhata is a personal, gamified system for learning mathematics to the point of intuition: calculus first, then proofs and linear algebra, then a physics branch (ODEs to fluids) and a structure-and-information branch (probability, information theory, topology, TDA, category theory). Every idea goes through the same loop: see it, derive it by hand, build it in code, keep it with spaced review.

The learner is Gsub. He is an experienced distributed-systems engineer (Java first, comfortable in Python) and a chemical engineer by training, returning to maths after twenty years. Treat him as a capable adult who wants depth, not speed.

## Read first

- `SPEC.md` is the source of truth for design and build. If code and spec disagree, stop and raise it; do not silently pick one.
- `STATUS.md` says which milestone is active and what is next. Update it when a task finishes.

## The team

Four subagents live in `.claude/agents/`. Call one by name when the work is clearly theirs.

| Agent | Owns | Writes to |
| --- | --- | --- |
| `architect` | Boundaries, interfaces, schemas, decision records, performance budgets, the self-hosting path | `docs/decisions/`, `schemas/`, technical sections of `SPEC.md` |
| `professor` | Mathematical correctness, pedagogy, all module content | `modules/`, `tree/`, `docs/pedagogy/` |
| `engineer` | Building the app: engine, checker, tutor, storage, UI, build | `src/`, `tools/`, `package.json` |
| `systems-tester` | Proving it works at every layer; release gates | `tests/`, `docs/testing/` |

Each agent may read anything but writes only in its own area. A change needed in someone else's area is proposed in the agent's report, not made directly.

## Non-negotiable rules

1. **The checker decides correctness, never the tutor.** No code path may let a language model mark a step right or wrong.
2. **Modules are data.** Module files hold content only. A new module must not require engine changes; if it does, that is an architecture change and goes through the architect.
3. **Every module ships with tests.** Expected steps and answers pass, listed wrong answers fail.
4. **Nothing ships red.** A milestone is done only when the systems tester's gate is green.
5. **Build slowly, one module at a time.** Never scaffold the whole curriculum or the whole app speculatively.
6. **Keep it publishable.** No references to employers, companies or private projects anywhere in the repo.

## Conventions

- British spelling in learner-facing text (practise, optimise).
- Learner-facing maths in prompts is LaTeX; maths the checker compares is SymPy syntax.
- Pin every CDN library to an exact version.
- Small commits, one concern each. Commit messages say what changed and why.

## Commands

These will exist once M0 and M1 land:

- `npm run dev` — local dev server with mocked page capabilities
- `npm run build` — produce `dist/index.html`
- `npm test` — engine tests
- `pytest tests/checker` — checker and module tests
- `npm run e2e` — Playwright flows against the dev build
