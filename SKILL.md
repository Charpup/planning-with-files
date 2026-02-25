---
name: planning-with-files
description: File-based planning and progress tracking for complex tasks. Use when starting multi-step projects, needing persistent task tracking across sessions, managing research findings, or preventing context loss. Creates task_plan.md, findings.md, and progress.md for filesystem-as-memory workflow.
metadata:
  openclaw:
    emoji: "📋"
    requires:
      bins: []
      env: []
    os: ["linux", "macos", "windows"]
    install: []
---

# Planning with Files

Work like Manus — use persistent markdown files for planning, progress tracking, and knowledge storage.

## Quick Start

```bash
# Start planning session
/planning-with-files:plan
# or type /plan for autocomplete
```

The skill automatically creates three files:

| File | Purpose | Content |
|------|---------|---------|
| **task_plan.md** | Track phases and progress | Tasks, checkboxes, status |
| **findings.md** | Store research and findings | Research, discoveries, decisions |
| **progress.md** | Session log and test results | Daily logs, test results |

## When to Use

**Use this skill when:**
- Starting a complex multi-step project
- Need persistent task tracking across sessions
- Managing research that spans multiple conversations
- Want to prevent context loss on `/clear`
- Working on tasks with 10+ steps

**Skip when:**
- Simple one-off tasks (< 5 steps)
- Quick fixes or documentation-only changes
- Tasks completable in single session

## The Core Principle

```
Context Window = RAM (volatile, limited)
Filesystem = Disk (persistent, unlimited)

→ Anything important gets written to disk.
```

## Usage Flow

1. **Invoke** — Type `/plan` or `/planning`
2. **Describe task** — Explain what you want to accomplish
3. **Review plan** — Skill creates task_plan.md with phases
4. **Execute** — Work through tasks, findings stored in findings.md
5. **Track progress** — Checkboxes updated in real-time
6. **Log session** — Progress captured in progress.md

## Commands

| Command | Description |
|---------|-------------|
| `/planning-with-files:plan` | Start new planning session |
| `/planning-with-files:status` | Show current progress |
| `/planning-with-files:start` | Original start command |

## File Structure

```
project/
├── task_plan.md      # Master task list with phases
├── findings.md       # Research and discoveries
└── progress.md       # Session logs and results
```

### task_plan.md Format

```markdown
# Task Plan: [Project Name]

## Phase 1: Research
- [x] Initial investigation
- [ ] Deep dive into X
- [ ] Document findings

## Phase 2: Implementation
- [ ] Setup environment
- [ ] Core functionality
- [ ] Testing
```

### findings.md Format

```markdown
# Findings: [Project Name]

## [2026-02-19] Discovery X
Key findings about X...

## [2026-02-19] Decision Y
We decided to use Y because...
```

### progress.md Format

```markdown
# Progress: [Project Name]

## Session 2026-02-19
**Started:** 09:00  
**Completed:** Phase 1 research  
**Next:** Implementation
```

## How It Works

### Automatic Hooks

The skill uses PreToolUse, PostToolUse, and Stop hooks to:

1. **Re-read plan** before major decisions
2. **Remind to update status** after file writes
3. **Verify completion** before stopping

### Session Recovery

If context is cleared with `/clear`:
1. Skill detects previous session data
2. Shows catchup report of lost context
3. Restores planning state

## Best Practices

- **Update checkboxes** as tasks complete
- **Write findings immediately** — don't wait
- **Review plan** before major decisions
- **Log errors** for future reference
- **Keep files in git** for history

## References

- **Full Guide:** See README.md in skill directory
- **Quickstart:** docs/quickstart.md
- **Installation:** docs/installation.md

---

*Based on Manus's context engineering approach — filesystem as working memory.*
