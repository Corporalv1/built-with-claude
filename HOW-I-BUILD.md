# How I Build: A Non-Dev's Playbook for Shipping Real Apps with Claude

I'm not a developer. I don't have a CS degree, I can't write Dart or Luau from scratch, and two years ago "ship an app" was not a sentence in my vocabulary. Today I have an app live on Google Play and four more projects in active development — a two-member team: me and Claude.

This doc is the process that actually works for me, written for the person I was before I started: full of ideas, zero ability to execute them. It's not theory — before writing this version, we went back through every one of my project repos and pulled out the patterns that all of them independently converged on. Every point here came from doing it wrong first.

## 1. Every project gets a constitution

Each repo has a `CLAUDE.md` at the root that loads into every Claude session automatically. The rule for that file: **keep it short, durable rules only**. Transient stuff goes elsewhere. Mine contain things like:

- What the project is, in a paragraph, and where the design truth lives
- Who decides what: *"Anthony directs (feel, fun, priorities); Claude sessions implement."*
- Code laws — no god files, no API keys in the client, config-driven tuning values, one supported build path
- A doc index so a fresh session knows exactly what to read first

When a session goes sideways, I don't argue in chat. I point Claude at the constitution. It's the contract that survives when the conversation doesn't.

## 2. Build a memory system, because chat doesn't have one

The single biggest problem with AI-assisted building is that every session starts with amnesia. My projects converged on the same cure independently:

- **A backlog file** — single source of truth for every open work item. First thing every session reads.
- **A one-page roadmap** — "where are we, what's next," updated *in the same commit* as the work. If the status change and the work don't land together, the status lies.
- **Plan docs** for anything big, ordered by "most likely active" → "shelved," with shelved ones marked *why* and what decision they're gated on.
- **Runbooks** for things that will fire later — the checklist for launch day, the procedure for a rare admin task — written when the knowledge is fresh, filed until needed.
- **An archive** — completed campaigns move out of the active docs but never get deleted. Deep-dive notes on solved problems stay findable, because solved problems come back.

You, the human, are the memory and the referee. These files are how one person keeps five projects coherent.

## 3. Write down the lessons, not just the fixes

When something goes wrong, the fix goes in the code and the *lesson* goes in the constitution — dated. Real entry from one of my projects: two sessions sharing one working tree, and a careless `git commit -a` swept the other session's staged work into an unrelated commit. The fix took a minute. The lesson — *stage only the files you edited, read `git status` before every commit* — is now law, with the date we learned it. It has never happened again.

Same pattern for forced deviations: when a locked decision has to change (a package that won't resolve, a store rejection), we record what changed, why, and what forced it. Next session doesn't re-fight settled battles.

## 4. Run multiple Claudes like a small team

This is the part that surprises people. On my bigger projects there isn't one Claude — there are lanes:

- **Split by machine:** on one app, Windows Claude writes and tests code; Mac Claude *only* builds and uploads to the store, and is explicitly forbidden from "fixing" source. They hand off through a build log in the repo — newest entry on top, one entry per meaningful attempt.
- **Split by territory:** on my game, two parallel sessions own different folders. Each has an "owns" list and a "does NOT touch" list. Shared files get small additive edits only. Disagreements between sessions escalate to me — they never resolve them by overwriting each other.
- **Sync protocol:** pull before starting any work, push at every checkpoint, update the status board in the same commit as the work.

If that sounds like managing a tiny dev team — it is. That's the actual job. Nobody on the team happens to be human except the director.

## 5. Be the director, and keep the verdicts

The most important sentence in any of my project docs: **"Feel verdicts come only from Anthony's playtests — never assume a tuning change worked."**

Claude can implement a change perfectly and still be wrong about whether it *feels* right. So decisions that matter get marked **director-signed** once I've personally tested them, and locked decisions don't get silently reopened. My game project also has a thesis doc — the one-line law the whole project lives or dies by, plus a standing checklist every new feature has to pass before it gets built. When a feature idea shows up mid-session (they always do), it runs through the filter instead of running over the roadmap.

Taste rules count too. Mine include "no bottom-sheet modals — short info gets a centered dialog, forms get a full page" and "don't stop to ask *keep going?* between queued tasks." Neither is technical. They're taste. That's the part of this partnership that's genuinely yours.

## 6. Audit with a second AI, then close every finding

Before my biggest launch-bound app went out, I ran the codebase through a *different* AI as an external auditor — multiple rounds. Each round produced a numbered findings list; each finding got fixed, checked off, and referenced in code comments for the audit trail; then a follow-up spot audit verified zero drift. Rounds of 80 findings went to zero.

You don't have to read the code to run this play. You just have to insist on it, keep the list, and not let anything get waved off.

## 7. You are the QA department. Act like it.

I run every build on a real device and use it like a stranger would. Not "does it compile" — does it survive me tapping fast, rotating, going offline, coming back. I can't read most of the code and it doesn't matter: precise observation ("the list jumps when I pull to refresh") beats vague code review you're not qualified to do anyway. For the game, that means actual playtests — me, a controller, and notes.

## 8. Treat it like a business from day one

The repos don't just have code docs. They have unit-economics models (per-tier margin, monthly caps), pre-launch funding plans (how much API spend to float before revenue), store-listing docs with every form field pre-written for submission day, and roadmap tables with a "why wait" column — because *deciding not to build something yet* is a decision worth recording. A subscription feature sits explicitly gated on hitting real user numbers first, because a paywall hurts growth more than it helps revenue at small scale. Claude helped me reason through all of it; I made the calls.

## 9. Ship something small first

My first shipped app is a lottery draw checker. It was never going to change the world — it was the test: can this partnership take an idea all the way through store review, listing, signing keys, and release builds? It could. Every project after it moves faster because that gauntlet is now a known road instead of a wall. Take your smallest real idea all the way to shipped before you start the dream project.

## 10. What this doesn't do

Honesty section. Claude doesn't remove the need to:

- **Make decisions.** It will present options forever if you let it. The project moves at the speed of your decisions.
- **Show up consistently.** Five projects means five doc systems to keep true. That's the price of being the memory.
- **Care about the result.** The gap between "works" and "worth using" is closed by you insisting on it, feature by feature.

## The point

I was never going to hand-copy thousands of lines of code from tutorials into folders. That path was closed to me, and I'd made peace with my ideas staying imaginary. This one is open. If you're the same kind of person — ideas, no degree, willing to be the director, the memory, and the QA department — the wall you think is there isn't anymore.

— Anthony ([@Corporalv1](https://github.com/Corporalv1))
