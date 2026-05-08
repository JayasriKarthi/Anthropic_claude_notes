## Hooks

Control Claude’s actions before/after tool execution.

## Agent SDK

Allows developers to build custom AI-powered automation using Claude programmatically.

# 1. Hook

## Meaning

A mechanism that runs code:

- before
- or after  
    Claude uses a tool.

## Real-Time Importance

Used for:

- automation
- security
- validation
- code quality checks

---

# 2. PreToolUse Hook

## Meaning

Runs BEFORE tool execution.

## Important Use

Can:

- allow
- block  
    tool operations.

## Real-Time Example

Prevent Claude from reading:

```
.env
```

files containing secrets.

---

# 3. PostToolUse Hook

## Meaning

Runs AFTER tool execution.

## Important Use

Used for:

- formatting
- testing
- linting
- type checking

## Real-Time Example

Run:

```
tsc --noEmit
```

after every code edit.

---

# 4. Matcher

## Meaning

Defines which tool triggers the hook.

## Examples

|Matcher|Tool|
|---|---|
|`Read`|File reading|
|`Write`|File writing|
|`Edit`|File editing|

## Real-Time Importance

Allows targeted automation.

---

# 5. `.env` Protection

## Meaning

Blocks access to secret environment variables.

## Real-Time Importance

Protects:

- API keys
- database passwords
- authentication secrets

## Interview Point

Security best practice.

---

# 6. `process.exit(0)`

## Meaning

Allow operation.

## Real-Time Importance

Signals successful validation.

---

# 7. `process.exit(2)`

## Meaning

Block operation.

## Real-Time Importance

Used in security and permission control.

---

# 8. `stderr`

## Meaning

Error output stream.

## Real-Time Importance

Sends feedback/error message to Claude.

Example:

```
You cannot read the .env file
```

---

# 9. TypeScript Type Checking Hook

## Meaning

Automatically checks for type errors after edits.

## Real-Time Importance

Prevents:

- broken builds
- missing function updates
- inconsistent code

## Interview Point

Continuous validation automation.

---

# 10. Query Duplication Hook

## Meaning

Checks whether Claude created duplicate database queries.

## Real-Time Importance

Improves:

- code reuse
- maintainability
- clean architecture

---

# 11. Agent SDK

## Meaning

A programming SDK to run Claude inside apps/scripts.

## Real-Time Importance

Build:

- AI coding tools
- automation systems
- AI workflows
- autonomous developer agents

---

# 12. `allowedTools`

## Meaning

Restricts which tools Claude can use.

## Real-Time Importance

Security + controlled environments.

Example:

```
allowedTools: ["Read", "Glob"]
```

---

# 13. `$PWD`

## Meaning

Current project directory path.

## Real-Time Importance

Creates portable configurations across different machines.

---

# 14. `settings.local.json`

## Meaning

Local Claude settings file.

## Real-Time Importance

Stores:

- hooks
- permissions
- personal configs

without affecting team members.

---

# 15. Real-Time Most Important Uses

|Feature|Real-Time Use|
|---|---|
|Hooks|Automation + security|
|Type checking hook|Prevent broken code|
|Query review hook|Reduce duplicate logic|
|Agent SDK|Build AI automation systems|
|Permissions|Secure Claude actions|

---

# 16. Most Important Interview Concepts

## Hooks

Tool interception system.

## PreToolUse

Security/control before execution.

## PostToolUse

Automation after execution.

## Agent SDK

Programmatic AI workflow integration.

## Type Checking

Automatic validation after edits.

## Permissions

Restricting AI capabilities securely.

---

# Final Key Idea

Claude Code hooks and SDK are mainly used in real projects for:

- secure AI coding
- automated validation
- workflow automation
- code quality enforcement
- AI-assisted development pipelines