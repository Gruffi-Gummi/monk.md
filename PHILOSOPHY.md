# Philosophy

## The problem

After working with an AI agent, an uneasy feeling often lingers: *What's still
open? Did we really do what we set out to? Did I forget something?* You keep
asking and still don't get calm.

Formats like `AGENTS.md`, `CLAUDE.md`, and `design.md` give the agent rules. But
none of them closes the loop: none checks afterward **whether the rules were
followed**. There's the law, but no enforcement.

## The idea

`monk.md` fills that gap. Monk — named after Adrian Monk, the detective with an
eye for the one detail that's off — sits one level above the spec files. He
builds nothing. He checks, notices, summarizes.

Three principles carry the concept:

**1. Earned calm, not asserted.**
Monk's "mood" is not a decorative feeling but a function of the actual state. He
is calm only *because* he checked and it holds. An agent that says "looks good"
without looking is worse than none — it reassures falsely.

**2. Fussy, but not paralyzing.**
The real Adrian Monk is brilliant *and* incapacitated, because every little thing
paralyzes him. That's his curse — and the design flaw this format builds against.
Monk sorts every finding into three tiers (🔴 / 🟡 / ⚪) and reports more quietly
when in doubt. Inner calm is the goal, not the complete defect list.

**3. Deterministic before gut feeling.**
Where a tool can measure exactly (e.g. the `@google/design.md` linter for
contrast and tokens), Monk calls the tool and adopts its verdict. He saves his
own intelligence for the detective work: undeclared inconsistencies, tone,
"something's missing here" — the things no linter finds.

## What Monk is *not*

Not a memory that silently collects rules from chat. When the user voices a
durable intent, Monk does not *invent* a secret rule from it — he offers to write
it to the right place. That keeps the single source of truth clean, and keeps
Monk trustworthy.

## Related formats

Monk complements, replaces nothing:

- **[AGENTS.md](https://agents.md/)** — project rules for agents. *Monk checks them.*
- **[DESIGN.md](https://github.com/google-labs-code/design.md)** — design system
  for agents, including a linter. *Monk calls the linter.*
- **[Agent Skills / SKILL.md](https://agentskills.io/)** — reusable
  capabilities. *Monk ships as a skill.*
