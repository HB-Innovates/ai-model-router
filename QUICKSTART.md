# Quick Start

Get up and running in 5 minutes.

## Option 1: No Setup (Browser Only)

**Just open `index.html` in your browser.**

```bash
git clone https://github.com/HB-Innovates/ai-model-router.git
cd ai-model-router
open index.html
```

Or double-click `index.html` in Finder/Explorer.

Works with mock data. No dependencies, no build step.

---

## Option 2: Live Demo

**No installation needed.** Just visit:

```
https://ai-model-router-demo.vercel.app
```

Try the app, see how it works.

---

## Option 3: Local Development (React Setup)

Plan for V1 (coming soon). For now, stick to Option 1.

---

## Typical User Flow

### 1. Enter Your Task

```
Task: "Write a product description for a SaaS tool that helps teams 
manage their AI model spending. Focus on ROI and ease of use."
```

Hit "Analyze Request" → System detects this as "copywriting"

### 2. Answer Clarifying Questions

System asks:
- "Target audience?" → You pick "C-suite"
- "Preferred tone?" → You pick "Professional"

### 3. Review Engineered Prompt

System generates structured prompt with 5 sections:

```
💫 ROLE & EXPERTISE
Expert B2B SaaS copywriter specializing in cost optimization tools

💫 CONTEXT
Product: Cost optimization platform for AI model selection
Target: C-suite executives (CFO, VP Eng)
Key benefit: 30-40% cost savings vs. defaulting to GPT-4

💫 CONSTRAINTS
- Keep it concise (150 words max)
- Focus on ROI and ease of use
- Professional tone, no hype
- Highlight decision speed (not time spent comparing)

💫 OUTPUT FORMAT
Single paragraph product description

💫 QUALITY CRITERIA
- Clarity: Is it obvious what problem this solves?
- Specificity: Does it mention concrete benefits (cost %, time savings)?
- Credibility: Does it feel trustworthy (avoid bold claims)?
```

You can edit any section. "Approve & Find Models" when ready.

### 4. Select Models to Compare

System recommends:

```
#1 🌟 92/100 GPT-4 (OpenAI)
   Best for complex writing, excellent reasoning
   Cost: $0.15  |  Latency: 2.5s

#2 🌟 88/100 Claude 3 Opus (Anthropic)  
   Excellent reasoning, great for nuanced content
   Cost: $0.12  |  Latency: 3.5s  |  Privacy-first

#3 🌟 85/100 Gemini Pro (Google)
   Balanced performance, cost-effective
   Cost: $0.08  |  Latency: 4.0s
```

Select 2-3 models (checkboxes). You pick all three.

### 5. See Results

```
┌────────────────────────────────────────├────────────────────────────────────────├────────────────────────────────────────┐
│ GPT-4                   │ Claude 3 Opus          │ Gemini Pro             │
├────────────────────────────────────────╪────────────────────────────────────────╪────────────────────────────────────────┘
│                          │                        │                        │
│ ModelRouter simplifies    │ ModelRouter simplifies │ ModelRouter helps...   │
│ AI model selection...     │ AI model selection...  │                        │
│                          │                        │                        │
├────────────────────────────────────────╪────────────────────────────────────────╪────────────────────────────────────────┘
│ ⏱️ 2.5s | 💰 $0.15 | ⭐ 9.2 │ ⏱️ 3.5s | 💰 $0.12 | ⭐ 8.9 │ ⏱️ 4.0s | 💰 $0.08 │
└────────────────────────────────────────┴────────────────────────────────────────┴────────────────────────────────────────┘

💰 TOTAL COST: $0.35  |  📌 422 tokens  |  ⏱️ Avg latency: 3.3s
```

**Decision:** Claude 3 Opus is $0.03 cheaper than GPT-4 with nearly identical quality (8.9 vs 9.2). In production, you'd choose Claude 3.

---

## What Happens Next

### Option A: Refine Prompt

Click "Refine Prompt" → Go back to edit engineered prompt → Re-run models with new version

Example: Change "150 words max" to "50 words max" and re-run. See which model still handles brevity well.

### Option B: Try Different Models

Click "Try Different Models" → Swap selections (e.g., try Llama instead of GPT-4) → Re-run

### Option C: New Request

Click "New Request" → Start fresh

---

## To Use Real API Keys (V1+)

When real API integration is available:

```bash
# Create .env file
cat > .env.local << EOF
VITE_OPENAI_API_KEY=sk-your-key-here
VITE_ANTHROPIC_API_KEY=sk-ant-your-key-here
VITE_GOOGLE_API_KEY=AIza-your-key-here
EOF

# Start app
npm run dev
```

Now requests run against real models (not mocks).

---

## Troubleshooting

**Q: App doesn't load**
A: Make sure you're opening `index.html` directly in browser (not via `file://` if it requires a server)

**Q: Something looks broken on mobile**
A: Try in Chrome DevTools mobile view (F12 → Toggle Device Toolbar)

**Q: Can I modify the prompts?**
A: Yes. Click "Approve & Find Models" screen, edit any of the 5 sections.

**Q: Why are results the same every time?**
A: MVP uses mock data. When V1 ships with real APIs, results will vary.

**Q: How do I contribute?**
A: Fork repo, make changes, open PR. See [CONTRIBUTING.md](.github/CONTRIBUTING.md)

---

## Next Steps

1. **Try the MVP:** Open `index.html`, test all 5 steps
2. **Read the spec:** [PRODUCT_SPEC.md](PRODUCT_SPEC.md) explains the vision
3. **Check the roadmap:** [IMPLEMENTATION_PLAN.md](IMPLEMENTATION_PLAN.md) shows what's next
4. **Deploy to Vercel:** Fork repo, deploy in 1 click. Get a live URL.
5. **Share:** Send link to friends. Ask for feedback.

---

**Questions?** Open an issue or start a discussion in GitHub.

Happy routing! 🚀