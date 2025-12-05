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

## ⚡ Quick Install (2 Commands)

Install this plugin instantly from the marketplace:

```bash
# Step 1: Add the marketplace
/plugin marketplace add houyc1217/plugins_personal_assistant

# Step 2: Install the plugin
/plugin install personal-assistant
```

That's it! 🎉 All commands and agents are now available. Try `/task-add "My first task" high` to get started.

### Verify Installation

```bash
# See all available commands
/help
```

You should see 6 new commands:
- `/task-add` - Create tasks
- `/task-list` - View tasks
- `/note-quick` - Capture notes
- `/note-search` - Search notes
- `/schedule-view` - View calendar
- `/daily-brief` - Daily briefing

And 5 specialized agents ready to help with complex workflows!

---

## 🚀 Alternative Installation Methods

### Installation on macOS

#### Method 1: Git Clone (Recommended)

1. **Open Terminal** (⌘ + Space, type "Terminal")

2. **Navigate to Claude Code plugins directory**:
   ```bash
   cd ~/.claude/plugins
   ```

   If the directory doesn't exist, create it:
   ```bash
   mkdir -p ~/.claude/plugins
   cd ~/.claude/plugins
   ```

3. **Clone the plugin repository**:
   ```bash
   git clone https://github.com/houyc1217/plugins_personal_assistant.git
   ```

4. **Verify installation**:
   ```bash
   ls -la ~/.claude/plugins/plugins_personal_assistant
   ```

   You should see:
   ```
   .claude-plugin/
   commands/
   agents/
   README.md
   ```

5. **Restart Claude Code**:
   - Quit Claude Code completely (⌘ + Q)
   - Relaunch from Applications
   - Or reload plugins if Claude Code supports hot-reload

#### Method 2: Manual Download

1. **Download the plugin**:
   - Visit: https://github.com/houyc1217/plugins_personal_assistant
   - Click "Code" → "Download ZIP"
   - Unzip the downloaded file

2. **Move to plugins directory**:
   ```bash
   # Open Finder and navigate to Downloads
   # Then in Terminal:
   mkdir -p ~/.claude/plugins
   mv ~/Downloads/plugins_personal_assistant-main ~/.claude/plugins/plugins_personal_assistant
   ```

3. **Verify and restart** (same as Method 1, steps 4-5)

### Initial Setup on macOS

After installation, set up the data directory:

```bash
# Create the personal assistant data directory
mkdir -p ~/.personal-assistant/{tasks,notes,schedule,research}

# Verify directory structure
ls -la ~/.personal-assistant
```

Expected output:
```
drwxr-xr-x  notes/
drwxr-xr-x  research/
drwxr-xr-x  schedule/
drwxr-xr-x  tasks/
```

### macOS-Specific Configuration

#### File Permissions

Ensure Claude Code has proper file system access:

1. **System Settings** → **Privacy & Security** → **Files and Folders**
2. Find "Claude Code" in the list
3. Grant access to:
   - Home folder (for `~/.personal-assistant/`)
   - Documents folder (if storing data there)

#### Finder Integration

To easily access your personal assistant data in Finder:

```bash
# Create a Finder sidebar shortcut
# Option 1: Drag ~/.personal-assistant to Finder sidebar
open ~/.personal-assistant

# Option 2: Create alias on Desktop
ln -s ~/.personal-assistant ~/Desktop/PersonalAssistant
```

#### Spotlight Integration

Make your notes searchable via Spotlight (⌘ + Space):

```bash
# Ensure notes directory is indexed
mdutil -E ~/.personal-assistant/notes
```

### Verification

Test the installation:

1. **Open Claude Code**
2. **Start a new conversation**
3. **Try a command**:
   ```
   /task-add "Test installation" high today
   ```
4. **Check data was created**:
   ```bash
   cat ~/.personal-assistant/tasks/tasks.json
   ```

If you see the JSON file with your task, installation is successful! 🎉

### Installation Troubleshooting (macOS)

**Problem**: "Command not found: /task-add"

