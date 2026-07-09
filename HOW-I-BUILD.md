# How I Build Real Apps With Claude (From a Guy Who Can't Code)

I can't write code from scratch. Not Dart, not Luau, none of it. Two years ago "ship an app" was not a sentence in my vocabulary. Today I have an app live on Google Play and four more projects in the works, all built by a two-member team: me and Claude.

The trick wasn't learning to be a developer. It was learning to run Claude like a tiny dev team that forgets everything overnight.

This is the actual process. Before writing this we went back through every repo I have and pulled out the stuff that shows up in all of them. Nothing here is theory. Every point came from doing it wrong first.

## 1. Every project gets a constitution

Each repo has a `CLAUDE.md` at the root that loads into every Claude session automatically. The rule for that file: keep it short, durable rules only. Everything temporary goes somewhere else. Mine have things like:

- What the project is, in one paragraph, and where the design truth lives
- Who decides what. Straight from one of my docs: *"Anthony directs (feel, fun, priorities); Claude sessions implement."*
- Code laws. No god files, no API keys in the app, tuning values live in config, one supported build path and no hand-built releases
- A doc index so a fresh session knows exactly what to read first

When a session goes sideways I don't argue in chat. I point Claude at the constitution. It's the contract that survives when the conversation doesn't.

## 2. Build a memory system, because chat doesn't have one

The biggest problem with building this way is every session starts with amnesia. Here's what fixes it, and I ended up doing the same thing on every project without planning to:

- **A backlog file.** One list, every open work item, first thing every session reads.
- **A one page roadmap.** Where are we, what's next. Updated in the same commit as the work, because if the status change and the work don't land together, the status lies.
- **Plan docs** for anything big, ordered by most likely active first. Shelved plans stay in the list with a note saying why and what decision they're waiting on.
- **Runbooks** for stuff that fires later. The launch day checklist, the rare admin procedure. You write them when the knowledge is fresh and file them until needed.
- **An archive.** Finished work moves out of the active docs but never gets deleted. Solved problems come back, so the notes stay findable.

You, the human, are the memory and the referee. These files are how one person keeps five projects straight.

## 3. Write down the lesson, not just the fix

When something breaks, the fix goes in the code and the lesson goes in the constitution, with a date. Real example from one of my projects: two Claude sessions were sharing one folder, and a lazy `git commit -a` swept the other session's work into an unrelated commit. The fix took a minute. The lesson (only stage the files you actually edited, read `git status` before every commit) is now law, dated the day we learned it. Hasn't happened since.

Same deal when a locked decision has to change, like a package that won't install or a store rejection. We write down what changed, why, and what forced it. Next session doesn't re-fight a settled battle.

## 4. Run multiple Claudes like a small team

This is the part people don't expect. On my bigger projects there isn't one Claude. There are lanes:

- **Split by machine.** On one app, the Claude on my Windows PC writes and tests code. The Claude on the Mac only builds and uploads to the store, and its instructions literally forbid it from "fixing" source code. They hand off through a build log in the repo, newest entry on top.
- **Split by territory.** On my game, two sessions run at the same time and own different folders. Each one has an "owns" list and a "does NOT touch" list. Shared files get small additive edits only. When they disagree, they bring it to me. They never resolve it by overwriting each other.
- **Sync rules.** Pull before starting any work. Push at every checkpoint. Update the status board in the same commit as the work.

If that sounds like managing a tiny dev team, that's because it is. That's the actual job. Nobody on the team is human except the boss.

## 5. Be the director, and keep the verdicts

The most important sentence in any of my project docs: **"Feel verdicts come only from Anthony's playtests. Never assume a tuning change worked."**

Claude can make a change perfectly and still be wrong about whether it feels right. So the decisions that matter get marked director-signed once I've tested them myself, and locked decisions don't get quietly reopened. My game also has a thesis doc: the one line law the whole project lives or dies on, plus a checklist every new feature idea has to pass before it gets built. Ideas show up mid-session constantly. They go through the filter, not over the roadmap.

Taste rules count too. Mine include "no bottom sheet modals, short info gets a centered dialog and forms get a full page" and "don't stop to ask keep going? between queued tasks." Neither one is technical. That's taste, and it's the part of this whole partnership that's genuinely yours.

## 6. Get a second AI to audit, then close every finding

Before my biggest launch-bound app went out, I ran the codebase through a different AI as an outside auditor. Multiple rounds. Every round produced a numbered list of findings, every finding got fixed and checked off with a reference in the code for the paper trail, then a follow-up spot audit confirmed nothing drifted. Rounds of 80 findings went to zero.

You don't need to read code to run this play. You just have to insist on it, keep the list, and not let anything get waved off.

## 7. You are the QA department. Act like it.

I run every build on a real device and use it like a stranger would. Not "does it compile." Does it survive me tapping fast, rotating the phone, going offline and coming back. I can't read most of the code and it doesn't matter. Saying exactly what's wrong ("the list jumps when I pull to refresh") beats pretending to review code you can't read. For the game it means actual playtests. Me, a controller, and notes.

## 8. Treat it like a business from day one

My repos don't just have code docs. They have unit economics (per-tier margins, monthly usage caps), a pre-launch funding plan (how much API money to float before revenue shows up), store listing docs with every form field pre-written for submission day, and roadmap tables with a "why wait" column, because deciding NOT to build something yet is a decision worth writing down. One app has a subscription feature sitting fully planned and deliberately unbuilt until it hits real user numbers, because a paywall hurts growth more than it helps revenue when you're small. Claude helped me reason through all of it. I made the calls.

## 9. Ship something small first

My first shipped app checks lottery tickets. It was never going to change the world. It was the test: can this partnership take an idea all the way through store review, the listing, signing keys, and release builds? It could. Now every project after it moves faster because that road is mapped. Take your smallest real idea all the way to shipped before you touch the dream project.

## 10. What this doesn't fix

Being honest. Claude does not remove the need to:

- **Make decisions.** It will hand you options forever if you let it. Your project moves at the speed of your decisions.
- **Show up.** Five projects means five sets of docs to keep true. That's the price of being the memory.
- **Care.** The gap between "works" and "worth using" gets closed by you insisting on it, feature by feature.

## The point

I was never going to hand copy thousands of lines of code from tutorials into folders. That path was closed to me, and I'd made peace with my ideas staying imaginary.

Claude didn't make me a developer. It made me the director of a tiny dev team that happens to not be human. That's a different job, and it turns out it's enough to ship.

If you're like me, ideas and no degree, willing to be the referee, the memory, and the QA department, then the wall you think is standing between you and shipping isn't there anymore.

Anthony ([@Corporalv1](https://github.com/Corporalv1))
