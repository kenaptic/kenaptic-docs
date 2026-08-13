# Review & publish links

This is the core of the **Connect** group — where proposed cross-links become published links. It's
the review loop in detail.

## Cross-link Review

The **Cross-link Review** page is your queue of proposed links. Each proposal shows:

- **The source and destination pages**, both clickable so you can read them.
- **The relationship type** — the plain-language reason the link makes sense (for example, one page
  *explains* a concept the other uses, or a forum thread *troubleshoots* a documented feature).
- **A confidence indicator** — Kenaptic's read on the strength of the match, to help you triage.
- **A preview** of exactly what will be added.

For each proposal you can **approve**, **edit then approve**, or **reject**. Filters let you focus —
for example, on links between two particular sources, or on a single relationship type, or on the
highest-confidence proposals first.

Alongside the proposal you get the **evidence**: the passages from both pages that led Kenaptic to
suggest the link. That's the part worth reading. The confidence figure helps you order your queue;
the evidence is what tells you whether the link is right.

!!! tip "See it the way a reader will"
    **See cross-link live render** opens the destination page with the proposed link in place,
    exactly as a visitor would meet it — in the position and style that source is configured to use.
    It's the quickest way to catch a link that is technically correct but lands somewhere useless.

!!! tip "A good review rhythm"
    Sort by confidence and work top-down. Approve the obviously-good links quickly; slow down only
    where a proposal needs a judgement call. You're training your estate to be well-connected, one
    decision at a time.

Approving a link doesn't publish it immediately — it moves it to the publish step. That lets you
review in a comfortable batch and publish when you're ready.

## Link Injection

**Link Injection** is where approved links go live. When you publish, Kenaptic writes each link
**into the page's own source**, so it's a genuine, native link — not an overlay, not a script that
can fail, not a widget an AI crawler ignores. It works for every visitor and every machine that
reads the page.

Two things make this safe:

- **Clearly marked.** Every link Kenaptic adds is tagged as its own, so you can always tell what
  Kenaptic added versus what was there before.
- **Fully reversible.** From the Injection page you can retract any link Kenaptic added, cleanly,
  leaving the page as it was. Nothing is permanent, and nothing is hidden.

You can also see the status of everything Kenaptic has published — what's live, what's pending, and
what's been retracted.

!!! warning "Check the route before you publish"
    A source with no credential, or no repository destination configured, has nowhere to receive a
    link. Kenaptic marks these with a warning icon in the preview list and tells you on hover
    exactly what's missing — so you find out before you publish, not from a publish that quietly
    did nothing. Fix it in **Domains**, or leave the link queued until the path exists.

Where each change actually turns up — a pull request, a merge request, a ticket, your own endpoint —
is covered in [Where cross-links are delivered](where-links-are-delivered.md).

## How links appear on the page

You choose how each source presents its cross-links — per domain, or per individual link:

- **Reference** — the links collect in a tidy "Related content" section at the foot of the page.
  Your prose is left exactly as written.
- **Immersive** — one short, neutral sentence is added where the page has no natural phrase to
  link from, and the link runs through it. This is the common case in siloed content: the page
  doesn't just lack the link, it lacks the words to refer to the other page at all.
- **Both** — the added sentence and the foot-of-page entry.

Immersive placement is **additive only**. Kenaptic never rewrites a word you wrote: the whole
sentence sits between its own markers, so retracting it restores your original text exactly.
The wording is deliberately plain and factual — it says another page covers a topic, and makes no
claims of its own.

Whatever the placement, the reference is a real link to your other content, and any internal
tracking information stays internal — it is never exposed in the published page.

---

Next, make sure machines can understand what you've connected:
[:octicons-arrow-right-24: Be found by AI](ai-readiness.md)
