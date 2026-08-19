# Settings & account

**Settings** covers workspace configuration, team management, and your account.

## Team

Invite the people who will work in Kenaptic: documentation writers, support leads, web team. Seats
are unlimited. Each person signs in with their own credentials and two-factor authentication.

Each person has a **role**. The permission boundary sits between reviewing and publishing, not
between reading and writing:

| | Reviewer | Admin |
|---|---|---|
| Read the estate, graph and reports | ✅ | ✅ |
| Run a crawl or a scoring pass | ✅ | ✅ |
| Approve, edit and reject proposed links | ✅ | ✅ |
| Publish approved links to live content | — | ✅ |
| Retract something already published | — | ✅ |
| Add, remove or re-point a source | — | ✅ |
| Change workspace settings | — | ✅ |

Review actions are internal and reversible, so the Reviewer role is safe to grant widely; more
reviewers means more scrutiny per link. Publishing makes a change public, so it is restricted to
administrators.

A reviewer can work through the whole queue. Approvals are saved, and an administrator deploys
them. When an action is outside someone's role, the message names the role that can perform it, so
they know who to ask.

## Projects

If your workspace covers more than one product, group its sources into **projects**. A project
keeps each product's estate distinct: each product's numbers are reported on their own, and one
team's review queue is not mixed with another's.

By default Kenaptic proposes links within a project. Where two products relate, you can enable
cross-project links explicitly.

## Security

- **Two-factor authentication (2FA)** is required for every account. You can manage your own 2FA
  from Settings, for example after getting a new phone.
- **Protected actions.** Sensitive changes, such as connecting a new source, require confirmation
  with your 2FA.

## Delivery destinations

Configure the repositories, ticketing destinations and endpoints that receive approved cross-links.
See [Where cross-links are delivered](where-links-are-delivered.md) for what each destination does.
No destination can approve a link.

## Contribution

To propose links into projects you do not own, enable **upstream mode** here. The workflow it
changes is described in [Contribute to projects you don't own](contributing-upstream.md).

## Estate review settings

These settings control how Kenaptic processes your content: how often sources are re-checked for
changes, and how the confidence on proposed links is presented. Defaults are set for every
workspace; adjust them to fit your team's workflow.

## Billing

Manage your plan and billing from Settings. Pricing is based on the size of the content estate you
keep connected (the number of sources and the volume of content), not on the number of people using
it. Plans scale with the estate you connect.

## Data export

You can export the data Kenaptic holds about your estate: for reporting, for feeding other tools,
or to keep your own copy.

---

For the reasoning behind these behaviors, see [the safety model](../concepts/safe-by-design.md).
Terms are defined in the [Glossary](../concepts/glossary.md).
