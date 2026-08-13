# Glossary

A quick reference for the terms you'll meet in Kenaptic.

**Silo**
: One self-contained source of content — your documentation site, knowledge base, blog, community
forum, or discussion board. The problem Kenaptic solves is that silos don't know about each other.

**Source / Domain**
: A silo you've connected to Kenaptic. You manage these on the **Domains** page. Each source is
either an estate you own (which Kenaptic can add links to) or a third-party destination (which
Kenaptic only links to).

**Estate**
: All of your connected content, taken together — the full set of sources Kenaptic reads and maps.

**Cross-link**
: A link Kenaptic proposes (and, once approved, publishes) that connects a page in one silo to a
related page in another. The core output of the product.

**Relationship type**
: The plain-language reason a cross-link makes sense — for example, one page *explains* a concept
another uses, *troubleshoots* a documented feature, or *discusses a real-world issue with* it.
Relationship types tell you *why* two pages should be linked, not just that they're similar.

**Confidence**
: Kenaptic's indication of how strong a proposed link is, shown to help you prioritise your review.
It's decision support, not a guarantee — you always make the final call.

**Document**
: A single page Kenaptic has read, from any of your sources. Listed on the **Documents** page.

**Orphan**
: A page nothing in your estate links to — not your own content, not Kenaptic's. Nobody arriving
from elsewhere can reach it, and an AI crawler following links will never see it.

**Siloed**
: A page that *is* linked, but only from inside its own bucket. Perfectly reachable if you are
already in that section, invisible if you are not. This is usually the largest group, and it is
the one Kenaptic exists to connect.

**Cross-linked**
: A page reachable from another bucket already — by your own link or by one Kenaptic deployed.
Nothing to do.

**Content gap**
: A topic your audience clearly cares about where your coverage is thin or missing — surfaced on the
**Content Gaps** page.

**Contradiction**
: A place where two of your own pages say different things about the same subject — surfaced on the
**Contradictions** page so you can reconcile them.

**Review queue**
: The list of proposed links (and fixes) waiting for a person to approve, edit, or reject. Found on
**Cross-link Review**.

**Placement**
: *Where* an approved cross-link appears on the page. **Reference** collects links in a "Related
content" section at the foot; **Immersive** adds one short factual sentence in the flow of the
prose with the link running through it; **Both** does each. Immersive is additive only — Kenaptic
never rewrites a word you wrote.

**Injection / Publish**
: Writing an approved link into a page's own source so it becomes a real, native link. Done on the
**Link Injection** page, and always reversible.

**Write path**
: The route by which an approved link actually reaches a source — a repository plus a credential,
or an API credential for a platform. A source without one can be a link *destination* but cannot
receive links, and Kenaptic marks it before you publish rather than failing at the end.

**Delivery destination**
: Somewhere a *record* of a proposed cross-link is filed — a Jira project, a ServiceNow table, your
own endpoint. Delivery is one-way: it never approves anything. See
[Where cross-links are delivered](../guide/where-links-are-delivered.md).

**Evidence**
: The passages from both pages that led Kenaptic to propose a link. Shown with every proposal — and
the part actually worth reading before you approve.

**Retract**
: Cleanly removing a link Kenaptic previously added, returning the page to how it was.

**Project**
: A group of sources belonging to one product. Kenaptic proposes links within a project by default;
cross-project linking is something you switch on deliberately.

**Role**
: What a person may do. A **Reviewer** can crawl, approve and reject; an **Admin** can additionally
publish, retract, and change sources and settings.

**Upstream mode**
: Proposing cross-links into repositories you don't own, as a fork-based pull request a maintainer
decides on. See [Contribute to projects you don't own](../guide/contributing-upstream.md).

**Not measured / cannot be computed**
: What Kenaptic reports instead of a zero when a figure genuinely has no answer yet — for example
content gaps when no source is writable. Deliberately distinct from "we found nothing". See
[When Kenaptic says no](../guide/when-kenaptic-says-no.md).

**AI Readiness**
: A measure of how well your content can be understood by AI assistants and search crawlers, with
prioritised fixes — on the **AI Readiness** page.

**Audit**
: The complete, timestamped record of activity and decisions in your workspace.
