# Design Agents for Claude Code

Three [Claude Code](https://claude.com/claude-code) subagents for day-to-day Product Design work: accessibility review, design critique and UX research.

Each agent is a text file with instructions. Claude Code reads the file and hands the task to the right agent when you ask.

## The agents

| Agent | What it is for | What it delivers |
|---|---|---|
| `accessibility-reviewer` | Reviewing screens, flows, Figma links, images or front-end code against WCAG 2.2 level AA | A table with the problem, WCAG criterion, severity and suggested fix |
| `design-critic` | Critiquing a screen or flow with Nielsen's 10 heuristics, with a focus on complex B2B products | A list of problems with heuristic, impact and suggestion, plus the 3 improvements with the highest impact and lowest effort |
| `ux-researcher` | Planning research, writing interview guides, synthesizing interviews and analyzing quantitative data | A research plan, an interview guide, a synthesis by theme with real quotes, or a cautious reading of the numbers |

## Principles

- **No invention.** The accessibility reviewer only cites criteria that exist in WCAG 2.2. The researcher never makes up data or quotes.
- **Evidence kept apart from hypothesis.** What came from the material and what is interpretation are marked.
- **Stated limits.** Each agent says what it could not verify with the material it received.
- **Read-only reviews.** The accessibility and critique agents do not change files.

## How to install

1. Download this repository.
2. Copy the three files from the `.claude/agents/` folder to one of these places:
   - **A single project:** the `.claude/agents/` folder inside the project.
   - **All your projects:** the `.claude/agents/` folder of your user. On Windows, `C:\Users\YOUR_USER\.claude\agents\`. On Mac and Linux, `~/.claude/agents/`.
3. Close and reopen Claude Code.

## How to use

Describe the task and Claude Code picks the agent. To be sure, mention the agent by name.

**Accessibility**

```
Use the accessibility-reviewer agent to review the login screen in src/pages/Login.tsx
```

**Design critique**

```
Use the design-critic agent to critique the screen in screens/dashboard.png
```

**UX research**

```
Use the ux-researcher agent to synthesize the interviews in the research/interviews folder
```

You can also call an agent with `@`: type `@agent-` and pick the agent from the list.

To review an image, save the file in a folder and give its path.

The agents reply in the language you write in.

## Structure

```
.claude/
  agents/
    accessibility-reviewer.md
    design-critic.md
    ux-researcher.md
README.md
```

## How to adapt

Open the agent file in any text editor. The header, between the `---` lines, sets the name, when the agent is used and which tools it has. The text below it is the instructions. Change what you want and save.

File format: [Claude Code subagents documentation](https://code.claude.com/docs/en/sub-agents).
