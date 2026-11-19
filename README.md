# AI Interactive Learning System

> An adaptive learning system powered by Claude Code or Codex, plus Obsidian. AI generates deep articles, you answer questions, AI assesses your mastery and adapts the next lesson to your understanding. Repeat until graduation.

**Cost: whatever you already pay for Claude Code (Claude Pro or Max) or Codex (a ChatGPT plan)**
**Tools: Claude Code or Codex, plus Obsidian (or any markdown editor)**

---

## How It Works

```
1. AI generates a deep article with Q&A section
         |
2. You read and write your answers
         |
3. You say "I'm done"
         |
4. AI evaluates mastery per concept: Mastered / Fuzzy / Not mastered
         |
5. AI generates next lesson, adapting to YOUR understanding
         |
    (loop until all concepts are mastered)
         |
6. Graduation: AI generates summary notes in YOUR words
```

The key difference from textbooks or courses: **the system doesn't follow chapters in order. It follows YOUR comprehension.** If you nail concept A but struggle with concept B, the next lesson focuses on B, not C.

---

## Quick Start (3 minutes)

**Prerequisites**: either one of these, whichever you already use.

- [Claude Code](https://docs.claude.com/en/docs/claude-code) (Claude Pro or Max)
- Codex (a ChatGPT plan): `npm install -g @openai/codex` (or `brew install codex`), then run `codex login` once

```bash
git clone https://github.com/siyaovo/ai-interactive-learning.git
cd ai-interactive-learning
claude      # or: codex
```

Prefer a desktop app or editor? Open the `ai-interactive-learning` folder in the Claude desktop app (Code) or the Codex app / IDE extension instead. The first time, it may ask whether to trust the folder; say yes.

Then type:

```
I want to learn [topic]. Teach me.
```

That's it. The rules live in `AGENTS.md`: Codex reads it automatically, and Claude Code loads it through `CLAUDE.md`. You don't need to explain anything; it starts generating your first lesson.

### What happens next

1. The AI generates a deep article in `my-courses/[topic]/01-....md`
2. Open the file, read it, answer the 3 questions at the bottom
3. Come back to the AI and say **"I'm done"**
4. It evaluates your answers, writes its feedback into the lesson file, and generates the next lesson
5. Repeat until you graduate

### See an example lesson

Check [`example/causal-inference/01-correlation-is-not-causation.md`](example/causal-inference/01-correlation-is-not-causation.md) to see what an AI-generated lesson looks like.

---

## File Structure

```
ai-interactive-learning/
├── README.md                <- You're reading this
├── AGENTS.md                <- The rules (Codex reads this automatically)
├── CLAUDE.md                <- Imports AGENTS.md for Claude Code
├── system-flow.html         <- Visual workflow diagram (open in browser)
├── example/                 <- See what a real lesson looks like
│   └── causal-inference/
│       └── 01-correlation-is-not-causation.md   <- AI-generated lesson
└── my-courses/              <- Your courses go here
    └── .gitkeep
```

---

## Article Format

Every lesson follows this structure:

```markdown
# Title

(Deep, engaging content - like a knowledgeable friend explaining what fascinates them)

---

## Questions

> These questions check if you truly understood the content.
> Write your real understanding, not "correct answers."

**Q1**: (Core concept comprehension)

Your answer:

**Q2**: (Apply to your own experience)

Your answer:

**Q3**: (Challenging extension question)

Your answer:

---

## Free Zone

(Your extra questions, insights, directions you want to explore - write anything)
```

---

## Mastery Assessment

After each lesson, the AI outputs:

```
### Mastery Assessment (Round N)

| Core Concept | Status | Notes |
|-------------|--------|-------|
| Concept 1   | Mastered / Fuzzy / Not mastered | one-line explanation |
| Concept 2   | ...    | ...   |

**Overall**: Continue learning / Ready to graduate
```

**Graduation criteria** (ALL must be met):
1. All core concepts are "Mastered"
2. You can explain in your own words (not parroting the article)
3. You can give examples beyond what the article covered
4. You can respond to counterarguments

---

## Built-in Safety Nets

- **Review rounds**: Every 3 lessons, the AI revisits fuzzy concepts with new scenarios
- **30-day review card**: Generated at graduation, prompts you to check retention a month later
- **Complete dialogue preserved**: Your answers + the AI's feedback are saved in each lesson file

---

## Writing Style

Articles are NOT textbook summaries. They are:
- Clear and deep, avoiding hollow academic tone
- Like a knowledgeable friend explaining what genuinely excites them
- Full of real examples and analogies, not abstract definitions
- Opinionated - willing to make judgments

---

## Why This Works

Traditional courses push content at you in a fixed order. This system:
- **Adapts to you**: Weak areas get more attention, strong areas move fast
- **Forces active recall**: You write answers, not passively consume
- **Preserves the journey**: Your mistakes and corrections are the most valuable part
- **Graduates you properly**: Not when you finish the material, but when you truly understand it

---

## License

MIT

---

Built with Claude Code. Designed by [@siyaovo](https://github.com/siyaovo).
