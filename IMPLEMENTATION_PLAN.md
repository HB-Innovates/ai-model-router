# Implementation Plan: AI Model Router

## Overview

**MVP Timeline:** 3 weeks, ~120 engineering hours (1 engineer full-time)

**V1 Timeline:** 6-10 weeks after MVP ship

**Philosophy:** Ship the smallest useful thing first (MVP). Get user feedback. Build V1 based on what matters.

---

## MVP: Weeks 1-3

### Goal
Working single-file app that demonstrates the complete 5-step workflow. No database, no auth, no real API calls. Just enough to show:
- Can classify tasks
- Can generate structured prompts
- Can route intelligently
- Can compare models (mock results)

### Week 1: Foundation

**Frontend Setup (40h)**
- [ ] Create project structure (React + Vite, or just HTML+JS)
- [ ] Set up routing (5 screens: request → clarify → prompt → route → results)
- [ ] Create base UI components (cards, buttons, forms)
- [ ] Implement state management (Zustand or Context API)
- [ ] Responsive design (mobile + desktop)
- [ ] Set up basic styling (Tailwind CSS or custom)

**Classifier Logic (20h)**
- [ ] Implement task type detection (rule-based, rule/keyword matching)
- [ ] Support 5 categories: copywriting, coding, research, brainstorming, translation
- [ ] Allow user override
- [ ] Add ~50 test cases

**Estimated Hours:** 60h

### Week 2: Core Logic

**Clarification Questions (20h)**
- [ ] Build question templates per task type (copywriting Q's != coding Q's)
- [ ] Implement max 3 question UX
- [ ] Store answers in state
- [ ] Show/hide questions based on confidence

**Prompt Engineering (30h)**
- [ ] Create 5-section template (role, context, constraints, format, rubric)
- [ ] Implement template population based on task type + answers
- [ ] Make prompt editable UI
- [ ] Test with actual requests (sanity check)

**Estimated Hours:** 50h

### Week 3: Routing & Results

**Model Router (20h)**
- [ ] Define model scoring algorithm (task fit, cost, latency, privacy)
- [ ] Create model cards with recommendations
- [ ] Implement model selection UI (checkboxes)
- [ ] Mock model data (GPT-4, Claude 3, Gemini Pro, etc.)

**Results & Comparison (20h)**
- [ ] Results screen layout (side-by-side columns)
- [ ] Cost calculation display
- [ ] Mock model responses (convincing text)
- [ ] Iteration flows (refine prompt, swap models, new request)

**Polish & Deploy (10h)**
- [ ] Bug fixes
- [ ] Mobile responsiveness check
- [ ] Deploy to Vercel (1-click)
- [ ] Write QUICKSTART.md
- [ ] Create demo link

**Estimated Hours:** 50h

### MVP Deliverables

```
✅ index.html (or App.jsx)         Single-file or minimal build
✅ README.md                       Overview + quick start
✅ QUICKSTART.md                   5-minute guide
✅ PRODUCT_SPEC.md                 Full specification
✅ Public GitHub repo               MIT license, live demo link
✅ Deployed live demo               Vercel URL
```

### MVP Success Criteria

- [ ] App loads instantly (no build step)
- [ ] Complete workflow works end-to-end (request → results in <2 min)
- [ ] Prompt engineering produces sensible output
- [ ] Routing recommendations seem reasonable
- [ ] Mobile friendly
- [ ] Code is clean enough for recruiter review

---

## V1: Weeks 4-10 (After MVP Ship)

### Before Starting V1

**Gather feedback (1 week):**
- Share MVP with 10-20 users
- Ask: What's missing? What's confusing? What would make you use this regularly?
- Identify top 3 features that matter most
- Adjust roadmap based on feedback

### Week 4: Backend Setup

**Database (20h)**
- [ ] Design PostgreSQL schema (users, projects, prompts, runs, costs, audit_logs)
- [ ] Set up Prisma ORM
- [ ] Create migrations
- [ ] Add seed data

**Backend Skeleton (20h)**
- [ ] Set up Express.js (or FastAPI)
- [ ] Create basic CRUD endpoints
- [ ] Add error handling middleware
- [ ] Set up logging

**Auth Setup (15h)**
- [ ] GitHub OAuth flow
- [ ] JWT token generation/validation
- [ ] Protected endpoints
- [ ] Session management

**Estimated Hours:** 55h

### Week 5: Frontend Migration

**React Setup (20h)**
- [ ] Convert MVP to React component structure
- [ ] Set up state management (Zustand)
- [ ] Implement React Router
- [ ] Add form handling (React Hook Form)

**API Integration (20h)**
- [ ] Create API client (axios + TanStack Query)
- [ ] Connect frontend to backend endpoints
- [ ] Handle loading/error states
- [ ] Add proper error messages

**Authentication UI (15h)**
- [ ] Login/signup screens
- [ ] OAuth flow integration
- [ ] Redirect after auth
- [ ] Logout functionality

**Estimated Hours:** 55h

### Week 6-7: Real Model Integration

**OpenAI Integration (20h)**
- [ ] Set up OpenAI SDK
- [ ] Create model adapter (abstract provider calls)
- [ ] Implement request formatting
- [ ] Handle streaming responses
- [ ] Cost calculation
- [ ] Error handling + retries

**Anthropic Integration (15h)**
- [ ] Set up Anthropic SDK
- [ ] Create adapter (consistent with OpenAI)
- [ ] Test Claude 3 models
- [ ] Cost tracking

**Google Gemini (15h)**
- [ ] Set up Google API
- [ ] Create adapter
- [ ] Test Gemini Pro
- [ ] Cost tracking

**Async Job Queue (15h)**
- [ ] Set up Bull.js (Redis-backed)
- [ ] Implement parallel model execution
- [ ] Stream results to frontend (WebSocket or polling)
- [ ] Handle timeouts/failures

