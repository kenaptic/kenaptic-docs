# Frequently asked questions

## What kinds of content can Kenaptic connect?

Documentation sites, knowledge bases, blogs, whitepapers and guides, community forums, and
discussion boards. If your audience reads it, Kenaptic can usually map it and link to it. Sources
you own can also have links added to them; sources you don't own are read-only link destinations.

## Will Kenaptic change my content without asking?

Not unless you've asked it to. By default every proposed link and every fix goes through a review
where a person on your team approves, edits, or rejects it. Kenaptic proposes; you decide.

There is one exception, and only an administrator of your workspace can create it: **auto-publish**
can be switched on for a given source, for links above a confidence threshold you set. It's off
until someone turns it on, it carries a warning, and we don't recommend it — but it exists, and
you should know it exists. See
[How linking stays safe](concepts/safe-by-design.md).

## Can I undo a link Kenaptic added?

Yes, completely. Every link Kenaptic publishes is clearly marked as its own and can be retracted
cleanly, leaving the page exactly as it was. Nothing is permanent.

## Does Kenaptic copy content from forums into my pages?

No. For a forum thread or discussion, Kenaptic adds a link that points readers to the original. It
never republishes other people's content into your pages.

## Does Kenaptic respect a site's crawling rules?

Yes. Kenaptic reads content the way a well-behaved visitor does and follows each site's stated
crawling and usage policies. A site that asks not to be crawled isn't.

## How does Kenaptic decide which links to propose?

It reads and understands your content, works out how pages relate across your silos, and surfaces
the connections worth making — each with a relationship type and a confidence indicator. The details
of how it does that are Kenaptic's own; what you see is a clear, reviewable proposal for every link.

## Will the links help with search engines and AI assistants?

Yes. Because Kenaptic writes real, native links into your content — not overlays or scripts — the
connections are visible to every visitor, every search crawler, and every AI assistant that reads
your pages. The **AI Readiness** page tracks how machine-friendly your estate is and how to improve
it.

## How is Kenaptic priced?

On the size of the content estate you keep connected — the number of sources and the volume of
content — not on the number of people using it. Seats are unlimited, so you can invite your whole
team.

## Who should be in our Kenaptic workspace?

Anyone who owns part of the content story: documentation writers, support and knowledge-base leads,
and the web team. More reviewers means a healthier, better-connected estate.

## How long until we see value?

Connect two or three clearly-related sources and Kenaptic will start proposing useful cross-links
quickly. Approving a handful of strong links on day one already improves how readers move between
your silos — you don't have to wait for a big rollout.

## We're not on GitHub. Can Kenaptic still write our links?

Yes. Kenaptic opens a pull request on **GitHub**, **Bitbucket** and **Azure DevOps**, and a merge
request on **GitLab**. It works out which one from the repository address, so there's no host
setting to get wrong. Content that isn't in a repository at all is written through the platform's
own interface. See [Where cross-links are delivered](guide/where-links-are-delivered.md).

## Can proposals go into Jira or ServiceNow instead?

They can go there **as well**. Kenaptic files a record of each proposed cross-link into Jira, a
ServiceNow table, or any endpoint you run, with a deep link back into the app.

What it won't do is treat that record as the decision. Closing the ticket does not approve or
publish the link — approval stays with a signed-in person in Kenaptic, with 2FA behind it, so the
audit trail can name a human rather than a workflow transition.

## Does Kenaptic remove personal data?

Yes, from everything it reads, before anything is stored. Email addresses, phone numbers, handles,
usernames and bylines are stripped at the moment a page is ingested — from every source, including
your own — so the working copy, the topic digests and every request that reaches a language model
are clean by construction rather than cleaned up afterwards. Nothing personal is ever part of a
prompt. See [How linking stays safe](concepts/safe-by-design.md).

## Can we connect a source without ever letting Kenaptic write to it?

Yes, and many estates run exactly this way. Marking a source as yours makes it a valid link
*destination* and lets Kenaptic map it; whether any link is ever written into it stays your
decision, link by link.

## Why does one of our sources show almost no pages?

Usually one of three things: a more specific source is legitimately claiming those pages (Kenaptic
assigns each page to exactly one source, so nothing is double-counted), the site's rules ask
crawlers not to read it, or the address needs checking. Kenaptic flags empty and thin sources rather
than averaging them into your estate figures — see
[When Kenaptic says no](guide/when-kenaptic-says-no.md).

## Why does the app sometimes say "not measured" instead of a number?

Because it can't answer that question yet, and a confident zero would be a lie. Content gaps need at
least one writable source to be measurable at all; orphan and siloed counts need a completed crawl.
Kenaptic tells you which it is.

## Can everyone on the team publish?

No — that's the point of roles. **Reviewers** can crawl, approve, edit and reject; **Admins** can
additionally publish, retract, and change sources and settings. Invite widely for review; keep
publishing with the people accountable for the live site.

## Is my data safe?

Kenaptic works from the public content of the pages you connect and is built to minimise personal
data. Every change is reviewed, marked, and reversible, and every decision is recorded in an audit
trail. See [How linking stays safe](concepts/safe-by-design.md) for the full picture.

## We still have a question.

Reach out to your Kenaptic contact — we're happy to help you get the most from your estate.
