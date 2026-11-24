# plantWaterer — Roadmap

Live at **not deployed yet** · Repo: **github.com/neely/plantwaterer**

**Purpose:** Remind me when each plant needs water, based on a per-plant schedule.
**Non-goals:** Not a plant-identification tool. Not a plant-care encyclopedia.

---

## Status
- **Active:** Phase 2 — Plant list page
- **Last updated:** 2026-11-24
- **Next action:** Get Ben's approval of the build plan in the handoff below. Then do build step 1.

---

## Conventions
- Keep README.md in sync with what's actually live.
- Move settled decisions to FINDINGS.md; mark them `(locked)`. Open questions
  stay here, not in FINDINGS.
- Check off phases below as completed. Don't delete finished items. A ticked
  box means you saw the thing work. Tests that pass are not proof on their
  own — name what you observed.
- When a phase finishes: move non-obvious rationale to FINDINGS first, then
  collapse the phase to one line under Completed.

---

## ✓ Completed
- Phase 1 — Kickoff: template set up, purpose set, phases drafted. No app code.

## Phase 2 — Plant list page  ← ACTIVE
Open questions (answer before code):
- [x] Where is the plant data stored? Answer: data/plants.json in this repo. See FINDINGS.
- [x] What web address? Answer: plantwaterer.benneely.com. See FINDINGS.
- [x] How does the page stop strangers from editing my plants? Answer: Cloudflare Access login, Ben's email only. See FINDINGS.

Build:
- [ ] Remove the word "tripwires" from the Files list in AGENTS.md. The Tripwires block was deleted at setup.
- [ ] Verify in current Cloudflare docs: how to stop a Pages rebuild when only data/plants.json changes. Quote the docs.
- [ ] Verify in current Cloudflare docs: how Access treats a link opened from an email (needed for Phase 4). Quote the docs.
- [ ] Define the plant record: name, location (optional), water every N days, last watered date, notes (optional).
- [ ] Page lists all plants. Plants due today or overdue show first.
- [ ] Add, edit, and remove a plant from the page.
- [ ] A "Watered today" button sets the last watered date to today.
- [ ] Save API: functions/api/plants.js reads and writes data/plants.json through the GitHub API. The GitHub token is a Cloudflare secret.
- [ ] Cloudflare setup: Pages project from this repo, plantwaterer.benneely.com, Access policy for Ben's email only, GitHub token secret, no rebuild on data-only changes. Try the Cloudflare connector first. Else give Ben click-by-click steps.
- [ ] Deploy to Cloudflare Pages. Open it on Ben's iPhone and confirm it works.

## Phase 3 — Daily email reminder
- [ ] Choose how to send email. Check how creel sends email and reuse it if it fits. Verify current Cloudflare email limits from the docs before you depend on them.
- [ ] A Cloudflare Worker runs once each morning on a schedule.
- [ ] The Worker reads the plant data and finds plants due today or overdue.
- [ ] If any plants are due, send one email that lists them. If none are due, send nothing.
- [ ] Confirm a real email arrives in Ben's inbox.

## Phase 4 — Mark watered from the email
- [ ] Each plant in the email has a "Watered" link.
- [ ] The link updates the last watered date. It must not work for someone who guesses the address.

## Future / if needed
- Phone pop-up notifications — Ben wants these, but iPhone web notifications need the site added to the Home Screen and can be unreliable. Email comes first.
- Outdoor and farm plants that skip watering after rain — needs a weather source; out of scope until indoor reminders work.
- Plant photos — nice to have; adds storage work.

---

<!-- Optional: when a phase is a clean stopping point, write next session's
     kickoff here so the cold start is exact. -->

## Handoff → next session
Start prompt:
> Read AGENTS.md, PLAN.md, and FINDINGS.md "Decisions". The three Phase 2
> questions are answered. Show Ben the Phase 2 build list in plain words and
> get his approval before you edit files. Then build it in order, with small
> commits. Ask Ben for a few real plants and their watering intervals to use
> as starting data. Explain choices in plain words; Ben is not a trained
> programmer. Watch out: each "Watered today" press makes a git commit.
