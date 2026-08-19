# Review & publish links

The **Connect** group covers the review loop: proposed cross-links are reviewed here and, once
approved, published.

## Cross-link Review

The **Cross-link Review** page is the queue of proposed links. Each proposal shows:

- The source and destination pages, both linked so you can read them.
- The **relationship type**: the reason for the link (for example, one page *explains* a concept
  the other uses, or a forum thread *troubleshoots* a documented feature).
- A **confidence indicator**: a score for the strength of the match, used to triage the queue.
- A preview of exactly what will be added.

For each proposal you can **approve**, **edit then approve**, or **reject**. Filters narrow the
queue: links between two particular sources, a single relationship type, or the highest-confidence
proposals first.

Each proposal includes the **evidence**: the passages from both pages the proposal is based on.
The confidence figure orders the queue; the evidence determines whether the link is correct.

!!! tip "Live render"
    **See cross-link live render** opens the destination page with the proposed link in place,
    rendered as a visitor would see it, in the position and style that source is configured to
    use. Use it to catch links that are technically correct but poorly placed.

!!! tip "Review order"
    Sort by confidence and work top-down. Approve clear matches quickly and spend review time on
    proposals that need a judgement call.

Approving a link does not publish it. Approval moves the link to the publish step, so you can
review a batch and publish separately.

## Link Injection

Approved links are published from **Link Injection**. When you publish, Kenaptic writes each link
into the page's own source: a native link, rather than an overlay, a client-side script that can
fail, or a widget that AI crawlers do not see. The link works for every visitor and for every
machine that reads the page.

Two properties make published links manageable:

- **Marked.** Every link Kenaptic adds is tagged as Kenaptic's, so added links are always
  distinguishable from what was there before.
- **Reversible.** Any link Kenaptic added can be retracted cleanly from the Injection page,
  restoring the page to its previous state.

The page also shows the status of everything Kenaptic has published: what is live, what is
pending, and what has been retracted.

!!! warning "Unconfigured destinations"
    A source with no credential, or no repository destination configured, cannot receive a link.
    Kenaptic marks these sources with a warning icon in the preview list; hovering the icon shows
    exactly what is missing. The check runs before publish, so a missing path is surfaced in the
    preview rather than by a publish that delivers nothing. Fix the configuration in **Domains**,
    or leave the link queued until the path exists.

Delivery targets (a pull request, a merge request, a ticket, your own endpoint) are covered in
[Where cross-links are delivered](where-links-are-delivered.md).

## Link placement

Placement is configurable per domain, or per individual link:

- **Reference**: links collect in a "Related content" section at the foot of the page. Existing
  prose is not modified.
- **Immersive**: a short, neutral sentence is added where the page has no existing phrase to
  carry the link, and the link is placed on that sentence. Siloed pages commonly lack not only
  the link but any wording that refers to the other page, which is why a carrier sentence is
  added.
- **Both**: the added sentence and the foot-of-page entry.

Immersive placement is additive only. Kenaptic never rewrites existing text: the whole added
sentence sits between its own markers, so retracting it restores the original text exactly. The
generated wording is plain and factual; it states that another page covers a topic and makes no
other claims.

In every placement, the reference is a real link to your other content, and internal tracking
information stays internal: it is never exposed in the published page.

---

Next: [:octicons-arrow-right-24: Be found by AI](ai-readiness.md) — making connected content
legible to machine readers.
