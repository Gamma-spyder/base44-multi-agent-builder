# System Architecture
# Base44 Multi-Agent Builder

## Overview

The Base44 Multi-Agent Builder is a distributed AI system that coordinates multiple specialized agents to build full-stack applications through natural conversation.

## Core Principles

1. **Separation of Concerns** - Each agent has a focused responsibility
2. **Context Compression** - Orchestrator summarizes long conversations
3. **Parallel Execution** - Agents work simultaneously when possible
4. **Fault Tolerance** - Graceful degradation and retry logic
5. **State Management** - Shared context across all agents

## System Components

### 1. Orchestrator Agent

**Purpose:** Master coordinator and conversationalist

**Responsibilities:**
- Maintain natural conversation with users
- Ask clarifying questions
- Decompose complex requests into sub-tasks
- Route tasks to appropriate specialist agents
- Monitor agent progress and handle failures
- Synthesize results from multiple agents
- Compress context when approaching token limits

**Key Algorithms:**
- **Context Summarization:** When conversation exceeds 80% of token limit, summarize into key points
- **Task Decomposition:** Parse user intent and break into atomic tasks
- **Agent Selection:** Route tasks based on type (frontend/backend/database/integration)
- **Progress Aggregation:** Collect and present unified status from all agents

**Context Management:**
```javascript
class OrchestratorContext {
  conversationHistory: Message[]
  projectRequirements: Requirements
  activeAgents: Map<AgentType, AgentStatus>
  generatedArtifacts: Artifact[]
  
  summarize(): CompressedContext {
    // Keep only essential information
    return {
      userGoals: extractGoals(this.conversationHistory),
      technicalDecisions: extractDecisions(this.conversationHistory),
      currentPhase: this.determinePhase(),
      artifacts: this.generatedArtifacts.map(a => a.summary)
    }
  }
}
```

### 2. Frontend Builder Agent

**Purpose:** Generate React UI components

**Responsibilities:**
- Create React components (JSX/TSX)
- Apply Tailwind CSS styling
- Integrate shadcn/ui components
- Implement responsive layouts
- Add form validation
- Handle state management

**Input Format:**
```javascript
{
  task: "frontend",
  requirements: {
    pages: ["dashboard", "login", "profile"],
    components: ["UserCard", "ExpenseForm"],
    styling: "modern, mobile-first, blue theme",
    features: ["authentication", "data display", "forms"]
  },
  context: CompressedContext
}
```

**Output Format:**
```javascript
{
  files: [
    {
      path: "src/pages/Dashboard.jsx",
      content: "...",
      description: "Main dashboard page"
    },
    {
      path: "src/components/UserCard.jsx",
      content: "...",
      description: "User profile card component"
    }
  ],
  dependencies: ["react-hook-form", "lucide-react"],
  notes: "Used shadcn/ui Card and Form components"
}
```

### 3. Backend Builder Agent

**Purpose:** Generate API routes and business logic

**Responsibilities:**
- Create API endpoints
- Implement serverless functions
- Add middleware and authentication
- Handle business logic
- Implement error handling

### 4. Database Builder Agent

**Purpose:** Design database schema and migrations

**Responsibilities:**
- Design entity schemas
- Generate SQL migrations
- Create RLS policies
- Define relationships and constraints
- Add indexes for performance

### 5. Integration Builder Agent

**Purpose:** Configure third-party API integrations

**Responsibilities:**
- Set up OAuth flows
- Create API client wrappers
- Handle webhooks
- Transform data formats
- Implement retry logic

## Communication Protocol

### Agent Communication Flow

```
User Message
    ↓
Orchestrator receives and analyzes
    ↓
Orchestrator decomposes into tasks
    ↓
Tasks dispatched to specialist agents (parallel)
    ↓
Agents work independently
    ↓
Results sent back to Orchestrator
    ↓
Orchestrator synthesizes results
    ↓
Response to User
```

## State Management

### Shared State Structure

```javascript
{
  project: {
    id: "proj-uuid",
    name: "Expense Tracker",
    status: "building" | "ready" | "failed"
  },
  
  conversation: {
    messages: Message[],
    compressedContext: CompressedContext
  },
  
  agents: {
    orchestrator: { status: "active" | "idle" },
    frontend: { status: "working" | "idle", progress: 0.75 },
    backend: { status: "idle", progress: 1.0 },
    database: { status: "working", progress: 0.50 },
    integration: { status: "idle", progress: 0.0 }
  },
  
  artifacts: {
    files: GeneratedFile[],
    entities: EntitySchema[],
    migrations: Migration[]
  }
}
```

## Error Handling

### Error Types

1. **Agent Failure** - Specialist agent returns error
2. **Timeout** - Agent exceeds execution time limit
3. **Invalid Output** - Agent returns malformed response
4. **Context Overflow** - Cannot compress context enough

### Recovery Strategies

**Agent Failure:**
```javascript
async function handleAgentFailure(task, error) {
  if (task.retries < task.maxRetries) {
    await delay(Math.pow(2, task.retries) * 1000);
    return await retryTask(task);
  } else {
    return await orchestrator.handleFailedTask(task, error);
  }
}
```

## Performance Optimizations

### Caching Strategy

1. **Agent Output Caching** - Cache common component patterns
2. **Context Compression** - Reuse compressed summaries
3. **Parallel Execution** - Run independent agents simultaneously
4. **Lazy Loading** - Load agent code only when needed

### Metrics Tracked

- Agent response time (p50, p95, p99)
- Token usage per build
- Cache hit rate
- Error rate by agent

## Security Considerations

### API Key Management

- Store API keys encrypted in environment variables
- Never expose keys in generated code
- Rotate keys regularly

### RLS Policies

All database tables must have RLS enabled:
```sql
ALTER TABLE table_name ENABLE ROW LEVEL SECURITY;

CREATE POLICY "Users view own data"
  ON table_name FOR SELECT
  USING (auth.uid() = user_id);
```

## Deployment Architecture

### Production Stack

```
[Users] → [Vercel CDN] → [React Frontend + API Routes]
                ↓
       [Orchestrator Agent]
                ↓
    ┌───────────┼───────────┐
    ↓           ↓           ↓
[Frontend]  [Backend]  [Database]
    ↓           ↓           ↓
         [Supabase]
              ↓
      [Anthropic API]
```

### Scaling Considerations

- **Horizontal Scaling:** Deploy multiple agent instances
- **Load Balancing:** Distribute requests across instances
- **Rate Limiting:** 100 requests/hour per user
- **Caching:** Redis for agent output caching
- **Monitoring:** Real-time dashboards

---

See `LOVABLE_PRD.md` for complete product requirements.