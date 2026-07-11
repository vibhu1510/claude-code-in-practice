# Claude Code in Practice

How I actually use Claude Code and Cursor as core development infrastructure — real conventions, real workflows, and honest notes on where agentic coding breaks. Not a review, not a hello-world demo. This is the working setup behind TechCoach AI (an agentic learning platform I built and deployed on the Claude API) and the material I use to onboard engineers onto agentic coding at Snowflake.

I'm building this repo in the open. The principles below are current; the deeper artifacts (annotated CLAUDE.md, documented sessions, the onboarding exercise) are landing incrementally — see the roadmap at the bottom.

**Who this is for:** engineers adopting AI coding agents seriously, and enablement folks designing programs to help them.

---

## How I work with coding agents

- **A conventions file in every repo.** Mine covers build/test commands, an architecture map, "never touch" zones, and the style decisions the agent kept getting wrong until I wrote them down. Every line in it exists because of a specific failure.
- **Plan before code on anything multi-file.** I ask for an approach and a file list first, correct the plan, then let it execute. It's cheaper to fix a plan than a diff.
- **The agent explores, I decide.** For unfamiliar code I have it trace the call path and summarize; I don't accept refactors of code that neither of us has actually read.
- **Tests are the contract.** Agent-generated code merges when tests I trust pass — and I treat agent-generated tests with suspicion until I've read the assertions myself.
- **Sessions have a budget.** Long sessions rot: context drifts, earlier constraints get forgotten. I'd rather restart with a tight summary than push a degraded session to "just finish."

## Where it goes wrong

The failure modes I've watched repeatedly while rolling agentic coding out to engineering teams:

1. **Confident wrong architecture** — the first plan sounds authoritative and is structurally wrong. Antidote: make it argue for the plan before writing code.
2. **Context rot** — constraints stated an hour ago silently stop applying. Antidote: short sessions, restated constraints, conventions in a file rather than in chat.
3. **Test theater** — tests that exercise the happy path and assert almost nothing. Antidote: read the assertions, not the pass count.
4. **Silent scope creep** — "while I was in there" changes nobody asked for. Antidote: file-list-first planning and diff review discipline.
5. **"It compiles so it's done"** — running is not the same as correct. Antidote: the human owns the definition of done.

## Roadmap (building in the open)

- [x] `conventions/` — my annotated CLAUDE.md and Cursor rules, with the failure that taught me each line
- [ ] `workflows/multi-file-refactor.md` — a real session on TechCoach AI, start to finish: prompts, the wrong first plan, the correction, the final diff
- [ ] `workflows/unfamiliar-codebase.md` — using the agent to map a codebase I've never seen
- [x] `teaching/onboarding-exercise.md` — the hands-on exercise I use to ramp engineers on Claude Code

---

Questions or want to compare setups: [LinkedIn](https://www.linkedin.com/in/vibhu-gupta-9a35b45a/) · vibhu1510@outlook.com
