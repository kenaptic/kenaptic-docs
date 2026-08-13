# How linking stays safe

Kenaptic changes your live content. That's the whole point — native links at the source are what
make it work for every reader and every machine. But changing published content is a responsibility,
and Kenaptic is built so that responsibility always sits with you. Here are the principles that keep
it safe.

## A person approves every change

Every proposed link, and every content fix, goes through a review where a member of your team
approves, edits, or rejects it. Kenaptic is the tireless analyst that finds the opportunities; your
team is the editor who decides. Kenaptic proposes, you decide.

!!! warning "The one exception, and it's yours to switch on"
    **Auto-publish** can be enabled per source, for links scoring above a confidence threshold you
    set. It is off everywhere until an administrator deliberately turns it on, only an administrator
    can turn it on, and the switch carries a warning we make no attempt to soften. We don't
    recommend it.

    Everything else on this page still applies when it's on. Links are marked and reversible;
    auto-approvals are recorded in the audit trail under an explicit system actor rather than
    attributed to a person; and switching it back off withdraws anything it approved that hasn't
    gone out yet. What it does **not** do is pull back links already published — taking live content
    off your site is always an explicit Retract, never a side effect of a settings toggle.

    **It cannot be combined with upstream contribution mode** — see the next section.

## Auto-publish and upstream contributions can't both be on

If you [contribute to projects you don't own](../guide/contributing-upstream.md), that mode and
auto-publish are mutually exclusive. Switching either on switches the other off, and Kenaptic
says so when it does.

This is a deliberate limitation and the reasoning is short. Auto-publish is defensible on your own
documentation because the worst case is a weak link on a page you control and can retract in one
click. Upstream, both halves of that defence disappear:

- **A maintainer who receives automated pull requests nobody read stops accepting them** — often
  publicly. Every other rule in upstream mode exists to avoid being that tool.
- **A DCO sign-off is a named person asserting they have the right to submit the change.** Signing
  off work that person never saw is not a technicality; it is the assertion being false.

Neither is undone by retracting the link. That's the line: auto-publish's whole justification is
that its mistakes are cheap and reversible, and upstream they are neither.

Your DCO identity, permitted organisations and volume caps are kept when the mode switches off, so
turning upstream mode back on doesn't quietly lose its guardrails. Any links auto-publish had
approved but not yet deployed return to the review queue.

## Every change is marked and reversible

When Kenaptic adds a link to a page, it's **clearly tagged** as Kenaptic's, so you can always tell
what it added from what was already there. And it's **fully reversible**: Kenaptic can remove or
update any link it added, cleanly, leaving the page exactly as it was. You're never locked in, and
there's never a mystery about where a link came from.

## Personal data is removed before anything is stored

Your estate contains people. Forum threads carry members' names and handles, support pages quote
customers' email addresses, blog posts carry bylines. Kenaptic does not want any of it, and does
not keep it.

**Every page Kenaptic reads is stripped of personal identifiers before it is stored** — email
addresses, phone numbers, `@handles`, `u/usernames`, byline and profile patterns are removed from
the title, body and description at the moment of ingestion. Everything downstream is built from
the cleaned text, so the working copy, the search index, the topic digests and every request sent
to a language model are clean by construction rather than cleaned up afterwards.

Two consequences worth knowing:

- **Nothing personal reaches a model.** The removal happens before any text is sent anywhere, so
  personal data is never part of a prompt. The detection itself is plain pattern matching that
  runs on your own infrastructure — Kenaptic does not send text to a model in order to find the
  personal data in it, which would defeat the purpose.
- **It applies to every source, including your own.** This is not a rule for other people's
  sites. Your forum belongs to you; the posts in it belong to the people who wrote them, and they
  are treated the same way as any other source.

!!! note "What this does and doesn't claim"
    Kenaptic removes the identifier patterns that appear on public pages, before storage. That is
    data minimisation, and it is applied to everything — but pattern matching is not the same as a
    guarantee that no personal data can ever survive in free-form prose. If part of a site needs to
    be left unread entirely rather than minimised, keep it outside the crawl's scope — a source
    reads only what sits under its configured path, so a narrower starting address is what keeps a
    section out. See
    [What you can and can't keep out of a crawl](../guide/when-kenaptic-says-no.md#what-you-can-and-cant-keep-out-of-a-crawl).

## Kenaptic refuses to write in places it shouldn't

Not every page in a repository is a safe place to add a link, and getting this wrong is worse than
doing nothing — because the change looks correct right up until it disappears. Kenaptic declines to
write to:

- **Generated pages.** Documentation built from code, schemas or configuration is overwritten on
  the next build. Editing it either vanishes or, worse, edits the thing that generates it.
- **Translations.** A translated page belongs to the people who maintain that language. An English
  link block dropped into it is broken for its readers and lands in front of reviewers who did not
  write the page. Kenaptic proposes against the source language and lets translation flow normally.
- **Frozen versions.** Old releases that no longer accept changes.
- **Content that lives somewhere else.** A folder synced in from another repository, or included as
  a sub-repository, belongs to that repository — a change made here is erased by the next sync.
- **Archived projects.** Something that has been wound down is a place to link *to*, never a place
  to propose work.

Every refusal is reported, never silent. A page Kenaptic won't touch is usually telling you
something true about your estate, and hiding it would just look like Kenaptic being unreliable.

## Kenaptic respects the sources it reads

- **It honours each site's rules.** Kenaptic reads content the way a well-behaved visitor does and
  follows each site's stated crawling and usage policies. A site that asks not to be crawled isn't.
- **It reads gently.** Requests to any one site are paced and capped per run, so a large estate
  never arrives as a burst of traffic on somebody's server. If a cap is reached, Kenaptic says the
  crawl was a partial view rather than quietly presenting it as the whole picture.
- **It only writes where it's entitled to.** Kenaptic can add links only to sources you've confirmed
  you own and control. Third-party sources — like public forums — are read-only destinations: it
  links *to* them, but never changes them.
- **It never republishes other people's content.** For a forum thread or discussion, Kenaptic adds
  a link that points readers to the original. It doesn't copy the content into your pages.

## Your data is handled carefully

Kenaptic works from the public content of the pages you connect and is built to **minimise personal
data** — it isn't interested in individuals, only in how content relates. Sensitive details are
kept out of the way it understands and stores your content.

## You stay accountable — and can prove it

Every decision and every change is recorded in the **Audit** trail. If anyone ever asks "why is this
link here, who approved it, and when?", the answer is one page away. That record is there for your
own peace of mind and for any compliance process you need to satisfy.

---

Together these principles mean Kenaptic can do something powerful — edit your live content across
every silo — while never taking a step your team didn't approve, and never making a change you can't
undo.