**Solution**:
- Verify plugin is in correct directory: `ls ~/.claude/plugins/plugins_personal_assistant`
- Check plugin.json exists: `cat ~/.claude/plugins/plugins_personal_assistant/.claude-plugin/plugin.json`
- Restart Claude Code completely (⌘ + Q, then relaunch)

**Problem**: "Permission denied" when creating tasks/notes

**Solution**:
```bash
# Fix permissions
chmod -R u+rw ~/.personal-assistant
```

**Problem**: Plugin directory doesn't exist

**Solution**:
```bash
# Create it manually
mkdir -p ~/.claude/plugins
# Then follow installation steps
```

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

## 🍎 macOS Power User Tips

### Terminal Aliases for Quick Access

Add these to your `~/.zshrc` or `~/.bash_profile`:

```bash
# Quick access to personal assistant data
alias pa='cd ~/.personal-assistant'
alias pa-tasks='cat ~/.personal-assistant/tasks/tasks.json | jq .'
alias pa-notes='cd ~/.personal-assistant/notes && ls -lt | head -10'
alias pa-backup='tar -czf ~/Desktop/pa-backup-$(date +%Y%m%d).tar.gz ~/.personal-assistant'

# Open data directories in Finder
alias pa-open='open ~/.personal-assistant'
alias pa-tasks-open='open ~/.personal-assistant/tasks'
alias pa-notes-open='open ~/.personal-assistant/notes'
```

Then reload your shell:
```bash
source ~/.zshrc  # or source ~/.bash_profile
```

### Automator Quick Actions

Create macOS Quick Actions for faster workflows:

#### 1. Quick Note from Selected Text

1. Open **Automator** → Create **Quick Action**
2. Set "Workflow receives" to **text** in **any application**
3. Add **Run Shell Script** action:
   ```bash
   note_text="$1"
   timestamp=$(date +"%Y-%m-%d-%H-%M")
   filename="$HOME/.personal-assistant/notes/${timestamp}-quick-note.md"

   cat > "$filename" << EOF
   ---
   title: Quick Note
   type: PERSONAL
   created: $(date +"%Y-%m-%d %H:%M")
   tags: [quick-capture]
   ---

   $note_text
   EOF

   osascript -e 'display notification "Note saved!" with title "Personal Assistant"'
   ```
4. Save as "Capture to Personal Assistant"
5. Use: Select text anywhere, right-click → Quick Actions → Capture to Personal Assistant

#### 2. Voice Note Capture (using macOS dictation)

1. Enable **Dictation** in System Settings → Keyboard
2. Press Fn twice to start dictation in Claude Code
3. Speak your task or note
4. Use `/task-add` or `/note-quick` with dictated text

### Keyboard Shortcuts

Set up macOS keyboard shortcuts for Claude Code:

1. **System Settings** → **Keyboard** → **Keyboard Shortcuts** → **App Shortcuts**
2. Click **+** to add new shortcut
3. Choose **Claude Code** as application
4. Add shortcuts for common commands:
   - Command: `/task-add` → Shortcut: `⌘⇧T`
   - Command: `/note-quick` → Shortcut: `⌘⇧N`
   - Command: `/daily-brief` → Shortcut: `⌘⇧D`

### Spotlight Search Integration

Make your notes searchable from Spotlight:

```bash
# Add metadata to notes for better search
# This script adds Spotlight comments to your notes
for file in ~/.personal-assistant/notes/*.md; do
    title=$(grep "^title:" "$file" | cut -d':' -f2- | xargs)
    xattr -w com.apple.metadata:kMDItemFinderComment "$title" "$file"
done
```

Now search notes from Spotlight (⌘ + Space) by typing their titles!

### Calendar App Integration

Sync with macOS Calendar:

