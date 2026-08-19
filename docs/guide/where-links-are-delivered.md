# Where cross-links are delivered

Approving a cross-link decides that it should exist. This page covers where the resulting change
is delivered once approved: the repository, the ticket, or the endpoint your team watches.

Kenaptic delivers to several kinds of destination because teams work in different places. In
every case the approval itself happens in Kenaptic, by a signed-in person. The destinations below
deliver the change; none of them acts as a second approval gate.

---

## Repository delivery

For docs-as-code content (a documentation site, handbook, or blog built from Markdown in a
repository), Kenaptic opens a change through the host's standard review mechanism.

| Host | How the change arrives |
|---|---|
| **GitHub** | A pull request |
| **GitLab** | A merge request |
| **Bitbucket** | A pull request |
| **Azure DevOps** | A pull request |

The host is not selected from a menu. Kenaptic detects it from the repository address you supply,
so a mismatch between a selected host and the actual repository cannot be configured.

!!! note "Branch or fork"
    For a repository you own, a branch pushed directly to it is the correct route: the proposal
    appears in the repository your reviewers already watch. For a repository you do not own, a
    fork is the only correct route.

    Kenaptic tests what the supplied credential is allowed to do and takes the direct-branch
    route only when the credential permits it. A capability check is used instead of a setting
    because a wrong setting fails at the end of the run, after the content has been read, the
    link written, and the commit made.

Both routes deliver an identical change: the same marked, reversible link block described in
[the safety model](../concepts/safe-by-design.md). Re-running does not open a second pull request
for the same page; it updates the one already open.

## Content without a repository

Content that is not in git (a knowledge base, a CMS-hosted blog, a community platform) is written
through the platform's own official interface, using a credential you create and control. The
same rules apply: changes are marked, reversible, and made only after approval.

On community platforms Kenaptic adds a reply pointing at the related page. It never edits an
existing post.

---

## Ticketing system records

Kenaptic can file a record describing each proposed cross-link in a ticketing system, for teams
whose process requires proposals to appear where work is tracked and audited.

| Destination | Status | What arrives |
|---|---|---|
| **Jira** | Available | An issue in the project you choose, updated by comment as things change |
| **Generic webhook** | Available | A structured JSON payload to any endpoint you run |
| **ServiceNow** | Groundwork in place | A record on the table you nominate |

Each record carries the two pages, the relationship type, and a deep link back to the item in
Kenaptic. Delivery is **idempotent**: delivering the same proposal twice updates the existing
ticket rather than creating a duplicate.

!!! warning "One-way delivery"
    Kenaptic does not read a status back. Closing the Jira ticket does not approve the link, and
    resolving the ServiceNow record does not publish it.

    This is deliberate. Approving a cross-link changes your live content, and Kenaptic accepts
    that instruction only from an authenticated person in the app, with 2FA. Accepting approval
    from a ticket transition would leave the audit trail recording a workflow event rather than
    the person who approved the change and when.

    Tickets remain the place for scheduling, assignment, visibility, and the record your process
    needs. The approval decision itself stays in Kenaptic.

!!! info "ServiceNow status"
    The ServiceNow path is built and will file a record. ServiceNow instances vary widely:
    different tables, different mandatory fields, different approval flows. The integration
    leaves a seam for those instance-specific fields rather than assuming a configuration. If
    you run ServiceNow and want the integration completed against your instance, contact us.

---

## Pre-publish destination checks

Kenaptic checks each destination before you publish. Any source with no usable write path (no
credential, or no repository destination configured) is marked with a warning in the preview
list.

Hovering the marker shows exactly what is missing. Fix the configuration in **Domains**, or
approve the link anyway and leave it queued until the path exists. Either way, the missing path
is surfaced before publish rather than by a publish that delivers nothing.

---

## Choosing destinations

- Content in git, with pull-request review: use the repository path alone. It is the most direct
  route, and the reviewers are already there.
- Content in git, with changes to published docs tracked in Jira: use both. The pull request
  carries the change; the Jira issue carries the record.
- Content not in git: use the platform's own interface, and add a ticketing destination if your
  process needs one.
- An internal workflow tool of your own: use the generic webhook and route the payload wherever
  you need it.

---

## Next

- [Review & publish links](review-and-publish.md) — the approval step
- [Approval workflows & notifications](notifications.md) — routing pending approvals to the
  right people
- [Refusal conditions](when-kenaptic-says-no.md) — actions Kenaptic declines to perform, and why
