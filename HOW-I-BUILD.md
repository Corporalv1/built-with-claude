# How I Build: A Non-Dev's Playbook for Shipping Real Apps with Claude

I'm not a developer. I don't have a CS degree, I can't write Dart from scratch, and two years ago "ship an app" was not a sentence in my vocabulary. Today I have an app live on Google Play and four more projects in active development, all built as a two-member team: me and Claude.

This doc is the process that actually works for me, written for the person I was before I started: full of ideas, zero ability to execute them. It's not theory. Every point here came from doing it wrong first.

## 1. Write the vision down BEFORE you open Claude

The single biggest upgrade to my results was writing a `VISION.md` for every project before asking for a single line of code. Mine include:

- **What the app is, in one paragraph.** If I can't write that paragraph, the idea isn't ready.
- **The full original prompt** — everything in my head, dumped. Features, screens, how it should feel.
- **A roadmap** — what's v1, what's later. Claude will happily build everything at once; that's how you get 60% of ten features instead of 100% of three.
- **A quality bar, per feature.** Not "make it good" — actual statements like "scrolling must stay smooth with 4,000+ items on screen" or "this screen has to feel finished, not functional."

When a session goes sideways, I don't argue in chat. I point Claude back at the vision doc. It's the contract we both work from, and it survives between sessions when the conversation doesn't.

## 2. Lock the spec, and write down every deviation

Early on, every session would "helpfully" upgrade packages, restructure folders, or swap one library for another. Each change was individually reasonable and collectively chaos.

Now my specs are **locked**: the architecture, the state management choice, the database, the package versions. Claude doesn't change them casually. When reality forces a deviation (a package that won't resolve, a version conflict), we don't just fix it — we **write the deviation down** in its own doc: what changed, why, and what forced it. Next session, Claude reads that file and doesn't re-fight settled battles.

If you take one thing from this doc, take this: **your job is to be the memory and the referee.** Claude is brilliant in the moment; you own what's true across weeks.

## 3. Develop taste, and enforce it

Claude will produce something *reasonable* by default. Reasonable is not the same as good. Shipping something people enjoy means noticing what you don't like and turning it into a standing rule, not a one-off fix.

Real examples from my rules file:

- **No bottom-sheet modals.** They feel cheap. Short info gets a centered dialog; forms and content get a full page. Every project, every time.
- **Don't stop and ask "keep going?" between tasks.** When we have a queued list, roll through it. Checkpoints are for decisions, not for reassurance.

Neither of those is a technical decision. They're taste. That's the part of this partnership that's genuinely yours — no model supplies it for you.

## 4. You are the QA department. Act like it.

I run every build on a real device and I actually use the app like a stranger would. Not "does it compile" — does it *feel* right, does it survive me tapping fast, rotating, going offline, coming back.

I can't read most of the code. It doesn't matter. I can observe behavior, describe exactly what's wrong ("the list jumps when I pull to refresh, video attached-style detail"), and Claude can take it from there. Precise observation from you beats vague code review you're not qualified to do anyway.

## 5. Ship something small first

My first shipped app is a lottery draw checker. It is not going to change the world. It was never supposed to — it was the test: can this partnership take an idea all the way through Play Store review, store listing, signing keys, release builds, the whole boring gauntlet?

It could. And every project after it moves faster because that gauntlet is now a known road instead of a wall. Pick your smallest real idea and take it all the way to shipped before you start your dream project.

## 6. What this doesn't do

Honesty section. Claude doesn't remove the need to:

- **Make decisions.** It will present options forever if you let it. The project moves at the speed of your decisions.
- **Show up consistently.** Five projects means five sets of context to maintain. The vision docs and deviation logs are what make that possible for one person.
- **Care about the result.** The gap between "works" and "worth using" is closed by you insisting on it, feature by feature.

## The point

I was never going to hand-copy thousands of lines of code from tutorials into folders. That version of the path was closed to me, and I'd made peace with my ideas staying imaginary. This one is open. If you're the same kind of person — ideas, no degree, willing to be the referee and the QA department — the wall you think is there isn't anymore.

— Anthony ([@Corporalv1](https://github.com/Corporalv1))
