Below is a drop-in README.md for your repo.
Feel free to tweak headers or wording, but the structure and links already follow Anthropic’s sub-agent spec and Deutsch/Clean-Code philosophy.

# Claude-Code “Good-Explanation” Agent Crew

A **six-agent crew**—Planner, Researcher, Code-Writer, Executor, Synthesizer, Critic—implemented as Markdown files with YAML front-matter.  Each agent embodies David Deutsch’s criterion of *good explanations* (“hard to vary”) and Robert Martin’s Clean-Code limits (≤ 20-line functions).  Drop the folder into Claude Code and you instantly get a transparent, inspectable multi-agent workflow.  

> **Quick start:**  
> `cp -r agents/ ~/.claude/agents/   # or  .claude/agents/ in a project`  
> Open Claude Code, run **`/agents`**, and confirm the crew appears.  

---

## 1 · Why these agents?

| Role | Core duty | Rationale |
| ---- | --------- | --------- |
| **Planner** | Break user goal into falsifiable steps | Plan-and-execute beats reactive loops  [oai_citation:0‡LangChain Blog](https://blog.langchain.com/planning-agents/?utm_source=chatgpt.com) |
| **Researcher** | Fetch primary-source facts with citations | Matches CrewAI’s *Researcher* archetype  [oai_citation:1‡CrewAI](https://docs.crewai.com/concepts/agents?utm_source=chatgpt.com) |
| **Code-Writer** | Draft minimal, self-explanatory code | Clean-Code: functions “should hardly ever be 20 lines”  [oai_citation:2‡Medium](https://medium.com/%40j.munguia/lessons-from-clean-code-c8514d30b175?utm_source=chatgpt.com) |
| **Executor** | Run code / CLI / API calls | Keeps execution separate from reasoning  [oai_citation:3‡langchain.com](https://www.langchain.com/agents?utm_source=chatgpt.com) |
| **Synthesizer** | Turn raw outputs into a coherent answer | Mirrors Writer in multi-agent playbooks  [oai_citation:4‡Medium](https://medium.com/%40harshav.vanukuri/a-complete-guide-to-crew-ai-and-agentic-frameworks-unleashing-the-power-of-autonomous-ai-crews-9911f39110f5?utm_source=chatgpt.com) |
| **Critic** | Veto unfalsifiable claims / sloppy code | Guardrails reduce hallucinations  [oai_citation:5‡GitHub](https://github.com/microsoft/autogen/discussions/5356?utm_source=chatgpt.com) |

All prompts lean on Deutsch’s “hard-to-vary” rule  [oai_citation:6‡Goodreads](https://www.goodreads.com/quotes/11783233-we-do-so-by-seeking-good-explanations-explanations-that?utm_source=chatgpt.com) and Clean-Code readability practices  [oai_citation:7‡Medium](https://medium.com/%40diego.coder/clean-code-pocket-manual-2e6035bb4e55?utm_source=chatgpt.com).

---

## 2 · Folder layout

agents/
├── plan-orchestrator.md
├── evidence-gatherer.md
├── code-writer.md
├── tool-runner.md
├── answer-writer.md
└── quality-guard.md

Claude Code auto-loads **user-scoped** agents from `~/.claude/agents/` and **project-scoped** agents from `.claude/agents/`  [oai_citation:8‡Anthropic](https://docs.anthropic.com/en/docs/claude-code/settings?utm_source=chatgpt.com).

---

## 3 · Installation

```bash
# Clone the repo
git clone https://github.com/<you>/claude-agent-crew.git

# Option A – project-local (share via Git)
mkdir -p .claude/agents
cp claude-agent-crew/agents/* .claude/agents/

# Option B – global (all projects)
mkdir -p ~/.claude/agents
cp claude-agent-crew/agents/* ~/.claude/agents/

No restart required; Claude watches the folders live  ￼.

⸻

4 · Using the crew

4.1 List agents

/agents

Browse with arrow keys, hit Enter to view any prompt.

4.2 Implicit delegation

Just ask:

“Create a slide deck summarising latest LLM safety papers.”

The Planner decides the sequence; downstream agents execute automatically  ￼.

4.3 Explicit invocation

Use the code-writer agent to draft a Python function that …


⸻

5 · Customising prompts & tools
	•	Edit any agent file—Claude reloads on save.
	•	Add built-ins (Bash, Python, WebFetch, etc.) under the tools: key  ￼.
	•	Prefer smaller, single-responsibility prompts; a long prompt is easy to vary and thus a bad explanation  ￼.

⸻

6 · Workflow in a nutshell

User ➜ Planner ➜ (Researcher | Code-Writer) ➜ Executor ➜ Synthesizer ➜ Critic ➜ User

If the Critic rejects output, the loop repeats until the checklist passes.

⸻

7 · Philosophical foundations
	•	Good explanations are “hard to vary without destroying their ability to explain” —David Deutsch  ￼.
	•	Clean Code cautions that functions “should hardly ever be 20 lines long” —Robert C. Martin  ￼.
These principles keep each agent lean, falsifiable, and readable.

⸻

8 · Contributing

Pull requests welcome—stick to the “hard-to-vary + ≤20 LOC” ethos and include at least one citation for any factual claim.

⸻

9 · License

MIT.  See LICENSE for details.

**Happy building—may every commit be a step toward infinity.**
