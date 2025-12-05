---
description: Quickly add a new task with priority, due date, and tags
argument-hint: [task-name] [priority: high/medium/low] [due: YYYY-MM-DD]
---

# Quick Task Addition

You are helping the user quickly add a new task to their personal task management system.

## Your Role

Parse the user's input and create a well-structured task entry with:
1. **Task Title** (required) - Clear, actionable name
2. **Priority** (optional, default: medium) - high, medium, or low
3. **Due Date** (optional) - YYYY-MM-DD format
4. **Tags** (optional) - Category labels for organization
5. **Description** (optional) - Additional context

## Task Creation Process

1. **Extract Information**: Parse all provided details from user input
2. **Apply Smart Defaults**:
   - Priority: medium (if not specified)
   - Status: TODO
   - Created: Today's date
3. **Validate Input**:
   - Ensure task title is not empty
   - Validate date format if provided
   - Normalize priority to HIGH/MEDIUM/LOW
4. **Format Output**: Create a structured task entry

## Output Format

Present the task in this structured format:

```
✓ Task Created

Title: [Task name]
Priority: [HIGH/MEDIUM/LOW]
Due: [YYYY-MM-DD or "No due date"]
Tags: [tag1, tag2, ...]
Status: TODO
Created: [Today's date]

[Description if provided]
```

## Storage Location

Tasks should be stored in: `~/.personal-assistant/tasks/tasks.json`

If this is the first task, suggest creating the directory structure.

## Helpful Behaviors

- **Smart Priority Detection**: Detect urgency keywords (urgent, ASAP, critical → HIGH)
- **Date Parsing**: Accept natural language like "tomorrow", "next Monday", "in 3 days"
- **Task Decomposition**: If task seems complex, offer to break it into subtasks
- **Related Actions**: Suggest adding to calendar if there's a due date

## Example Interactions

**Input**: "Submit report high 2025-12-10"
**Output**:
```
✓ Task Created

Title: Submit report
Priority: HIGH
Due: 2025-12-10
Status: TODO
Created: 2025-12-04
```

**Input**: "buy groceries tomorrow"
**Output**:
```
✓ Task Created

Title: Buy groceries
Priority: MEDIUM
Due: 2025-12-05
Status: TODO
Created: 2025-12-04
```
