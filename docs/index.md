# The problem Kenaptic solves

## Content silos

The answer a customer needs usually already exists somewhere in a company's content estate, but
in a different system from the one the customer is searching. Content accumulates in separate
systems over the years:

- Product documentation explains how a feature is meant to work.
- The knowledge base holds fixes for when features do not behave as documented.
- The blog announces changes and the reasoning behind them.
- Community forums and discussion boards carry user-reported problems and solutions, often
  before the documentation is updated.
- Whitepapers and guides cover the underlying concepts in depth.

Each of these is a **silo**: a self-contained system that holds its own content and carries no
references to content in the others.

## Cost of unlinked content

A reader on a documentation page can only reach related content in another silo if a link is
present on the page. Where links are missing:

- Avoidable support tickets. A forum thread that solves the customer's problem exists, but the
  docs page they landed on does not link to it, so they open a ticket instead.
- Underused content. Knowledge-base articles, blog posts, and in-depth guides that are not
  linked from the pages where readers start go unread.
- Duplicated effort. Teams rewrite explanations that another team has already published, because
  nothing shows them what exists in the other silos.
- Weaker visibility to search engines and AI assistants. Well-connected content is easier for
  both people and machines to navigate and trust.

## Limits of manual cross-linking

Manual cross-linking does not scale:

- No single person has visibility across the whole estate. The docs writer does not read every
  forum thread; the support team does not track every blog post.
- The silos run on different tools and are owned by different teams. There is no single place to
  add a link that spans all of them.
- Content changes constantly. A link added by hand today is stale next quarter, and the work of
  maintaining links by hand is never finished.

Single-platform tools have the same limit. A docs search box or a knowledge-base "related
articles" widget indexes only the content inside its own platform, so it cannot surface a forum
thread from a docs page.

## The Kenaptic approach

Kenaptic maps relationships across the entire content estate. It proposes the links that should
exist between silos, routes each one through human approval, writes approved links into the
content at the source, and keeps them current as content changes.

The next pages describe [how this works](introduction/how.md) and
[what the product provides](introduction/what.md).
