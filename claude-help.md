# Best Way Claude

Guide for Claude Code on this Mac and the Windows PC. Updated 19 Oct 2026.

Use this file two ways:

- Read it yourself when you start a session.
- Point Claude at it: `Read ~/Documents/Best Way Claude.md and follow it for this task.`

**Contents**

1. The rule that saves tokens
2. Daily habits
3. User scope: every project
4. Project scope: Unity, Next.js, FastAPI
5. Session tools: turn on for a day
6. Optional extras: desktop app only
7. Set up a new machine
8. Clean up a machine with the old set
9. Removed and why
10. Gotchas

Restart `claude` after any plugin install, uninstall, enable or disable. Changes load on the next session.

## 1. The rule that saves tokens

Every **enabled** plugin adds its skills, MCP tools and startup text to every message, even when you never use it. Disabled or uninstalled plugins cost nothing.

| Where | What goes there |
|---|---|
| User scope | Only what every project needs |
| Project scope | What one kind of project needs. Install it inside that project folder. |
| Disabled | Tools you use some days. Enable for the session, then disable again. |

Effort is `medium` for Sonnet 5.5 and Opus 5.5 in `~/.claude/settings.json`. Use `/effort high` for a hard bug or architecture work.

## 2. Daily habits

```text
/context
/compact
```

- `/context` shows what fills the window. `/compact` shrinks a long chat.
- Start a fresh chat when the topic changes. A long mixed chat costs more than a new one.
- Ask for one job per message. Name the skill or slash command, the file, and the done check.

Good:

```text
Use the unity ui-ugui skill.
Add a pause button to the match HUD in <file>.
Keep the existing Canvas scaler. Do not restyle other screens.
Done when the button calls <method> and the layout still matches phone and pad.
```

Weak: "Make the UI better and also check security and Firebase."

## 3. User scope: every project

| Job | Plugin | How to use |
|---|---|---|
| Engineering method | `superpowers` | Name the skill: systematic-debugging, test-driven-development, writing-plans, verification-before-completion |
| GitHub | `github` | Plain language: issues, PRs, search |
| Commits | `commit-commands` | `/commit`, `/commit-push-pr`, `/clean_gone` |
| Review | `code-review` | `/code-review` |
| New feature | `feature-dev` | `/feature-dev <feature>` |
| Library docs | `context7` | Ask for current docs instead of pasting them (log in once with `/mcp`) |
| Live security check | `security-guidance` | Hooks only, no command |
| Short CLAUDE.md | `claude-md-management` | `/revise-claude-md` |
| Cost report | `session-report` | Run it when you want a report |

All nine come from `claude-plugins-official` and work in every terminal: Cursor, macOS Terminal and PowerShell. This is the full working setup.

## 4. Project scope: Unity, Next.js, FastAPI

Open a terminal **in the project's root folder** first. `--scope project` writes the plugin into that project's `.claude/settings.json`. Commit that file and anyone who clones the repo gets the same plugins. Use `--scope local` instead for a plugin only you want in that project.

Each line runs the same on macOS and Windows.

### Unity game

```text
claude plugin install unity@claude-plugins-official --scope project
claude plugin install csharp-lsp@claude-plugins-official --scope project
```

Add only what the game uses:

```text
claude plugin install firebase@claude-plugins-official --scope project
claude plugin install revenuecat@claude-plugins-official --scope project
claude plugin install sentry@claude-plugins-official --scope project
```

- `unity`: say the skill by name. There is no `/unity` command. Game UI is `ui-ugui` (Canvas) or `ui-uitk` (UI Toolkit).
- `csharp-lsp`: code navigation for Unity C#.
- `firebase`: Firestore, Auth, Functions. Log in to its MCP once.
- `revenuecat`: only if the game uses RevenueCat for IAP. For Unity IAP, use the `implement-in-app-purchases` skill in `unity`.
- `sentry`: only if you send crash reports to Sentry.

A project that already has `unity` at project scope but disabled:

```text
claude plugin enable unity@claude-plugins-official --scope project
```

Common Unity prompts:

