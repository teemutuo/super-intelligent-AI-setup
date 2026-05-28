# Push the repo to GitHub with Claude Code

Step-by-step. The whole publish takes about ten minutes the first time, less than two after that.

## Before you start

You need:
- A GitHub account.
- A GitHub Personal Access Token with `repo` scope, or `gh` CLI installed and authenticated.
- Claude Code installed on your machine (or any terminal you are comfortable with).
- The `super-intelligent-AI-setup-v6-FINAL.zip` unzipped on your machine.

## Step 1, create the empty GitHub repo

Use whichever path you prefer.

### Path A, web UI

1. Go to github.com, click "+" then "New repository".
2. Owner: your account. Repository name: `super-intelligent-AI-setup`.
3. Visibility: Public.
4. **Do not** initialize with a README, .gitignore, or license. The local folder already has those.
5. Click "Create repository".

### Path B, `gh` CLI

```bash
gh repo create super-intelligent-AI-setup --public --description "Ten skills and two bootstrap prompts that climb the Superintelligence Ladder. Installable Claude plugin. MIT licensed."
```

## Step 2, initialize the local folder as a git repo

Open Claude Code (or any terminal) in the unzipped `super-intelligent-AI-setup-v6` folder.

In Claude Code, run this prompt:

```
You are in a folder that should become a public GitHub repo at github.com/teemutuo/super-intelligent-AI-setup. The folder contains a .claude-plugin manifest, skills, prompts, and docs. Please:

1. Initialize git in this folder.
2. Set the default branch to "main".
3. Add all files to the staging area.
4. Verify the .gitignore is excluding my-profile.md, memory-filled.md, setup-filled.md, mapping files, .DS_Store.
5. Make the initial commit with message "Initial release, v1.0.0".
6. Add the remote origin: https://github.com/teemutuo/super-intelligent-AI-setup.git
7. Push to origin main.

Stop and ask me before each destructive operation. Do not push secrets or my-profile.md. Use the gh CLI if available; fall back to git commands if not.
```

Claude Code will walk through it. If you prefer to do it by hand:

```bash
cd super-intelligent-AI-setup-v6
git init -b main
git add .
git status            # confirm no my-profile.md, no memory-filled.md, no secrets
git commit -m "Initial release, v1.0.0"
git remote add origin https://github.com/teemutuo/super-intelligent-AI-setup.git
git push -u origin main
```

## Step 3, the URL is already set

All repo links in this kit already point at `https://github.com/teemutuo/super-intelligent-AI-setup`. If you publish under a different handle or repo name, update these four files before pushing:

- `README.md`
- `docs/install.md`
- `.claude-plugin/plugin.json` (the `homepage` field)
- `docs/push-to-github.md` (this file)

Then commit and push:

```bash
git commit -am "chore: set repo URL"
git push
```

## Step 4, verify the repo is live

Visit `https://github.com/teemutuo/super-intelligent-AI-setup`. Confirm:

- README renders with the inventory table.
- LICENSE shows MIT.
- The `skills/` folder has 10 numbered subfolders.
- The `prompts/` folder has the two .txt files.
- The `docs/` folder has install, quickstart, governance, open-source-stack.
- `.claude-plugin/plugin.json` is present.

If anything is missing, the local folder is the source of truth. Re-commit and re-push.

## Step 5, set the repo topics

On the GitHub repo page, click the gear icon next to "About". Add these topics so people can find it:

```
ai, claude, claude-cowork, productivity, plugin, skills, agents, personal-ai, memory, prompts
```

Set the website URL to your LinkedIn profile or your personal site.

## Step 6, test the install from scratch

On a second machine (or a fresh user account on your machine), follow `docs/install.md` Path A. The whole flow should work without touching the local source folder. If anything fails, fix in the repo, push, and re-test.

This is the verification step the user's reviewers actually run. Do not skip it.

## Step 7, ship

The repo URL is now stable. The DM message can include it. The LinkedIn post can ship.

## If you want to use a private repo while testing

1. Step 1, choose Private visibility.
2. Use the same flow.
3. When ready to launch, in repo Settings: Danger Zone, Change visibility to Public.
4. The URL stays the same.

## If you want to use a different repo name

The default is `super-intelligent-AI-setup`. If you want something shorter (`sai-toolkit`, `ai-os`, your-name/`sai`), update:

- The repo name on GitHub.
- The `homepage` field in `.claude-plugin/plugin.json`.
- The `https://github.com/...` URL in `README.md` and `docs/install.md`.
- The URL in your DM message file.

Test the install path again after renaming.

## What you do not push

- `my-profile.md`. Personal context. Never commit.
- `memory-filled.md`, `setup-filled.md`. Filled-in versions of the bootstrap prompts. Personal context. Never commit.
- `.DS_Store` or `Thumbs.db`. OS metadata.
- Any secret tokens, API keys, or credentials.

The `.gitignore` in the repo already excludes all of these. Verify with `git status` before every push that none of them appear in the staging area.

## Rollback if something goes wrong

If the first push exposes something you did not mean to expose:

1. **Stop using the repo immediately.** Do not push more commits.
2. **Delete the repo on GitHub.** Repo Settings, Danger Zone, Delete this repository.
3. **Fix the source locally.** Remove the file, re-check `.gitignore`, re-do the initial commit clean.
4. **Recreate the repo and push again.** Same URL, fresh history.

Force-push to overwrite history works for small accidents (an extra commit, a wrong message). For exposed secrets, delete and recreate is safer because forks and caches can hold the old commits.

## After publication

- Star your own repo (signals to others that you stand behind it).
- Pin the repo on your GitHub profile.
- Add the repo URL to your LinkedIn profile under Featured.
- Update the README acknowledgments section as people PR improvements.

The repo is now live. Time to post.
