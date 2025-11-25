# Quick Start Guide
# Base44 Multi-Agent Builder

## 🚀 Get Up and Running in 5 Minutes

### Step 1: Prerequisites

Make sure you have:
- **Node.js 18+** installed ([download](https://nodejs.org/))
- **npm** or **yarn** package manager
- **Anthropic API key** ([get one](https://console.anthropic.com/))
- **Supabase account** ([sign up](https://supabase.com/))

### Step 2: Clone the Repository

```bash
git clone https://github.com/Gamma-spyder/base44-multi-agent-builder.git
cd base44-multi-agent-builder
```

### Step 3: Install Dependencies

```bash
npm install
```

This will install all required packages including:
- React & Vite
- Anthropic SDK
- Supabase client
- Tailwind CSS & shadcn/ui
- And more...

### Step 4: Set Up Supabase

1. Go to [supabase.com](https://supabase.com/) and create a new project
2. Wait for the project to be ready (takes ~2 minutes)
3. Go to **Settings** → **API**
4. Copy:
   - Project URL
   - `anon` public key
   - `service_role` secret key (only for backend)

### Step 5: Configure Environment Variables

```bash
cp .env.example .env
```

Edit `.env` and add your keys:

```bash
# Anthropic API
ANTHROPIC_API_KEY=sk-ant-api03-YOUR-KEY-HERE

# Supabase
VITE_SUPABASE_URL=https://your-project.supabase.co
VITE_SUPABASE_ANON_KEY=your-anon-key-here
SUPABASE_SERVICE_ROLE_KEY=your-service-role-key-here
```

### Step 6: Run Database Migrations

```bash
npm run setup:supabase
```

This will create the necessary database tables and RLS policies.

### Step 7: Start Development Server

```bash
npm run dev
```

Your app should now be running at `http://localhost:5173` 🎉

---

## 🎯 Your First Build

1. Open http://localhost:5173 in your browser
2. Sign up with email/password
3. Click **"New Project"**
4. Try this prompt:

```
Create a simple task manager with:
- List of tasks with title and status
- Add new task button
- Mark tasks as complete
- Filter by status (all, active, completed)
- Clean, modern blue design
```

5. Watch the Orchestrator coordinate the specialist agents
6. See your app being built in real-time!

---

## 🔧 Common Commands

```bash
# Development
npm run dev              # Start dev server
npm run build            # Build for production
npm run preview          # Preview production build

# Testing
npm run test             # Run unit tests
npm run test:watch       # Watch mode
npm run test:e2e         # E2E tests

# Linting & Formatting
npm run lint             # Check code style
npm run lint:fix         # Auto-fix issues
npm run format           # Format with Prettier

# Database
npm run migrate          # Run new migrations
npm run seed             # Seed sample data

# Deployment
npm run deploy           # Deploy to Vercel
```

---

## 🐛 Troubleshooting

### "Module not found" errors
```bash
rm -rf node_modules package-lock.json
npm install
```

### Supabase connection issues
- Check your `.env` file has correct values
- Verify project URL doesn't have trailing slash
- Make sure RLS policies are set up

### Anthropic API errors
- Verify API key is correct
- Check you have credits in your Anthropic account
- Ensure API key starts with `sk-ant-`

### Build errors
```bash
npm run lint:fix
npm run format
npm run build
```

---

## 📚 Next Steps

1. **Read the PRD**: Check out [LOVABLE_PRD.md](LOVABLE_PRD.md) for full product details
2. **Review Architecture**: See [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md)
3. **Try Examples**: Explore the `/examples` folder
4. **Customize Agents**: Edit agent prompts in `/prompts`
5. **Deploy**: Follow deployment guide in docs

---

## 📞 Need Help?

- **Documentation**: Check `/docs` folder
- **Issues**: [GitHub Issues](https://github.com/Gamma-spyder/base44-multi-agent-builder/issues)
- **Discussions**: [GitHub Discussions](https://github.com/Gamma-spyder/base44-multi-agent-builder/discussions)

---

**Happy Building! 🚀**