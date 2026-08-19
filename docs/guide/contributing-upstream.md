# Upstream contributions

Most of Kenaptic assumes you are improving your own documentation. Sometimes the content that
would help your readers most sits in a project you don't control: an open-source tool you build
on, a partner's documentation, a community-maintained handbook.

**Upstream mode** lets Kenaptic propose cross-links into those repositories the way any other
contributor would: as a pull request, from a fork, that a maintainer reviews and decides on.

Turn it on in **Settings → Contribution**.

---

## Upstream mode rules

The assumptions that hold for your own estate do not hold for someone else's, so upstream mode
changes these rules:

| | Your own docs | Upstream |
|---|---|---|
| How a change arrives | A branch pushed to your repository | A pull request from a fork |
| Who decides | Your team | The project's maintainers |
| Link tracking | Optional | Unavailable; cannot be enabled |
| Auto-publish | Available, not recommended | Unavailable; cannot be enabled |
| Sign-off | Not required | A DCO sign-off on every commit |
| How much at once | Your call | Capped, and spread out |

!!! warning "Upstream mode switches auto-publish off everywhere"
    The two cannot both be on. Kenaptic lists which sources it changed, and any links
    auto-publish had approved but not yet deployed return to the review queue.

    On your own documentation, the worst case for auto-publish is a weak link on a page you
    control, retractable in one click. Upstream, neither safeguard applies. A maintainer who
    receives automated pull requests nobody read stops accepting them, and a DCO sign-off is a
    named person asserting they have the right to submit the change, so signing off work that
    person never saw makes the assertion false. Retracting a link undoes neither.

    Switching back preserves your DCO identity, permitted organisations and volume caps, so
    re-enabling upstream mode restores the same guardrails.

---

## Before your first contribution

Name a real person for the sign-off. Most open-source projects require a Developer Certificate
of Origin: a statement that the person submitting a change has the right to submit it. That is
an assertion by a human being, so it cannot be an automated identity. Kenaptic asks for a name
and email and puts them on every commit.

List the organisations you intend to contribute to. Kenaptic refuses to open a pull request
anywhere else. Because of how forks work on GitHub, a single mistyped repository name could
otherwise send an unsolicited pull request to a project nobody chose. An empty list permits
nothing, so the default is to deny.

---

## Pre-proposal checks

- **Automated-contribution policy.** Some projects state in their contributing guide that they
  do not accept automated contributions. Kenaptic reads the guide and stops before creating a
  fork, quoting the sentence it found.
- **CLA requirement.** A Contributor License Agreement is signed by a person or organisation,
  out of band. Kenaptic cannot sign one, so it warns you before a pull request opens rather
  than leaving one stuck failing a check.
- **File, repository and version validity.** Generated pages, translations, frozen releases and
  content synced from elsewhere are all declined; see
  [Safety model](../concepts/safe-by-design.md).

---

## Maintainer interaction

- **One pull request per repository.** However many pages and sources are involved, Kenaptic
  opens a single pull request per repository, not one per source.
- **Capped size.** A pull request touching two hundred files will not get reviewed. Kenaptic
  limits how many pages go into one request, holds the rest for the next run, and reports what
  it held back, so a capped run is distinguishable from a finished one.
- **Idempotent re-runs.** If the content did not change, a re-run leaves the pull request as it
  is: no force-push, no new notifications, no CI re-run.
- **Closed pull requests stay closed.** If a maintainer closes a pull request without merging
  it, Kenaptic does not open another one on the next run. Automated systems that re-propose
  after a refusal get excluded from projects, so re-proposing is off by default and must be
  enabled deliberately.
- **Withdrawal.** Retracting closes the pull request and removes the branch. Nothing was
  published on the project's site, so nothing remains afterwards.

---

## Grouping properties by project

A single project often publishes in several places at once: documentation, a blog, a wiki, a
proposals repository. Grouping them lets you:

- review one project at a time instead of everything at once;
- set what that project asked for: how many links per page, which kinds, how they appear;
- pause a project while it is mid-restructure. It stays readable and linkable; Kenaptic stops
  proposing changes to it.

Anything a project asked for that Kenaptic then declined to propose is reported, so a run
constrained by the project's limits is distinguishable from a run that found nothing.

---

## Maintainer reports

Maintainers won't have a Kenaptic login, and a pull request shows only the change itself.
Kenaptic can produce a plain report for a project: how many links were proposed, how many are
live, how many candidates were discarded, and how to stop or reverse any of it. The report is
written to be pasted into an issue or an email, carries no branding, and includes unfavourable
numbers alongside favourable ones.
