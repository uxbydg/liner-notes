---
name: career-record
description: Build or refresh the Career Record, a private page on this computer that shows what Claude read, where the documents disagree, the questions still open, and where every application stands. Also saves the answers the person copies back from it. Use after Track 01 or 02, when someone says "career record", "/career-record", "update my record", or pastes a block that starts "My Career Record answers".
---

# /career-record: one page, built from the files

The page is `career-record/index.html`. It never changes. Everything it shows comes from
`career-record/record.js`, which you write from the files. The page only reads it, so the files
stay the source of truth.

## Build or refresh

1. Read `sources/`, `CLAIMS.md`, `answers.md`, and `applications.md`.
2. Write `career-record/record.js`, replacing it whole:

```js
window.RECORD = {
  updated: 'Oct 12, 9:14 PM',            // now, in plain words
  documents: [{ file: 'resume.pdf', status: 'Read' }],
  conflicts: [                           // where two documents disagree
    { id: 'c-start-date', k: 'Start date', text: 'Your resume says 2021. Your offer letter says March 2022.', choices: ['March 2022', '2021'] }
  ],
  questions: [                           // claims with no proof yet, and blanks in answers.md
    { id: 'q-budget', text: 'Your 2022 job description says the role managed the budget. Did you?', choices: ['Yes, I did', 'Not really'] }
  ],
  fresh: [                               // new questions from application forms
    { id: 'f-travel', k: "From Acme's form", text: 'Are you open to occasional travel?', choices: ['Yes', 'No'] }
  ],
  evidence: 14,                          // rows in CLAIMS.md
  answers: 18,                           // filled lines in answers.md
  applications: [{ company: 'Acme', role: 'Senior Designer', status: 'Submitted Oct 12', note: 'posting still live' }]
};
```

3. Run `open career-record/index.html` (macOS), `start` (Windows), or `xdg-open` (Linux).
4. Tell the person how many conflicts and questions are open. That's all.

Rules for what goes on the page:
- **Never** salary, home address, government IDs, or demographic answers (gender, race, veteran
  status, disability). Those stay in `answers.md` and get asked when a form needs them.
- One question per item, in plain words, answerable from a phone. Give choices when the answer is
  one of a few; leave `choices` empty when it needs their words.
- Every `id` is stable: the same question keeps the same id across rebuilds, so an answer saved in
  the browser still matches it.
- A job description shows what a role was, not what the person did. Ask; never assume.

## Save the answers

When the person pastes a block that starts `My Career Record answers`:

1. For each line, find the item by its `[id]`.
2. A conflict answer fixes the fact everywhere it appears: `CLAIMS.md`, and a note in the
   "Where my documents disagree" table. Never edit anything in `sources/`.
3. A claim answered yes goes into `CLAIMS.md` with "my own words, <date>" as its proof. A no means it
   stays off every resume.
4. A form answer goes into `answers.md`.
5. `(skipped)` stays open and comes back next time.
6. Rebuild `record.js` without the answered items, and say what changed in two or three lines.
