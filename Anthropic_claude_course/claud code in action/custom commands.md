# 1. What Are Custom Commands?

Custom commands let you create reusable prompts/workflows in Claude Code.

Instead of repeatedly typing the same instructions, you can create commands like:

- `/audit`
- `/write_tests`
- `/refactor`
- `/review`
- `/document`

---

# 2. Folder Structure

Inside your project:

```
project-folder/└── .claude/    └── commands/        ├── audit.md        ├── write_tests.md        └── review.md
```

### Important

- Create a `.claude` folder
- Inside it, create `commands`
- Each `.md` file becomes a command

---

# 3. Command Naming

Filename → Command Name

|Filename|Command|
|---|---|
|audit.md|`/audit`|
|write_tests.md|`/write_tests`|
|review.md|`/review`|

---

# 4. Example: Audit Command

## File

```
.claude/commands/audit.md
```

## Purpose

Automates dependency vulnerability checking.

### Workflow

1. Run `npm audit`
2. Run `npm audit fix`
3. Run tests to verify nothing broke

### Benefit

- Saves time
- Standardizes workflows
- Reduces repetitive prompting

---

# 5. Automatic Detection

After creating the command file:

✅ Claude detects it automatically  
❌ No restart needed

---

# 6. Commands with Arguments

Claude custom commands support dynamic input using:

```
$ARGUMENTS
```

This placeholder inserts whatever text you pass after the command.

---

# 7. Example: `write_tests.md`

## File

```
.claude/commands/write_tests.md
```

## Example Content

```
Write comprehensive tests for: $ARGUMENTSTesting conventions:* Use Vitest with React Testing Library* Place test files in a __tests__ directory* Name test files as [filename].test.ts(x)* Use @/ prefix for importsCoverage:* Test happy paths* Test edge cases* Test error states
```

---

# 8. Using the Command

## Example Usage

```
/write_tests the use-auth.ts file in the hooks directory
```

### What Happens

Claude replaces:

```
$ARGUMENTS
```

with:

```
the use-auth.ts file in the hooks directory
```

---

# 9. Arguments Can Be Anything

Arguments are not limited to file paths.

You can pass:

- feature descriptions
- bug explanations
- folder names
- coding tasks
- requirements

### Examples

```
/review authentication flow
```

```
/refactor dashboard state management
```

```
/document payment API
```

---

# 10. Benefits of Custom Commands

## Reusability

Avoid repeating long prompts.

## Consistency

Enforce project standards automatically.

## Faster Workflow

Execute common tasks instantly.

## Team Standardization

Everyone uses the same development instructions.

## Better Context

Commands can encode project-specific conventions.

---

# 11. Best Use Cases

## Testing

- `/write_tests`

## Security

- `/audit`

## Code Review

- `/review`

## Documentation

- `/document`

## Refactoring

- `/refactor`

## Bug Fixing

- `/fix_bug`

---

# Quick Summary Table

|Feature|Purpose|
|---|---|
|`.claude/commands`|Stores custom commands|
|`.md` files|Define commands|
|Filename|Command name|
|`$ARGUMENTS`|Dynamic user input|
|Auto-detection|No restart needed|
