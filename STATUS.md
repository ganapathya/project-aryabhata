# Status

**Active milestone:** M0 — Spikes
**Last updated:** 11 October 2026

## M0 — Spikes

Prove the risky parts work inside a claude.ai artifact before real building starts. See SPEC, Risks and spikes.

| # | Spike | Owner | Status |
| --- | --- | --- | --- |
| 1 | Pyodide with NumPy, SymPy and Matplotlib loads from the allowed CDN inside an artifact | engineer, with architect | Not started |
| 2 | MathLive MathJSON converts to SymPy for 50 sample inputs | engineer; golden set by systems-tester | Not started |
| 3 | The `sample` capability is fast enough for step-by-step tutoring (20 calls timed) | engineer | Not started |
| 4 | IndexedDB survives reload and republish to the same artifact URL | engineer | Not started |
| 5 | Cold and warm Python load times measured | engineer | Not started |

Alongside the spikes:

| Task | Owner | Status |
| --- | --- | --- |
| Decision records 0001–0005 and the three interfaces | architect | Not started |
| JSON Schemas for curriculum and module files | architect | Not started |
| Misconception catalogue and authoring guide | professor | Not started |
| Module 1 (Limits) content draft | professor | Not started |
| Checker and conversion test harness | systems-tester | Not started |

## Open decisions for Gsub

- Add a short algebra fitness check before Module 1? (Proposed by the professor.)

## Done

- Design and technical specification (SPEC.md)
- Repository, project guide and team of four agents
