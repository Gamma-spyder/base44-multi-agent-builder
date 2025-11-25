# 🚀 Base44 Multi-Agent Builder

**Build full-stack applications through natural conversation with specialized AI agents.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Status: Active Development](https://img.shields.io/badge/Status-Active%20Development-green)](https://github.com/Gamma-spyder/base44-multi-agent-builder)

---

## 🎯 What Is This?

A **live, web-based AI application builder** that uses **multi-agent orchestration** to build production-ready full-stack applications. Describe what you want in plain English, and watch as specialized AI agents collaborate to bring your vision to life.

### Key Innovation: Multi-Agent Orchestration

Unlike traditional single-agent builders that hit context limits and struggle with complex tasks, our system uses:

```
👑 ORCHESTRATOR AGENT (Master Coordinator)
    ↓
    Delegates to specialist agents:
    ↓
🎨 Frontend Agent → React components, UI/UX
⚙️ Backend Agent → APIs, business logic  
🗄️ Database Agent → Schema, migrations, RLS
🔌 Integration Agent → Third-party APIs
```

**Benefits:**
- ✅ **Unlimited conversations** - Orchestrator handles context compression
- ✅ **Better code quality** - Each agent is a specialized expert
- ✅ **Parallel execution** - Multiple agents work simultaneously  
- ✅ **Seamless handoffs** - Context flows between agents automatically
- ✅ **Scalable architecture** - Add new specialist agents easily

---

## 🎬 Example Usage

```
You: "Build me an expense tracking app for my team"

Orchestrator: "I'll help you build that! Let me get some details:
- How many team members?
- What approval workflow do you need?
- Any integrations? (QuickBooks, Slack, etc.)"

You: "10 people, manager approval, QuickBooks sync"

Orchestrator: "Perfect! I'm coordinating:
🎨 Frontend Agent: Building expense form + dashboard
🗄️ Database Agent: Creating expense schema with RLS
🔌 Integration Agent: Setting up QuickBooks connection
⚙️ Backend Agent: Implementing approval workflow

[Agents work in parallel with real-time progress...]

Orchestrator: "Your expense tracker is ready! ✨
✅ Expense submission form
✅ Manager approval dashboard
✅ QuickBooks integration (placeholder ready)
✅ Real-time updates

Want to preview it?"
```

---

## ⚡ Quick Start

### Prerequisites

- Node.js 18+
- npm or yarn
- Supabase account (free tier works)
- Anthropic API key

### Installation

```bash
# Clone the repository
git clone https://github.com/Gamma-spyder/base44-multi-agent-builder.git
cd base44-multi-agent-builder

# Install dependencies
npm install

# Set up environment variables
cp .env.example .env
# Edit .env with your keys

# Set up Supabase
npm run setup:supabase

# Run development server
npm run dev
```

### Environment Setup

Create a `.env` file:

```bash
# Anthropic API
ANTHROPIC_API_KEY=sk-ant-api03-...

# Supabase
VITE_SUPABASE_URL=https://xxxxx.supabase.co
VITE_SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
SUPABASE_SERVICE_ROLE_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...

# Optional: For deployment features
VERCEL_TOKEN=your_vercel_token
GITHUB_TOKEN=your_github_token
```

---

## 🏗️ Architecture

See [LOVABLE_PRD.md](LOVABLE_PRD.md) for complete technical architecture.

### System Overview

```
┌─────────────────────────────────────────────┐
│           USER INTERFACE (React)            │
│  Chat • Code View • Preview • Dashboard     │
└──────────────────┬──────────────────────────┘
                   ↓
┌─────────────────────────────────────────────┐
│         ORCHESTRATOR AGENT (Claude)         │
│  • Natural conversation                     │
│  • Task decomposition                       │
│  • Context management                       │
│  • Progress synthesis                       │
└──────────────────┬──────────────────────────┘
                   ↓
        ┌──────────┴──────────┐
        │   SHARED STATE      │
        │  (Conversation +    │
        │   Build Context)    │
        └──────────┬──────────┘
                   ↓
    ┌──────────────┼──────────────┬─────────────┐
    ▼              ▼              ▼             ▼
┌────────┐    ┌────────┐    ┌────────┐    ┌────────┐
│Frontend│    │Backend │    │Database│    │Integr. │
│ Agent  │    │ Agent  │    │ Agent  │    │ Agent  │
└────────┘    └────────┘    └────────┘    └────────┘
```

---

## 📁 Project Structure

```
base44-multi-agent-builder/
├── docs/                        # Full documentation
├── src/
│   ├── agents/
│   │   ├── orchestrator.js      # Main orchestrator
│   │   └── specialists/         # Specialist agents
│   ├── components/              # React components
│   ├── lib/                     # Utilities & clients
│   └── prompts/                 # Agent system prompts
├── supabase/                    # Database migrations
├── examples/                    # Example applications
├── LOVABLE_PRD.md              # Complete PRD
└── README.md                   # This file
```

---

## 🎯 Features

### ✅ Current Features

- **Multi-Agent Orchestration** - Specialized agents for each domain
- **Unlimited Conversations** - Context compression enables endless dialogue
- **Real-Time Streaming** - Watch responses generate live
- **Code Generation** - Production-ready React + Supabase code
- **Live Preview** - See your app running in real-time
- **Project Management** - Save, resume, and manage projects
- **Entity Auto-Discovery** - Database entities created automatically

### 🚧 Coming Soon

- **Template Library** - Pre-built app templates
- **One-Click Deployment** - Deploy to Vercel instantly
- **GitHub Integration** - Push code to your repository
- **Collaboration** - Build apps with your team
- **Integration Marketplace** - Pre-configured third-party integrations

---

## 🛠️ Development

### Tech Stack

**Frontend:** React 18, Vite, Tailwind CSS, shadcn/ui  
**Backend:** Node.js, Express.js, Anthropic Claude API  
**Infrastructure:** Vercel, Supabase

### Scripts

```bash
npm run dev              # Start dev server
npm run build            # Build for production
npm run test             # Run tests
npm run lint             # Check code style
npm run deploy           # Deploy to Vercel
```

---

## 📖 Documentation

Comprehensive documentation:

- **[LOVABLE_PRD.md](LOVABLE_PRD.md)** - Complete Product Requirements Document
- **docs/ARCHITECTURE.md** - System design and data flow (coming soon)
- **docs/AGENT_SYSTEM.md** - Agent communication protocol (coming soon)
- **docs/API_REFERENCE.md** - REST and WebSocket APIs (coming soon)
- **docs/DEPLOYMENT_GUIDE.md** - Production deployment (coming soon)

---

## 🚀 Deployment

### Deploy to Vercel

```bash
vercel deploy --prod
```

### Environment Variables

Set in Vercel dashboard:
- `ANTHROPIC_API_KEY`
- `VITE_SUPABASE_URL`
- `VITE_SUPABASE_ANON_KEY`
- `SUPABASE_SERVICE_ROLE_KEY`

---

## 💰 Cost Optimization

**Free Tier (Development):**
- Supabase: $0
- Vercel: $0
- Anthropic: ~$1-5
- **Total: ~$5/month**

**Production (Small Scale):**
- Supabase Pro: $25
- Vercel Pro: $20
- Anthropic: ~$20-50
- **Total: ~$70/month**

---

## 🆚 Comparison

| Feature | Our Builder | v0.dev | Bolt.new | Base44 |
|---------|-------------|--------|----------|--------|
| Multi-Agent | ✅ | ❌ | ❌ | ❌ |
| Unlimited Conversation | ✅ | ❌ | ❌ | ❌ |
| Open Source | ✅ | ❌ | ❌ | ❌ |
| Your Database | ✅ | ❌ | ❌ | ❌ |
| No Vendor Lock-in | ✅ | ❌ | ❌ | ❌ |

---

## 📝 License

MIT License - see [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- **Base44** - Original inspiration for entity system
- **Anthropic** - Claude API powers our agents
- **Supabase** - Backend infrastructure
- **Vercel** - Hosting and deployment

---

## 📞 Support

- **Documentation:** Check `LOVABLE_PRD.md` and `/docs` folder
- **Issues:** [GitHub Issues](https://github.com/Gamma-spyder/base44-multi-agent-builder/issues)

---

## 🎯 Roadmap

### Phase 1 - MVP (Weeks 1-2)
- [ ] Chat interface with streaming
- [ ] Orchestrator agent implementation
- [ ] Frontend + Database specialist agents
- [ ] Code generation and display
- [ ] Basic project saving

### Phase 2 - Enhanced (Weeks 3-4)
- [ ] Backend + Integration agents
- [ ] Live preview panel
- [ ] Project dashboard
- [ ] Template library
- [ ] Deployment integration

---

**Built with ❤️ for developers who want to build faster without compromises.**

**Ready to build? Get started now:**
```bash
git clone https://github.com/Gamma-spyder/base44-multi-agent-builder.git
cd base44-multi-agent-builder
npm install
npm run dev
```

**Read the complete PRD:** [LOVABLE_PRD.md](LOVABLE_PRD.md)

---

**Questions? Check the PRD or open an issue!** 🚀
