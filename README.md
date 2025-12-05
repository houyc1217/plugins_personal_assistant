# Personal Assistant Plugin for Claude Code

A comprehensive, modular personal assistant plugin that helps you manage tasks, capture notes, organize your schedule, conduct research, and maintain productive daily routines—all within Claude Code.

## 🎯 Overview

This plugin implements industry best practices for AI personal assistants with a modular, loosely-coupled architecture. Each module (tasks, notes, schedule, research, daily planning) operates independently while integrating seamlessly to create a powerful productivity system.

## ✨ Features

### 📋 Task Management
- **Quick Task Creation** (`/task-add`) - Capture tasks with priority, due dates, and tags
- **Smart Task Listing** (`/task-list`) - View and filter tasks by priority, date, or status
- **Task Manager Agent** - Intelligent task planning, prioritization, and productivity coaching

### 📝 Note Taking
- **Rapid Note Capture** (`/note-quick`) - Save ideas instantly with automatic organization
- **Powerful Note Search** (`/note-search`) - Find notes by content, tags, dates, or type
- **Note Organizer Agent** - Structure notes, build knowledge graphs, and synthesize information

### 📅 Schedule Management
- **Schedule Viewer** (`/schedule-view`) - Display daily, weekly, or monthly schedules
- **Schedule Planner Agent** - Optimize calendar, manage time blocks, resolve conflicts

### 🔍 Research Assistant
- **Research Agent** - Comprehensive web research, source evaluation, fact-checking, and knowledge synthesis

### 🌅 Daily Planning
- **Daily Brief** (`/daily-brief`) - Comprehensive morning briefing with tasks, schedule, and priorities
- **Daily Assistant Agent** - Morning planning, daily reviews, routine building, and productivity coaching

## 🚀 Quick Start

### Installation

1. Clone or download this plugin to your Claude Code plugins directory
2. Restart Claude Code or reload plugins
3. Start using commands and agents!

### First Steps

```bash
# Create your first task
/task-add "Set up personal assistant system" high today

# Capture a quick note
/note-quick "Personal assistant plugin ideas: integrate with calendar apps, add voice notes"

# View today's schedule
/schedule-view

# Get your daily briefing
/daily-brief

# View your tasks
/task-list
```

## 📖 Usage Guide

### Commands Reference

| Command | Description | Example |
|---------|-------------|---------|
| `/task-add` | Create a new task | `/task-add "Submit report" high 2025-12-10` |
| `/task-list` | View tasks with filters | `/task-list today` or `/task-list high` |
| `/note-quick` | Capture a note | `/note-quick "Meeting idea: weekly sync on Mondays"` |
| `/note-search` | Search notes | `/note-search tag:work type:meeting` |
| `/schedule-view` | View calendar | `/schedule-view week` |
| `/daily-brief` | Get daily briefing | `/daily-brief` or `/daily-brief tomorrow` |

### Agents Reference

Invoke agents by asking Claude to help with their specialty areas:

| Agent | Specialty | When to Use |
|-------|-----------|-------------|
| **task-manager** | Task planning & prioritization | "Help me organize my tasks" |
| **note-organizer** | Note structure & knowledge management | "Help me find and organize my notes on project X" |
| **schedule-planner** | Calendar optimization & time management | "Help me optimize my weekly schedule" |
| **research-assistant** | Information gathering & synthesis | "Research AI productivity tools and summarize findings" |
| **daily-assistant** | Daily planning & routines | "Help me plan my day" or "Let's do my evening review" |

## 🏗️ Architecture

### Modular Design

The plugin follows a modular architecture with clear separation of concerns:

```
personal-assistant/
├── commands/           # Quick-action slash commands
│   ├── task-add.md
│   ├── task-list.md
│   ├── note-quick.md
│   ├── note-search.md
│   ├── schedule-view.md
│   └── daily-brief.md
│
├── agents/            # Specialized AI agents
│   ├── task-manager.md
│   ├── note-organizer.md
│   ├── schedule-planner.md
│   ├── research-assistant.md
│   └── daily-assistant.md
│
└── .claude-plugin/
    └── plugin.json    # Plugin manifest
```

### Data Storage

The plugin stores data in `~/.personal-assistant/`:

```
~/.personal-assistant/
├── tasks/
│   └── tasks.json           # Task database
├── notes/
│   └── YYYY-MM-DD-*.md      # Individual note files
├── schedule/
│   └── events.json          # Calendar events
└── research/
    └── [topic]/             # Research by topic
```

## 💡 Best Practices

### Task Management
- Use **HIGH** priority for urgent/important tasks (Eisenhower Matrix)
- Set realistic due dates with buffer time
- Break complex tasks into subtasks
- Review and update tasks daily

### Note Taking
- Capture ideas immediately (organize later)
- Use consistent tagging (2-5 tags per note)
- Link related notes together
- Weekly review to organize and connect notes

### Schedule Management
- Block 90-120 minute focus time daily
- Add 5-minute buffers between meetings
- Batch similar activities
- Protect deep work time during peak energy hours

### Daily Planning
- Start each day with `/daily-brief`
- Set 1-3 top priorities (not more!)
- Do evening review to plan tomorrow
- Track what works and adjust routines

## 🔧 Configuration

### Customizing Storage Location

Edit the storage paths in command and agent files to change where data is stored. Look for references to `~/.personal-assistant/` and update as needed.

### Adjusting Command Behavior

Each command file (in `commands/`) can be edited to customize:
- Output formatting
- Default behaviors
- Argument parsing
- Smart features

### Tuning Agent Personalities

Each agent file (in `agents/`) can be customized:
- Communication style
- Expertise focus areas
- Templates and workflows
- Integration behaviors

## 🤝 Integration

### With External Tools

The plugin can integrate with:
- Calendar apps (import/export ICS)
- Task managers (export/import JSON)
- Note apps (markdown compatibility)
- Research tools (web search, fetch)

### With Other Claude Code Plugins

Works well alongside:
- Project management plugins
- Development workflow plugins
- Communication plugins
- Documentation plugins

## 📊 Productivity Methodologies

This plugin implements concepts from:
- **GTD (Getting Things Done)** - Capture, organize, review workflow
- **Eisenhower Matrix** - Priority-based task management
- **Time Blocking** - Calendar-based productivity
- **Zettelkasten** - Note linking and knowledge graphs
- **Pomodoro Technique** - Time management and focus

## 🎓 Learning Resources

### Productivity Frameworks
- [A Modular Framework for AI Personal Assistants](https://www.researchgate.net/publication/388449530_A_Modular_Framework_for_AI_Personal_Assistants_Design_Implementation_and_Scalability)
- [Agentic AI Architectures: Modular Design Patterns](https://digitalthoughtdisruption.com/2025/07/31/agentic-ai-architecture-modular-design-patterns/)
- [How to Build Your Own AI Assistant](https://shadhinlab.com/how-to-make-your-own-ai-assistant/)

### Claude Code Documentation
- [Claude Code Best Practices for Agentic Coding](https://www.anthropic.com/engineering/claude-code-best-practices)
- [Plugins Reference](https://code.claude.com/docs/en/plugins-reference)
- [Building Agents with Claude Agent SDK](https://www.anthropic.com/engineering/building-agents-with-the-claude-agent-sdk)

## 🐛 Troubleshooting

### Data Not Persisting
- Check that `~/.personal-assistant/` directory exists
- Verify write permissions on the directory
- Review error messages in Claude Code console

### Commands Not Showing
- Ensure `plugin.json` paths are correct
- Restart Claude Code to reload plugin
- Check command file frontmatter format

### Agents Not Activating
- Agents activate based on conversation context
- Try explicitly mentioning the agent name
- Check that agent descriptions match use case

## 📝 License

MIT License - feel free to use, modify, and distribute.

## 🙏 Acknowledgments

Built following best practices from:
- Anthropic's Claude Code documentation and examples
- AI personal assistant research community
- Productivity methodology experts
- Claude Code plugin developers community

## 📮 Feedback & Contributions

Issues, suggestions, and contributions are welcome! This plugin is designed to be modular and extensible—feel free to add new modules or customize existing ones for your workflow.

---

**Version**: 1.0.0
**Last Updated**: 2025-12-04
**Compatibility**: Claude Code (all versions)

Happy productivity! 🚀