```text
Use the unity ui-ugui skill. Build this Canvas screen: <what>.
Use the unity ui-uitk skill. Edit <file>.uxml and <file>.uss: <what>.
Use the unity-cli skill. In the open Editor: <what>.
Use the unity-package-management skill. Add or upgrade <package>.
Use the implement-in-app-purchases skill.
Use the build-live-game skill.
Use the optimize-text-mesh-pro skill.
Use the localization skill.
```

### Next.js

```text
claude plugin install frontend-design@claude-plugins-official --scope project
claude plugin install typescript-lsp@claude-plugins-official --scope project
claude plugin install playwright@claude-plugins-official --scope project
```

Add only what the app uses:

```text
claude plugin install vercel@claude-plugins-official --scope project
claude plugin install supabase@claude-plugins-official --scope project
claude plugin install firebase@claude-plugins-official --scope project
claude plugin install stripe@claude-plugins-official --scope project
claude plugin install sentry@claude-plugins-official --scope project
```

- `frontend-design`: `Use the frontend-design skill. Implement <screen>. Reuse existing components.`
- `typescript-lsp`: type-aware code navigation.
- `playwright`: open the page, click through the flow, report what broke.
- `vercel`: only if you deploy on Vercel. It adds a long startup block, so skip it otherwise.
- Pick one database plugin, `supabase` or `firebase`, not both.

### FastAPI

```text
claude plugin install pyright-lsp@claude-plugins-official --scope project
```

Add only what the API uses:

```text
claude plugin install logfire@claude-plugins-official --scope project
claude plugin install sentry@claude-plugins-official --scope project
claude plugin install supabase@claude-plugins-official --scope project
claude plugin install firebase@claude-plugins-official --scope project
```

- `pyright-lsp`: Python type checking and code navigation.
- `logfire`: Pydantic's tracing and logs, which work well with FastAPI.
- `context7` at user scope already covers FastAPI, Pydantic and SQLAlchemy docs.

### Next.js front end with a FastAPI back end in one repo

Install the Next.js set and `pyright-lsp` in the repo root.

### Current project setups

| Machine | Project | Project-scope plugins |
|---|---|---|
| Mac | `~/Documents/Work/MatchUp_Games/PowerUp_Pool` | `unity` (enable it), `csharp-lsp`, `firebase` if used |
| Windows | `D:\Work\Solitaire\Unity-Color-Solitaire` | `unity` (enable it), `csharp-lsp`, `firebase` if used |
| Windows | `D:\Work\Solitaire\fc-solitaire` | Old `code-review` copy. Remove it. |

## 5. Session tools: turn on for a day

These are installed but disabled. Enable one for the day you need it, then disable it again.

| Plugin | Use it for |
|---|---|
| `figma` | Figma frames to code |
| `canva`, `adobe-for-creativity` | Marketing art |
| `superdesign` | Screen redesigns |
| `stripe`, `auth0` | Web payments, web login |
| `expo` | React Native apps |
| `sentry` | Crash reports, if a project doesn't have it at project scope |
| `circle-skills` | USDC and web3 |
| `42crunch-api-security-testing` | OpenAPI spec audits |

```text
claude plugin enable figma@claude-plugins-official
claude plugin disable figma@claude-plugins-official
```

If enable says "not found", that plugin isn't installed on this machine. Install it instead:

```text
claude plugin install figma@claude-plugins-official --scope user
```

## 6. Optional extras: desktop app only

| Job | Plugin | Command |
|---|---|---|
| Secrets | `env-protector-secret-scanner` | `/scan-secrets` |
| Short answers | `caveman-mode-short-answers` | `/caveman` |
| Shorter prompts | `prompt-tightener-clearer-shorter-llm-prompts` | `/prompt-review <prompt or file>` |
| Compression | `agentone-token-compression` | `/tokens-on`, then `/tokens` |

These come from `anthropic-plugin-directory`. **The terminal can't install them**, whether that's Cursor's console, macOS Terminal or PowerShell.

- The directory marketplace syncs only into the **Claude desktop app** from your claude.ai account. The `claude` CLI only knows `claude-plugins-official`, which you can confirm with `claude plugin marketplace list`.
- `claude plugin marketplace add` and `claude plugin marketplace update anthropic-plugin-directory` both fail with `Marketplace 'anthropic-plugin-directory' not found`. Signing the CLI in with `/login` doesn't add it either.
- To use them, install them from the **Discover** tab in the Claude desktop app. They then work in desktop app sessions only. In Cursor's terminal they show `failed to load`, which costs no tokens.
- On the Windows PC they aren't installed, and that's fine.

