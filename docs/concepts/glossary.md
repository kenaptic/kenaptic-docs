# Glossary

Terms used in Kenaptic and throughout this documentation.

**Silo**
: One self-contained source of content — your documentation site, knowledge base, blog, community
forum, or discussion board. Silos rarely link to one another; Kenaptic exists to connect them.

**Source / Domain**
: A silo you've connected to Kenaptic. You manage these on the **Domains** page. Each source is
either an estate you own (which Kenaptic can add links to) or a third-party destination (which
Kenaptic only links to).

**Estate**
: All of your connected content, taken together — the full set of sources Kenaptic reads and maps.

**Cross-link**
: A link Kenaptic proposes (and, once approved, publishes) that connects a page in one silo to a
related page in another. Cross-links are Kenaptic's primary output.

**Relationship type**
: The plain-language reason a cross-link makes sense — for example, one page *explains* a concept
another uses, *troubleshoots* a documented feature, or *discusses a real-world issue with* it.
The relationship type records the reason two pages should be linked, beyond raw similarity.

**Confidence**
: Kenaptic's indication of how strong a proposed link is, used to prioritise review. Confidence is
decision support rather than a guarantee; a person makes the final approval decision.

**Document**
: A single page Kenaptic has read, from any of your sources. Listed on the **Documents** page.

**Orphan**
: A page that nothing in your estate links to, neither your own content nor a link Kenaptic added.
Readers cannot reach it from any other page, and an AI crawler following links will not find it.

**Siloed**
: A page that is linked, but only from inside its own bucket. It is reachable from within that
section and unreachable from any other silo. Siloed pages are usually the largest group and the
primary target for cross-linking.

**Cross-linked**
: A page already reachable from another bucket, through your own link or one Kenaptic deployed.
No action is needed.

**Content gap**
: A topic with clear audience demand where your coverage is thin or missing — surfaced on the
**Content Gaps** page.

**Contradiction**
: A place where two of your own pages say different things about the same subject — surfaced on the
**Contradictions** page so you can reconcile them.

**Review queue**
: The list of proposed links (and fixes) waiting for a person to approve, edit, or reject. Found on
**Cross-link Review**.

**Placement**
: Where an approved cross-link appears on the page. **Reference** collects links in a "Related
content" section at the foot; **Immersive** adds one short factual sentence in the flow of the
prose with the link running through it; **Both** does each. Immersive is additive only; existing
prose is never modified.

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
: The passages from both pages that led Kenaptic to propose a link. Shown with every proposal.
Review the evidence before approving.

**Retract**
: Cleanly removing a link Kenaptic previously added, returning the page to how it was.

**Project**
: A group of sources belonging to one product. Kenaptic proposes links within a project by default;
cross-project linking must be enabled explicitly.

**Role**
: What a person may do. A **Reviewer** can crawl, approve and reject; an **Admin** can additionally
publish, retract, and change sources and settings.

**Upstream mode**
: Proposing cross-links into repositories you don't own, as a fork-based pull request a maintainer
decides on. See [Contribute to projects you don't own](../guide/contributing-upstream.md).

**Not measured / cannot be computed**
: What Kenaptic reports instead of a zero when a figure genuinely has no answer yet — for example
content gaps when no source is writable. This is distinct from a measured zero. See
[When a value cannot be measured](../guide/when-kenaptic-says-no.md).

**AI Readiness**
: A measure of how well your content can be understood by AI assistants and search crawlers, with
prioritised fixes — on the **AI Readiness** page.

**Audit**
: The complete, timestamped record of activity and decisions in your workspace.
