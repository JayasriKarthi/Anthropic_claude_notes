
# . Environment Setup / Installation

## 1.1 Install Node.js (for backend apps)

Node.js is required to build API servers.

### Install:

```
sudo apt updatesudo apt install nodejs npm
```

Check:

```
node -vnpm -v
```

---

## 1.2 Install Python (for MCP / SDK tools)

Python is used for MCP servers and tools.

```
sudo apt install python3 python3-pip
```

Check:

```
python3 --versionpip3 --version
```

---

## 1.3 Install Claude SDK (Python example)

```
pip install anthropic
```

---

## 1.4 API Key Setup

Store API key safely:

### Linux/Mac:

```
export ANTHROPIC_API_KEY="your_key_here"
```

### Windows (PowerShell):

```
setx ANTHROPIC_API_KEY "your_key_here"
```

---

# 2. Basic Claude API Request

## Python Example

```
from anthropic import Anthropicclient = Anthropic(api_key="YOUR_API_KEY")response = client.messages.create(    model="claude-3-opus",    max_tokens=200,    messages=[        {"role": "user", "content": "Explain AI in simple terms"}    ])print(response.content)
```

---

# 3. API Core Concepts

## 3.1 API Key

Used for authentication.

## 3.2 Model Name

Defines Claude version:

- Claude 3 Haiku → fast
    
- Claude 3 Sonnet → balanced
    
- Claude 3 Opus → most powerful
    

---

## 3.3 Messages Structure

```
[  {"role": "system", "content": "You are a tutor"},  {"role": "user", "content": "Explain ML"}]
```

---

## 3.4 Max Tokens

Controls response length.

---

# 4. Conversation Handling

## Multi-turn chat

You must resend full history:

```
User: What is AI?Assistant: AI is...User: Explain more
```

Claude does NOT remember automatically.

---

# 5. System Prompt

Defines behavior:

```
You are a coding assistant. Give step-by-step explanations.
```

Used for:

- tutors
    
- assistants
    
- coding bots
    
- finance bots
    

---

# 6. Temperature

Controls randomness:

|Value|Behavior|
|---|---|
|0.0|strict, factual|
|0.5|balanced|
|1.0|creative|

---

# 7. Streaming

Real-time output:

```
stream=True
```

Used in:

- chat apps
    
- AI assistants
    

---

# 8. Structured Output (JSON Mode)

Example:

```
{  "name": "product",  "price": 1200}
```

Used for:

- automation
    
- backend systems
    
- AI pipelines
    

---

# 9. Prompt Engineering

## Key techniques:

- Be specific
    
- Use examples
    
- Use structured tags
    
- Avoid ambiguity
    

---

## Few-shot example:

```
Input: happy → Output: positive  Input: sad → Output: negative
```

---

## XML structuring:

```
<instruction>Summarize text</instruction><data>...</data>
```

---

# 10. Prompt Evaluation System

Workflow:

1. Create dataset
    
2. Run prompts
    
3. Generate outputs
    
4. Grade results
    
5. Improve prompt
    

Used in production AI systems.

---

# 11. Model Grader

AI model that scores outputs automatically.

---

# 12. Tool Use System

Claude can call external functions.

Example:

- weather API
    
- calculator
    
- database
    
- GitHub
    

---

## Tool function example:

```
def get_price(product):    return 100
```

---

# 13. Tool Schema (VERY IMPORTANT)

Defines function structure:

```
{  "name": "get_weather",  "parameters": {    "location": "string"  }}
```

---

# 14. Batch Tool

Runs multiple tool calls together:

- reduces API calls
    
- improves speed
    

---

# 15. MCP (Model Context Protocol)

## What it does:

Connects Claude to tools, files, apps.

---

## MCP Server

Provides:

- tools
    
- prompts
    
- resources
    

---

## MCP Client

Connects to server and sends requests.

---

## Communication types:

- stdin/stdout (local)
    
- HTTP (remote)
    

---

## MCP Inspector

Tool to test MCP servers.

---

# 16. MCP Resources

Used to expose files:

Example:

- PDFs
    
- documents
    
- database entries
    

---

# 17. MCP Tools

Executable functions:

- read_file
    
- search_db
    
- run_command
    

---

# 18. Files API

Upload once → reuse later:

Benefits:

- avoids re-uploading large files
    
- reduces token usage
    

---

# 19. Prompt Caching

Stores repeated prompts:

- reduces cost
    
- improves speed
    

Requirement:

- ≥ 1024 tokens
    

---

# 20. Citations

Links answers to source documents:

- improves trust
    
- shows where info came from
    

---

# 21. Extended Thinking

Allows deeper reasoning before final answer.

---

# 22. Code Execution Tool

Runs code in secure sandbox:

- no internet access
    
- isolated environment (Docker)
    

---

# 23. Computer Use

Claude can:

- click
    
- type
    
- navigate UI  
    like a human desktop user.
    

---

# 24. AI Agents

Agents can:

- think
    
- plan
    
- use tools
    
- complete tasks autonomously
    

---

# 25. Workflows

Predefined process steps.

### Types:

- chaining
    
- routing
    
- parallelization
    
- evaluator-optimizer
    

---

## 25.1 Chaining

Step-by-step execution.

## 25.2 Routing

Direct tasks to correct pipeline.

## 25.3 Parallelization

Run multiple tasks simultaneously.

## 25.4 Evaluator-Optimizer

Generate → evaluate → improve loop.

---

# 26. Environment Inspection

Agents observe:

- results of actions
    
- system state
    

Used for decision making.

---

# 27. Key Architecture Idea

Real AI apps combine:

```
API + Prompts + Tools + RAG + Evaluation + Agents + Workflows
```

---

# 28. RAG (Retrieval Augmented Generation)

AI reads external documents before answering.

Steps:

1. Store docs
    
2. Embed text
    
3. Retrieve relevant chunks
    
4. Pass to Claude
    

---

# 29. Embeddings

Convert text → numbers for semantic search.

---

# 30. Computer Tool Sandbox

- isolated environment
    
- no internet
    
- secure execution
    

---

# 31. Prompt Caching + Optimization

Used to:

- reduce cost
    
- reuse context
    
- speed up repeated prompts
    

---

# 🚀 Final Summary

This entire course teaches:

👉 How to build real AI systems using Claude:

- APIs
    
- prompts
    
- tools
    
- MCP
    
- agents
    
- workflows
    
- evaluation systems
    
- document understanding
    
- automation pipelines
    
