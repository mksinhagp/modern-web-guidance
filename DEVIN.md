# Devin mirror of GoogleChrome/modern-web-guidance

Mirror of [GoogleChrome/modern-web-guidance](https://github.com/GoogleChrome/modern-web-guidance) (Apache-2.0), installed as an org-level Devin plugin. Devin loads it through `.claude-plugin/plugin.json` and `skills/`.

## Local changes (keep minimal)

| Change | Why |
|---|---|
| CLI pinned: `npx -y modern-web-guidance@1.0.0` instead of `@latest` | No unreviewed npm code in sessions; the version matches the bundled guides (`--skill-version`). |
| `DISABLE_TELEMETRY=1` on every CLI call | Turns off the CLI's anonymous usage logging to `play.googleapis.com`. |
| `skills/chrome-extensions/` removed (also from `kimi.plugin.json`) | Chrome-extension building is out of scope. |

## Pinned upstream

- Upstream commit: `4dd968349e54ca45a05dd5c818fb035c9054b022` (2026-11-10)
- npm package: `modern-web-guidance@1.0.0`, skill version `2026_11_09-5bcc021b`

## Syncing upstream (about monthly)

1. `git fetch https://github.com/GoogleChrome/modern-web-guidance main` and merge into a branch.
2. Get the new npm version (`npm view modern-web-guidance version`). Run `npm pack modern-web-guidance@<v>` and confirm `skills/modern-web-guidance/skill-version.txt` matches the `--skill-version` in `SKILL.md`.
3. Reapply the changes above: replace every `@latest` with `@<v>`, keep `DISABLE_TELEMETRY=1`, keep `chrome-extensions` removed.
4. Check: `DISABLE_TELEMETRY=1 npx -y modern-web-guidance@<v> search "light dismiss dialog" --skill-version <ver>` returns results.
5. Update the pins above, open a PR, merge, then move the `devin-v*` tag. Both orgs install from that tag.
