
## Context Management

- Claude works better with **relevant context only**
- Too many unnecessary files reduce performance
- Guide Claude toward important files and documentation

---

# `/init` Command

When starting Claude in a new project, run:

```
/init
```

### What `/init` does

Claude analyzes the codebase and understands:

- Project purpose
- Architecture
- Important commands
- Critical files
- Coding patterns
- Folder structure

### After analysis

Claude creates a:

```
CLAUDE.md
```

file containing project guidance.

### Permission Options

- **Enter** → approve each file write
- **Shift + Tab** → allow Claude to write files freely during the session

---

# `CLAUDE.md` File

## Purpose

Acts like a **persistent system prompt** for your project.

### Main Uses

1. Guides Claude through:
    - Architecture
    - Commands
    - Coding style
    - Important files
2. Allows custom instructions for Claude

### Important

- Included in **every request**
- Claude reads it automatically at the start of each session

---

# Types of `CLAUDE.md` Files

## 1. Project Shared File

```
CLAUDE.md
```

- Created using `/init`
- Shared with team
- Added to source control

---

## 2. Personal File

```
CLAUDE.local.md
```

- Personal instructions
- Not shared with team

---

## 3. Global File

```
~/.claude/CLAUDE.md
```

- Applies to all projects
- Machine-wide instructions

---

# Adding Custom Instructions

You can customize Claude behavior.

Example:

```
Use comments sparingly. Only comment complex code.
```

### Ways to edit

- Directly edit `CLAUDE.md`
- Run:

```
/memory
```

### Note

Changes apply from the **next message onward**.

---

# File Mentions with `@`

Use:

```
@filepath
```

to include file contents automatically.

Example:

```
How does the auth system work? @auth
```

Claude suggests related files and includes them in context.

---

# Referencing Files Inside `CLAUDE.md`

You can permanently reference important files.

Example:

```
The database schema is defined in the @prisma/schema.prisma file.Reference it anytime you need to understand the database structure.
```

### Benefit

Claude automatically loads the file contents in every request.

Useful for:

- Schema files
- Config files
- Architecture docs
- API references

---

# Using Existing `AGENTS.md`

If your repo already has:

```
AGENTS.md
```

Add this to the first line of `CLAUDE.md`:

```
@AGENTS.md
```

Then add Claude-specific instructions below it.

This avoids duplicating instructions.

---

# Quick Summary

|Feature|Purpose|
|---|---|
|`/init`|Analyze project and create `CLAUDE.md`|
|`CLAUDE.md`|Persistent project instructions|
|`CLAUDE.local.md`|Personal instructions|
|`~/.claude/CLAUDE.md`|Global instructions|
|`@file`|Include file contents in context|
|`/memory`|Open/edit memory instructions|