# Safety model

Kenaptic modifies live content: it injects native links into page source, where every reader and
every crawler can see them. Because it changes published pages, the product is built so that
control over every change stays with your team. This page describes the mechanisms that enforce
that.

## Human review

Every proposed link and every content fix goes through review. A member of your team approves,
edits, or rejects each proposal before anything is published.

!!! warning "Auto-publish"
    **Auto-publish** can be enabled per source, for links scoring above a confidence threshold you
    set. It is off by default everywhere. Only an administrator can enable it, and enabling it
    displays a warning. We recommend leaving it off.

    Everything else on this page still applies when it is on. Links remain marked and reversible.
    Auto-approvals are recorded in the audit trail under an explicit system actor rather than
    attributed to a person. Switching auto-publish back off withdraws anything it approved that
    has not yet been published. It does not pull back links already published: removing live
    content from your site always requires an explicit Retract and is never a side effect of a
    settings toggle.

    Auto-publish cannot be combined with upstream contribution mode. See the next section.

## Auto-publish and upstream contributions

If you [contribute to projects you don't own](../guide/contributing-upstream.md), upstream
contribution mode and auto-publish are mutually exclusive. Switching either on switches the other
off and reports that it has done so.

The reasoning: auto-publish is defensible on your own documentation because the worst case is a
weak link on a page you control, retractable in one click. Upstream, both halves of that defence
disappear:

- A maintainer who receives automated pull requests nobody read stops accepting them, often
  publicly. Every other rule in upstream mode exists to avoid producing that outcome.
- A DCO sign-off is a named person asserting they have the right to submit the change. Signing
  off work that person never saw makes the assertion false.

Neither problem is undone by retracting the link. Auto-publish is acceptable only where its
mistakes are cheap and reversible; upstream contributions are neither.

Your DCO identity, permitted organisations, and volume caps are kept when upstream mode switches
off, so turning it back on does not lose its guardrails. Any links auto-publish had approved but
not yet deployed return to the review queue.

## Change marking and reversibility

Every link Kenaptic adds to a page is tagged as Kenaptic's, so its additions are always
distinguishable from pre-existing content. Every link is also reversible: Kenaptic can remove or
update any link it added, cleanly, leaving the page exactly as it was. There is no lock-in, and
the origin of every link is recorded.

## Personal data removal

Public content contains personal data: forum threads carry members' names and handles, support
pages quote customers' email addresses, blog posts carry bylines. Kenaptic does not store any of
it.

Every page Kenaptic reads is stripped of personal identifiers before it is stored. Email
addresses, phone numbers, `@handles`, `u/usernames`, and byline and profile patterns are removed
from the title, body, and description at the moment of ingestion. Everything downstream is built
from the cleaned text: the working copy, the search index, the topic digests, and every request
sent to a language model are clean by construction rather than cleaned up afterwards.

Two consequences:

- No personal data reaches a model. Removal happens before any text is sent anywhere, so personal
  data is never part of a prompt. Detection is plain pattern matching that runs on your own
  infrastructure; Kenaptic does not send text to a model to find the personal data in it.
- Removal applies to every source, including your own. Your forum belongs to you, but the posts
  in it belong to the people who wrote them, and they are treated the same way as any other
  source.

!!! note "Limits of pattern matching"
    Kenaptic removes the identifier patterns that appear on public pages, before storage. This is
    data minimisation applied to everything, not a guarantee that no personal data can survive in
    free-form prose. If part of a site must be left unread entirely rather than minimised, keep it
    outside the crawl's scope: a source reads only what sits under its configured path, so a
    narrower starting address is what keeps a section out. See
    [Crawl scope](../guide/when-kenaptic-says-no.md#crawl-scope).

## Write restrictions

Not every page in a repository is a safe place to add a link, and a misplaced change looks
correct until the next build or sync erases it. Kenaptic declines to write to:

- **Generated pages.** Documentation built from code, schemas, or configuration is overwritten on
  the next build. An edit either vanishes or, worse, modifies the thing that generates it.
- **Translations.** A translated page belongs to the people who maintain that language. An English
  link block inserted into it is broken for its readers and lands in front of reviewers who did
  not write the page. Kenaptic proposes against the source language and lets translation flow
  normally.
- **Frozen versions.** Old releases that no longer accept changes.
- **Content that lives somewhere else.** A folder synced in from another repository, or included
  as a sub-repository, belongs to that repository. A change made here is erased by the next sync.
- **Archived projects.** A wound-down project is a link destination, not a place to propose work.

Every refusal is reported, never silently applied. A refused page usually reflects a structural
fact about your estate, such as a generated section or a synced folder.

## Source handling

- Kenaptic follows each site's stated crawling and usage policies. A site that asks not to be
  crawled is not crawled.
- Requests to any one site are paced and capped per run, so a large estate never arrives as a
  burst of traffic on one server. If a cap is reached, the crawl result is reported as a partial
  view rather than presented as complete.
- Kenaptic adds links only to sources you have confirmed you own and control. Third-party
  sources, such as public forums, are read-only destinations: Kenaptic links to them but never
  changes them.
- Third-party content is never republished. For a forum thread or discussion, Kenaptic adds a
  link that points readers to the original. It does not copy the content into your pages.

## Data handling

Kenaptic works from the public content of the pages you connect and minimises personal data. It
stores how content relates, not information about individuals, and keeps sensitive details out of
the way it understands and stores your content.

## Audit trail

Every decision and every change is recorded in the **Audit** trail: which link was added, who
approved it, and when. The record supports internal review and any compliance process you need to
satisfy.

---

These principles let Kenaptic edit live content across every silo while ensuring that every
change is approved by your team and every change can be undone.
