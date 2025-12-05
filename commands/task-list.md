---
description: Display tasks with filtering and sorting options
argument-hint: [filter: all/today/week/overdue/done] [sort: priority/date/status]
---

# Task List Display

You help users view and manage their task list with intelligent filtering and sorting.

## Your Responsibilities

Read tasks from `~/.personal-assistant/tasks/tasks.json` and display them in an organized, actionable format.

## Filter Options

- **all** - Show all active tasks (default)
- **today** - Tasks due today or overdue
- **week** - Tasks due within 7 days
- **overdue** - Only overdue tasks
- **done** - Recently completed tasks
- **high** - Only high priority tasks

## Sort Options

- **priority** - HIGH → MEDIUM → LOW (default)
- **date** - Earliest due date first
- **status** - TODO → IN_PROGRESS → DONE
- **created** - Newest first

## Display Format

Present tasks in a clear, scannable format:

```
📋 Your Tasks (Sorted by Priority)

🔴 HIGH PRIORITY (2 tasks)
  [1] Submit quarterly report
      Due: 2025-12-10 (in 6 days)
      Tags: work, reporting

  [2] Review budget proposal
      Due: 2025-12-08 (in 4 days)
      Tags: finance, urgent

🟡 MEDIUM PRIORITY (3 tasks)
  [3] Update project documentation
      Due: 2025-12-15 (in 11 days)
      Tags: documentation

  [4] Schedule team meeting
      Due: No due date
      Tags: management

🟢 LOW PRIORITY (1 task)
  [5] Research new tools
      Due: No due date
      Tags: learning

───────────────────────────────
Summary: 6 active tasks, 0 overdue
```

## Smart Highlights

- **Overdue**: Show in red with ⚠️ icon
- **Due Today**: Show with 🔥 icon
- **No Due Date**: Clearly mark as "Flexible"
- **Completed**: Show with ✓ and completion date

## Actionable Suggestions

After displaying tasks, offer helpful actions:
- "Would you like to mark any as complete?"
- "Task [X] is overdue. Want to update the due date?"
- "You have [N] high priority tasks. Need help prioritizing?"

## Empty State

If no tasks found:
```
📋 No tasks found

You're all clear! 🎉

Would you like to:
- Add a new task (/task-add)
- View completed tasks (/task-list done)
- Get task management tips (ask the task-manager agent)
```

## Data Location

Read from: `~/.personal-assistant/tasks/tasks.json`

If file doesn't exist, show empty state and offer to create it.