**Estimated Hours:** 65h

### Week 8: Data Persistence & History

**Save/Load Projects (20h)**
- [ ] Implement project CRUD
- [ ] Project versioning
- [ ] Prompt history
- [ ] Run history with results

**Cost Tracking (15h)**
- [ ] Store cost per run
- [ ] Aggregate by user/month
- [ ] Build cost dashboard (simple charts)
- [ ] Invoice/usage export (stretch)

**Estimated Hours:** 35h

### Week 9: Advanced Features (Choose Top 3)

**Option A: Multimodal (20h)**
- [ ] Image upload UI
- [ ] Image description generation
- [ ] Vision model support (GPT-4V, Claude 3V)
- [ ] Image results display

**Option B: Web Search Integration (20h)**
- [ ] Integrate search API (Google Custom Search or SerpAPI)
- [ ] Fetch + summarize results
- [ ] Add search results to context
- [ ] Cite sources in output

**Option C: Local Ollama (20h)**
- [ ] Detect local Ollama instance
- [ ] Model selector UI
- [ ] Request formatting for Ollama
- [ ] Privacy mode (local-only)

**Option D: PII Detection (20h)**
- [ ] Implement regex + ML-based PII detection
- [ ] Redaction UI
- [ ] Logging with redaction
- [ ] Configuration per user

**Estimated Hours:** 20h (choose 1, defer others)

### Week 10: Polish & Ship V1

**QA (15h)**
- [ ] End-to-end testing
- [ ] Edge case handling
- [ ] Performance testing
- [ ] Mobile check

**Documentation (10h)**
- [ ] Update README
- [ ] Write API docs
- [ ] Create user guide
- [ ] Write deployment guide

**Infrastructure (10h)**
- [ ] Set up monitoring (Sentry for errors)
- [ ] Configure CI/CD (GitHub Actions)
- [ ] Deploy backend (Railway or Render)
- [ ] Set up logging

**Estimated Hours:** 35h

### V1 Deliverables

```
✅ Frontend (React)             Fully connected to backend
✅ Backend API                  Express.js + PostgreSQL
✅ Real API Integration         OpenAI, Anthropic, Google
✅ User Auth                    GitHub OAuth
✅ Project Persistence          Save/load history
✅ Cost Tracking                Per-run, per-user, per-month
✅ Async Execution              Parallel model runs
✅ Deployed Production           Frontend + backend live
✅ Documentation                API docs, user guides
```

### V1 Success Criteria

- [ ] Users can sign up, save projects, get real model results
- [ ] Cost tracking is accurate
- [ ] System handles 100+ concurrent users
- [ ] Uptime >99.5%
- [ ] Page load <2s
- [ ] API response <3s (typical)
- [ ] Feature parity with MVP (no regression)

---

## V2 & Beyond

### V2 Ideas (Post-MVP + V1 feedback)

- **Team features:** Share projects, collaborate on prompts
- **Fine-tuning:** Create custom models
- **Specialized tools:** Image gen (DALL-E), transcription (Whisper), video
- **Advanced routing:** ML-based scoring (instead of rules)
- **Integrations:** Slack, email, webhooks
- **Marketplace:** Sell prompts, share templates
- **Analytics:** Per-task type insights, trends

Decide based on user feedback.

---

## Resources & Estimates

### Team
- **MVP:** 1 full-time engineer, 3 weeks = ~120 hours
- **V1:** 1-2 engineers, 6-10 weeks = ~240-400 hours

### Infrastructure Costs
- **MVP:** $0 (Vercel free tier)
- **V1:** ~$100-200/month (database, hosting, monitoring)

### Third-Party Costs
- **OpenAI:** $10-50/month (development)
- **Anthropic:** $5-20/month
- **Google Gemini:** Free (first month)
- **Database:** $15-30/month (Heroku Postgres or similar)

### Tools Needed
- Git + GitHub (free)
- VS Code (free)
- Vercel (free tier)
- Railway or Render (free tier)
- Postman or Insomnia (testing API)

---

## Risks & Contingencies

### Risk: Features take longer than estimated
**Plan B:** Cut features (prioritize auth + real API integration over persistence)

### Risk: API rate limits hit during testing
**Plan B:** Use smaller request batches, cache responses

### Risk: User feedback says we're solving the wrong problem
**Plan B:** Pivot. Have a backlog of alternative problems to validate.

### Risk: Competitor launches similar product
**Plan B:** Focus on UX and speed. Move faster. Build community.

---

## Success Criteria (Overall)

**By end of V1 (Week 10):**
- [ ] 500+ GitHub stars
- [ ] 100+ active users
- [ ] Users saving projects and comparing models regularly
- [ ] Cost savings demonstrated (30%+ vs. GPT-4 baseline)
- [ ] Featured in 1-2 AI newsletters
- [ ] Codebase is portfolio-worthy
- [ ] Deployment is stable and scalable

**Feel:** This should feel like a real product, not a demo.

---

## Decision Points

**After MVP (End of Week 3):**
- Proceed to V1? Or pivot based on feedback?
- Which 3 advanced features matter most to users?

**After V1 (End of Week 10):**
- Go public (ProductHunt, HN, etc.)?
- Build a team?
- Explore monetization?
- Or pivot to different problem?

---

## Notes for Yourself

- **Don't over-engineer MVP.** Rough is fine. It's a prototype.
- **Ship early, get feedback, iterate.** Guessing is worse than learning.
- **Track time honestly.** If it's taking longer than estimated, say so. Adjust plan.
- **Take breaks.** 3 weeks full-time is intense. Sleep > code.
- **Have fun with it.** This is a portfolio piece. Make it something you're proud of.

---

**Go build it. 🚀**