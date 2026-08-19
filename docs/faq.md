# Frequently asked questions

## What kinds of content can Kenaptic connect?

Documentation sites, knowledge bases, blogs, whitepapers and guides, community forums, and
discussion boards. Most content your audience can read can be mapped and linked to. Sources you
own can also receive links; sources you don't own are read-only link destinations.

## Does Kenaptic change content without review?

No, unless you enable it. By default every proposed link and every fix goes through a review
where a person on your team approves, edits, or rejects it.

The exception is **auto-publish**, which only a workspace administrator can enable, per source,
for links above a confidence threshold you set. It is off by default, the app shows a warning
when it is enabled, and we recommend leaving it off. See
[Safety model](concepts/safe-by-design.md).

## Can I undo a link Kenaptic added?

Yes. Every link Kenaptic publishes is marked as its own and can be retracted cleanly, restoring
the page to its previous state.

## Does Kenaptic copy content from forums into my pages?

No. For a forum thread or discussion, Kenaptic adds a link that points readers to the original.
Third-party content is never republished into your pages.

## Does Kenaptic respect a site's crawling rules?

Yes. Kenaptic follows each site's stated crawling and usage policies. Sites that ask not to be
crawled are not crawled.

## How does Kenaptic decide which links to propose?

Kenaptic analyses your content, identifies how pages relate across silos, and proposes candidate
links, each with a relationship type and a confidence indicator. The details of the method are
Kenaptic's own. Every proposal is shown in full for review.

## Will the links help with search engines and AI assistants?

Yes. Kenaptic writes native links into the page source rather than overlays or scripts, so the
links are visible to every visitor, every search crawler, and every AI assistant that reads your
pages. The **AI Readiness** page tracks how machine-friendly your estate is and how to improve
it.

## How is Kenaptic priced?

By the size of the content estate you keep connected: the number of sources and the volume of
content. Seats are unlimited; pricing does not depend on the number of users, so you can invite
your whole team.

## Who should be in our Kenaptic workspace?

Anyone responsible for part of the content estate: documentation writers, support and
knowledge-base leads, and the web team. Wider reviewer coverage produces a better-connected
estate.

## How quickly do results appear?

Connect two or three closely related sources and cross-link proposals start arriving quickly.
Approving even a few strong links improves how readers move between silos; a full rollout is not
a prerequisite.

## Which repository hosts are supported besides GitHub?

Kenaptic opens a pull request on GitHub, Bitbucket, and Azure DevOps, and a merge request on
GitLab. The host type is detected from the repository address; there is no host setting to
configure. Content that isn't in a repository at all is written through the platform's own
interface. See [Where cross-links are delivered](guide/where-links-are-delivered.md).

## Can proposals go into Jira or ServiceNow instead?

Yes, in addition to the review queue. Kenaptic files a record of each proposed cross-link into
Jira, a ServiceNow table, or any endpoint you run, with a deep link back into the app.

Delivery is one-way. Closing the ticket does not approve or publish the link; approval happens
in Kenaptic by a signed-in person with 2FA behind it, so the audit trail records a person rather
than a workflow transition.

## Does Kenaptic remove personal data?

Yes. Email addresses, phone numbers, handles, usernames, and bylines are stripped at the moment
a page is ingested, before anything is stored. This applies to every source, including your own.
The working copy, the topic digests, and every request that reaches a language model contain no
personal data. See [Safety model](concepts/safe-by-design.md).

## Can we connect a source without ever letting Kenaptic write to it?

Yes; many estates run this way. Marking a source as yours makes it a valid link destination and
lets Kenaptic map it. Whether any link is ever written into it stays your decision, link by
link.

## Why does one of our sources show almost no pages?

Usually one of three causes: a more specific source is legitimately claiming those pages
(Kenaptic assigns each page to exactly one source, so nothing is double-counted), the site's
rules ask crawlers not to read it, or the address needs checking. Kenaptic flags empty and thin
sources rather than averaging them into your estate figures. See
[When a value cannot be measured](guide/when-kenaptic-says-no.md).

## Why does the app report "not measured" instead of a number?

A value is reported as "not measured" when it cannot yet be computed; a zero in that case would
be inaccurate. Content gaps need at least one writable source to be measurable. Orphan and
siloed counts need a completed crawl. The app states which condition applies.

## Can everyone on the team publish?

No. **Reviewers** can crawl, approve, edit, and reject. **Admins** can additionally publish,
retract, and change sources and settings. Invite widely for review; restrict publishing to the
people accountable for the live site.

## Is my data safe?

Kenaptic works from the public content of the pages you connect and minimises the personal data
it holds. Every change is reviewed, marked, and reversible, and every decision is recorded in an
audit trail. See [Safety model](concepts/safe-by-design.md).

## Further questions

For anything not covered here, contact your Kenaptic representative.
