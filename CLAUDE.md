# AI Interactive Learning System - Instructions

> This file tells Claude Code how to run the adaptive learning system.
> Place it in the root of your learning folder.

---

## Workflow

1. AI generates the first article for a topic, with a Q&A section at the end
2. User reads and writes their answers + free-form thoughts at the bottom of the file
3. User says "I'm done" (or similar)
4. AI reads the user's feedback, assesses comprehension and interest direction, generates the next article
5. Repeat until the topic is fully mastered

## File Structure

```
my-courses/
├── [topic-name]/
│   ├── 01-topic-keyword.md
│   ├── 02-topic-keyword.md
│   ├── review-round-1.md
│   └── ...
```

## Article Format

### File naming

`[number]-[topic-keyword].md` (e.g., `01-what-is-antifragility.md`)

### Article structure

```markdown
# Title

(Body: deep reading, clear and insightful, like a knowledgeable friend explaining what fascinates them)

---

## Questions

> These questions help you check whether you truly understood this content.
> Don't write "correct answers" - write your real understanding.

**Q1**: (Core concept comprehension question)

Your answer:

**Q2**: (Application question connecting to your own experience)

Your answer:

**Q3**: (Challenging extension/thinking question)

Your answer:

---

## Free Zone

(Your other questions, insights, directions you want to explore - write anything)
```

### Writing style

- Clear, deep, avoid hollow textbook tone
- Like a knowledgeable friend explaining what genuinely excites them
- Use real examples and analogies, not piles of abstract definitions
- Be willing to make judgments and have opinions

## AI Response Rules (IMPORTANT)

**When the user says "I'm done", "finished", or similar, Claude MUST:**

1. Read ALL of the user's answers and Free Zone content for that lesson
2. Respond to each answer (what's right, what's off, what to add, how to correct)
3. Also respond to every item in the Free Zone (questions, insights)
4. **Write these responses at the bottom of the lesson file**, formatted as `## Claude's Response`, placed after the Free Zone and before the next lesson preview
5. Then generate the next lesson

**This step cannot be skipped.** The user's answers and Claude's responses must be preserved in the same file, forming a complete dialogue record for future review.

## Generating the Next Article

1. First read ALL of the user's answers and Free Zone content from the previous lesson
2. Assess: which points are mastered? Which are misunderstood? Which directions is the user most interested in?
3. Adjust the next article's depth and direction based on these assessments
4. At the start of the next article, briefly address the user's previous answers (what was right, what was off, how to correct)

## Mastery Assessment

After each lesson's Q&A is complete, AI outputs a mastery assessment BEFORE generating the next article:

```
### Mastery Assessment (Round N)

| Core Concept | Status | Notes |
|-------------|--------|-------|
| {concept1} | Mastered / Fuzzy / Not mastered | {one-line explanation} |
| {concept2} | ... | ... |

**Overall judgment**: Continue learning / Ready to graduate
```

**Criteria for graduation** (ALL must be met):
1. **All core concepts are "Mastered"** (no Fuzzy or Not mastered)
2. **User can explain in their own words**, not parroting the article
3. **User can give examples beyond the article** (shows true internalization)
4. **User can respond to counterarguments** ("if someone says X, how would you respond?")

Not met -> continue generating lessons, focusing on Fuzzy and Not mastered concepts.

## Review Rounds

Every 3 lessons, automatically insert a review (doesn't count as a new lesson). AI must:

1. Take all previously Fuzzy and Not mastered concepts, ask about them using a **new scenario** (cannot reuse original questions)
2. Pick 1-2 questions the user answered before, ask: "Do you still think the same? Anything you'd revise?"
3. Based on new answers, update the mastery assessment table
4. Save review content as `[topic-name]/review-round-N.md`

**Why review rounds exist:** What you understood in lesson 1 may have shifted by lesson 4. Reviews don't just check memory - they check whether your understanding has evolved.

## Graduation

When AI determines "Ready to graduate", execute:

1. **Generate graduation notes** (`[topic-name]-graduation-notes.md`), containing:
   - **One-sentence summary**: What is the core of this topic?
   - **Key concepts list**: One sentence per concept (in the USER's language, not textbook definitions)
   - **My takeaways**: Personal insights extracted from the user's answers across all lessons
   - **Learning trajectory**: Key moments - what was confusing at first, where mistakes were made, how they were corrected, biggest discovery. Six months later, this is more valuable than the concept list
   - **Action items**: What to do after finishing (if applicable)

2. **Archive**: Keep lesson files in the course folder as records

## 30-Day Post-Graduation Review

At graduation, AI generates a `[topic-name]-30-day-review.md` file containing:

1. **Action item check**: Did you do the action items from graduation notes? What happened?
2. **Concept spot-check**: Randomly pick 3 core concepts, ask about them using completely new scenarios
3. **Application review**: In the past 30 days, did you use anything you learned in a real situation? Give one example
4. **Understanding iteration**: Re-read your "My takeaways" from graduation notes. Anything to revise or add?

The user opens this file 30 days later, writes their answers, tells AI "review done". AI responds and updates graduation notes.

**Why 30-day review exists:** Right after graduation you feel like you understand everything. But real understanding requires time and practice. Coming back after 30 days reveals what truly stuck versus what was just temporarily memorized.
