# cyberpunk-help

**Agent skill for a Cyberpunk 2077 playthrough** — missions, Night City locations, CET console lookup, and a live read of whatever is actually installed (Vortex or manual mods).

Works on **Windows, Linux, and macOS**. The skill does **not** ship a frozen mod list or save-folder table. On each machine it **discovers** the game and saves by signature files.

<p align="center">
  <img src="https://img.shields.io/badge/License-MIT-c8ff00?style=flat-square" alt="MIT" />
  <img src="https://img.shields.io/badge/skills.sh-cyberpunk--help-00f0ff?style=flat-square" alt="skills.sh" />
  <img src="https://img.shields.io/badge/npx%20skills%20add-xyz--rainbow%2Fcyberpunk--help-ff2bd6?style=flat-square" alt="npx skills add" />
  <img src="https://img.shields.io/badge/platform-Windows%20%7C%20Linux%20%7C%20macOS-00ffff?style=flat-square" alt="Platform" />
  <img src="https://img.shields.io/badge/game-Cyberpunk%202077-ff6a00?style=flat-square" alt="Cyberpunk 2077" />
  <img src="https://img.shields.io/badge/python-3%2B-3776ab?style=flat-square&logo=python&logoColor=white" alt="Python" />
</p>

![Banner](assets/banner.svg)

## One-command installation

```bash
npx skills add xyz-rainbow/cyberpunk-help
```

Or via URL:

```bash
npx skills add https://github.com/xyz-rainbow/cyberpunk-help
```

Global, non-interactive:

```bash
npx skills add xyz-rainbow/cyberpunk-help -g -y
```

## What it does

- Reads **this** playthrough from save metadata (`metadata.9.json`) — quest path, position, patch — without editing `sav.dat`.
- Discovers **CET** version from the log next to the game, then looks up console commands on the **current** redmodding wiki (commands change per patch).
- On **first use in a session**, or when the Vortex deploy list changes, or when you say you added mods: inventory of installed mods + versions, OS, today’s date, then Nexus pages for newer files and relevant posts.
- Does **not** auto-deploy mods. Load-order fights and “should I install this?” belong in a separate `vortex-mods` skill.

![Architecture](assets/architecture.svg)

![Workflow](assets/workflow.svg)

## Prerequisites

- Python 3 (stdlib only) for `scripts/get_cp2077_help_context.py`
- Cyberpunk 2077 installed (Steam / GOG / Epic / Heroic / Proton)
- Optional: Vortex, Cyber Engine Tweaks

## Discovery script

From the skill directory:

```bash
python3 scripts/get_cp2077_help_context.py
```

Windows:

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File .\scripts\Get-Cp2077HelpContext.ps1
```

The script searches for `Cyberpunk2077.exe`, `vortex.deployment.json`, and save folders that contain both `metadata.9.json` and `sav.dat`. It does not assume a single canonical path.

## Limits

- Read-only on Vortex and saves
- No trainer / item dumps unless you explicitly ask
- CET mutate commands (teleport, facts) only on a clear request

## GitHub topics

`skills-sh` `npx-skills-add` `cyberpunk-2077` `vortex` `cyber-engine-tweaks` `ai-agent-skill` `linux` `windows` `steam-proton` `macos` `agent-skills`

## License

MIT. See [LICENSE](LICENSE).
