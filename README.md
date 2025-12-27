# AI Model Router

Intelligent task classification, prompt optimization, and multi-model orchestration. Pick the right model for the right task.

## The Problem

You're using AI models but don't really know which one to use:

- Defaulting to GPT-4 for everything (expensive, slow for simple tasks)
- Writing vague prompts because you're not sure what matters
- Running one model at a time, guessing if it's actually the best choice
- No visibility into cost vs quality vs speed tradeoffs
- Painful to iterate or try a different provider

This wastes money and gets suboptimal results.

## What This Does

1. **Classify** your request automatically (copywriting, code, research, etc.)
2. **Engineer** a better prompt using structured templates (role, context, constraints, quality rubric)
3. **Route** to 2-5 models intelligently based on task fit, cost, latency, privacy
4. **Run** them in parallel with real cost/time estimates
5. **Compare** results side-by-side to see which model actually performs better

Simple. Clear. Decision-focused.

## Features

- **Auto task classification** – detects what you're trying to do
- **Structured prompt templates** – role + context + constraints + output format + quality criteria
- **Smart model routing** – scoring considers task fit, cost, speed, privacy, capability
- **Parallel execution** – run 2-5 models simultaneously, results stream as they complete
- **Real cost tracking** – see exactly how much each model costs
- **Side-by-side comparison** – evaluate quality, speed, and cost at a glance
- **Iterate without friction** – refine prompt or swap models and re-run instantly
- **Privacy controls** – PII detection, no-store mode, audit logs (roadmap)

## Try It

**Live demo:** No setup needed, works in browser:

```bash
# Clone
git clone https://github.com/HB-Innovates/ai-model-router.git
cd ai-model-router

# Open in browser
open index.html
```

Or deploy to Vercel (1 click):
- Fork repo on GitHub
- Connect to Vercel
- Deploy
- Get live URL

**To use real API keys:**

```bash
# Create .env
cat > .env.local << EOF
VITE_OPENAI_API_KEY=sk-...
VITE_ANTHROPIC_API_KEY=sk-ant-...
VITE_GOOGLE_API_KEY=AIza...
EOF
```

## How It Works

```
Input (plain English task)
        ↓
Classify (task type detection)
        ↓
Clarify (ask 1-3 critical questions)
        ↓
Engineer (structured prompt generation)
        ↓
Route (scoring algorithm picks models)
        ↓
Execute (parallel API calls)
        ↓
Compare (normalized results, cost analysis)
```

**Routing considers:**
- Task fit (is this model good at this task?)
- Cost (tokens × rate)
- Latency (expected response time)
- Privacy (does this provider train on inputs?)
- Capability (does it support this task type?)

## Project Layout

```
ai-model-router/
├── index.html              # Single-file MVP demo
├── README.md               # This file
├── QUICKSTART.md           # 5-minute guide
├── PRODUCT_SPEC.md         # Full specification
├── IMPLEMENTATION_PLAN.md  # Timeline & milestones
├── docs/
│   ├── API.md
│   ├── ROUTING_ALGORITHM.md
│   ├── PROMPT_TEMPLATES.md
│   ├── DATABASE.md
│   └── SAFETY.md
└── [backend/frontend coming week 1]
```

## Roadmap

**MVP (done):**
- Text requests, 5 task types, prompt engineering, 3-model comparison

**V1 (next 6-10 weeks):**
- User auth + persistent projects
- Database (PostgreSQL)
- Multimodal (image input)
- Web search integration
- Local Ollama (privacy mode)
- PII detection
- Audit logs
- Advanced routing (ML-based scoring)

**V2 (later):**
- Team workspaces
- Fine-tuning support
- Specialized tools (video gen, transcription)
- Real-time collaboration

## Tech Stack

**Frontend:**
- React 18 + Vite
- Tailwind CSS
- Zustand (state)

**Backend:**
- Node.js + Express (or Python + FastAPI)
- PostgreSQL + Prisma
- Redis (caching, queues)

**DevOps:**
- Vercel (frontend)
- Railway/Render (backend)
- Docker (local development)
- GitHub Actions (CI/CD)

## Documentation

- **[QUICKSTART.md](QUICKSTART.md)** – Get running in 5 minutes
- **[PRODUCT_SPEC.md](PRODUCT_SPEC.md)** – Full specification (problem, users, features, success metrics)
- **[IMPLEMENTATION_PLAN.md](IMPLEMENTATION_PLAN.md)** – Week-by-week timeline and effort estimates
- **[docs/API.md](docs/API.md)** – REST API endpoints
- **[docs/ROUTING_ALGORITHM.md](docs/ROUTING_ALGORITHM.md)** – How model selection works
- **[docs/PROMPT_TEMPLATES.md](docs/PROMPT_TEMPLATES.md)** – Task-specific templates

## Why Build This

This project demonstrates:
- Full-stack architecture (frontend → backend → database)
- AI/ML system design (routing, optimization, multi-provider orchestration)
- Product thinking (user stories, acceptance criteria, prioritization)
- Real engineering (state management, error handling, async jobs)
- DevOps (deployment, monitoring, scaling)

Good for portfolio, interview prep, and actually learning how to build AI products.

## Testing

```bash
npm run test              # Run all tests
npm run test:watch       # Watch mode
npm run test:coverage    # Coverage report
```

## Contributing

Bug reports and PRs welcome. Open an issue first to discuss.

## License

MIT – use for anything.

## Questions?

- GitHub Issues: bug reports, feature requests
- GitHub Discussions: Q&A, ideas
- Email: bagichawala.husain@gmail.com