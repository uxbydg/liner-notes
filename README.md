# Liner Notes

An AI harness for applying to jobs with Claude Code. The AI does the typing. Every call stays yours.

Job hunting turned into robots screening robots. Liner Notes goes the other way: fewer, truer applications, where every sentence about you traces to proof, and nothing goes out until you click Submit yourself.

Free to use, copy, and change. See [LICENSE](LICENSE).

## The three stops

Every application stops three times, every time:

1. **Go or no go.** After the fit read, you decide whether to apply.
2. **Approve the resume.** After tailoring, you read it before it goes anywhere.
3. **You click Submit.** Never the AI.

## What you need

- **Claude Code**, on a Claude plan (the kit is free; Claude Code needs a paid plan)
- **Claude in Chrome**, for filling in application forms
- **This folder**, for your search
- **Your documents**: resume, LinkedIn saved as a PDF, offer letters, old job descriptions, and certificates

## Set it up

1. Download this folder (the green **Code** button, then **Download ZIP**), unzip it, and put it somewhere you'll keep it, like `~/job-search`.
2. Put your documents in `sources/`.
3. Open a terminal in the folder and start Claude Code: `cd ~/job-search && claude`
4. Paste the prompt from `prompts/01-evidence-file.md`.

That's it. `CLAUDE.md` holds the house rules, and Claude Code reads it at the start of every session.

## The seven tracks

Play them in order. Each one is a prompt you paste into Claude Code.

| Track | What it makes | Have ready |
|---|---|---|
| [01. Your Evidence File](prompts/01-evidence-file.md) | `CLAIMS.md`: everything you've done, each line with its proof | Your documents in `sources/` |
| [02. Your Answers File](prompts/02-answers-file.md) | `answers.md`: the questions every form asks, answered once | Your salary range and where you're willing to work |
| [03. Your Company List](prompts/03-company-list.md) | A daily digest of new openings at the companies and boards you pick. Add or drop one any time in `digest/watchlist.md` | Ten companies you'd be glad to work for |
| [04. Apply to One Role](prompts/04-apply.md) | A fit read, a tailored resume, and the form filled in | One posting link |
| [05. Track It](prompts/05-track-it.md) | `applications.md`, plus a watch on every posting | Nothing. Track 04 adds the row |
| [06. The Dream Role](prompts/06-dream-role.md) (bonus) | One small thing made for one team, and a note asking for input | A role you'd really want, and an evening |
| [07. Interview Prep](prompts/07-interview-prep.md) | A one-page prep sheet per company and per round | The interview invite |

Tracks 04 and 07 also come as skills: type `/apply <link>` or `/prep` in Claude Code, from inside this folder.

## Your Career Record

You don't have to read all these files. After Track 01, type `/career-record`. Claude builds a private page on your computer that shows what it read, where your documents disagree, and the questions it still has. Answer them right on the page, skip any of them, then copy your answers back into Claude Code. Claude saves them to your files and rebuilds the page. It also shows where every application stands.

Salary, your address, and demographic answers never show up on it.

## What's in the folder

```
CLAUDE.md            The house rules, read at the start of every session
sources/             Your documents. Claude reads them; it never edits them
CLAIMS.md            Your evidence file (Track 01 fills it)
answers.md           Your answers file (Track 02 fills it)
applications.md      Every application and where it stands (Tracks 04, 05)
resume/              Your base resume and the phrases you've cut
prompts/             The seven tracks
digest/              Your watchlist and the daily digest (Track 03)
career-record/       Your Career Record page
.claude/skills/      /apply, /prep, and /career-record
```

Each application gets its own folder, like `acme-senior-designer/`, holding the posting, the fit read, the tailored resume, and the prep sheet.

## Four ways AI fails, and the fix for each

- **Making things up.** No source, no sentence: every claim needs a row in `CLAIMS.md`, and phrases you've cut are checked again before every export.
- **Agreeing with itself.** It rates the job from the posting alone before it reads your evidence, so a strong match can't shrink the gaps.
- **Moving too fast.** It checks every posting and form for an AI-use policy first, and it stops three times.
- **Forgetting everything.** When you correct it, the rule goes into `CLAUDE.md` with the reason, so it's asked once.

## Questions

**Does it apply for me?** No. It reads the posting, tailors your resume, and fills in the form, then it stops. It never clicks Submit.

**Does it work with other AI tools?** The prompts and house rules are plain English, so they paste into any AI assistant. Filling in forms and the skills are built and tested on Claude Code only.

**Do I need to know how to code?** No. You talk to it in plain English. Setting up Claude Code happens once.

**Where do my files live?** In this folder on your computer. Nothing goes to an employer until you click Submit.

**What if a company doesn't allow AI?** It checks every posting and every form for an AI-use policy first. If a company asks people not to use AI, it stops and tells you.

## More skills

Five more Claude Code skills, free for any project: [claude-design-skills](https://github.com/uxbydg/claude-design-skills).

---

Designed by [Daniel Glaze](https://danielglaze.com). Written with Claude Code.
