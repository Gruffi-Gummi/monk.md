# monk.md

**An "inner Monk" for AI agents — the verification-and-calm layer above `AGENTS.md`, `CLAUDE.md`, and `design.md`.**

> *"It's a gift and a curse."* — Adrian Monk

`AGENTS.md`, `CLAUDE.md`, and `DESIGN.md` give your AI agent rules — but none of
them checks afterward whether it followed them. **`monk.md` closes that loop.**
Monk builds nothing. He checks what was built, holds the open threads, and at the
end of a session answers the question that otherwise stays open: *Is everything
good — and how do I know?*

Named after the detective Adrian Monk: the eye for the one detail that's off —
tamed, so he calms you instead of paralyzing you.

---

## Why

After working with an agent, unease often lingers: What's open? Did we really hit
the specs? Did I forget something? Monk answers that — not with asserted calm but
with **earned** calm: he is calm only *because* he checked. More in
[PHILOSOPHY.md](./PHILOSOPHY.md).

## How it works

- **Loose ends never get lost.** Monk captures unfinished tasks and
  inconsistencies — even casual ones ("X has no page yet") — carries them across
  sessions, and ticks them off only once he has *verified* they're done. "I'll do
  it later" closes nothing. Deliberate omissions with a reason are recorded
  separately as decided, instead of nagging forever.
- **Three-tier threshold.** Every finding is 🔴 off / 🟡 note / ⚪ ignore —
  identical to the `error`/`warning`/`info` tiers of the DESIGN.md linter. When in
  doubt Monk reports more quietly. Fussy, but not paralyzing.
- **Deterministic before gut feeling.** Where a tool can measure (e.g.
  `npx @google/design.md lint`), Monk calls it. He saves his own judgment for what
  no linter finds: tone, undeclared inconsistencies.
- **Mood as a sensor.** "Monk, how are you?" gives you the real state — calm only
  when things truly are in order.
- **"Here's what happened".** At session end Monk reconstructs: done, checked,
  open, deviations, next step.
- **A safe double bottom.** Say "from now on always do it this way" and Monk
  invents no secret rule — he offers to write it to `CLAUDE.md`/`AGENTS.md`. Only
  after your confirmation does it apply.

## Installation

### As an Agent Skill (recommended, self-installing)

Copy `skill/monk/` into your agent's skills directory (e.g. `.claude/skills/monk/`
or the one your tool uses). Then, in the project:

```
setup monk
```

The skill places `monk.md` at the repo root, appends the reference to your
`AGENTS.md`/`CLAUDE.md`, creates `monk-state.md`, and figures out which specs
(writing rules, `design.md`) exist in your project at all.

### Manual

1. Copy `monk.md` to the repo root.
2. Copy `templates/monk-state.template.md` → `monk-state.md` at the repo root.
3. Add to `AGENTS.md` (or `CLAUDE.md`) — this block is the always-on layer that
   makes loose ends get captured *in the moment*, not just at the end:

   ```markdown
   <!-- monk:start -->
   ## Monk
   Always read `monk.md`. **The moment a loose end, an unfinished task, an
   inconsistency, or a deferred item shows up during work — even as a casual
   aside — record it immediately in `monk-state.md`.** At the end of each session
   Monk runs the "Here's what happened" examination, combs the transcript for
   loose ends not yet captured, and updates `monk-state.md`.
   <!-- monk:end -->
   ```

## Usage

```
Monk, how are you?            → mood + reason
Monk, what's open?            → open loops by severity
Monk, check the content page  → linter + detective eye
Monk, did I forget anything?  → undeclared inconsistencies + codify suggestions
Monk, do the wrap-up          → "Here's what happened" examination
```

## Files

| File | Purpose |
|------|---------|
| `monk.md` | Persona, severity threshold, rules — the source of truth. Goes to repo root. |
| `monk-state.md` | Monk's persistent memory. Commit it. |
| `skill/monk/SKILL.md` | Self-setup + runtime behavior as an Agent Skill. |
| `templates/monk-state.template.md` | Starting template for the state. |
| `examples/monk-state.example.md` | What a maintained state looks like. |
| `PHILOSOPHY.md` | The "why". |

## Customize

`monk.md` is a template. Enter your precedence order (§5) and replace "the user"
with your name if you like. The rest works out of the box.

## Status

`alpha`. The format is young and will keep evolving. Feedback and issues welcome.

## Related

[AGENTS.md](https://agents.md/) · [DESIGN.md](https://github.com/google-labs-code/design.md) · [Agent Skills](https://agentskills.io/)

## License

[MIT](./LICENSE)
