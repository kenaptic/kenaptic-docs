# Settings & account

**Settings** is where you tune your workspace, manage your team, and handle your account. You'll set
it up once and revisit it occasionally.

## Your team

Invite the people who'll work in Kenaptic — documentation writers, support leads, web team. Seats
are unlimited, so there's no reason to leave anyone out. Each person signs in with their own
credentials and two-factor authentication.

Each person also has a **role**. The line Kenaptic draws is not read versus write — it's **review
versus publish**:

| | Reviewer | Admin |
|---|---|---|
| Read the estate, graph and reports | ✅ | ✅ |
| Run a crawl or a scoring pass | ✅ | ✅ |
| Approve, edit and reject proposed links | ✅ | ✅ |
| **Publish** approved links to live content | — | ✅ |
| **Retract** something already published | — | ✅ |
| Add, remove or re-point a source | — | ✅ |
| Change workspace settings | — | ✅ |

Reviewing is the job you want lots of people doing: it's internal, reversible, and the more eyes on
it the better. Publishing is the moment a change becomes public, so it sits with administrators.

A reviewer can work through the whole queue and their approvals are saved — an administrator
deploys them. When someone hits a limit, Kenaptic says which role can do it, rather than just
refusing, so they know who to ask.

## Projects

If your workspace covers more than one product, group its sources into **projects**. A project keeps
each product's estate distinct, so its numbers mean something on their own and reviewers aren't
wading through another team's queue.

By default Kenaptic proposes links **within** a project. Where two products genuinely relate, you
can allow cross-project links deliberately rather than by accident.

## Security

- **Two-factor authentication (2FA)** is required for every account. You can manage your own 2FA
  from Settings — for example, if you get a new phone.
- **Protected actions.** Sensitive changes — like connecting a new source — ask you to confirm with
  your 2FA, so nothing significant happens without a deliberate, verified step.

## Where things get delivered

Configure the repositories, ticketing destinations and endpoints that receive approved cross-links.
See [Where cross-links are delivered](where-links-are-delivered.md) for what each one does and why
none of them can approve anything.

## Contribution

If you want to propose links into projects you *don't* own, turn on upstream mode here — it changes
the rules rather than the settings. See
[Contribute to projects you don't own](contributing-upstream.md).

## How Kenaptic reviews your estate

You can influence how Kenaptic works across your content — for example, how often it re-checks your
sources for changes, and how it presents the confidence on proposed links. Sensible defaults are in
place from day one; adjust them as you learn what fits your team's rhythm.

## Billing

Manage your plan and billing from Settings. Kenaptic is priced on the **size of the content estate**
you keep connected — the number of sources and the volume of content — not on the number of people
using it. As you connect more of your estate, your plan scales with it.

## Getting content out of Kenaptic

Kenaptic isn't a walled garden. You can export what it knows — for reporting, for feeding other
tools, or simply to keep your own copy — so the value stays yours.

---

That's the tour. If you're after the *why* behind how Kenaptic behaves, read
[**How linking stays safe**](../concepts/safe-by-design.md), or keep the
[**Glossary**](../concepts/glossary.md) handy for any unfamiliar terms.
