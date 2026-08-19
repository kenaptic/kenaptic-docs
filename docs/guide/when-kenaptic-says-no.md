# Refusals and unmeasured states

This page describes what Kenaptic declines to do, and what it reports instead of a number when one
cannot be computed honestly. "We found nothing" and "we were unable to look" are different
statements, and Kenaptic keeps them distinct.

---

## Unmeasured values

Several figures can only be computed once certain conditions hold. When the conditions do not
hold, Kenaptic reports that in plain words rather than showing a zero.

**Content gaps** require a writable source. A gap is a topic with demand in one place and no
coverage in a place you could publish to. If none of your sources is writable, there is no such
place, so the value is reported as **cannot be computed** rather than as zero gaps. Connect a
writable source and the number appears.

**Orphan and siloed counts** require a completed crawl. Until Kenaptic has read enough of your
estate to see which pages link to which, the Overview shows **not measured**. These counts include
your existing links as well as Kenaptic's, so they describe your estate rather than Kenaptic's
coverage of it; that description is only meaningful once the coverage is real.

**Capped crawls** are reported as a partial view. Kenaptic paces its requests and caps how much it
reads from any one site in a single run, so a large estate does not arrive at a server as a burst
of traffic. If a run hits the cap, the result is reported as partial rather than presented as
complete.

---

## Thin and empty sources

A source that returned one page, or none, is almost always a configuration problem: the wrong
address, an aggressive robots rule, a site that needs JavaScript to render, or an address that
redirects somewhere unexpected. Unaddressed, it drags down every estate-wide number.

Kenaptic flags these on the source itself:

- **Empty** — nothing was read at all.
- **Thin** — so little was read that any conclusion drawn from it would be noise.
- **Absorbed by another source** — everything found here belongs to a source you already
  connected (see below).

The flag is the output to act on. A source showing zero results indicates a setup problem, and the
flag reports it rather than hiding it in dashboard totals.

---

## Overlapping sources

If you connect `docs.example.com` and also `example.com`, the two overlap, and a page counted
twice would inflate every total in the product.

Kenaptic assigns each page to the most specific source that claims it. A page under
`docs.example.com` belongs to your docs source even though the broader `example.com` source could
also have claimed it. Addresses that redirect are followed first, so a source configured at an
address that has since moved is still matched correctly rather than appearing to own nothing.

If a source looks emptier than you expected, check whether a more specific source is claiming its
pages. This is the usual cause, and the estate totals remain correct even when one row looks low.

---

## Pages Kenaptic does not write to

Some pages are unsafe targets for an added link. A write that will later be discarded looks
correct until it disappears, which is worse than not writing at all. Kenaptic does not write to:

- **Generated pages** — documentation built from code, schemas or configuration is overwritten by
  the next build.
- **Translations** — translated pages are maintained by each language's translators. Kenaptic
  proposes against the source language and leaves translations to the normal translation flow.
- **Frozen versions** — old releases that no longer take changes.
- **Content synced in from elsewhere** — a folder mirrored from another repository is erased by
  the next sync.
- **Archived projects** — a wound-down project remains a valid link destination but receives no
  proposals.

Every refusal is reported; none is silent. See
[the safety model](../concepts/safe-by-design.md) for the full reasoning.

---

## robots.txt handling

For **third-party** sites, `robots.txt` is honoured as a complete opt-out: pages a site's rules
ask crawlers not to read are skipped, and the refusal is recorded.

For **your own** sources the rule is different, by design. Kenaptic records what your `robots.txt`
says and shows it against the source, but does not treat it as a refusal. Your `robots.txt` is
aimed at search engines and other crawlers; connecting the site is the instruction to read it. A
`Disallow: /` meant to keep a staging site out of search engines would otherwise produce an empty
estate. To keep a section of your own site out of a crawl, scope the crawl (below) rather than
relying on `robots.txt`.

In both cases the source appears in your list with its status, so a missing silo can be traced.
**A domain refused crawling** is one of the events available in [notifications](notifications.md).

---

## Crawl scope

Today, a crawl is scoped by what you include, not by filtering pages out.

Each source is configured with a starting address, and Kenaptic reads only what lives under that
path, on that host. Point a source at `example.com/docs/` and `/pricing`, `/careers` and
everything else on the domain are never read at all. A narrower starting address is the available
control, and for most estates it is the right one: it is also faster and cheaper than reading
pages you will discard.

Kenaptic also excludes some pages automatically:

- **Listing pages** — archive indexes, tag pages and paginated "page 2 of 47" pages. These are
  navigation rather than content, and counting them as pages distorts every number downstream.
- **Another source's pages** — where a more specific source claims a subtree, the broader source
  cedes it, so nothing is read or counted twice.
- **Platform interface pages** — a repository host's own interface routes, as opposed to the
  content hosted on it.
- **Non-canonical versions** — where a docs site publishes many versions of the same page.
- **Crawler traps** — hidden links no human would follow, planted by some sites to catch
  misbehaving crawlers.

!!! note "No per-page or pattern exclusion list yet"
    You can't currently say "read this source, but never `/internal/*`". The workarounds are to
    connect the narrower path as its own source, or to connect several specific sub-paths instead
    of one broad one.

    If this matters for your estate, tell us. The shape of the real requirement decides whether it
    should be a path list, a pattern list, or something else entirely.

---

## No publishing route

A source with no credential, or no repository destination, cannot receive a link. Kenaptic marks
these in the preview list before you publish rather than failing at the end. See
[Where cross-links are delivered](where-links-are-delivered.md).

---

## Auto-publish

By default, every link waits for a person to approve it. **Auto-publish** is the one setting that
changes this. It is configured per source, applies above a confidence threshold you choose, and
can be enabled only by an administrator. Off by default. We recommend leaving it off.

With auto-publish on, that source's links publish without individual review. The other safeguards
still hold: links are marked, they are reversible, and the audit trail attributes them to the
system rather than to a person who never saw them. Turning auto-publish off withdraws anything it
approved that has not yet gone out; anything already live stays live until you explicitly retract
it. See [the safety model](../concepts/safe-by-design.md).
