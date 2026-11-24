# Schedule protocol

My calendar is the **single source of truth** for anything with a date. Anything *without* a date goes
on a plain-text task list. Every tool and routine I use reads and writes the calendar directly, so there is no
sync step: if it's on the calendar, everything sees it.

## Where things go

| It has... | Goes to |
|---|---|
| A date and time (film Tuesday 2pm, long ride Sat 8am) | Calendar timed event |
| A date, no time (post by Friday, pay rent the 1st) | Calendar all-day event |
| No date (someday/maybe, "look into X") | Task list, Inbox |
| A date AND a checkbox-style chore | Calendar all-day event, prefixed `[Task]` |

## Area tags (title prefix + colour)

Every event starts with a tag so the calendar can be filtered at a glance.

| Tag | Area | colorId |
|---|---|---|
| `[Content]` | Filming, editing, posting, content planning | 5 (banana) |
| `[Tri]` | Triathlon training: swim, bike, run, brick, strength, race | 10 (basil) |
| `[Task]` | General to-dos, errands, admin | 8 (graphite) |
| `[School]` | Coursework and deadlines | 9 (blueberry) |
| `[Life]` | Family, social, travel | 6 (tangerine) |

A new area gets a row here first, then it gets used.

## Event format

- **Title:** `[Tag] Short action`, for example `[Content] Film: gear review` or `[Tri] Long ride 90min Z2`.
- **Description:** details, then a footer, always:
  ```
  ---
  src: <area> · by: <tool that wrote it> · added: YYYY-MM-DD
  ```
- **Timed events** need a real duration. If none is given, pick a sensible one and say so.
- **Time zone:** leave unset so the calendar uses mine. Never pass a UTC offset.
- **Reminders:** default, unless it's a hard deadline (then add a popup one day before).

## Rules for writing

1. **Search before creating.** Look at the target day first. If a matching event exists, update it instead of adding a duplicate.
2. **Move, don't duplicate.** "Push filming to Wednesday" means updating the existing event.
3. **Check for conflicts.** Before placing a timed event, look at that day and flag overlaps instead of silently double-booking.
4. **Only touch events you own.** Events with a `src:` footer are system events. Classes, imported deadlines and invites from others are read-only.
5. **A finished task comes off the calendar.** When a `[Task]` is done, delete it. Anything else is rescheduled or asked about, never deleted unprompted.
6. **Confirm briefly after writing:** what, when, which calendar. One line.
7. **Close finished tasks in the same turn.** A `[Task]` all-day event is deleted; a task-list item is ticked and moved to "Done (recent)" with the date. Never touch classes, imported deadlines, or events without a `src:` footer.

## Completing things

- **`[Task]` all-day events:** delete when done, so the calendar to-do list only shows what's still open.
- **Task-list items:** tick `[x]` and move to "Done (recent)"; prune that section weekly.
- **Timed events:** leave them. They pass on their own and are the record of what was planned.
- **Not sure it's done?** Check the source first (a workout log, for instance) before removing it or calling it outstanding. Never assume from the clock.

## Reading ("what do I have today?")

For the day requested, pull:
- Primary calendar events
- Any imported deadline calendars
- Task-list items due that day or overdue

Present a time-ordered list, then a short "no time set" list. Call out conflicts and anything overdue. No padding.