## 7. Set up a new machine

These lines work the same in macOS Terminal, Windows PowerShell and Command Prompt:

```text
claude plugin marketplace add anthropics/claude-plugins-official
claude plugin install superpowers@claude-plugins-official --scope user
claude plugin install github@claude-plugins-official --scope user
claude plugin install commit-commands@claude-plugins-official --scope user
claude plugin install code-review@claude-plugins-official --scope user
claude plugin install feature-dev@claude-plugins-official --scope user
claude plugin install context7@claude-plugins-official --scope user
claude plugin install security-guidance@claude-plugins-official --scope user
claude plugin install claude-md-management@claude-plugins-official --scope user
claude plugin install session-report@claude-plugins-official --scope user
```

Then set effort to medium (the commands are in section 8, step 4), and add each project's plugins from section 4.

## 8. Clean up a machine with the old set

Run every step in order, then restart `claude`. "Not found in installed plugins" means it is already gone. That's fine.

### Windows PowerShell

**Step 1.** Uninstall the directory plugins. Run both commands. Each PC had a different set.

```powershell
foreach ($p in "context-bar-akash001uts","weektoken","tokenomics","token-guardian","claude-activity","delegate-agents-sized-to-the-job","crypto-bitcoin-analyst-charts-research","smoower-minified","buses","toru-claude-agents","tesserai","lux","mobile-design-system","spendcap","ux-ui-audit","figma-to-code-design-to-react-vue-and-html") { claude plugin uninstall "$p@anthropic-plugin-directory" }
```

```powershell
foreach ($p in "agent-architecture-designer","ai-ready-design-system","codesign","coding-agent-skills","design-dev-bridge","design-system-by-blue","design","frontier-simplify","intent","make-poster","platform-skills","poc-architect-by-ateam","pragmatic-dev-toolkit","prompt-design","ratemycode","resource-broker","uxkin","vectorlab-ui-ux-skills","visual-docs") { claude plugin uninstall "$p@anthropic-plugin-directory" }
```

**Step 2.** Uninstall the official duplicates, unused cloud tools and user-scope copies of project-only plugins:

```powershell
foreach ($p in "ui-theme-designer","pr-review-toolkit","hostinger","mongodb","azure","aws-core","aws-serverless","aws-amplify","vercel","cloudflare","supabase","terraform","firebase","csharp-lsp","playwright","frontend-design","unity","claude-security","code-simplifier","hookify","plugin-dev","skill-creator","playground") { claude plugin uninstall "$p@claude-plugins-official" }
```

**Step 3.** Disable the session tools (they stay installed):

```powershell
foreach ($p in "figma","adobe-for-creativity","canva","superdesign","stripe","auth0","expo","sentry","circle-skills","42crunch-api-security-testing") { claude plugin disable "$p@claude-plugins-official" }
```

**Step 4.** Set effort to medium:

```powershell
(Get-Content "$env:USERPROFILE\.claude\settings.json" -Raw) -replace '"effortLevel": "high"','"effortLevel": "medium"' | Set-Content "$env:USERPROFILE\.claude\settings.json" -NoNewline
```

**Step 5.** Make sure superpowers is installed:

```powershell
claude plugin install superpowers@claude-plugins-official --scope user
```

**Step 6.** Find project copies:

```powershell
Select-String -Path "$env:USERPROFILE\.claude\plugins\installed_plugins.json" -Pattern '"projectPath"'
```

**Step 7.** Check what's left:

```powershell
claude plugin list
```

### macOS Terminal

**Step 1.** Uninstall the directory plugins:

```bash
for p in context-bar-akash001uts weektoken tokenomics token-guardian claude-activity delegate-agents-sized-to-the-job crypto-bitcoin-analyst-charts-research smoower-minified buses toru-claude-agents tesserai lux mobile-design-system spendcap ux-ui-audit figma-to-code-design-to-react-vue-and-html; do claude plugin uninstall "$p@anthropic-plugin-directory"; done
```

