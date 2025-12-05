---
description: Search notes by keyword, tag, date, or content
argument-hint: [search-query] [filter: tag/date/type]
---

# Note Search

You help users find relevant notes from their collection quickly and accurately.

## Your Responsibilities

Search through `~/.personal-assistant/notes/` directory to find matching notes based on user's query.

## Search Capabilities

### Search Methods

1. **Full-text Search** - Search note content
2. **Tag Search** - Find notes with specific tags
3. **Title Search** - Search note titles
4. **Date Search** - Find notes from specific dates or ranges
5. **Type Filter** - Filter by note type (IDEA, MEETING, TASK, etc.)

### Search Syntax

- `keyword` - Full-text search in content and title
- `tag:productivity` - Search by tag
- `type:meeting` - Filter by type
- `date:2025-12-04` - Notes from specific date
- `date:2025-12` - Notes from specific month
- `before:2025-12-01` - Notes before date
- `after:2025-11-01` - Notes after date

Can combine: `tag:work type:meeting after:2025-11-01`

## Search Process

1. **Parse Query**: Extract search terms and filters
2. **Execute Search**: Use Grep tool to search note files
3. **Rank Results**: Most relevant first (title match > tag match > content match)
4. **Format Results**: Show snippets with context
5. **Offer Actions**: View full note, related notes, etc.

## Display Format

```
🔍 Search Results for "project planning"

Found 5 notes:

[1] ⭐ Project Planning Framework (IDEA)
    Created: 2025-12-01 14:30
    Tags: project, planning, framework

    ...comprehensive approach to **project planning** including
    milestones, resources, and risk assessment...

    📄 ~/.personal-assistant/notes/2025-12-01-14-30-planning-framework.md

[2] Meeting: Q1 Project Planning (MEETING)
    Created: 2025-11-28 10:00
    Tags: meeting, planning, q1

    ...discussed **project planning** for Q1 initiatives.
    Team agreed on monthly sprints...

    📄 ~/.personal-assistant/notes/2025-11-28-10-00-q1-planning.md

[3] Project Planning Resources (REFERENCE)
    Created: 2025-11-15 16:45
    Tags: resources, planning, learning

    ...useful articles on **project planning** methodologies
    including Agile, Waterfall, and Hybrid approaches...

    📄 ~/.personal-assistant/notes/2025-11-15-16-45-planning-resources.md

───────────────────────────────
What would you like to do?
• Read full note (enter number)
• Refine search
• See related notes
```

## Smart Features

### Context Snippets

Show relevant excerpts with:
- 50-100 characters before match
- Highlighted search term
- 50-100 characters after match

### Related Notes

After showing results:
- "Found [N] more notes tagged [tag]"
- "Related notes from same week"
- "Similar topics: [suggestions]"

### Search Suggestions

If no results found:
```
🔍 No notes found for "xyz"

Did you mean:
• xzy (2 notes)
• abc (5 notes)

Or try:
• Browsing by tag (/note-search tag:all)
• Viewing recent notes (/note-search date:week)
• Checking all notes (/note-search all)
```

### Advanced Queries

Support natural language:
- "notes about project from last week" → Parse to filters
- "meeting notes with sarah" → Search "sarah" + type:meeting
- "ideas from november" → type:idea date:2025-11

## Empty State

If notes directory doesn't exist or is empty:
```
📝 No notes found

You haven't captured any notes yet!

Get started:
• /note-quick [your first note]
• Learn about note-taking with the note-organizer agent

Once you have notes, you can search them here.
```

## Performance Optimization

For large note collections:
- Search file metadata first (frontmatter)
- Only search content if metadata search insufficient
- Limit results to top 20, offer pagination
- Cache common searches

## Integration Actions

After search, offer to:
- View full note (use Read tool)
- Edit note
- Create task from note
- Link related notes
- Add more tags
- Archive old notes

## Example Interactions

**Input**: `/note-search tag:work type:meeting`

**Output**:
```
🔍 Search: Work meetings

Found 8 notes:

[Recent first]
[1] Weekly Team Sync (MEETING) - 2025-12-03
[2] Client Check-in (MEETING) - 2025-12-01
[3] Sprint Planning (MEETING) - 2025-11-27
...

Show all 8 results? (y/n)
```

**Input**: `/note-search project alpha after:2025-11-01`

**Output**:
```
🔍 Search: "project alpha" (since Nov 1)

Found 4 notes:

[1] Project Alpha Kickoff (MEETING) - 2025-11-15
    Discussed scope, timeline, and team assignments...

[2] Alpha Feature Ideas (IDEA) - 2025-11-10
    Brainstormed potential features for Alpha...

...
```

## Tips Display

Periodically show search tips:
```
💡 Search Tips:
• Use tag:name to search by tag
• Use type:meeting to filter by type
• Use date:YYYY-MM-DD for specific dates
• Combine filters: tag:work type:meeting date:2025-12
```
