# Contribute to projects you don't own

Most of Kenaptic assumes you are improving your own documentation. Sometimes the content that
would help your readers most sits in a project you don't control — an open-source tool you build
on, a partner's documentation, a community-maintained handbook.

**Upstream mode** lets Kenaptic propose cross-links into those repositories the way any other
contributor would: as a pull request, from a fork, that a maintainer reviews and decides on.

Turn it on in **Settings → Contribution**.

---

## What changes when upstream mode is on

Every assumption that is reasonable for your own estate is wrong for someone else's, so upstream
mode changes the rules rather than the settings:

| | Your own docs | Upstream |
|---|---|---|
| How a change arrives | A branch pushed to your repository | A pull request from a fork |
| Who decides | Your team | The project's maintainers |
| Link tracking | Optional | **Impossible** — not merely switched off |
| Auto-publish | Available, not recommended | **Impossible** — not merely switched off |
| Sign-off | Not required | A DCO sign-off on every commit |
| How much at once | Your call | Capped, and spread out |

!!! warning "Turning upstream mode on switches auto-publish off everywhere"
    The two cannot both be on, and Kenaptic tells you which sources it changed. Any links
    auto-publish had approved but not yet deployed go back to the review queue.

    The reasoning is short. On your own documentation, auto-publish is a calculated risk: the
    worst case is a weak link on a page you control and can retract in one click. Upstream,
    both halves of that disappear. A maintainer who receives automated pull requests nobody
    read stops accepting them — and a DCO sign-off is a **named person** asserting they have
    the right to submit the change, so signing off work that person never saw is not a
    technicality, it's the assertion being false. Neither is undone by retracting a link.

    Switching back is safe: your DCO identity, permitted organisations and volume caps are
    kept, so re-enabling upstream mode doesn't quietly lose its guardrails.

---

## Before your first contribution

**Name a real person for the sign-off.** Most open-source projects require a Developer
Certificate of Origin: a statement that the person submitting a change has the right to submit
it. That is an assertion by a human being, so it cannot be an automated identity. Kenaptic asks
for a name and email and puts them on every commit.

**List the organisations you intend to contribute to.** Kenaptic will refuse to open a pull
request anywhere else. This matters more than it sounds: because of how forks work on GitHub, a
single mistyped repository name could otherwise send an unsolicited pull request to a project
nobody chose. An empty list means nothing is permitted, which is the safe way round.

---

## What Kenaptic checks before it proposes anything

- **Does the project accept automated contributions?** Some projects say plainly in their
  contributing guide that they don't. Kenaptic reads it and stops, quoting the sentence, before
  it even creates a fork.
- **Does the project require a CLA?** A Contributor License Agreement is signed by a person or
  organisation, out of band. Kenaptic can't sign one, so it warns you *before* a pull request
  opens rather than leaving one stuck failing a check.
- **Is this the right file, in the right repository, at the right version?** Generated pages,
  translations, frozen releases and content synced from elsewhere are all declined — see
  [How linking stays safe](../concepts/safe-by-design.md).

---

## Living with maintainers

**One pull request per repository.** However many pages and sources are involved, a maintainer
gets one thing to review, not one per source.

**A capped, reviewable size.** A pull request touching two hundred files won't be reviewed by
anyone. Kenaptic limits how many pages go into one request and holds the rest for next time —
and tells you what it held back, so a capped run never looks like a finished one.

**Re-running changes nothing on its own.** If nothing about the content changed, Kenaptic leaves
the pull request exactly as it is. No force-push, no new notifications, no CI re-run.

**"No" is respected.** If a maintainer closes a pull request without merging it, Kenaptic stops.
It will not open another one on the next run. An automated system that keeps re-asking a question
it has been told no to is the fastest way to get shut out of a project — so re-proposing is off
by default and has to be turned on deliberately.

**Withdrawing is clean.** Retracting closes the pull request and removes the branch. Nothing was
ever live on the project's site, so there is nothing left behind.

---

## Grouping properties by project

A single project often publishes in several places at once — documentation, a blog, a wiki, a
proposals repository. Group them so you can:

- **review one project at a time** instead of everything at once;
- **set what that project asked for** — how many links per page, which kinds, how they appear;
- **pause a project** while it is mid-restructure. It stays readable and linkable; Kenaptic just
  stops proposing changes to it.

Anything a project asked for that Kenaptic then declined to propose is reported, so "they asked
for two links per page and we honoured it" never looks the same as "nothing was found".

---

## Sending maintainers something to read

Maintainers won't have a Kenaptic login, and a pull request only shows *what* changed. Kenaptic
can produce a plain report for a project — how many links were proposed, how many are live, how
many candidates were **discarded**, and how to stop or reverse any of it. It is written to be
pasted into an issue or an email, with no branding and no numbers that only flatter Kenaptic.
