# How it works

Kenaptic runs one pipeline: connect, understand, propose, review, publish, keep current. By
default, nothing goes live without human approval.

## 1. Connect your sources

Add each place your content lives as a **domain** in the app: documentation site, knowledge base,
blog, forum. Kenaptic reads the content the same way any visitor would and respects each site's
crawling rules.

Sources have one of two roles:

- **Writable sources**, such as a docs site you control. Kenaptic can add links to these, always
  through your review.
- **Link destinations**, such as a public forum. Kenaptic reads these so it can link to them, and
  never modifies them.

## 2. Understand the content

Kenaptic reads every page and determines the topics it covers and how it relates to the rest of
your estate. The result is a map of your content: pages as points, and the relationships between
them as connections.

!!! note "Data handling"
    Kenaptic works from the public content of the pages you connect, and honours each site's
    stated crawling and usage rules. It never republishes forum or discussion content; it only
    links to it.

    Personal data is removed before anything is stored. Email addresses, phone numbers, handles,
    usernames and bylines are stripped from every page as it is ingested, from every source
    including your own. Nothing personal is kept, and nothing personal is sent to a language
    model. See the [safety model](../concepts/safe-by-design.md).

## 3. Propose links

From that map, Kenaptic generates cross-link proposals. Each proposal includes:

- The two pages the link would connect, and the direction of the link.
- A **relationship type**: for example, one page *explains* a concept another page uses, or a
  forum thread *discusses a real-world issue with* a documented feature. The type records why the
  link applies, beyond the fact that two pages are similar.
- A **confidence indicator** of how strong the match is, used to triage proposals. It informs the
  review decision and does not replace it.

## 4. Review

Every proposed link enters a **review queue**, where a member of your team approves, edits, or
rejects it. A preview shows the exact change before anything is published.

Review is required by default. Your team owns the content, and no link is published without an
explicit approval.

## 5. Publish at the source

An approved link is written into the page's own source as a native link, not as an overlay or a
script-injected widget. Because the link is part of the content itself, it reaches every visitor,
every search engine, and every AI assistant that reads the page, and it does not disappear if a
script fails.

Injected links are clearly marked and reversible. Kenaptic can remove or update any link it added,
cleanly, at any time.

## 6. Keep links current

Pages move, get rewritten, or are retired. Kenaptic re-checks your estate on a schedule and keeps
the cross-links current: it proposes new links as new content appears and retires links that no
longer apply. These changes pass through the same review queue.

---

For the full set of product capabilities, see [Capabilities](what.md).
