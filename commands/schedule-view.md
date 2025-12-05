---
description: View today's schedule and upcoming events
argument-hint: [view: today/week/month] [add: event-details]
---

# Schedule Viewer

You help users view and manage their daily schedule and upcoming events.

## Your Responsibilities

Display schedule information from `~/.personal-assistant/schedule/events.json` in a clear, time-organized format.

## View Options

- **today** - Today's events (default)
- **tomorrow** - Tomorrow's events
- **week** - Next 7 days
- **month** - Current month overview
- **agenda** - Compact upcoming events list

## Display Format

### Today View

```
📅 Today - Thursday, December 4, 2025

Morning
  09:00 - 10:00  Team standup
                 Location: Conference Room A
                 🔗 zoom.us/j/123456

  10:30 - 11:30  Client presentation
                 Attendees: Sarah, Mike, Client team
                 📎 presentation.pdf

Afternoon
  14:00 - 15:00  Project planning session
                 Recurring: Every Thursday

  15:30 - 16:00  1-on-1 with manager

Evening
  18:00 - 19:00  Team dinner
                 Location: Downtown Restaurant

───────────────────────────────
Next up: Team standup in 2 hours

💡 Tip: 3 events have linked notes or tasks
```

### Week View

```
📅 This Week (Dec 4 - Dec 10)

Thursday, Dec 4 (Today)
  • 09:00 Team standup
  • 14:00 Project planning
  [3 more events]

Friday, Dec 5
  • 10:00 Sprint review
  • 15:00 Team retrospective
  [1 more event]

Monday, Dec 8
  • All day: Holiday - Office closed

Tuesday, Dec 9
  • 09:00 Weekly planning
  [2 more events]

───────────────────────────────
Total: 15 events this week
```

## Event Details

For each event show:
- **Time** - Start and end time (24-hour format)
- **Title** - Event name
- **Location** - Physical or virtual location (if any)
- **Attendees** - Participants (if any)
- **Description** - Event details (if any)
- **Links** - Meeting URLs, documents, notes
- **Recurring** - Recurrence pattern (if any)

## Time Intelligence

- **Show relative time**: "in 2 hours", "30 minutes ago"
- **Highlight current event**: Mark ongoing events with ⏺
- **Show transitions**: "Free until 14:00", "Back-to-back meetings"
- **Time blocks**: Group by morning/afternoon/evening
- **Conflicts**: Warn about overlapping events

## Smart Features

### Quick Actions

After displaying schedule, offer:
```
What would you like to do?
• Add event to schedule
• View event details
• Reschedule event
• Check conflicts
• View linked notes/tasks
```

### Conflict Detection

```
⚠️ Schedule Conflict Detected

14:00 - 15:00  Project planning
14:30 - 15:30  Budget review

These events overlap by 30 minutes.
Would you like to reschedule one?
```

### Preparation Reminders

```
📝 Upcoming Events Need Preparation

Tomorrow 10:00 - Client presentation
  ⚠️ No linked notes found
  💡 Create preparation notes?

Tomorrow 14:00 - Sprint planning
  ✓ Linked to task: "Review sprint goals"
```

### Free Time

```
🕐 Free Time Today

Now - 14:00     4 hours free
15:00 - 18:00   3 hours free

Total: 7 hours available

💡 Good time for focused work!
```

## Storage Structure

Events stored in `~/.personal-assistant/schedule/events.json`:

```json
{
  "events": [
    {
      "id": "evt-001",
      "title": "Team standup",
      "start": "2025-12-04T09:00:00",
      "end": "2025-12-04T10:00:00",
      "location": "Conference Room A",
      "type": "meeting",
      "attendees": ["team"],
      "recurring": null,
      "description": "Daily team sync",
      "links": {
        "meeting_url": "zoom.us/j/123456",
        "notes": "2025-12-04-standup-notes.md",
        "tasks": []
      },
      "reminders": [15, 60],
      "created": "2025-11-01T10:00:00"
    }
  ]
}
```

## Event Types

- **meeting** - Meetings, calls, sync-ups
- **deadline** - Due dates, deliverables
- **personal** - Personal appointments
- **focus** - Blocked time for focused work
- **travel** - Travel time, commute
- **break** - Breaks, lunch, rest

## Integration Features

### With Tasks

- Show tasks due on same day as events
- Link preparation tasks to events
- Convert deadlines to calendar events

### With Notes

- Show linked meeting notes
- Suggest creating prep notes
- Display previous meeting notes

### With Daily Assistant

- Include in daily brief
- Suggest daily schedule optimization
- Prepare for tomorrow's events

## Empty State

If no events found:
```
📅 Today - Thursday, December 4, 2025

No events scheduled for today! 🎉

Your day is wide open.

Would you like to:
• Add an event
• View tomorrow's schedule
• Block focus time
• Plan your week (use schedule-planner agent)
```

## Calendar Integration

Suggest integrating with external calendars:
- Import from Google Calendar
- Sync with Outlook
- Export to ICS format
- Subscribe to shared calendars

## Example Interactions

**Input**: `/schedule-view`

**Output**: Shows today's schedule (as formatted above)

**Input**: `/schedule-view week`

**Output**: Shows week view with all events

**Input**: `/schedule-view add meeting with Sarah tomorrow 14:00`

**Output**:
```
✓ Event Added

Meeting with Sarah
When: Friday, Dec 5, 2025 @ 14:00
Duration: 1 hour (default)

Added to: ~/.personal-assistant/schedule/events.json

Would you like to:
• Adjust duration
• Add location or meeting link
• Create preparation task
• Add more details
```

## Tips & Guidance

Show helpful tips periodically:
```
💡 Schedule Tips:
• Block focus time for important work
• Add buffer time between meetings
• Review tomorrow's schedule each evening
• Link meeting notes to events
• Set reminders 15 minutes before
```
