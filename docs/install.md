# Install

Three install paths. Pick the one that matches your stack and your comfort level.

## Path A · Claude Cowork (no terminal, ~3 minutes)

1. Download the repo as a ZIP from GitHub. Green "Code" button, "Download ZIP".
2. Unzip. You will have a folder called `super-intelligent-AI-setup`.
3. Drag the folder into your Claude plugins directory:
   - macOS: Finder, Shift+Cmd+G, paste `~/Library/Application Support/Claude/plugins/`, drag the folder in.
   - Windows: Explorer, paste `%APPDATA%\Claude\plugins\` in the address bar, drag the folder in.
   - Linux: paste `~/.config/Claude/plugins/` in your file manager, drag the folder in.
4. Quit Claude Cowork and reopen.
5. In a new conversation ask: `what skills do I have installed?` All ten skills should appear by their names.

No git, no terminal, no developer background required.

## Path B · Claude Cowork (terminal, ~30 seconds)

```bash
# macOS / Linux
cd ~/Library/Application\ Support/Claude/plugins
git clone https://github.com/teemutuo/super-intelligent-AI-setup

# Windows (PowerShell)
cd $env:APPDATA\Claude\plugins
git clone https://github.com/teemutuo/super-intelligent-AI-setup
```

Restart Claude Cowork. Updates later with `git pull`.

## Path C · ChatGPT, Copilot, or any other LLM

The skill bodies are model-portable. None of the auto-triggering works the way it does in Claude Cowork, but you can still install the skills as saved instructions or Custom GPTs.

For each skill in `skills/`:

- **ChatGPT** (Pro / Plus / Enterprise): Explore GPTs, Create, name the GPT after the skill, paste the SKILL.md body (everything below the frontmatter) into Instructions. Enable Web search and Code interpreter where the skill needs them.
- **Microsoft Copilot for Microsoft 365**: Copilot Studio, Create agent, paste the SKILL.md body into Instructions, attach your filled-in memory bootstrap to knowledge.
- **Generic LLM (Gemini, Mistral, local models)**: Save the SKILL.md body as a system prompt. Attach your filled-in memory bootstrap at the top of the conversation when invoking the skill.

The prompts in `prompts/` are even simpler. Open the file. Paste it into a fresh conversation. Fill in the bracketed placeholders. Save what Claude returns.

## Verify

Run this query to verify install:

> Use the superintelligence-ladder skill on me. I have memory bootstrap done, no plugins installed yet, no scheduled tasks. Tell me where I am and what my next move is.

If the answer references Level 2 or Level 3 by name and gives you a concrete next move, the skill loaded correctly.

## Update

Plugin install: `cd` into the plugin folder and `git pull`. Restart Cowork.

Manual install: re-paste the SKILL.md body if the file has changed since last use. The `version:` in the frontmatter tells you when to re-paste.

## Uninstall

Plugin install: delete the folder. Your `my-profile.md` lives in project knowledge, not in the plugin folder, so it is preserved.

Manual install: delete the Custom GPT / agent / saved instruction. Same memory persistence.
