<p align="center">
  <img src="./logo.png" alt="i-have-adhd-plan" width="140" />
</p>
<p align="center">
  <strong align="center">ADHD-friendly planning for agents and developers</strong>
</p>
<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/github/license/BnJam/i-have-adhd-plan?style=flat" alt="License"></a>
</p>

<p align="center">
  <strong title="English" aria-label="English">🇬🇧</strong> ·
  <a href=".github/readme/README.zh-CN.md" title="简体中文" aria-label="简体中文">🇨🇳</a> ·
  <a href=".github/readme/README.pt-BR.md" title="Português (Brasil)" aria-label="Português (Brasil)">🇧🇷</a> ·
  <a href=".github/readme/README.ja.md" title="日本語" aria-label="日本語">🇯🇵</a> ·
  <a href=".github/readme/README.vi.md" title="Tiếng Việt" aria-label="Tiếng Việt">🇻🇳</a> ·
  <a href=".github/readme/README.ko.md" title="한국어" aria-label="한국어">🇰🇷</a> ·
  <a href=".github/readme/README.th.md" title="ภาษาไทย" aria-label="ภาษาไทย">🇹🇭</a>
</p>


## Install

Copy/paste into your CLI prompt:

```text
Install the `i-have-adhd-plan` skill/plugin from this repository: https://github.com/BnJam/i-have-adhd-plan. Refer to `AGENTS.md` for repository instructions.
```

Or 🔗 [check the installation instructions](INSTALL.md).

If Claude says `Marketplace 'i-have-adhd-plan' already on disk`, remove the stale
marketplace registration by its configured name, then add this repository:

```bash
claude plugin marketplace remove i-have-adhd-plan
claude plugin marketplace add BnJam/i-have-adhd-plan
claude plugin install i-have-adhd-plan@i-have-adhd-plan
```

This removes the marketplace entry only; it does not uninstall the original
`i-have-adhd` plugin.

## What it does

`i-have-adhd-plan` is the planning-focused adaptation for agents and ADHD
developers. It helps an agent turn a request into a short, executable plan,
keep the current state visible, and maintain momentum during implementation.

This repository does not replace the original [`i-have-adhd` plugin or skill](https://github.com/ayghri/i-have-adhd).
That project provides the general ADHD-friendly response style. This project
builds on the same principles for the planning mode of agents: define the
goal, break work into bounded actions, identify dependencies and verification,
and stop at the next meaningful decision boundary.

During authorized implementation, it also keeps a visible
`Done / Current / Blocker / Next` checkpoint loop. No "Hope this helps!"

## Who it is for

- Developers who want agent plans that are easier to start and finish.
- Agents that need compact, stateful planning and execution checkpoints.
- Teams adapting ADHD-friendly interaction patterns to planning workflows.

It is an accessibility style, not a diagnosis or treatment claim. It can be
used by anyone who benefits from lower-friction plans and visible progress.


## What changes

The adaptation changes how an agent plans and carries work forward. It turns a
large request into a bounded goal, keeps verification beside the relevant
step, and makes the next action explicit.


<table>
<tr>
<td width="50%">

## Before: vague implementation guidance

> Your auth change has several moving pieces: routes, middleware, token
> verification, cookies, and tests. You could update the package and rewrite
> the verification function, then run the tests. There may also be other
> dependency updates to consider.

</td>

<td width="50%">

## After: an executable agent plan

> Goal: Update token verification while keeping existing login behavior working.
>
> 1. Open `src/auth.ts`
> 2. Inspect `verifyToken` and its callers; record the compatibility requirements.
> 3. Update the implementation and add focused regression coverage.
> 4. Run `npm test -- auth.spec.ts`; stop if the contract changes unexpectedly.
>
> Next: inspect `src/auth.ts` and identify the current token-verification contract.

</td>
</tr>
</table>


## The rules

10 rules. Full text in [SKILL.md](./skills/i-have-adhd-plan/SKILL.md).

1. Lead with the next action.
2. Number multi-step tasks.
3. End with one concrete next step.
4. Suppress tangents.
5. Restate state every turn.
6. Specific time estimates (minutes, not "a bit").
7. Make wins visible.
8. Matter-of-fact errors.
9. Cap lists at 5 items.
10. No preamble. No recap. No closers.

In plan mode, the default shape is a one-line goal, 3–5 bounded actions, and
one concrete next action. During execution, the agent works in meaningful
chunks, verifies before claiming completion, and reconstructs confirmed state
after interruptions. Detail stays beside the step it protects: add
verification, dependencies, and rollback points when the task needs them.

The skill is an accessibility style, not a diagnosis or treatment claim. See
[the research rationale](./docs/research-rationale.md) for evidence and limits.

## Tune it

To install this repository's uniquely named copy:

```bash
claude plugin marketplace add BnJam/i-have-adhd-plan
claude plugin install i-have-adhd-plan@i-have-adhd-plan
```

Restart Claude Code, then re-invoke `/i-have-adhd-plan`.

## Credits

Loosely based on *The Adult ADHD Tool Kit* by J. Russell Ramsay and Anthony L. Rostain. Adapted for how an LLM should respond, not how a human should organize their day.

## License

MIT.

Star ⭐ if it saved you one scroll past one "Great question!"
