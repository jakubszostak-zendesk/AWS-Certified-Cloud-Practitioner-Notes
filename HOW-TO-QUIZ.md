# How to practice with the aws-quiz skill

Interactive AWS certification practice exams, run by Claude Code. Claude acts as the exam UI: shows one question at a time, checks your answers, explains mistakes, and tracks the questions you failed for later retakes.

## Setup (once)

1. Install [Claude Code](https://claude.com/claude-code) if you don't have it.
2. Clone this repo and enter it:

   ```sh
   git clone https://github.com/jakubszostak-zendesk/AWS-Certified-Cloud-Practitioner-Notes.git
   cd AWS-Certified-Cloud-Practitioner-Notes
   ```

3. Start Claude Code **in this directory** — the skill lives in `.claude/skills/aws-quiz/` and loads automatically here.

## Use

In Claude Code, say:

- `exam 5` — start Practice Exam 5 (you'll pick mode: instant feedback vs score-at-end, and pace)
- answer questions with letters: `c`, or multi-select `a,d`
- `retake failed` — get quizzed on questions you previously failed

Your personal progress lives in `practice-exam/failed-questions.md`. It's git-ignored, never committed, never shared — everyone tracks their own.

## Rules the skill follows

- Never reveals answers before you answer
- One question at a time, instant feedback with explanation and exam-pattern hints
- End-of-exam report: score, wrong answers table, patterns to drill
- Failed questions go to the bank; a question drops out only after you answer it right **twice in a row**

Exams: 23 practice exams, ~50 questions each, in `practice-exam/` (content from [kananinirav/AWS-Certified-Cloud-Practitioner-Notes](https://github.com/kananinirav/AWS-Certified-Cloud-Practitioner-Notes)).
