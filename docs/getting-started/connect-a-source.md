# Connect a source

A **source** is one place your content lives: a documentation site, a knowledge base, a blog, a
community forum, or a discussion board. You connect sources on the **Domains** page. Kenaptic then
reads that content and adds it to your estate map.

## Add your first domain

1. Go to **Discover → Domains**.
2. Choose **Add domain** and enter the web address of the source.
3. Select the source type and its role (see the two roles below).
4. Confirm. Kenaptic begins reading the content and adding its pages to your **Documents** list.

!!! note "Domain changes require 2FA"
    A domain decides what Kenaptic reads and where it may later add links. Adding or changing a
    domain is therefore done in the app and confirmed with your 2FA, which prevents unwanted or
    untrusted sources from being connected on your behalf.

## Source roles

When you add a source, you assign it one of two roles:

- **Your own estate** — content you own and control, such as your documentation site or knowledge
  base. Kenaptic can both read it (to understand your content) and, later, add links to it through
  your review.
- **A third-party source** — content you don't own, such as a public community forum. Kenaptic
  reads it so it can point to it, but it never modifies it and never republishes its content.
  These sources are link destinations only.

The role controls write access: Kenaptic only writes links into content marked as your own estate.

!!! note "Own sources without publishing into them"
    Marking a source as your own does not commit you to publishing into it. It makes the source a
    valid destination: Kenaptic can propose links pointing there, and you decide later whether
    any of them get written. Many estates run this way, with everything mapped and only some of it
    edited.

## Overlapping sources

If you connect both `docs.example.com` and `example.com`, pages under `docs.example.com` match both.
Kenaptic assigns each page to the most specific source that claims it, so a page under
`docs.example.com` belongs to your docs source and is counted exactly once.

Redirects are resolved before this assignment, so a source configured at an address that has since
moved is still matched correctly.

This assignment is the usual reason a source contains fewer pages than expected. The estate totals
remain correct. See [When Kenaptic says no](../guide/when-kenaptic-says-no.md).

## Discovering sources with Domain Scout

**Domain Scout** maps a content estate from a single starting address. Point it at your main site
and it scans for the other places your content lives (a docs subdomain, a help centre, a blog, a
forum) and proposes them as sources with a suggested role for each.

It follows the same crawl rules as the rest of Kenaptic. Its findings are proposals only: nothing
is connected until you choose to connect it.

## Sources behind a login

Some support content sits inside a workspace or community that only members can see. Kenaptic reads
these through the platform's own official interface, using a credential you create and control:

| Source | What Kenaptic reads |
|---|---|
| **Slack** | Channel *threads* — a question with its replies |
| **Discord** *(beta)* | Forum-channel threads only |
| **Stack Overflow / Stack Exchange** | Questions and their top answers for a tag you choose |
| **Notion** | Pages you grant access to |
| **GitHub Discussions** | Each thread as one page — the question, the accepted answer and the most useful replies |
| **GitHub Issues** | Closed issues, with the comments that resolved them |

These are always link destinations only. Kenaptic reads them to map what your community has
already answered, and never posts into them.

!!! note "Closed issues only"
    An open issue is an unanswered question, so linking a documentation page to it points the
    reader at a known, unresolved problem. A closed issue usually carries the resolution: the
    workaround, the version it was fixed in, or the reason it is working as intended. Kenaptic
    reads closed issues for this reason and skips open ones.

## Blogs and repositories

| Source | What Kenaptic reads |
|---|---|
| **Medium publications** | Posts from a Medium-hosted blog, including one on your own domain |
| **Git repositories with no website** | Markdown that is never published as a page — design documents, proposals, examples, per-component READMEs |
| **GitHub wikis** | Wiki pages, which most tools treat as unreachable |

!!! note "Medium shows recent posts only"
    Medium's feed exposes only a publication's most recent articles and offers no way to page back
    through the archive. Kenaptic reports when it has hit that limit, so a long-running blog is not
    silently under-counted.

!!! note "Discord reads forum channels, not general chat"
    A forum-channel thread has a title, a question and answers: the same shape as a help article,
    so it can be linked to and reasoned about. Ordinary chat channels are a continuous stream with
    no beginning or end, so there is no page a reader could be sent to. Kenaptic reads forum
    channels and skips the rest, rather than inventing page boundaries that do not exist.

    A Discord link only opens for people who are members of that server, and search engines and AI
    assistants cannot read it at all. Discord is often most useful as a signal of what your
    community keeps asking, so you can answer those questions in your docs, rather than as a link
    target.

## Start small

A practical first setup is two or three sources that clearly relate: for example, your product
docs, your knowledge base and one community forum. That is enough for Kenaptic to find useful
cross-links quickly, and for you to run the review loop end to end before scaling up.

## After connecting

After a source is connected, Kenaptic:

1. Reads its pages and adds them to **Documents**.
2. Builds them into your estate map (visible on the **Knowledge Graph**).
3. Begins finding cross-link opportunities, which appear in **Cross-link Review**.

The first read of a large source can take a while. Progress is shown in the app, and Kenaptic
notifies you when the read completes.

## Next

[:octicons-arrow-right-24: The review loop](the-review-loop.md)
