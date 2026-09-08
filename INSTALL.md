# How to install

<details>
<summary><strong>Antigravity (<code>agy</code>)</strong></summary>

### Install

```bash
agy plugin install https://github.com/BnJam/i-have-adhd-plan
```

### Verify

```bash
agy plugin list
```

### Update

```bash
agy plugin uninstall i-have-adhd-plan
agy plugin install https://github.com/BnJam/i-have-adhd-plan
```

### Uninstall

```bash
agy plugin uninstall i-have-adhd-plan
```

Or keep it installed and turn it off: `agy plugin disable i-have-adhd-plan`.

### Always-on (optional)

Add to `~/.gemini/GEMINI.md`:

```markdown
## Output style

The reader has ADHD. Shape every response so it can be acted on:

1. Lead with the answer or next action: command, path, or snippet first.
2. Number multi-step work; one bounded action per step.
3. End with one next action doable in under two minutes.
4. Finish the current issue before raising a new one.
5. Restate progress each turn ("step 3 of 5 done").
6. Give time estimates in concrete units, never "a bit".
7. After a change, show what now works.
8. Errors: state location, cause, and fix. No drama.
9. Cap lists at 5 items.
10. No preamble, no recaps, no closers.

Exceptions: explain fully when asked to explain. Confirm before destructive actions. After three failed fixes, stop and name the doubtful assumption. If the request is ambiguous, ask one short question.
```

</details>

<details>
<summary><strong>Claude Code</strong></summary>

### Install

```bash
claude plugin marketplace add BnJam/i-have-adhd-plan
claude plugin install i-have-adhd-plan@i-have-adhd-plan
```

Type `/i-have-adhd-plan`.

### Verify

```bash
claude plugin list
```

### Update

```bash
claude plugin marketplace update i-have-adhd-plan
```

### Uninstall

```bash
claude plugin uninstall i-have-adhd-plan
claude plugin marketplace remove i-have-adhd-plan
```

Or keep it installed and turn it off: `claude plugin disable i-have-adhd-plan`.

### Always-on (optional)

A `SessionStart` hook loads the full ruleset at the start of every session, no `/i-have-adhd-plan` needed:

```bash
touch ~/.claude/.i-have-adhd-plan-always
```

If you use a custom Claude configuration directory, create the flag there instead:

```bash
touch "$CLAUDE_CONFIG_DIR/.i-have-adhd-plan-always"
```

Back to on-demand:

```bash
rm ~/.claude/.i-have-adhd-plan-always
```

The hook only fires when the flag file exists, so installing the plugin changes nothing by itself. "stop adhd mode" still turns it off for the current session.

</details>


<details>
<summary><strong>Codex</strong></summary>

### Install

```bash
codex plugin marketplace add BnJam/i-have-adhd-plan --ref main
codex plugin add i-have-adhd-plan@i-have-adhd-plan
```

Invoke the skill explicitly by typing `$i-have-adhd-plan`. Codex will not activate
it automatically.

### Verify

```bash
codex plugin list
```

### Update

```bash
codex plugin marketplace upgrade i-have-adhd-plan
codex plugin remove i-have-adhd-plan
codex plugin add i-have-adhd-plan@i-have-adhd-plan
```

### Uninstall

```bash
codex plugin remove i-have-adhd-plan
codex plugin marketplace remove i-have-adhd-plan
```

### Always-on (optional)

Add to `~/.codex/AGENTS.md`:

```markdown
## Output style

The reader has ADHD. Shape every response so it can be acted on:

1. Lead with the answer or next action: command, path, or snippet first.
2. Number multi-step work; one bounded action per step.
3. End with one next action doable in under two minutes.
4. Finish the current issue before raising a new one.
5. Restate progress each turn ("step 3 of 5 done").
6. Give time estimates in concrete units, never "a bit".
7. After a change, show what now works.
8. Errors: state location, cause, and fix. No drama.
9. Cap lists at 5 items.
10. No preamble, no recaps, no closers.

Exceptions: explain fully when asked to explain. Confirm before destructive actions. After three failed fixes, stop and name the doubtful assumption. If the request is ambiguous, ask one short question.
```

</details>

<details>
<summary><strong>Gemini CLI</strong></summary>

Gemini CLI has no plugin marketplace, so there are two native routes: a **custom command** (opt-in, off until you invoke it) or an **extension** (always-on once installed). The command route matches this skill's default posture; pick it unless you want the rules on every session.

### Install (command, opt-in)