**Step 2.** Uninstall the official duplicates, unused cloud tools and user-scope copies of project-only plugins:

```bash
for p in ui-theme-designer pr-review-toolkit hostinger mongodb azure aws-core aws-serverless aws-amplify vercel cloudflare supabase terraform firebase csharp-lsp playwright frontend-design unity claude-security code-simplifier hookify plugin-dev skill-creator playground; do claude plugin uninstall "$p@claude-plugins-official"; done
```

**Step 3.** Disable the session tools (they stay installed):

```bash
for p in figma adobe-for-creativity canva superdesign stripe auth0 expo sentry circle-skills 42crunch-api-security-testing; do claude plugin disable "$p@claude-plugins-official"; done
```

**Step 4.** Set effort to medium:

```bash
sed -i '' 's/"effortLevel": "high"/"effortLevel": "medium"/g' ~/.claude/settings.json
```

**Step 5.** Make sure superpowers is installed:

```bash
claude plugin install superpowers@claude-plugins-official --scope user
```

**Step 6.** Find project copies:

```bash
grep '"projectPath"' ~/.claude/plugins/installed_plugins.json
```

**Step 7.** Check what's left:

```bash
claude plugin list
```

### What you should see

- **User scope, enabled:** the nine plugins from section 3.
- **User scope, disabled:** whichever session tools from section 5 are installed on that machine.
- **Project scope:** only plugins from section 4, inside their projects.
- The directory extras from section 6 may show `failed to load` in the terminal. That's fine.

### Remove an old project copy

If an entry shows `Scope: project` and that project shouldn't have it, `cd` into that project folder and run this, using the plugin's name:

```text
claude plugin uninstall <name>@claude-plugins-official --scope project
```

## 9. Removed and why

Don't reinstall these at user scope:

- **Usage trackers that all measure the same thing:** `tokenomics`, `token-guardian`, `weektoken`, `context-bar`, `claude-activity`, `delegate-agents-sized-to-the-job`, `spendcap`. Use `/context` and `session-report` instead.
- **Wrong product:** `ui-theme-designer` (SAP Fiori), `smoower-minified` (ASP.NET), `crypto-bitcoin-analyst` (price charts), `buses`, `tesserai`.
- **Duplicates:** `toru-claude-agents` (repeats superpowers), `pr-review-toolkit` (repeats code-review), `code-simplifier` (the built-in `/simplify` does this).
- **Project-only, now installed per project:** `firebase`, `csharp-lsp`, `playwright`, `frontend-design`, `unity`.
- **Cloud you don't use with Firebase:** `azure`, `aws-core`, `aws-serverless`, `aws-amplify`, `cloudflare`, `terraform`, `mongodb`, `hostinger`, `vercel`, `supabase`. Install one at project scope if a project needs it.
- **On-demand tools:** `claude-security`, `hookify`, `plugin-dev`, `skill-creator`, `playground`. Install them for the day you use them.
- **Unused design and agent extras:** `lux`, `mobile-design-system`, `ux-ui-audit`, `figma-to-code`, and the 19 directory plugins on the Windows PC (`agent-architecture-designer` through `visual-docs` in section 8).

## 10. Gotchas

- **"Enabled at project scope" when uninstalling.** You ran the command inside a project that turns the plugin on. That's the per-project setup working. Don't run the suggested `disable --scope local`.
- **"Installed in user scope, not project".** You're not in the project folder. `cd` into it and run the command again. Never add `--scope user` to get past it, because that removes the copy every project uses.
- **Commands run from the folder you're in.** Uninstalls are global, but project-scope installs, enables and removals apply to the current folder. On Windows, PowerShell often opens in `C:\Windows\system32`, so `cd` first.
- **Synced plugins.** `design`, `engineering`, `marketing`, `product-management`, `productivity`, `postiz` and `unity@synced` come from your claude.ai account. They load only in synced sessions, like the desktop app, and the CLI can't remove them. Turn them off in claude.ai settings. For game work, turn off `marketing`, `product-management` and `postiz` first.
- **Check what's loaded:** `claude plugin list`. **See a plugin's cost before you add it:** `claude plugin details <name>@claude-plugins-official`.
