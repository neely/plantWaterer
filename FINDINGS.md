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

### Plant data in a JSON file in this repo
- What: The plant list is data/plants.json in this repo. A Pages Function reads and writes it through the GitHub API.
- Why: Ben chose this on 2026-11-24. It matches his other apps. Git history shows every change.
- Cost: Each save (for example, "Watered today") makes a commit on main. Plant commits and code commits mix in one history. If this becomes a problem, move the data to a separate repo.
- Rejected: Cloudflare KV (faster, but the data is not in the repo).

### Web address: plantwaterer.benneely.com (locked)
- What: The site uses plantwaterer.benneely.com.
- Why: Ben chose this on 2026-11-24. It matches the repo name and his other benneely.com apps.
- Rejected: plants.benneely.com.

### Cloudflare Access login, Ben's email only (locked)
- What: Cloudflare Access protects the site. Only Ben's email can sign in, with a one-time code.
- Why: Ben chose this on 2026-11-24. The app needs no password code. Ben's creel app uses the same method (this is from agent memory; check the creel repo if it matters).
- Rejected: A secret key stored in the browser (anyone with the key gets in). Family logins (not needed now; add emails to the Access policy later if wanted).

### Personal repo, small commits
- What: Repo lives at github.com/neely/plantwaterer. Commits use benaneely@gmail.com. Frequent small commits straight to main. Debriefs go in JOURNAL.md.
- Why: Hobby project. Keeps work and personal history separate.
- Rejected: NIST GitLab (not a work project). Batched commits and GitHub-issue journal (Ben chose the simpler defaults).
