# Where cross-links are delivered

Approving a cross-link decides *that* it should exist. This page is about *where the change turns
up* once you've approved it — the repository, the ticket, the endpoint your team actually watches.

Different teams work in different places, so Kenaptic delivers to several. What never changes is
who decided: **the approval always happens in Kenaptic, by a signed-in person.** Everything below
is delivery, not a second gate.

---

## Changes land in your repository

For docs-as-code content — a documentation site, handbook or blog built from Markdown in a
repository — Kenaptic opens a change the way one of your own engineers would.

| Host | How the change arrives |
|---|---|
| **GitHub** | A pull request |
| **GitLab** | A merge request |
| **Bitbucket** | A pull request |
| **Azure DevOps** | A pull request |

You don't pick the host from a menu. Kenaptic works it out from the repository address you gave it,
so it's impossible to select "GitHub" for a Bitbucket repository and then spend an afternoon
puzzling over an error from the wrong service.

!!! note "Branch or fork — Kenaptic checks, rather than assuming"
    For **your own** repository, a branch pushed straight to it is what you want: the proposal shows
    up in the repository your reviewers already watch. For a repository you **don't** own, a fork is
    the only correct route.

    Kenaptic tests what the credential you supplied is actually allowed to do, and takes the
    direct-branch route only when it can. A capability check beats a setting here, because a wrong
    setting fails at the very end — after the content has been read, the link written and the commit
    made — which is the most annoying possible moment to discover it.

Whichever route it takes, the change itself is identical: the same marked, reversible link block
described in [How linking stays safe](../concepts/safe-by-design.md). Re-running doesn't open a
second pull request for the same page — it updates the one already open.

## Content with no repository behind it

Plenty of good content isn't in git. A knowledge base, a CMS-hosted blog, a community platform.
Kenaptic writes to those through the platform's own official interface, using a credential you
create and control, and the same rules apply: marked, reversible, and only ever after approval.

On community platforms Kenaptic adds a **reply** pointing at the related page. It never edits
somebody's post — those words belong to the person who wrote them.

---

## Records in your ticketing system

Some teams need the proposal to appear in the system where their work is tracked and audited, not
only in Kenaptic. So Kenaptic can also **file a record** describing each proposed cross-link.

| Destination | Status | What arrives |
|---|---|---|
| **Jira** | Available | An issue in the project you choose, updated by comment as things change |
| **Generic webhook** | Available | A structured JSON payload to any endpoint you run |
| **ServiceNow** | Groundwork in place | A record on the table you nominate |

Each record carries the two pages, the relationship type, and a deep link straight back to the item
in Kenaptic. Delivery is **idempotent** — if the same proposal is delivered twice, you get one
ticket that gets updated, not a duplicate.

!!! warning "Delivery is one-way, on purpose"
    Kenaptic **does not read a status back**. Closing the Jira ticket does not approve the link, and
    resolving the ServiceNow record does not publish it.

    This is a deliberate line, not a missing feature. Approving a cross-link is the moment a change
    to your live content becomes real, and Kenaptic will only accept that instruction from an
    authenticated person in the app, with 2FA behind it. Anything else means the audit trail records
    a workflow transition rather than a human — and "the ticket was closed" is not an answer to
    "who approved this, and when?".

    Use the ticket for the things tickets are good at: scheduling, assignment, visibility, and the
    record your process needs. Use Kenaptic for the decision.

!!! info "What 'groundwork in place' means for ServiceNow"
    The ServiceNow path is built and will file a record, but every ServiceNow instance is customised
    — different tables, different mandatory fields, different approval flows. We've left a clear
    seam for those extra fields rather than guessing at a configuration nobody asked for. If you run
    ServiceNow and want this finished properly, talk to us: we'd rather build it against your actual
    instance than against our imagination of it.

---

## Before you publish: check there's a way through

A cross-link with nowhere to go is the worst kind of failure, because everything looks fine right
up to the end. Kenaptic therefore checks each destination **before** you publish, and shows a
warning marker in the preview list against any source that has no usable write path — no
credential, or no repository destination configured.

Hover it and Kenaptic tells you exactly what's missing. Fix it in **Domains**, or approve the link
anyway and leave it queued until the path exists — but you'll know either way, rather than finding
out from a publish that quietly did nothing.

---

## Choosing where things go

- **Your content is in git and your team reviews pull requests.** Use the repository path alone.
  It's the most direct route and the reviewers are already there.
- **Your content is in git, but a change to published docs must be tracked in Jira.** Use both: the
  pull request carries the change, the Jira issue carries the record.
- **Your content isn't in git.** Use the platform's own interface, and add a ticketing destination
  if your process needs one.
- **You have an internal workflow tool of your own.** Use the generic webhook and route the payload
  wherever you like.

---

## Next

- [Review & publish links](review-and-publish.md) — the approval step itself
- [Cross-link notifications](notifications.md) — telling your team there's something waiting
- [When Kenaptic says no](when-kenaptic-says-no.md) — the refusals and the reasons behind them
