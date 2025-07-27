This repo drops a ready-made six-agent crew—Planner, Researcher, Code-Writer, Executor, Synthesizer, Critic—into Claude Code. Each agent lives in a Markdown file with YAML front-matter and a focused system prompt. Copy (or symlink) the folder into .claude/agents/ for project-local use or ~/.claude/agents/ for global use, then run /agents inside a Claude Code session to confirm they’re picked up. That’s it—instant virtual team.  ￼ ￼ ￼

⸻

Contents

File	Role	Why it exists
plan-orchestrator.md	Planner	Breaks user goals into minimal, falsifiable steps
evidence-gatherer.md	Researcher	Pulls primary-source facts with citations
code-writer.md	Code-Writer	Drafts clean, ≤20-LOC modules plus doctest
tool-runner.md	Executor	Runs code or CLI safely, logs outcome
answer-writer.md	Synthesizer	Crafts a single-voice answer, flags open questions
quality-guard.md	Critic	Rejects sloppy code or unfalsifiable claims

All prompts lean on David Deutsch’s “good-explanation” standard and classic Clean-Code limits.

⸻

Quick install

# clone wherever you keep dotfiles
git clone https://github.com/<you>/claude-agent-crew.git
# project-scoped
cp -r claude-agent-crew/agents ./.claude/agents/
# or user-scoped
mkdir -p ~/.claude/agents && cp claude-agent-crew/agents/* ~/.claude/agents/

Claude Code watches those folders live—no restart needed. Conflicting names: project agents beat user agents.  ￼ ￼

⸻

Using the crew
	1.	Open Claude Code in your terminal.
	2.	Run /agents → you should see the six new entries. Use arrow keys + enter to inspect.  ￼
	3.	Invoke implicitly: just ask for a task; Claude auto-delegates based on each file’s description. Or call explicitly:

Use the code-writer agent to draft a Python function that…


	4.	The Critic agent’s veto loops the workflow until output meets the checklist.

⸻

Tweaking
	•	Edit any prompt; on save Claude reloads instantly.
	•	Add tools: under tools: list built-ins like Bash, Python, Read.  ￼
	•	Rename or remove agents as your project evolves.

Happy building—may every commit be a hard-to-vary step toward infinity.