```bash
# Export schedule to ICS format (for Calendar.app)
# Add this function to ~/.zshrc
pa-export-calendar() {
    python3 << 'EOF'
import json
import os
from datetime import datetime

events_file = os.path.expanduser("~/.personal-assistant/schedule/events.json")
if os.path.exists(events_file):
    with open(events_file) as f:
        data = json.load(f)

    # Generate ICS file
    ics_content = "BEGIN:VCALENDAR\nVERSION:2.0\nPRODID:-//Personal Assistant//EN\n"

    for event in data.get("events", []):
        ics_content += f"""BEGIN:VEVENT
UID:{event['id']}@personal-assistant
DTSTART:{event['start'].replace('-','').replace(':','')}
DTEND:{event['end'].replace('-','').replace(':','')}
SUMMARY:{event['title']}
DESCRIPTION:{event.get('description', '')}
END:VEVENT
"""

    ics_content += "END:VCALENDAR"

    output_file = os.path.expanduser("~/Desktop/personal-assistant.ics")
    with open(output_file, 'w') as f:
        f.write(ics_content)

    print(f"Calendar exported to {output_file}")
    print("Double-click to import to Calendar.app")
EOF
}
```

### Notification Center Integration

Get reminders via macOS notifications:

```bash
# Add to crontab for daily briefing reminder
# Run: crontab -e
# Add this line for 9am daily reminder:
0 9 * * * osascript -e 'display notification "Time for your daily brief!" with title "Personal Assistant" sound name "Glass"'

# For task deadline reminders, create a script:
#!/bin/bash
# Save as ~/bin/pa-check-deadlines.sh
tasks=$(cat ~/.personal-assistant/tasks/tasks.json)
today=$(date +%Y-%m-%d)

# Check for tasks due today (requires jq)
due_today=$(echo "$tasks" | jq -r ".tasks[] | select(.due_date == \"$today\") | .title")

if [ ! -z "$due_today" ]; then
    osascript -e "display notification \"$due_today\" with title \"Tasks Due Today\" sound name \"Basso\""
fi
```

### Backup Automation with Time Machine

Ensure your personal assistant data is backed up:

```bash
# Verify Time Machine includes personal assistant data
tmutil isexcluded ~/.personal-assistant

# If excluded, include it:
tmutil removeexclusion ~/.personal-assistant

# Create additional backup script
cat > ~/Library/LaunchAgents/com.user.pa-backup.plist << 'EOF'
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>Label</key>
    <string>com.user.pa-backup</string>
    <key>ProgramArguments</key>
    <array>
        <string>/bin/sh</string>
        <string>-c</string>
        <string>tar -czf ~/Documents/Backups/pa-backup-$(date +\%Y\%m\%d).tar.gz ~/.personal-assistant</string>
    </array>
    <key>StartCalendarInterval</key>
    <dict>
        <key>Hour</key>
        <integer>20</integer>
        <key>Minute</key>
        <integer>0</integer>
    </dict>
</dict>
</plist>
EOF

# Create backup directory
mkdir -p ~/Documents/Backups

# Load the backup job (runs daily at 8pm)
launchctl load ~/Library/LaunchAgents/com.user.pa-backup.plist
```

### Alfred Integration (if installed)

Create Alfred workflows for ultra-fast access:

1. **Open Alfred Preferences** → **Workflows** → **+** → **Blank Workflow**
2. Add **Keyword** input: `task`
3. Connect to **Run Script** (bash):
   ```bash
   query="{query}"
   /usr/bin/open "claude://command/task-add?text=$query"
   ```
4. Repeat for other commands (`note`, `brief`, etc.)

Now use: `⌥Space` → type `task Submit report` → instantly creates task!

### VS Code Integration

If you use VS Code alongside Claude Code:

1. Install **Markdown All in One** extension
2. Open `~/.personal-assistant/notes` as workspace
3. Use VS Code's search for powerful note searching
4. Create tasks.json workspace file:
   ```json
   {
     "version": "2.0.0",
     "tasks": [
       {
         "label": "Open in Claude Code",
         "type": "shell",
         "command": "open -a 'Claude Code' ${file}"
       }
     ]
   }
   ```

### Menu Bar Integration

Show task count in menu bar using **BitBar** or **SwiftBar**:

