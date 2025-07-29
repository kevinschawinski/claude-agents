# Claude-Code "Good-Explanation" Agent Crew

A six-agent crew—Planner, Researcher, Code-Writer, Executor, Synthesizer, Critic—implemented as Markdown files with YAML front-matter. Each agent embodies David Deutsch's criterion of good explanations ("hard to vary") and Clean-Code limits (≤ 20-line functions). Drop the folder into Claude Code and you instantly get a transparent, inspectable multi-agent workflow.

## Quick start

```bash
cp -r agents/ ~/.claude/agents/   # or .claude/agents/ inside a project
```

Open Claude Code, run `/agents`, and confirm the crew appears.

---

## 1 · Why these agents?

| Role | Core duty | Rationale |
| ---- | --------- | --------- |
| **Planner** | Break user goal into falsifiable steps | Plan-and-execute beats reactive loops.  [oai_citation:0‡Anthropic](https://docs.anthropic.com/en/docs/agents-and-tools/tool-use/text-editor-tool?utm_source=chatgpt.com) |
| **Researcher** | Fetch primary-source facts with citations | Mirrors CrewAI’s “Researcher” archetype.  [oai_citation:1‡Ethan B. Holland](https://ethanbholland.com/2025/07/04/anthropic-ai-news-week-ending-07-04-2025/?utm_source=chatgpt.com) |
| **Code-Writer** | Draft minimal, self-explanatory code | Clean-Code rule of ≤ 20-line functions.  [oai_citation:2‡AWS Documentation](https://docs.aws.amazon.com/bedrock/latest/userguide/model-parameters-claude.html?utm_source=chatgpt.com) |
| **Executor** | Run code / CLI / API calls | Keeps execution separate from reasoning.  [oai_citation:3‡AWS Documentation](https://docs.aws.amazon.com/bedrock/latest/userguide/model-parameters-claude.html?utm_source=chatgpt.com) |
| **Synthesizer** | Turn raw outputs into a coherent answer | Matches Writer role in multi-agent playbooks.  [oai_citation:4‡Ethan B. Holland](https://ethanbholland.com/2025/07/04/anthropic-ai-news-week-ending-07-04-2025/?utm_source=chatgpt.com) |
| **Critic** | Veto unfalsifiable claims or sloppy code | Guardrails reduce hallucinations.  [oai_citation:5‡Anthropic](https://docs.anthropic.com/en/docs/agents-and-tools/tool-use/text-editor-tool?utm_source=chatgpt.com) |
| **Documentation-Writer *(opt-in)*** | Compile accurate, structured release docs; **only runs when explicitly invoked as `@documentation-writer`** | Named-agent invocation shipped in Claude Code’s July 2025 update, so doc generation doesn’t slow normal PR loops.  [oai_citation:6‡YouTube](https://www.youtube.com/watch?v=DNGxMX7ym44&utm_source=chatgpt.com) |

Now seven agents in total—six for everyday work, plus one you call on release day.

---

## 2 · Folder layout

```
agents/
├── plan-orchestrator.md
├── evidence-gatherer.md
├── code-writer.md
├── tool-runner.md
├── answer-writer.md
└── quality-guard.md
└── documentation-writer.md
```

Claude Code auto-loads user-scoped agents from `~/.claude/agents/` and project-scoped agents from `.claude/agents/`.

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
```

No restart required; Claude watches the folders live.

---

## 4 · Using the crew

### 4.1 List agents

```
/agents
```

Browse with arrow keys, hit Enter to view any prompt.

### 4.2 Implicit delegation

Just ask:

> "Create a slide deck summarising the latest LLM-safety papers."

The Planner decides the sequence; downstream agents execute automatically.

### 4.3 Explicit invocation

> Use the code-writer agent to draft a Python function that …

### 4.4 Writing release documentation (opt-in)

When you’re ready for docs, **call the agent by name**:

@documentation-writer  Generate release notes and API docs for v2.3

The agent won’t run automatically during everyday PRs, so normal coding loops stay fast.  
(Pro-tip: update your Planner prompt to delegate only tasks containing “@documentation-writer”.)

---

## 5 · Customising prompts & tools

- Edit any agent file—Claude reloads on save.
- Add built-ins (Bash, Python, WebFetch, etc.) under the `tools:` key.
- Prefer smaller, single-responsibility prompts; a long prompt is easy to vary and thus a bad explanation.

---

## 6 · Workflow in a nutshell

```
User → Planner → (Researcher | Code-Writer) → Executor → Synthesizer → Critic → User
```

If the Critic rejects output, the loop repeats until the checklist passes.

---

## 7 · Philosophical foundations

- **Good explanations** are "hard to vary without destroying their ability to explain" — David Deutsch.
- **Clean Code** cautions that functions "should hardly ever be 20 lines long" — Robert C. Martin.

These principles keep each agent lean, falsifiable and readable.

---

## 8 · Contributing

Pull requests welcome—stick to the "hard-to-vary + ≤ 20 LOC" ethos and cite any factual claims.

---

## 9 · License

MIT. See LICENSE for details.
