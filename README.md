Claude-Code “Good-Explanation” Agent Crew

A six-agent crew—Planner, Researcher, Code-Writer, Executor, Synthesizer, Critic—implemented as Markdown files with YAML front-matter. Each agent embodies David Deutsch’s criterion of good explanations (“hard to vary”) and Clean-Code limits (≤ 20-line functions). Drop the folder into Claude Code and you instantly get a transparent, inspectable multi-agent workflow.

Quick start:
cp -r agents/ ~/.claude/agents/   # or .claude/agents/ inside a project
Open Claude Code, run /agents, and confirm the crew appears.

⸻

1 · Why these agents?

Role	Core duty	Rationale
Planner	Break user goal into falsifiable steps	Plan-and-execute beats reactive loops
Researcher	Fetch primary-source facts with citations	Mirrors CrewAI’s “Researcher” archetype
Code-Writer	Draft minimal, self-explanatory code	Clean-Code: functions “should hardly ever be 20 lines”
Executor	Run code / CLI / API calls	Keeps execution separate from reasoning
Synthesizer	Turn raw outputs into a coherent answer	Matches Writer role in multi-agent playbooks
Critic	Veto unfalsifiable claims / sloppy code	Guardrails reduce hallucinations


⸻

2 · Folder layout

agents/
├── plan-orchestrator.md
├── evidence-gatherer.md
├── code-writer.md
├── tool-runner.md
├── answer-writer.md
└── quality-guard.md

Claude Code auto-loads user-scoped agents from ~/.claude/agents/ and project-scoped agents from .claude/agents/.

⸻

3 · Installation

# Clone the repo
git clone https://github.com/<you>/claude-agent-crew.git

# Option A – project-local (share via Git)
mkdir -p .claude/agents
cp claude-agent-crew/agents/* .claude/agents/

# Option B – global (all projects)
mkdir -p ~/.claude/agents
cp claude-agent-crew/agents/* ~/.claude/agents/

No restart required; Claude watches the folders live.

⸻

4 · Using the crew

4.1 List agents

/agents

Browse with arrow keys, hit Enter to view any prompt.

4.2 Implicit delegation

Just ask:

“Create a slide deck summarising the latest LLM-safety papers.”

The Planner decides the sequence; downstream agents execute automatically.

4.3 Explicit invocation

Use the code-writer agent to draft a Python function that …


⸻

5 · Customising prompts & tools
	•	Edit any agent file—Claude reloads on save.
	•	Add built-ins (Bash, Python, WebFetch, etc.) under the tools: key.
	•	Prefer smaller, single-responsibility prompts; a long prompt is easy to vary and thus a bad explanation.

⸻

6 · Workflow in a nutshell

User → Planner → (Researcher | Code-Writer) → Executor → Synthesizer → Critic → User

If the Critic rejects output, the loop repeats until the checklist passes.

⸻

7 · Philosophical foundations
	•	Good explanations are “hard to vary without destroying their ability to explain” — David Deutsch.
	•	Clean Code cautions that functions “should hardly ever be 20 lines long” — Robert C. Martin.

These principles keep each agent lean, falsifiable and readable.

⸻

8 · Contributing

Pull requests welcome—stick to the “hard-to-vary + ≤ 20 LOC” ethos and cite any factual claims.

⸻

9 · License

MIT. See LICENSE for details.