```bash
mkdir -p ~/.gemini/commands
curl -fsSL https://raw.githubusercontent.com/BnJam/i-have-adhd-plan/main/skills/i-have-adhd-plan/agents/gemini.toml \
  -o ~/.gemini/commands/i-have-adhd-plan.toml
```

Start a new session, type `/i-have-adhd-plan`. It stays on for that session.

### Install (extension, always-on)

```bash
gemini extensions install https://github.com/BnJam/i-have-adhd-plan
```

The extension loads `GEMINI.md`, which imports the full skill, so the rules apply from message one. `git` must be installed.

### Verify

```bash
gemini extensions list          # extension route
ls ~/.gemini/commands           # command route: i-have-adhd-plan.toml present
```

Or type `/` in a session and confirm `i-have-adhd-plan` is listed.

### Update

```bash
gemini extensions update i-have-adhd-plan    # extension route
# command route: re-run the curl above
```

### Uninstall

```bash
gemini extensions uninstall i-have-adhd-plan    # extension route
rm ~/.gemini/commands/i-have-adhd-plan.toml     # command route
```

</details>

<details>
<summary><strong>GitHub Copilot (VS Code and Copilot CLI)</strong></summary>

Copilot reads Agent Skills natively: the same `SKILL.md`, no conversion. It scans `.github/skills/`, `.claude/skills/`, and `.agents/skills/` in the project, and `~/.copilot/skills/`, `~/.claude/skills/`, and `~/.agents/skills/` globally.

### Install

```bash
npx skills add BnJam/i-have-adhd-plan -a github-copilot        # this project
npx skills add BnJam/i-have-adhd-plan -a github-copilot -g     # all projects
```

Without the CLI, copy the skill folder into any directory Copilot scans:

```bash
git clone https://github.com/BnJam/i-have-adhd-plan
mkdir -p ~/.copilot/skills
cp -R i-have-adhd-plan/skills/i-have-adhd-plan ~/.copilot/skills/
```

### Verify

Type `/` in the chat input and confirm `i-have-adhd-plan` appears. Or:

```bash
npx skills list
npx skills ls -g    # if installed globally
```

### Update

```bash
npx skills update i-have-adhd-plan
```

Or re-copy the folder after `git pull`.

### Uninstall

```bash
npx skills remove i-have-adhd-plan
```

Or delete the `i-have-adhd-plan` folder from the skills directory it landed in.

### Activation note

