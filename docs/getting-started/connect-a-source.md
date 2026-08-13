# Connect a source

A **source** is one place your content lives: a documentation site, a knowledge base, a blog, a
community forum, or a discussion board. You connect sources on the **Domains** page. Kenaptic then
reads that content and folds it into your estate map.

## Add your first domain

1. Go to **Discover → Domains**.
2. Choose **Add domain** and enter the web address of the source.
3. Tell Kenaptic what kind of source it is and how it should treat it (see the two roles below).
4. Confirm. Kenaptic begins reading the content and adding its pages to your **Documents** list.

!!! note "Adding a source is a deliberate, protected action"
    Because connecting a new source is significant — it decides what Kenaptic reads and where it
    might one day add links — adding or changing a domain is done in the app and confirmed with your
    2FA. This keeps unwanted or untrusted sources from being connected on your behalf.

## The two roles a source can play

When you add a source, you tell Kenaptic how it may use it:

- **Your own estate** — content you own and control, such as your documentation site or knowledge
  base. Kenaptic can both **read** it (to understand your content) and, later, **add links** to it
  through your review.
- **A third-party source** — content you don't own, such as a public community forum. Kenaptic
  **reads** it so it can point *to* it, but it **never modifies** it and never republishes its
  content. These sources are link destinations only.

This distinction matters: it's how Kenaptic makes sure it only ever writes links into content you're
entitled to change.

!!! note "Own it, but don't want links in it? That's fine too"
    Marking a source as your own doesn't commit you to publishing into it. It makes it a **valid
    destination** — Kenaptic can propose links pointing there, and you can decide later whether any
    of them ever get written. Plenty of estates run this way: everything is mapped, only some of it
    is edited.

## If two sources overlap

Connect `docs.example.com` and `example.com` and the second could, in principle, claim the first
one's pages. Kenaptic assigns each page to the **most specific** source that claims it, so a page
under `docs.example.com` belongs to your docs source and is counted exactly once.

Addresses that redirect are followed before this is worked out, so a source you configured at an
address that has since moved is still matched correctly.

If a source ends up looking emptier than you expected, this is usually why — and the estate totals
are still right. See [When Kenaptic says no](../guide/when-kenaptic-says-no.md).

## Not sure what you've got?

If you know your main site but not everything hanging off it, **Domain Scout** will map it for you.
Point it at one address and it looks for the other places your content lives — a docs subdomain, a
help centre, a blog, a forum — and proposes them as sources with a suggested role for each.

It reads politely and honours the same rules as everything else in Kenaptic, and it proposes: you
choose which of its findings to actually connect.

## Sources that live behind a login

Not everything is on the open web. Some of the most useful support content sits inside a workspace
or a community that only members can see. Kenaptic can read these through the platform's own
official interface, using a credential you create and control:

| Source | What Kenaptic reads |
|---|---|
| **Slack** | Channel *threads* — a question with its replies |
| **Discord** *(beta)* | **Forum-channel threads** only |
| **Stack Overflow / Stack Exchange** | Questions and their top answers for a tag you choose |
| **Notion** | Pages you grant access to |
| **GitHub Discussions** | Each thread as one page — the question, the accepted answer and the most useful replies |
| **GitHub Issues** | **Closed** issues, with the comments that resolved them |

These are always **link destinations only** — Kenaptic reads them to understand what your community
already answered, and never posts into them.

!!! note "Why closed issues, and not open ones"
    An open issue is an unanswered question. Linking a documentation page to it tells the reader
    "this is broken and nobody has fixed it", which is rarely the help they came for. A closed issue
    usually carries the resolution — the workaround, the version it was fixed in, or the reason it
    is working as intended — and that is what makes it worth pointing someone at.

## Blogs and repositories

| Source | What Kenaptic reads |
|---|---|
| **Medium publications** | Posts from a Medium-hosted blog, including one on your own domain |
| **Git repositories with no website** | Markdown that is never published as a page — design documents, proposals, examples, per-component READMEs |
| **GitHub wikis** | Wiki pages, which most tools treat as unreachable |

!!! note "Medium shows recent posts only"
    Medium's feed exposes only a publication's most recent articles and offers no way to page back
    through the archive. Kenaptic tells you when it has hit that limit rather than leaving you to
    assume a long-running blog only ever published ten posts.

!!! note "Discord reads forum channels, not general chat"
    A forum-channel thread has a title, a question and answers — the same shape as a help article,
    so it can be linked to and reasoned about. Ordinary chat channels are a continuous stream with
    no beginning or end, so there is no page a reader could ever be sent to. Kenaptic therefore
    reads forum channels and skips the rest, rather than inventing page boundaries that don't exist.

    Keep in mind that a Discord link only opens for people who are members of that server, and
    search engines and AI assistants cannot read it at all. Discord is often most valuable as a
    **signal** — showing you what your community keeps asking so you can answer it in your docs —
    rather than as a link target.

## Start small

You don't need to connect everything at once. A great first setup is **two or three sources that
clearly relate** — for example, your product docs plus your knowledge base plus one community
forum. That's enough for Kenaptic to find genuinely useful cross-links quickly, and for you to see
the review loop end to end before scaling up.

## What happens next

After a source is connected, Kenaptic:

1. Reads its pages and adds them to **Documents**.
2. Builds them into your estate map (visible on the **Knowledge Graph**).
3. Begins finding cross-link opportunities, which appear in **Cross-link Review**.

The first read of a large source can take a little while. You can watch progress in the app and
carry on with other work; Kenaptic will let you know when it's done.

## Next

Learn the everyday rhythm of using Kenaptic:

[:octicons-arrow-right-24: The review loop](the-review-loop.md)
