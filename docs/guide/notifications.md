# Approval workflows & notifications

By default a link waits for a person to approve it. That safeguard only works if the right
person knows something is waiting — and the right person is usually the **owner of the domain**
the link would be written into, not whoever happens to be logged into Kenaptic.

An **approval workflow** belongs to a domain. It gives that domain's owners two things in the
tool they already have open:

- **Decisions** — approve or reject a proposed cross-link from Slack, a webhook-connected tool,
  or their inbox, **without a Kenaptic login**.
- **Notifications** — short messages when something on that domain needs attention, with a link
  straight to the right page.

One destination per domain, both jobs.

## Why this is safe to do outside the app

A decision can only **accept or reject a link Kenaptic has already proposed** between two pages
of your own estate. No message, callback or emailed link can introduce a URL of its own, change
what a link says, or touch a page — the worst any of them can do is answer yes or no to a
question Kenaptic already asked. And approved links still wait for an administrator to deploy
them; nothing publishes from a chat click alone.

Who may answer is fixed by you, in advance: each workflow carries a list of **approvers**, named
by an administrator on the domain record. A click from anyone else is politely refused and
changes nothing. That is why a legitimate approver never sees a login form — the identity
question was settled when you named them.

## Setting one up

When you **add a domain**, the last step of the wizard offers the approval workflow. You can
skip it — and add one later from the domain's record — or remove one at any time without
affecting the domain's crawling or cross-link publishing.

For an existing domain: **Domains → open the domain → Approval workflow**.

1. Pick the tool: **Slack**, **Webhook** (any tool that accepts one), or **Email**.
2. Fill in what that tool genuinely needs — the form only asks for what it can't know:

   | Tool | You provide |
   |---|---|
   | **Slack** (push) | The channel's incoming webhook URL and your Slack app's signing secret |
   | **Slack** (pull) | A bot token and the channel ID — for networks where Slack can't call in; approvers decide with ✅ / ❌ reactions |
   | **Discord** (push) | A bot token, the channel ID, and your app's public key — approvers decide with buttons |
   | **Discord** (pull) | A bot token and the channel ID; approvers decide with ✅ / ❌ reactions |
   | **Webhook** | The URL Kenaptic posts to and a shared secret |
   | **Email** | Nothing — the mail goes to the approvers you name |

   For Discord push, set the app's *Interactions Endpoint URL* to the address shown on the
   form; Kenaptic answers Discord's validation handshake automatically. Approvers are Discord
   user IDs. Microsoft Teams is reachable through the **Webhook** tool via a Power Automate
   Workflows flow (Office 365 connectors are retired).

3. Name the **approvers** — Slack member IDs, email addresses, or whatever identity your tool
   reports. For email, the approvers *are* the recipients, and each person's message carries
   single-use Approve / Reject links tied to them, so the decision is recorded in their name.
4. Tick which **notifications** should also go to this destination.

!!! note "Your webhook URL is a credential"
    A webhook URL contains its own secret token — anyone holding it can post into that channel.
    Kenaptic stores it like a password and never shows it again after you save it. Leaving the
    field blank keeps the one already stored.

## Choosing what you're told about

Notifications are only useful if they're rare enough to be believed. Per domain workflow, you
choose which events are worth interrupting someone for:

| Event | Sent when |
|---|---|
| **Cross-links awaiting review** | New suggested links have entered the review queue |
| **Contradictions found** | A scan found pages that state conflicting things |
| **Injection deployed** | Approved links were published back to your content |
| **A domain refused crawling** | A source blocked Kenaptic, so its content is missing |

## Asking for a decision

From the review queue, any reviewer can press **Send for approval** on a proposed link. The
domain's approvers get the request in their tool; their answer lands in Kenaptic exactly as if
it had been decided in the console, attributed to the person who gave it. Sending the same
request twice doesn't post twice — Kenaptic tells you it's already awaiting a decision, and a
deliberate *Re-send* invalidates the links in the earlier message first.

## If a channel stops working

A broken channel never affects your content. Delivery happens separately from the work itself,
so an expired webhook or an unreachable mail server can't block discovery, hold up a review, or
stop a link being published. Kenaptic reports the failure so you can fix it.

## Next

- [The review loop](../getting-started/the-review-loop.md) — what happens around a decision
- [Settings & account](settings.md) — the rest of your configuration
