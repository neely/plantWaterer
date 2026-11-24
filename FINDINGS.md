# plantWaterer — Findings

What this project has concluded. Topical, not chronological. Resolved only —
no open items; those stay in PLAN.md.

Both sections are edited in place. If a result contradicts an entry, correct
that entry. The history lives in JOURNAL.md.

---

## Established

Discovered truths. Facts you did not choose.

### Intentional, not bugs
Things that look wrong but are correct. Do not "fix" these.
- No LICENSE.md file — this is a personal project, not a U.S. government work. The NIST license was removed on purpose at setup.
- No reproducibility or tripwire rules in AGENTS.md — this is not a data-analysis project. They were removed on purpose at setup.

### Known permanent limitations
- None yet.

### Dead-ends (do not re-explore)
- None yet.

### Reference
- None yet.

---

## Decisions

Choices made, and why. Mark settled ones `(locked)`.

### Email reminders first (locked)
- What: Reminders go out as a daily email. Phone pop-up notifications come later, if at all.
- Why: Ben chose this on 2026-11-24. Email is reliable and uses the same Cloudflare setup as his other apps. iPhone web notifications need extra setup and can be unreliable.
- Rejected: Phone notifications first (too much for the first version). Checklist page only (no reminder is sent, so it does not solve the problem).

### Stack: plain web page on Cloudflare
- What: Plain HTML, CSS, and JavaScript, with no framework. Hosted on Cloudflare Pages. A Cloudflare Worker on a daily schedule sends the email.
- Why: This matches Ben's other personal apps, so the patterns and accounts already exist.
- Rejected: Native iPhone app (needs an Apple developer account and App Store work). Not locked: Ben accepted it, but he has not reviewed the details.

### Personal repo, small commits
- What: Repo lives at github.com/neely/plantwaterer. Commits use benaneely@gmail.com. Frequent small commits straight to main. Debriefs go in JOURNAL.md.
- Why: Hobby project. Keeps work and personal history separate.
- Rejected: NIST GitLab (not a work project). Batched commits and GitHub-issue journal (Ben chose the simpler defaults).