```bash
# Install SwiftBar: brew install swiftbar
# Create plugin: ~/.config/swiftbar/pa-tasks.5m.sh

#!/bin/bash
# <bitbar.title>Personal Assistant Tasks</bitbar.title>
# <bitbar.version>v1.0</bitbar.version>
# <bitbar.author>You</bitbar.author>
# <bitbar.desc>Shows pending tasks count</bitbar.desc>

if [ -f ~/.personal-assistant/tasks/tasks.json ]; then
    count=$(cat ~/.personal-assistant/tasks/tasks.json | jq '[.tasks[] | select(.status != "COMPLETED")] | length')
    echo "📋 $count"
    echo "---"
    echo "Open Personal Assistant | bash=open -a 'Claude Code'"
else
    echo "📋 ?"
fi

chmod +x ~/.config/swiftbar/pa-tasks.5m.sh
```

### iCloud Sync (Optional)

Sync data across multiple Macs:

```bash
# Move data to iCloud Drive
mkdir -p ~/Library/Mobile\ Documents/com~apple~CloudDocs/PersonalAssistant
mv ~/.personal-assistant/* ~/Library/Mobile\ Documents/com~apple~CloudDocs/PersonalAssistant/

# Create symlink
rm -rf ~/.personal-assistant
ln -s ~/Library/Mobile\ Documents/com~apple~CloudDocs/PersonalAssistant ~/.personal-assistant

# Verify
ls -la ~/.personal-assistant
```

⚠️ **Note**: Be cautious with iCloud sync for frequently-updated files. Consider syncing only notes and research, not tasks/schedule.

### Daily Routine with macOS Shortcuts

Create a Shortcuts.app automation:

1. Open **Shortcuts** app
2. Create new shortcut: "Morning Routine"
3. Add actions:
   - Show notification "Good morning! Starting your daily brief..."
   - Open URL: `claude://command/daily-brief`
   - Wait 2 seconds
   - Open URL: `claude://command/task-list?filter=today`
4. Add automation trigger: Daily at 9:00 AM

### Performance Optimization

For faster plugin loading:

```bash
# Ensure plugins directory isn't in Time Machine's frequent backup
tmutil addexclusion ~/.claude/plugins

# Use SSD for data storage (verify):
diskutil info / | grep "Solid State"

# If using HDD, consider moving to SSD:
# (Only if you have a separate SSD)
mkdir -p /Volumes/SSD/personal-assistant
ln -s /Volumes/SSD/personal-assistant ~/.personal-assistant
```

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

### How to Contribute

1. **Report Issues**: [GitHub Issues](https://github.com/houyc1217/plugins_personal_assistant/issues)
2. **Submit PRs**: Fork, modify, and submit pull requests
3. **Share Ideas**: Suggest new features or improvements
4. **Star the Repo**: If you find it useful! ⭐

## 🌐 Community & Distribution

### Install from Marketplace

**Recommended**: Use the 2-command install (see top of README)

```bash
/plugin marketplace add houyc1217/plugins_personal_assistant
/plugin install personal-assistant
```

### Also Available On

- **Community Marketplaces**: Submit requests to include in curated marketplaces
- **Claude Code Commands Directory**: [claudecodecommands.directory](https://claudecodecommands.directory/)

### Share with Others

Recommend this plugin to colleagues:
```bash
# Just share these 2 lines!
/plugin marketplace add houyc1217/plugins_personal_assistant
/plugin install personal-assistant
```

---

## 📄 Plugin Information

**Name**: personal-assistant
**Version**: 1.0.0
**Last Updated**: 2025-12-05
**License**: MIT
**Compatibility**: Claude Code (all versions)
**Category**: Productivity

**Repository**: https://github.com/houyc1217/plugins_personal_assistant
**Marketplace**: `houyc1217/plugins_personal_assistant`

### Plugin Stats

- **6 Commands** - Quick-action slash commands
- **5 Agents** - Specialized AI assistants
- **5 Core Modules** - Task, Note, Schedule, Research, Daily Planning
- **13+ macOS Integrations** - Native productivity features

---

Happy productivity! 🚀

Built with ❤️ following [Claude Code best practices](https://www.anthropic.com/engineering/claude-code-best-practices) and [AI assistant research](https://www.researchgate.net/publication/388449530_A_Modular_Framework_for_AI_Personal_Assistants_Design_Implementation_and_Scalability).
