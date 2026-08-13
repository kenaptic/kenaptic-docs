# How it works

Kenaptic follows one simple loop: **connect → understand → propose → review → publish → keep
fresh.** You stay in control at every step, and by default nothing goes live without your approval.

## 1. Connect your sources

You tell Kenaptic where your content lives — your documentation site, knowledge base, blog,
forum, and so on. Each source is added as a **domain** in the app. Kenaptic reads the content the
same way any visitor would, and it respects each site's crawling rules.

Sources come in two roles:

- **Sources Kenaptic can write to** (like a docs site you control) — Kenaptic can add links here,
  always through your review.
- **Sources Kenaptic only links to** (like a public forum) — Kenaptic reads them so it can point
  *to* them, but never modifies them.

## 2. Understand the content

Kenaptic reads every page and builds an understanding of what each one is *about* — the topics it
covers and how it relates to everything else in your estate. The result is a map of your content:
pages as points, and the meaningful relationships between them as connections.

!!! note "What Kenaptic reads, and what it doesn't"
    Kenaptic works from the public content of the pages you connect, and honours each site's
    stated crawling and usage rules. It never republishes forum or discussion content — it only
    links to it.

    **Personal data is removed before anything is stored.** Email addresses, phone numbers,
    handles, usernames and bylines are stripped from every page as it is ingested — from every
    source, including your own — so nothing personal is kept and nothing personal is ever sent to
    a language model. See [How linking stays safe](../concepts/safe-by-design.md).

## 3. Propose the links that should exist

From that map, Kenaptic surfaces the cross-links worth adding. Each proposal comes with:

- **The two pages it would connect**, and the direction of the link.
- **A relationship type** — for example, one page *explains* a concept another page uses, or a
  forum thread *discusses a real-world issue with* a documented feature. These plain-language types
  tell you *why* the link makes sense, not just that two pages are similar.
- **A confidence indicator** — Kenaptic's read on how strong the match is, to help you triage. It's
  decision support, not a verdict.

## 4. Review — a person decides

Every proposed link goes into a **review queue**. A member of your team approves, edits, or rejects
each one. You can preview exactly what will change before anything happens.

This human review gate is deliberate. Kenaptic is confident, but your team owns your content and
your voice. Kenaptic proposes; you decide.

## 5. Publish at the source

When you approve a link, Kenaptic writes it **into the page's own source** — not as an overlay or a
widget that disappears if a script fails, but as a real, native link in the content itself. That
means it works for every visitor, every search engine, and every AI assistant that reads your
pages.

Links are added in a way that is **clearly marked and fully reversible**. Kenaptic can remove or
update any link it added, cleanly, at any time.

## 6. Keep it fresh — automatically

Content changes. Pages move, get rewritten, or are retired. Kenaptic re-checks your estate on a
schedule and keeps the cross-links current: adding new ones as new content appears, and retiring
links that no longer make sense — again, with your review in the loop.

---

Curious what all of this adds up to in the product? See [**what Kenaptic does**](what.md).
