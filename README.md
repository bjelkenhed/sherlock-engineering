# Sherlock Engineering Plugin

A starter Claude Code plugin for engineering workflows.

## Installation

### Option 1: One-Command Installation

```bash
npx claude-plugins install @bjelkenhed/sherlock-engineering
```

### Option 2: Manual Installation

1. Add the marketplace:
```
/plugin marketplace add https://github.com/bjelkenhed/sherlock-engineering
```

2. Install the plugin:
```
/plugin install sherlock-engineering
```

## Features

### Commands

- `/sherlock-engineering:plan` - Develops a refined spec for a new feature through multiple iterations. Pass a requirements document as an argument, and the command will:
  1. Ask clarifying questions to reduce ambiguity
  2. Fetch relevant documentation using the Docs Fetcher sub-agent
  3. Create an initial spec using the Application Architect sub-agent
  4. Refine the spec through Code Reviewer feedback
  5. Iterate through three spec versions with reviews
  6. Notify you when the final spec is ready for review

- `/sherlock-engineering:ralph-loop` - Start an iterative development loop (based on [Ralph Wiggum](https://github.com/anthropics/claude-code/tree/main/plugins/ralph-wiggum)). The loop feeds the same prompt back when Claude tries to exit, allowing autonomous iteration until completion criteria are met.

  **Usage:**
  ```
  /ralph-loop "<prompt>" --max-iterations <n> --completion-promise "<text>"
  ```

  **Options:**
  - `--max-iterations <n>` - Stop after N iterations (default: unlimited)
  - `--completion-promise <text>` - Phrase that signals completion

  **Example:**
  ```
  /ralph-loop "Build a REST API for todos. Requirements: CRUD operations, input validation, tests. Output <promise>COMPLETE</promise> when done." --completion-promise "COMPLETE" --max-iterations 50
  ```

  **Best for:** Tasks with clear success criteria, TDD workflows, greenfield projects, tasks with automatic verification (tests, linters).

- `/sherlock-engineering:cancel-ralph` - Cancel the active Ralph Wiggum loop

### Agents

- `code-reviewer` - Reviews code for quality and best practices
- `docs-fetcher-summarizer` - Fetches and summarizes documentation from external sources
- `meta-agent` - Generates new Claude Code sub-agent configurations

## Project Structure

```
sherlock-engineering/
├── .claude-plugin/
│   └── marketplace.json       # Marketplace configuration
├── plugins/
│   └── sherlock-engineering/
│       ├── .claude-plugin/
│       │   └── plugin.json    # Plugin metadata
│       ├── agents/            # Agent definitions
│       ├── commands/          # Slash commands
│       └── skills/            # Reusable skills
├── CLAUDE.md                  # Claude-specific documentation
└── README.md                  # This file
```

## Creating New Components

### Adding a Command

Create a new `.md` file in `plugins/sherlock-engineering/commands/`:

```markdown
# Command Name

Description of what this command does.

## Usage

How to use the command and what it expects.

## Behavior

What the command does step by step.
```

### Adding a Skill

Create a new directory in `plugins/sherlock-engineering/skills/` with a `SKILL.md` file:

```markdown
# skill-name

Description of when this skill should be used.

## Instructions

Detailed instructions for how Claude should use this skill.
```

### Adding an Agent

Create a new `.md` file in `plugins/sherlock-engineering/agents/`:

```markdown
# Agent Name

Description of the agent's purpose and capabilities.

## Tools

What tools this agent has access to.

## Behavior

How the agent should behave.
```

## License

MIT
