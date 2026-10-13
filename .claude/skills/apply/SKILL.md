---
name: apply
description: Apply to one job posting with three stops. Pulls the posting, checks it for an AI-use policy, writes a fit read against CLAIMS.md, tailors the top third of the base resume, drafts any short answers, exports the PDF, and fills the form in Chrome, stopping before Submit. Use when someone pastes a job link, says "apply to this", "/apply", or asks whether they should apply somewhere.
---

# /apply: one posting, three stops

Read `CLAUDE.md` first. The house rules there win over anything here.

**Three stops, never skipped, not even in auto mode:** after the fit read (go or no go), after
tailoring (approve the resume and answers), and before Submit (the person clicks it). **Never
click Submit, Apply, or Send on an application.** A sent application can't be taken back.

## 0. Intake

- One posting at a time. This is not a batch tool.
- Check `applications.md` for the company. If there's an earlier application there, say so first:
  which role, when, and what went out. Two applications to one company must not contradict each other.
- Make a folder for it: `<company>-<role>/` in kebab-case.

## 1. Pull the posting

Save the posting text as `<folder>/posting.md` with today's date. Postings get edited and taken
down, and an interview weeks later needs the original.

Most careers pages wrap a job board with a public API. Try it first; it often shows the pay range
and the form's questions:

| Job board | URL looks like | API |
|---|---|---|
| Ashby | `jobs.ashbyhq.com/<org>/<id>` | `https://api.ashbyhq.com/posting-api/job-board/<org>?includeCompensation=true` |
| Greenhouse | `boards.greenhouse.io/<token>/jobs/<id>` | `https://boards-api.greenhouse.io/v1/boards/<token>/jobs/<id>?questions=true` |
| Lever | `jobs.lever.co/<company>/<id>` | `https://api.lever.co/v0/postings/<company>/<id>` |

Anything else: read the page in Chrome. If the branded page and the job board disagree, the job
board is the truth, and say so.

**AI-use policy, every posting and every form.** Search the posting and the form for rules about
candidates using AI (`AI`, `generative`, `GenAI`, `AI-generated`, `your own work`). Ignore lines
about the company using AI to screen. Write one line at the top of `notes.md`:
`AI policy: none | <their words, quoted>`. Then:
- **They ban AI in the application:** say so first at Stop 1, and recommend skipping.
- **They want your own words for written answers:** the person writes those answers; you fix
  spelling and facts only. Filling fields and reordering their own sentences is fine.
- **Interviews only:** apply normally, and note it for /prep.

## 2. The fit read, then Stop 1

Write `<folder>/notes.md`:

1. **The basics:** link, location and on-site rule, pay range (or "not posted").
2. **What they ask for**, in their words.
3. **The form:** every field, which are required, any written questions word for word.
4. **The fit read, in two passes, in this order:**
   - **Pass 1, the posting alone, before opening `CLAIMS.md`:** rate each requirement `critical`
     (their must-haves, the title, a daily duty), `high`, `meaningful`, or `preferred`. Rate from
     their words, never from what you know the person has.
   - **Pass 2, the evidence:** match each requirement to a row in `CLAIMS.md`. Name the row, not an
     adjective. **Never change a pass-1 rating here.** Rating after matching makes the gaps look
     smaller than they are.
5. **Gaps, named plainly.** For each `critical` or `high` requirement only partly met: the interview
   question it will trigger, and an honest answer from a `CLAIMS.md` row. If no row answers it,
   write "no answer: name the gap."
6. **Verdict:** apply or skip, in one sentence with the reason.

Add a row to `applications.md` with status `fit-read`.

**Stop 1.** Give the verdict, the two biggest gaps, and any risks, and ask: go or no go? If it's a
skip, set `skipped` and stop.

## 3. Tailor, then Stop 2

Copy `resume/base-resume.md` to `<folder>/resume-<company>.md`.

**Change the top third only:** the title line, the summary, and which achievements come first.
Everything from `## Experience` down stays exactly the same. Check with a diff.

**Tailoring changes emphasis and order, never claims.** Every sentence must already be in the base
resume or backed by a row in `CLAIMS.md`. If the posting tempts a claim with no proof, that's a gap
for the fit read, not a sentence for the resume.

Then check for phrases already cut. Any hit stops the export until it's fixed:

```
grep -n -i -F -f resume/cut-phrases.txt <folder>/resume-<company>.md
```

Export a PDF (ask before installing anything; Chrome can print an HTML version to PDF). Two pages
at most: cut achievements, never the type size. Read the PDF back before showing it. Name it
`<First>-<Last>-Resume-<Company>.pdf`.

**Written answers:** draft each into `<folder>/<slug>-draft.md` from `CLAIMS.md` and anything the
person has said. **Never invent their reasons.** If "why this company" has no source, ask them one
question instead.

**Stop 2.** Show the diff, the page count, and the drafts. Status `tailoring`. Wait for approval.

## 4. Fill the form, then Stop 3

Open the application in a new Chrome tab.

- **Logins, new accounts, CAPTCHAs, and verification codes are the person's.** Stop and say what
  the page wants. Never create an account or set a password.
- **Never automate LinkedIn Easy Apply.** LinkedIn prohibits it. Find the company's own form instead.
- Upload the tailored PDF. If the form autofills from it, re-check every autofilled field.
- Fill every other field from `answers.md`. **A blank there, or a question it doesn't cover, means
  stop and ask.** Never guess work authorization, sponsorship, salary, or voluntary questions.
  Add the answer to `answers.md` so it's asked once.
- Paste written answers only from approved files.
- Don't tick marketing, text, or talent-community opt-ins unless `answers.md` says yes.

When every field is filled, scroll the form top to bottom and list anything left empty and why.

**Stop 3.** Status `ready`. Say: "It's filled in and waiting in the open tab. Review it and click
Submit yourself." Then stop. Don't touch the tab unless asked. If a new page appears after they say
"submit," ask again.

## 5. After they submit

- Status `submitted` in `applications.md`, with the resume file that went out.
- Keep the exact PDF in the folder. Note anything unusual the form asked; it predicts the interview.
- A new fact with proof goes into `CLAIMS.md`. A new answer goes into `answers.md`.
