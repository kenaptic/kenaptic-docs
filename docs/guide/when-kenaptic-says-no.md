# When Kenaptic says no

Most documentation describes what a product does. This page describes what Kenaptic **declines** to
do, and what it says instead of a number when it can't produce one honestly.

It's here because a tool that writes into your live content earns its trust in exactly these
moments. "We found nothing" and "we were unable to look" are completely different statements, and a
product that blurs them will be believed at precisely the wrong time.

---

## "Not measured" is not zero

Several figures in Kenaptic can only be computed once certain conditions hold. When they don't,
Kenaptic says so in plain words rather than showing a confident zero.

**Content gaps need somewhere to publish.** A gap is a topic with demand in one place and no
coverage in a place you could publish to. If none of your sources is writable, there is no such
place — so the question has no answer, and Kenaptic reports that it **cannot be computed** rather
than reporting no gaps. Connect a writable source and the number appears.

**Orphan and siloed counts need a completed crawl.** Until Kenaptic has read enough of your estate
to see which pages link to which, the Overview says **not measured**. These counts include *your*
existing links as well as Kenaptic's, so they describe your estate rather than our coverage of it —
which only works once the coverage is real.

**A capped crawl is reported as a partial view.** Kenaptic paces its requests and caps how much it
reads from any one site in a single run, so a large estate never lands on somebody's server as a
burst of traffic. If a run hits that cap, Kenaptic tells you the picture is partial instead of
quietly presenting it as complete.

---

## Thin and empty sources are flagged, not averaged away

A source that returned one page, or none, is almost always a configuration problem — the wrong
address, an aggressive robots rule, a site that needs JavaScript to render, or an address that
redirects somewhere unexpected. Left alone, it silently drags down every estate-wide number you
look at.

Kenaptic flags these on the source itself:

- **Empty** — nothing was read at all.
- **Thin** — so little was read that any conclusion drawn from it would be noise.
- **Absorbed by another source** — everything found here actually belongs to a source you already
  connected (see below).

The flag is the useful output. A source showing zero results tells you something true about your
setup, and hiding it behind a tidy dashboard would just make Kenaptic look unreliable later.

---

## Overlapping sources: one page has one owner

If you connect `docs.example.com` and also `example.com`, the two overlap — and a page counted
twice would inflate every total in the product.

Kenaptic assigns each page to the **most specific** source that claims it. A page under
`docs.example.com` belongs to your docs source even though the broader `example.com` source could
also have claimed it. Addresses that redirect are followed first, so a source configured at an
address that has since moved is still matched correctly rather than appearing to own nothing.

The practical consequence: if a source looks emptier than you expected, check whether a more
specific source is legitimately claiming its pages. That's usually the answer, and the totals are
right even when one row looks surprising.

---

## Pages Kenaptic refuses to write to

Some pages are unsafe places to add a link, and getting this wrong is worse than doing nothing —
the change looks correct right up until it disappears. Kenaptic declines to write to:

- **Generated pages** — documentation built from code, schemas or configuration is overwritten by
  the next build.
- **Translations** — a translated page belongs to the people who maintain that language. Kenaptic
  proposes against the source language and lets translation flow normally.
- **Frozen versions** — old releases that no longer take changes.
- **Content synced in from elsewhere** — a folder mirrored from another repository is erased by the
  next sync.
- **Archived projects** — something wound down is a place to link *to*, never a place to propose
  work.

Every refusal is reported, never silent. See
[How linking stays safe](../concepts/safe-by-design.md) for the reasoning in full.

---

## Sources that decline to be read

If a **third-party** site's rules ask crawlers not to read it, Kenaptic doesn't — the page is
skipped and the refusal recorded. `robots.txt` is how the rest of the web says no to us, and it is
honoured as a complete opt-out.

For **your own** sources the rule is different, and deliberately so. Kenaptic records what your
`robots.txt` says and shows it against the source, but it does not treat it as a refusal. Your
`robots.txt` is aimed at search engines and other people's crawlers; you have already told Kenaptic
to read this site by connecting it, and a `Disallow: /` meant to keep a staging site out of Google
should not silently produce an empty estate. If you want a section of your own site left alone,
scope the crawl (below) rather than relying on `robots.txt` to do it.

Either way the source appears in your list with a clear status, so a missing silo is never a
mystery. You can also ask to be told — **A domain refused crawling** is one of the events available
in [notifications](notifications.md).

---

## What you can and can't keep out of a crawl

Today, **you scope a crawl in rather than filtering pages out.**

Each source is configured with a starting address, and Kenaptic reads only what lives **under that
path, on that host**. Point a source at `example.com/docs/` and `/pricing`, `/careers` and
everything else on the domain are never read at all. A narrower starting address is the control you
have — and for most estates it's the one you want, because it's also faster and cheaper than
reading pages you'll discard.

Kenaptic also drops some things on its own, without being asked:

- **Listing pages** — archive indexes, tag pages and paginated "page 2 of 47" pages. They're
  navigation, not content, and counting them as pages distorts every number downstream.
- **Another source's pages** — where a more specific source claims a subtree, the broader source
  cedes it, so nothing is read or counted twice.
- **Platform interface pages** — a repository host's own menus-and-buttons routes, as opposed to
  the content hosted on it.
- **Non-canonical versions** — where a docs site publishes many versions of the same page.
- **Links no human would follow** — hidden traps some sites plant to catch impolite crawlers.

!!! note "There's no per-page or pattern exclusion list yet"
    You can't currently say "read this source, but never `/internal/*`". The workarounds are to
    connect the narrower path as its own source, or to connect several specific sub-paths instead
    of one broad one.

    If this matters for your estate, tell us. It's a small piece of work, and the shape of the real
    requirement is what decides whether it should be a path list, a pattern list, or something else
    entirely.

---

## No publishing route

A source with no credential, or no repository destination, cannot receive a link. Kenaptic marks
these in the preview list before you publish rather than failing at the end. See
[Where cross-links are delivered](where-links-are-delivered.md).

---

## Nothing publishes itself unless you asked it to

The default everywhere is that a link waits for a person, and that's the setting we'd like you to
leave alone. **Auto-publish** is the one way to change it: per source, above a confidence threshold
you choose, switchable only by an administrator, and carrying a warning we make no attempt to
soften.

If it's on, that source's links stop waiting for you. Everything else still holds — they're marked,
they're reversible, and the audit trail attributes them to the system rather than to a person who
never saw them. Turning the switch off withdraws whatever it approved that hasn't gone out yet;
anything already live stays live until you explicitly retract it. See
[How linking stays safe](../concepts/safe-by-design.md).
