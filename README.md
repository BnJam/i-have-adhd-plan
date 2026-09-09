<p align="center">
  <img src="./logo.png" alt="i-have-adhd-plan" width="140" />
</p>
<p align="center">
  <strong align="center">ADHD-friendly outputs. No ADHD diagnosis needed!</strong>
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

If Claude says `Marketplace 'i-have-adhd' already on disk`, remove the stale
marketplace registration by its configured name, then add this repository:

```bash
claude plugin marketplace remove i-have-adhd
claude plugin marketplace add BnJam/i-have-adhd-plan
claude plugin install i-have-adhd-plan@i-have-adhd-plan
```

This removes the marketplace entry only; it does not uninstall the original
`i-have-adhd` plugin.

## What it does

A skill for your coding assistant that stops it from burying the answer. Action first. Steps numbered. Plans stay short and executable. During authorized implementation, it also keeps a visible `Done / Current / Blocker / Next` checkpoint loop. No "Hope this helps!"


## What changes


<table>
<tr>
<td width="50%">

## Before

> Great question! Let me think about this. Your auth flow has a few moving pieces: the middleware, the token verification, and the cookie handling. Looking at `src/auth.ts`, the `verifyToken` function (around lines 42-58) seems to be using an older `jsonwebtoken` API. One approach would be to update the package and rewrite that function. After making the change, you'd want to run the auth tests to confirm nothing breaks. By the way, you might also want to look at your dependency versions overall. Hope this helps! Let me know if you want to dig deeper.

</td>

<td width="50%">

## After

> Run `npm install jsonwebtoken@latest`, then edit `src/auth.ts:42`.
>
> 1. Open `src/auth.ts`
> 2. Replace `verifyToken` (lines 42–58) with the snippet below
> 3. Run `npm test -- auth.spec.ts`
>
> Next: paste the first failing line if any test fails.

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
