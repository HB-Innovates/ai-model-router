# 🚀 Quick Start Guide

## 5-Minute Setup

### Option 1: Try the Live Demo (No Installation)

🜐 **[Visit ai-model-router-demo.vercel.app](https://ai-model-router-demo.vercel.app)**

1. Click the link above
2. Enter a task description (e.g., "Write a product description for a SaaS expense tracker")
3. Select or auto-detect the task type
4. Answer 1-3 clarifying questions
5. Review the engineered prompt
6. Select 2-3 models to compare
7. See side-by-side results with cost/quality/speed metrics

**Tip:** The demo uses mock data. To use real models, add your own API keys.

---

### Option 2: Run Locally

#### 1. Clone the Repository

```bash
git clone https://github.com/HB-Innovates/ai-model-router.git
cd ai-model-router
```

#### 2. Install Dependencies

```bash
npm install
```

#### 3. Set Up Environment Variables (Optional)

To use real AI models, create a `.env.local` file:

```bash
cat > .env.local << EOF
# OpenAI
VITE_OPENAI_API_KEY=sk-your-key-here

# Anthropic
VITE_ANTHROPIC_API_KEY=sk-ant-your-key-here

# Google
VITE_GOOGLE_API_KEY=AIza-your-key-here

# Backend URL (optional, defaults to localhost:3000)
VITE_API_URL=http://localhost:3000
EOF
```

**Important:** Never commit `.env.local` to version control. Use `.env.example` as template.

#### 4. Start Development Server

```bash
npm run dev
```

Open [http://localhost:5173](http://localhost:5173) in your browser.

#### 5. (Optional) Start Backend Server

If you want to use the full backend with database persistence:

```bash
cd backend
npm install

# Create database
createdb ai_model_router_dev

# Run migrations
npm run migrate:dev

# Start server
npm run dev  # Runs on http://localhost:3000
```

---

## 📋 Typical User Flow

### Step 1: Request Input
```
🧠 User: "I need to write a compelling product description for a SaaS tool..."
🧦 System: Task category detected as 'copywriting' (92% confidence)
```

### Step 2: Clarifying Questions (if needed)
```
Question 1: Who is your target audience?
  Options: [C-level] [Product managers] [Engineers] [Other]
  User selects: Product managers

Question 2: What tone do you want?
  Options: [Professional] [Friendly & casual] [Creative & bold] [Technical]
  User selects: Friendly & casual
```

### Step 3: Engineered Prompt
```
Role: You are an expert copywriter specializing in friendly, persuasive writing for product managers.

Context: You are writing a product description for ModelRouter, a SaaS tool that helps teams manage AI model costs.

Constraints:
  - Word count: 100-150 words
  - Tone: Friendly & casual
  - Must include: Value proposition, call-to-action
  - Must avoid: Technical jargon

Output Format: Markdown

Quality Rubric:
  ✓ Clarity: Easy to understand for non-experts
  ✓ Persuasion: Creates desire or sense of FOMO
  ✓ Brand voice: Matches intended tone
  ✓ CTA: Clear call-to-action
  ✓ Length: Between 100-150 words
```

### Step 4: Model Recommendations
```
Rank  Model              Provider     Score  Cost      Speed    Reason
─────────────────────────────────────────────────
1     GPT-4             OpenAI       92     $0.15    2.5s    Excellent writing quality
2     Claude 3 Opus     Anthropic    88     $0.12    3.5s    Privacy-first, no input training
3     Gemini Pro        Google       85     $0.08    4.0s    Cost-effective alternative
4     Claude 3 Sonnet   Anthropic    82     $0.10    3.0s    Balanced performance
```

**User selects:** GPT-4, Claude 3 Opus, Gemini Pro

### Step 5: Run Models (Parallel Execution)
```
Running 3 models in parallel...

[=======================] GPT-4 completed (95 tokens, 2.4s) ✓
[=======================] Claude 3 Opus completed (88 tokens, 3.2s) ✓
[=======================] Gemini Pro completed (92 tokens, 3.9s) ✓
```

### Step 6: Results Comparison
```
┌──────────────────────────────────────┐
│ Model             Cost    Speed   Quality  Best For
├──────────────────────────────────────┤
│ GPT-4            $0.15  2.5s    9.2/10   🤟 Best overall
│ Claude 3 Opus    $0.12  3.5s    8.9/10   🔐 Privacy-first
│ Gemini Pro       $0.08  4.0s    8.5/10   💰 Budget option
└──────────────────────────────────────┘

Total Cost: $0.35
Total Tokens: 275
Recommendation: Use GPT-4 for best quality, or Gemini Pro to save $0.07/query

Consolidated Answer Option: Merge best parts from all models ✅
```

### Step 7: Iterate or Export
```
Options:
  📝 Refine Prompt   → Go back, tweak clarifications
  🔄 Try Different Models → Swap models and re-run
  💳 Lock Models    → Save this combo for similar tasks
  🏠 New Request    → Start fresh
  💾 Save Project   → Store results for later (V1+)
```

---

## 🐉 Docker Setup

### Run Everything with Docker Compose

```bash
cd docker
docker-compose up -d
```

This starts:
- **Frontend**: http://localhost:3000
- **Backend API**: http://localhost:5000
- **PostgreSQL**: localhost:5432
- **Redis**: localhost:6379

---

## 🚫 Troubleshooting

### Issue: "API key invalid"

**Solution:**
1. Check your `.env.local` file has correct key format
2. Verify key has required permissions
3. Test key on provider's website
4. Try demo mode (without real keys) first

### Issue: "Models not running"

**Solution:**
1. Check browser console for errors (F12)
2. Verify API keys are provided or use demo mode
3. Check internet connection
4. Try one model at a time

### Issue: "Slow responses"

**Solution:**
1. Check network latency
2. Some models are slower (Claude 3, Gemini) — expected
3. Try fewer models to speed up execution
4. Use cheaper models for speed (Gemini Pro)

### Issue: "Port already in use"

**Solution:**
```bash
# Kill process using port 5173
lsof -ti:5173 | xargs kill -9

# Or use different port
npm run dev -- --port 3456
```

---

## 🎉 Next Steps

1. **Explore features**: Try different task types and models
2. **Add your API keys**: Enable real model execution
3. **Check docs**: Read [PRODUCT_SPEC.md](PRODUCT_SPEC.md) for full features
4. **Deploy**: Follow [DEPLOYMENT.md](DEPLOYMENT.md) for cloud setup
5. **Contribute**: See [CONTRIBUTING.md](.github/CONTRIBUTING.md) to help improve

---

## 🚧 Common Questions

### Q: Is this free?

**A:** The app is free (open source, MIT licensed). Costs come from AI model providers:
- Use your own API keys (pay providers directly)
- Or try demo mode (mock results, no cost)

### Q: Which models does it support?

**A:** MVP supports:
- ✅ OpenAI (GPT-4, GPT-3.5-turbo)
- ✅ Anthropic (Claude 3 Opus, Sonnet, Haiku)
- ✅ Google (Gemini Pro)

V1 adds:
- Ollama (local, private)
- DALL-E, Whisper (image/audio specialists)

### Q: Can I use it offline?

**A:** Yes! Use Ollama for fully local inference (no API keys needed). See [DEPLOYMENT.md](DEPLOYMENT.md).

### Q: Is my data private?

**A:** By default:
- Prompts sent to model providers (follow their privacy policies)
- Results stored locally in your browser
- Backend only stores if you sign up (optional)

Use "Do not store" mode or local Ollama for maximum privacy.

### Q: How do I report bugs?

**A:** Open an issue: https://github.com/HB-Innovates/ai-model-router/issues

---

**Happy routing! 🦀**

