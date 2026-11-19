# Install or update the Vibe Design Tips Skills

Steps for an AI coding agent (Claude Code, Codex, Cursor and others) to install or update these Skills on the user's machine. Ask the user before doing anything these steps do not describe.

The files are kept in one place, `~/.vibedesign-skills` (on Windows `%USERPROFILE%\.vibedesign-skills`), and each tool links to them, so one update reaches every tool.

## Which Skill

- **`kubai-design-tips`**: every tip in one Skill. It reviews a product's UI, suggests what to change and applies a tip the user names. Install this one unless the user asks for another.
- **`kubai-<name>`** (for example `kubai-liquid-glass`): one tip each. Install one only if the user names it. `kubai-design-tips` already holds every tip, so do not install both unless the user asks.

## Install

### 1. Get the files

If `~/.vibedesign-skills` already exists, go to [Update](#update) instead.

With git, and GitHub reachable:

```sh
git clone --depth 1 https://github.com/kubai087/vibedesign-skills.git ~/.vibedesign-skills
```

Without git, or if github.com cannot be reached, download the ZIP of every Skill from the first address that works:

- https://github.com/kubai087/vibedesign-skills/releases/latest/download/vibedesign-skills.zip
- https://vibedesign.tips/downloads/vibedesign-skills.zip

It holds a `vibedesign-skills` folder. Unpack it and move that folder to `~/.vibedesign-skills`, so the Skills are at `~/.vibedesign-skills/skills/<name>/SKILL.md`.

### 2. Link the Skill where the tool loads Skills

Find the folder where your tool loads the user's own Skills, the ones that work in every project: for Claude Code it is `~/.claude/skills/`. If you are not sure where it is for your tool, ask the user.

If that folder already has a `kubai-design-tips` folder (an older copy downloaded from vibedesign.tips), replace it. Then link the Skill:

```sh
ln -sfn ~/.vibedesign-skills/skills/kubai-design-tips ~/.claude/skills/kubai-design-tips
```

If the tool does not follow symbolic links, or links cannot be made (for example on Windows without the right to make them), copy the folder instead, and tell the user that each update then copies it again.

If the user works with more than one AI tool, ask whether to link it for the others too.

### 3. Tell the user

Read `VERSION` in the installed folder. Tell the user the version, where the files are and where you linked them, and that asking you to "update the design tips Skill" later updates it. If your tool loads new Skills only in a new session, say so.

## Update

1. Note the version in `~/.vibedesign-skills/skills/kubai-design-tips/VERSION`.
2. Get the new files:
   - If `~/.vibedesign-skills` is a git clone: `git -C ~/.vibedesign-skills pull --ff-only`. If local changes stop it, show them to the user and ask before discarding them.
   - Otherwise: download the ZIP again (addresses above) and replace `~/.vibedesign-skills` with the new `vibedesign-skills` folder.
   - If `~/.vibedesign-skills` does not exist (an older copy downloaded from vibedesign.tips), follow [Install](#install) from the start.
3. Where a Skill was copied rather than linked, copy the new folder over it again.
4. Tell the user the old and new versions, and what changed from [CHANGELOG.md](https://github.com/kubai087/vibedesign-skills/blob/main/CHANGELOG.md) (or https://vibedesign.tips/downloads/CHANGELOG.md). If the version did not change, say it is already up to date.

## Remove

Delete the links (or copies) in each tool's Skills folder, then `~/.vibedesign-skills`.
