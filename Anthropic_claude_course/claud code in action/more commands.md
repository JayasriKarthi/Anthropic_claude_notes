## Interrupting Claude with `Escape`

### Purpose

Stop Claude while it is generating a response.

### When to Use

- Claude is going in the wrong direction
- Response is becoming too broad
- You want Claude to focus on one small task at a time
- Claude is over-planning instead of executing

### Example

Instead of:

> “Write tests for all functions”

Interrupt and redirect:

> “Focus only on the login validation function first.”

### Benefit

- Keeps responses targeted
- Prevents unnecessary context buildup
- Improves accuracy and control

---

# 2. Combining `Escape` with Memories

### Purpose

Fix recurring mistakes permanently.

### Steps

1. Press `Escape`
2. Run `/memory` or edit `CLAUDE.md`
3. Add the correct instruction or rule
4. Continue conversation

### Example

If Claude repeatedly:

- uses wrong coding style
- ignores project conventions
- formats output incorrectly

Add a memory like:

> “Always use async/await instead of promises in this project.”

### Benefit

- Prevents repeated errors
- Improves future conversations
- Creates project-specific behavior

---

# 3. Rewinding Conversations

### Commands

- Double press `Escape`
- or use `/rewind`

### Purpose

Go back to an earlier point in the conversation.

### Useful When

- Conversation became messy
- Too much debugging context accumulated
- Irrelevant discussion is distracting Claude
- You want to retry from a cleaner state

### Benefit

- Removes distracting context
- Keeps useful project understanding
- Helps Claude stay focused

---

# 4. `/compact`

### Purpose

Summarizes conversation while preserving important knowledge.

### Best Used When

- Conversation is long
- Claude learned important project details
- You want to continue related work
- Context window is becoming large

### What It Does

- Compresses conversation history
- Retains key learnings
- Removes unnecessary verbosity

### Benefit

- Saves context space
- Maintains continuity
- Improves performance in long sessions

---

# 5. `/clear`

### Purpose

Start a completely fresh conversation.

### Best Used When

- Switching to a different project/task
- Old context may confuse Claude
- You want a clean start

### Important

- Previous conversation is NOT deleted
- Can return later using `/resume`

### Benefit

- Eliminates unrelated context
- Improves clarity for new tasks

---

# 6. `/resume`

### Purpose

Return to a previous conversation after using `/clear`.

### Benefit

- Allows task switching without losing history

---

# When These Techniques Are Most Useful

## Long Development Sessions

- Prevent context clutter
- Maintain focus

## Complex Projects

- Keep Claude aligned with architecture and conventions

## Debugging

- Remove irrelevant failed attempts
- Retry cleanly

## Task Switching

- Separate unrelated workflows cleanly

## Repeated Errors

- Use memories to permanently correct behavior

---

# Quick Summary Table

|Technique|Purpose|Best Use Case|
|---|---|---|
|`Escape`|Stop current response|Redirect Claude|
|`Escape + Memory`|Fix recurring mistakes|Project conventions|
|`/rewind`|Return to earlier state|Remove messy context|
|`/compact`|Compress conversation|Long related sessions|
|`/clear`|Start fresh|New unrelated task|
|`/resume`|Return to old chat|Continue previous work|

---

# Key Idea

These tools help with:

- Context management
- Better focus
- Cleaner conversations
- Faster iteration
- More reliable AI-assisted development

They are essential for managing long or complex coding workflows effectively.