---
name: aws-quiz
description: Interactive AWS certification practice exam UI — runs practice exams from this repo one question at a time with instant feedback, scoring, and a persistent failed-questions bank for spaced retakes. Use when the user says "exam", "quiz", "practice exam", "retake failed", or asks to practice AWS questions.
---

# AWS Practice Exam UI

Run interactive practice exams from `practice-exam/` in this repo. Act as the UI; the user is the test-taker.

## Sources

- Exams: `practice-exam/practice-exam-<N>.md` (N = 1–23, ~50 questions each)
- Failed-question bank: `practice-exam/failed-questions.md` (personal, never commit — see below)

Question format in exam files: numbered questions, lettered options (A–E), answer inside `<details>` blocks ("Correct Answer: X"). Some questions are multi-select ("Choose two" / "Choose THREE").

## Rules

- NEVER reveal or hint at an answer before the user answers. Read the exam file, track the key internally.
- One question at a time. Show full question text and all options.
- User answers with letters: `c`, or multi-select `a,d` / `dc` (order doesn't matter).
- If a multi-select question gets too few letters, don't score yet — ask for the rest (extra letters may still be added to the first ones).
- After each answer: **Correct/Wrong** + correct letter(s) + 1–3 sentence explanation. Point out the exam-pattern or memory hook when one exists.
- Track running score. Show it briefly after each answer.
- If the user argues an answer, engage honestly — real-world nuance beats the key, but state what the exam wants.
- Never modify exam source files. Never commit.

## Session start

Ask three things (offer defaults):
1. Which exam number (1–23) — or "retake failed"
2. Mode: **practice** (instant feedback per question) or **exam-style** (answer all, score at end)
3. Pace: 1 / 5 / 10 questions per batch

## End of exam

Full report:
- Score X/50 and percent; CCP passing benchmark ≈ 70%
- Table of wrong answers: Q#, topic, pattern
- Patterns-to-drill section for repeated themes
- Append newly failed questions to `practice-exam/failed-questions.md` (format below)

## Failed-questions bank

File `practice-exam/failed-questions.md`. Structure:

```markdown
# Failed Questions — Review Bank

Wrong answers collected from practice exams. Retake periodically: cover the answer, answer all, check at end. Remove a question only after getting it right twice in a row.

Format: `[exam] [date failed] [times failed]`

---

## Exam N — failed YYYY-MM-DD

### K. Short topic name
<full question text>
- <options>

**Answer: X** — <why>

I answered: <what the user picked> — <pattern note>
```

- Append after every exam (and after failed retakes — increment a "times failed" note).
- Retake mode ("retake failed"): quiz the user from the bank, one at a time, instant feedback, score at end. A question answered right is dropped only after **two consecutive correct retakes**.
- Never commit this file. Keep it listed in `.git/info/exclude` so it stays out of `git status`.

## Ending a question

Keep momentum: feedback → updated score → next question, no filler between questions.