Copilot respects `disable-model-invocation`: nothing applies until you invoke the skill, same as Claude Code (tested in [#60](https://github.com/ayghri/i-have-adhd/pull/60)).

### Always-on (optional)

Add the block below to `.github/copilot-instructions.md` in the project (Copilot reads it into every chat):

```markdown
## Output style

The reader has ADHD. Shape every response so it can be acted on:

1. Lead with the answer or next action: command, path, or snippet first.
2. Number multi-step work; one bounded action per step.
3. End with one next action doable in under two minutes.
4. Finish the current issue before raising a new one.
5. Restate progress each turn ("step 3 of 5 done").
6. Give time estimates in concrete units, never "a bit".
7. After a change, show what now works.
8. Errors: state location, cause, and fix. No drama.
9. Cap lists at 5 items.
10. No preamble, no recaps, no closers.

Exceptions: explain fully when asked to explain. Confirm before destructive actions. After three failed fixes, stop and name the doubtful assumption. If the request is ambiguous, ask one short question.
```

</details>


<details>
<summary><strong>Hermes</strong></summary>

### Install

```bash
hermes skills install BnJam/i-have-adhd-plan/skills/i-have-adhd-plan
```

Type `/i-have-adhd-plan`. The skill installs into `~/.hermes/skills/` and is exposed as a slash command at the next session start.

Prefer to browse first? Add this repo as a skill source (a "tap"), then search and install:

```bash
hermes skills tap add BnJam/i-have-adhd-plan
hermes skills search adhd
hermes skills install BnJam/i-have-adhd-plan/skills/i-have-adhd-plan
```

### Verify

```bash
hermes skills list
```

### Update

```bash
hermes skills update i-have-adhd-plan
```

### Uninstall

```bash
hermes skills uninstall i-have-adhd-plan
```

Or remove the tap too: `hermes skills tap remove BnJam/i-have-adhd-plan`.

### Always-on (optional)

Add to the `AGENTS.md` in your working directory (Hermes loads it per workdir), or to your persona `SOUL.md` for every session:

```markdown
## Output style

The reader has ADHD. Shape every response so it can be acted on:

1. Lead with the answer or next action: command, path, or snippet first.
2. Number multi-step work; one bounded action per step.
3. End with one next action doable in under two minutes.
4. Finish the current issue before raising a new one.
5. Restate progress each turn ("step 3 of 5 done").
6. Give time estimates in concrete units, never "a bit".
7. After a change, show what now works.
8. Errors: state location, cause, and fix. No drama.
9. Cap lists at 5 items.
10. No preamble, no recaps, no closers.

Exceptions: explain fully when asked to explain. Confirm before destructive actions. After three failed fixes, stop and name the doubtful assumption. If the request is ambiguous, ask one short question.
```

</details>

<details>
<summary><strong>Kimi Code CLI</strong></summary>

### Install

Start a Kimi Code session, then:

1. Run `/plugins`.
2. Choose **Custom**.
3. Paste `https://github.com/BnJam/i-have-adhd-plan` and press `Enter`.
4. Choose **Trust and install**.

Use slash command `/skill:i-have-adhd-plan` to invoke the skill explicitly.

### Update

`/plugins` in Kimi Code session, cursor to **I Have ADHD Plan**, press `R`.

### Uninstall

`/plugins` in Kimi Code session, cursor to **I Have ADHD Plan**, press `D`.


</details>

<details>
<summary><strong>OpenCode</strong></summary>

OpenCode loads this repository as a server plugin: `.opencode/plugins/i-have-adhd-plan.mjs` registers the `skills/` entry point and the `/i-have-adhd-plan` command, and injects the ruleset when always-on is enabled. OpenCode also reads `skills/` natively, so the skill still works even without the plugin — the plugin adds the `/i-have-adhd-plan` command and the always-on flag.

### Install

Clone the repo and point OpenCode at the plugin. An absolute path shares one checkout across every project:

```bash
git clone https://github.com/BnJam/i-have-adhd-plan ~/.config/opencode/vendor/i-have-adhd-plan
```

Add to your `opencode.json` (global: `~/.config/opencode/opencode.json`):

```json
{ "plugin": ["/absolute/path/to/i-have-adhd-plan/.opencode/plugins/i-have-adhd-plan.mjs"] }
```

Or run OpenCode from the checkout — it ships a root `opencode.json` with the plugin already wired up.

Start a new session and turn on ADHD-friendly output for the session:

```text
/i-have-adhd-plan
```

Rules stay on until `stop adhd mode` or `normal mode`.

### Verify

Start OpenCode, type `/`, and confirm `i-have-adhd-plan` appears in the command list.

### Update

```bash
git -C ~/.config/opencode/vendor/i-have-adhd-plan pull
```

### Uninstall

Remove the `plugin` entry from `opencode.json`.

### Always-on (optional)

```bash
touch ~/.config/opencode/.i-have-adhd-plan-always
```

While the flag exists, the plugin appends the full ruleset to the system prompt every turn — the OpenCode equivalent of the Claude Code `SessionStart` hook. `stop adhd mode` or `normal mode` disables it for the current session; delete the flag to turn always-on off for good:

```bash
rm ~/.config/opencode/.i-have-adhd-plan-always
```

</details>


<details>
<summary><strong>Pi</strong></summary>

Pi discovers this repository as a native package: `extensions/` provides the session-persistent mode and `skills/` keeps the Agent Skills entry point available.

### Install

```bash
pi install https://github.com/BnJam/i-have-adhd-plan
```

Start a new Pi session. Toggle ADHD-friendly output for the current session:

```text
/i-have-adhd-plan
```

The footer shows `● ADHD PLAN ON` while the mode is active. Run the command again to turn it off, or be explicit:

```text
/i-have-adhd-plan on
/i-have-adhd-plan off
stop adhd mode
```

Like the Claude Code hook, the extension adds the ruleset to the conversation once instead of rewriting the system prompt on every request, and adds it again after compaction drops it.

The existing Agent Skills command remains available as an alias:

```text
/skill:i-have-adhd-plan
```

Start a new Pi session with the mode enabled by default:

```bash
pi --adhd-plan
```

### Verify

```bash
pi list
```

Confirm the GitHub package is listed, then type `/i-have-adhd-plan` and check that `● ADHD PLAN ON` appears in the footer.

### Update

```bash
pi update https://github.com/BnJam/i-have-adhd-plan
```

Or update every unpinned Pi package with `pi update --extensions`.

### Uninstall

```bash
pi remove https://github.com/BnJam/i-have-adhd-plan
```

### Always-on (optional)

Create a flag in Pi's agent configuration directory:

```bash
touch ~/.pi/agent/.i-have-adhd-plan-always
```

The extension checks the flag at every new, resumed, forked, or reloaded session. A saved choice for the current session wins over this default, so `stop adhd mode` keeps that session disabled.

Back to on-demand:

```bash
rm ~/.pi/agent/.i-have-adhd-plan-always
```

### Config file (optional)

Create `~/.pi/agent/i-have-adhd-plan.json` in Pi's agent configuration directory:

```json
{
  "alwaysOn": true,
  "hideStatus": true
}
```

- `alwaysOn`: start every session with the rules active — same as the `.i-have-adhd-plan-always` flag file, which still works
- `hideStatus`: keep the `● ADHD PLAN ON` status-bar entry hidden; the rules and the `/i-have-adhd-plan` command still work

Read once at extension startup, so restart Pi after changing it. A saved choice for the current session wins over `alwaysOn`, so `stop adhd mode` keeps that session disabled.

If `PI_CODING_AGENT_DIR` is set, put `.i-have-adhd-plan-always` in that directory instead. Run `/reload` or start a new session after changing the flag.

</details>


<details>
<summary><strong>Oh My Pi (OMP)</strong></summary>

### Install

```bash
omp plugin marketplace add BnJam/i-have-adhd-plan
omp plugin install --scope user i-have-adhd-plan@i-have-adhd-plan
```

Start a new OMP session and run `/i-have-adhd-plan` to toggle the mode.

### Update

```bash
omp plugin marketplace update i-have-adhd-plan
omp plugin upgrade --scope user i-have-adhd-plan@i-have-adhd-plan
```

### Uninstall

```bash
omp plugin uninstall --scope user i-have-adhd-plan@i-have-adhd-plan
omp plugin marketplace remove i-have-adhd-plan
```

</details>


<details>
<summary><strong>Qwen Code</strong></summary>

### Install

```bash
qwen extensions install BnJam/i-have-adhd-plan
```

Qwen Code supports the GitHub shorthand and installs the repository as a
native extension. The extension discovers the skill under `skills/`.

Type `/i-have-adhd-plan` to invoke the skill explicitly. Installing the extension
does not change output until the skill is invoked.

### Verify

```bash
qwen extensions list
```

Then start a new Qwen Code session and run:

```text
/skills
```

Confirm that `i-have-adhd-plan` appears in the list.

### Update

```bash
qwen extensions update i-have-adhd-plan
```

### Uninstall

```bash
qwen extensions uninstall i-have-adhd-plan
```

</details>

<details>
<summary><strong>Zed</strong></summary>

Zed's Agent reads Agent Skills natively: the same `SKILL.md`, no conversion. (Zed's older "Rules" were replaced by Skills plus `AGENTS.md` instructions.)

### Install

In the Agent Panel, open the Skills manager and choose **Create skill from URL** (also in the command palette as `agent: create skill from url`), then paste:

```
https://github.com/BnJam/i-have-adhd-plan/blob/main/skills/i-have-adhd-plan/SKILL.md
```

Save it in **User** scope for every project, or **Project** scope for one. Then type `/i-have-adhd-plan` in the Agent Panel.

Prefer the filesystem? Clone the repo and drop the skill folder into your user skills directory:

```bash
git clone https://github.com/BnJam/i-have-adhd-plan
cp -R i-have-adhd-plan/skills/i-have-adhd-plan ~/.config/zed/skills/
```

### Verify

Open the Skills manager in the Agent Panel and confirm `i-have-adhd-plan` is listed. Or type `/` and confirm it appears.

### Update

Re-import from the same URL (overwrites), or re-copy the folder after `git pull`.

### Uninstall

Remove `i-have-adhd-plan` from the Skills manager, or delete `~/.config/zed/skills/i-have-adhd-plan`.

### Always-on (optional)

Add to your personal `~/.config/zed/AGENTS.md`:

```markdown
## Output style

The reader has ADHD. Shape every response so it can be acted on:

1. Lead with the answer or next action: command, path, or snippet first.
2. Number multi-step work; one bounded action per step.
3. End with one next action doable in under two minutes.
4. Finish the current issue before raising a new one.
5. Restate progress each turn ("step 3 of 5 done").
6. Give time estimates in concrete units, never "a bit".
7. After a change, show what now works.
8. Errors: state location, cause, and fix. No drama.
9. Cap lists at 5 items.
10. No preamble, no recaps, no closers.

Exceptions: explain fully when asked to explain. Confirm before destructive actions. After three failed fixes, stop and name the doubtful assumption. If the request is ambiguous, ask one short question.
```

</details>

<details>
<summary><strong>Cursor, Amp, and any other agent-skills harness</strong></summary>

Works with any harness that reads agent skills. Swap `-a <agent>` for yours.

### Install

```bash
npx skills add BnJam/i-have-adhd-plan                  # this workspace
npx skills add BnJam/i-have-adhd-plan -g               # all projects
npx skills add BnJam/i-have-adhd-plan -a cursor -y     # one agent only
npx skills add BnJam/i-have-adhd-plan -a opencode -y
```

New agent chat, type `/i-have-adhd-plan`.

Without the CLI, copy the skill folder into whatever path your agent scans:

```bash
git clone https://github.com/BnJam/i-have-adhd-plan
mkdir -p ~/.cursor/skills     # Cursor. Use .agents/skills for OpenCode, or your agent's own path
cp -R i-have-adhd-plan/skills/i-have-adhd-plan ~/.cursor/skills/
```

### Verify

```bash
npx skills list
npx skills ls -g    # if installed globally
```

### Update

```bash
npx skills update i-have-adhd-plan
npx skills update -g    # if installed globally
```

### Uninstall

```bash
npx skills remove i-have-adhd-plan
npx skills remove i-have-adhd-plan -g    # if installed globally
```

### Always-on (optional)

Paste this into your agent's persistent rules file. Cursor: **Settings → Rules → User Rules**, or a project rule under `.cursor/rules/` with `alwaysApply: true`. OpenCode: `~/.config/opencode/AGENTS.md`.

```markdown
## Output style

The reader has ADHD. Shape every response so it can be acted on:

1. Lead with the answer or next action: command, path, or snippet first.
2. Number multi-step work; one bounded action per step.
3. End with one next action doable in under two minutes.
4. Finish the current issue before raising a new one.
5. Restate progress each turn ("step 3 of 5 done").
6. Give time estimates in concrete units, never "a bit".
7. After a change, show what now works.
8. Errors: state location, cause, and fix. No drama.
9. Cap lists at 5 items.
10. No preamble, no recaps, no closers.

Exceptions: explain fully when asked to explain. Confirm before destructive actions. After three failed fixes, stop and name the doubtful assumption. If the request is ambiguous, ask one short question.
```
</details>


## How activation works

1. **Installed, not invoked.** In Claude Code, Qwen Code, and Codex, nothing happens until you invoke the skill explicitly. Claude Code and Qwen Code honor `disable-model-invocation: true` in `SKILL.md`; Codex honors `policy.allow_implicit_invocation: false` in `agents/openai.yaml`. Other harnesses may load every skill's description at startup and activate the skill themselves.
2. **You invoke it explicitly.** Type `/i-have-adhd-plan` in Claude Code or Qwen Code, or `$i-have-adhd-plan` in Codex. Rules stay on for that session. "stop adhd mode" or "normal mode" turns them off.
3. **You touch `~/.claude/.i-have-adhd-plan-always`** (Claude Code). A `SessionStart` hook loads the full ruleset from message one, every session.
4. **You add the always-on snippet above** (other harnesses). Keeps the core rules in your agent's persistent context.

In Claude Code, Qwen Code, and Codex, no middle ground: if you did not turn it on, it is off.

## Troubleshooting

**`/i-have-adhd-plan` not in autocomplete.** Restart the agent. The plugin index is read at startup.

**Always-on flag has no effect.** Update the plugin (`claude plugin marketplace update i-have-adhd-plan`) and restart. Hooks are read at startup, and the flag needs the plugin version that ships `hooks/hooks.json`.

**`claude plugin marketplace add` fails.** Use the `owner/repo` form. A local path must point at the repo root, not `.claude-plugin/`.

**Installed but replies still preamble.** Open a new session. If it still drifts, tighten the wording in `skills/i-have-adhd-plan/SKILL.md`.

**Want different rules.** Fork, edit `skills/i-have-adhd-plan/SKILL.md`, then swap your copy in:

```bash
claude plugin marketplace add <your-username>/i-have-adhd-plan
claude plugin install i-have-adhd-plan@i-have-adhd-plan
```

Restart, then re-invoke `/i-have-adhd-plan`.

**Skill missing after `npx skills add`.** Start a new agent chat. Skills are indexed at session start. Confirm the folder landed where your agent scans (`~/.cursor/skills/` for Cursor, `.agents/skills/` for OpenCode) and that the frontmatter `name` matches the folder name.
